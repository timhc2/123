graph TD
    %% 定义样式
    classDef macro fill:#f9f7fb,stroke:#d1c4e9,stroke-width:2px,color:#4a148c;
    classDef core fill:#e3f2fd,stroke:#90caf9,stroke-width:2px,color:#0d47a1;
    classDef channel fill:#e8f5e9,stroke:#a5d6a7,stroke-width:2px,color:#1b5e20;
    classDef audience fill:#fff3e0,stroke:#ffcc80,stroke-width:2px,color:#e65100;
    classDef feedback stroke:#ffab91,stroke-width:2px,stroke-dasharray: 5 5,color:#bf360c;

    %% --- 最外层：宏观生态环境（文明互鉴视域） ---
    subgraph MacroEnv [宏观生态环境：文明互鉴与地缘政治场域]
        direction TB
        PolicyCN[中国文化走出去政策<br>指标：资助项目数量/丝路书香工程]
        PolicyKR[韩国文化产业振兴政策<br>指标：引进扶持资金/出版审查尺度]
        Relations[中韩地缘政治关系<br>指标：外交事件/民间情绪指数]
    end
    class PolicyCN,PolicyKR,Relations macro;

    %% --- 中间层：译介生产核心（中介与转化） ---
    subgraph ProductionCore [译介生产核心：符号资本转化]
        direction LR
        SourceCN[中国文学源头<br>指标：作家知名度/国内奖项/IP热度]
        Translator[译者：文化摆渡人<br>指标：译者声望/翻译策略(归化异化比)/改写度]
        PublisherKR[韩国出版机构：守门人<br>指标：出版社层级/选题偏好/营销预算占比]
        
        SourceCN -->|版权输出| PublisherKR
        SourceCN -->|文本提供| Translator
        Translator -->|译本交付| PublisherKR
    end
    class SourceCN,Translator,PublisherKR core;
    
    MacroEnv -.->|规约与引导| ProductionCore

    %% --- 渠道层：多元传播模式（分发与触达） ---
    subgraph Channels [多元传播模式矩阵：媒介融合]
        direction TB
        PrintMedia[传统纸媒传播<br>指标：首印数/重印率/书店上架率/图书馆借阅量]
        DigitalPlatform[数字平台传播 (Naver/Kakao)<br>指标：点击量/订阅数/付费率/算法推荐频次]
        TransMedia[跨媒介IP联动 (影游漫)<br>指标：改编视听收视率/票房/原著销量转化率]
    end
    class PrintMedia,DigitalPlatform,TransMedia channel;

    PublisherKR -->|经典化路径| PrintMedia
    PublisherKR -->|快餐化路径| DigitalPlatform
    PublisherKR -->|IP化运作| TransMedia

    %% --- 底层：受众接受与反馈（共鸣与误读） ---
    subgraph AudienceFeedback [受众接受与动态反馈系统]
        direction TB
        KoreanReaders[韩国大众读者<br>指标：评分均值/评论情感倾向(正负比)/关键词云]
        EliteCritics[学术与媒体精英<br>指标：书评发表数/学术论文引用率/媒体曝光度]
        CulturalResonance[文化共振与折扣<br>指标：议题相关性(如内卷、职场)/文化理解障碍点]
    end
    class KoreanReaders,EliteCritics,CulturalResonance audience;

    Channels -->|触达| KoreanReaders
    Channels -->|触达| EliteCritics
    KoreanReaders --> CulturalResonance
    EliteCritics --> CulturalResonance

    %% --- 反馈回路 ---
    CulturalResonance -.->|市场信号反馈| PublisherKR
    CulturalResonance -.->|阅读期待反馈| Translator
    KoreanReaders -.->|大数据反哺算法| DigitalPlatform

    linkStyle 13,14,15,16 stroke:#ff5722,stroke-width:2px,fill:none,stroke-dasharray: 5 5;
