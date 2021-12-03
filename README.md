# 快手磁力引擎MarketingAPI Golang SDK

[![Go Reference](https://pkg.go.dev/badge/github.com/bububa/kwai-marketing-api.svg)](https://pkg.go.dev/github.com/bububa/kwai-marketing-api)
[![Go](https://github.com/bububa/kwai-marketing-api/actions/workflows/go.yml/badge.svg)](https://github.com/bububa/kwai-marketing-api/actions/workflows/go.yml)
[![goreleaser](https://github.com/bububa/kwai-marketing-api/actions/workflows/goreleaser.yml/badge.svg)](https://github.com/bububa/kwai-marketing-api/actions/workflows/goreleaser.yml)
[![GitHub go.mod Go version of a Go module](https://img.shields.io/github/go-mod/go-version/bububa/kwai-marketing-api.svg)](https://github.com/bububa/kwai-marketing-api)
[![GoReportCard](https://goreportcard.com/badge/github.com/bububa/kwai-marketing-api)](https://goreportcard.com/report/github.com/bububa/kwai-marketing-api)
[![GitHub license](https://img.shields.io/github/license/bububa/kwai-marketing-api.svg)](https://github.com/bububa/kwai-marketing-api/blob/master/LICENSE)
[![GitHub release](https://img.shields.io/github/release/bububa/kwai-marketing-api.svg)](https://GitHub.com/bububa/kwai-marketing-api/releases/)
# Kwai Marketing Api


- Oauth2 授权 (api/oauth)
    - 生成授权链接 [ Url(clt *core.SDKClient, req *oauth.UrlRequest) string ]
    - 获取AccessToken [ AccessToken(clt *core.SDKClient, authCode String) (*oauth.AccessTokenResponse, error) ]
    - 刷新Token [ RefreshToken(clt *core.SDKClient, refreshToken string) (*oauth.AccessTokenResponse, error)]
- 账号服务
    - 广告主 (api/advertiser)
        - 获取广告主信息 [ Info(clt *core.SDKClient, accessToken string, advertiserID int64) (*advertiser.Info, error) ]
        - 获取广告账户余额信息 [ FundGet(clt *core.SDKClient, accessToken string, advertiserID int64) (float64, error) ]
        - 获取广告主账户流水信息 [ FundDailyFlows(clt *core.SDK, accessToken string, req *advertiser.FundDailyFlowsRequest) (*advertiser.FundDailyFlowsResponse, error) ]
- 广告投放
    - 获取各层级信息
        - 获取广告计划信息 [ campaign.List(clt *core.SDKClient, accessToken string, req *campaign.ListRequest) (*campaign.ListResponse, error) ]
        - 获取广告组信息 [ unit.List(clt *core.SDKClient, accessToken string, req *unit.ListRequest) (*unit.ListResponse, error) ]
        - 获取广告创意信息 [ creative.List(clt *core.SDKClient, accessToken string, req *creative.ListRequest) (*creative.ListResponse, error) ]
        - 获取程序化创意2.0信息 [ creative.AdvancedProgramList(clt *core.SDKClient, accessToken string, req *creative.AdvancedProgramListRequest) (*creative.AdvancedProgramListResponse, error) ]
        - 获取程序化创意2.0审核信息 [ creative.AdvancedProgramReviewDetail(clt *core.SDKClient, accessToken string, req *creative.AdvancedProgramReviewDetailRequest) (*creative.AdvancedProgramReviewDetail, error) ]
        - 账户操作记录信息查询 [ tool.OperationRecordList(clt *core.SDKClient, accessToken string, req *tool.OperationRecordListRequest) (*tool.OperationRecordListResponse, error) ]
        - 定向人群预估查询 [ tool.AudiencePredict(clt *core.SDKClient, accessToken string, req *tool.AudiencePredictRequest) (int64, error) ]
    - 账户层级
        - 账户日预算查询 [ advertiser.BudgetGet(clt *core.SDKClient, accessToken string, advertiserID int64) (*advertiser.Budget, error) ]
        - 修改账户预算 [ advertiser.UpdateBudget(clt *core.SDKClient, accessToken string, req *advertiser.UpdateBudgetRequest) error ]
    - 广告计划(api/campaign)
        - 创建广告计划 [ Create(clt *core.SDKClient, accessToken string, req *campaign.CreateRequest) (int64, error) ]
        - 修改广告计划 [ Update(clt *core.SDKClient, accessToken string, req *campaign.UpdateRequest) (int64, error) ]
        - 修改广告计划预算 [ UpdateBudget(clt *core.SDKClient, accessToken string, req *campaign.UpdateBudgetRequest) error ]
        - 修改广告计划状态 [ UpdateStatus(clt *core.SDKClient, accessToken string, req *campaign.UpdateStatusRequest) ([]int64, error) ]
    - 广告组(api/unit)
        - 创建广告组 [ Create(clt *core.SDKClient, accessToken string, req *unit.CreateRequest) (int64, error) ]
        - 创建创建联盟定投广告组 [ CreateUnion(clt *core.SDKClient, accessToken string, req *unit.CreateUnionRequest) (int64, error) ]
        - 修改广告组 [ Update(clt *core.SDKClient, accessToken string, req *unit.UpdateRequest) (int64, error) ]
        - 修改联盟定投广告组 [ UpdateUnion(clt *core.SDKClient, accessToken string, req *unit.UpdateUnionRequest) (int64, error) ]
        - 修改广告组预算 [ UpdateDayBudget(clt *core.SDKClient, accessToken string, req *unit.UpdateDayBudgetRequest) error ]
        - 修改广告组状态 [ UpdateStatus(clt *core.SDKClient, accessToken string, req *unit.UpdateStatusRequest) ([]int64, error) ]
        - 修改广告组出价 [ UpdateBid(clt *core.SDKClient, accessToken string, req *unit.UpdateBidRequest) error ]
    - 广告创意(api/creative)
        - 创建创意 [ Create(clt *core.SDKClient, accessToken string, req *creative.CreateRequest) (int64, error) ]
        - 创建程序化2.0创意 [ AdvancedProgramCreate(clt *core.SDKClient, accessToken string, req *creative.AdvancedProgramCreateRequest) (int64, error) ]
        - 批量创建&修改创意 [ BatchUpdate(clt *core.SDKClient, accessToken string, req *creative.BatchUpdateRequest) (*creative.BatchUpdateResponse, error) ]
        - 修改创意 [ Update(clt *core.SDKClient, accessToken string, req *creative.UpdateRequest) (int64, error) ]
        - 修改程序化2.0创意 [ AdvancedProgramUpdate(clt *core.SDKClient, accessToken string, req *creative.AdvancedProgramUpdateRequest) error ]
        - 修改创意状态 [ UpdateStatus(clt *core.SDKClient, accessToken string, req *creative.UpdateStatusRequest) ([]int64, error) ]
        - 创意体验 [ Preview(clt *core.SDKClient, accessToken string, req *creative.PreviewRequest) error ]
        - 创意标签填写建议 [ CreativeTagAdvise(clt *core.SDKClient, accessToken string, req *creative.CreativeTagAdviseRequest) (*creative.CreativeTagAdviseResponse, error) ]
    - 高级创意(api/asset)
        - 获取高级创意列表 [ AdvCardList(clt *core.SDKClient, accessToken string, req *asset.AdvCardListRequest) (*asset.AdvCardListResponse, error) ]
        - 创建高级创意接口 [ AdvCardCreate(clt *core.SDKClient, accessToken string, req *asset.AdvCardCreateRequest) ([]int64, error) ]
        - 删除高级创意接口 [ AdvCardRemove(clt *core.SDKClient, accessToken string, req *asset.AdvCardRemoveRequest) ([]int64, error) ]
- 数据报表
    - 广告数据报表 (api/report)
        - 代理商数据 [ AgentReport(clt *core.SDKClient, accessToken string, req *report.AgentReportRequest) (*report.AgentReportResponse, error) ]
        - 广告主数据 [ AccountReport(clt *core.SDKClient, accessToken string, req *report.AccountReportRequest) (*report.ReportResponse, error) ]
        - 广告计划数据 [ CampaignReport(clt *core.SDKClient, accessToken string, req *report.CampaignReportRequest) (*report.ReportResponse, error) ]
        - 广告单元数据 [ UnitReport(clt *core.SDKClient, accessToken string, req *report.UnitReportRequest) (*report.ReportResponse, error) ]
        - 广告创意数据 [ CreativeReport(clt *core.SDKClient, accessToken string, req *report.CreativeReportRequest) (*report.ReportResponse, error) ]
        - 程序化创意数据 [ ProgramCreativeReport(clt *core.SDKClient, accessToken string, req *report.ProgramCreativeReportRequest) (*report.ReportResponse, error) ]
        - 广告素材数据 [ CreativeReport(clt *core.SDKClient, accessToken string, req *report.MaterialReportRequest) (*report.ReportResponse, error) ]
        - 人群分析数据 [ AudienceReport(clt *core.SDKClient, accessToken string, req *report.AudienceReportRequest) (*report.ReportResponse, error) ]
        - 小店通转化数据 [ MerchantDeatailReport(clt *core.SDKClient, accessToken string, req *report.MerchantDetailReportRequest) (*report.MerchantDetailReportResponse, error) ]
- 素材管理(api/file)
    - 图片素材
        - 上传图片v1接口 [ AdImageUploadV1(clt *core.SDKClient, accessToken string, req *file.AdImageUploadRequestV1) (*file.Image, error) ]
        - 上传图片v2接口 [ AdImageUploadV2(clt *core.SDKClient, accessToken string, req *file.AdImageUploadRequestV2) (*file.Image, error) ]
        - 查询图片信息get接口 [ AdImageGet(clt *core.SDKClient, accessToken string, req *file.AdImageGetRequest) (*file.Image, error) ]
        - 查询图片信息list接口 [ AdImageList(clt *core.SDKClient, accessToken string, req *file.AdImageListRequest) (*file.AdImageListResponse, error) ]
    - 视频素材
        - 上传视频接口v1 [ AdVideoUploadV1(clt *core.SDKClient, accessToken string, req *file.AdVideoUploadRequestV1) (string, error) ]
        - 上传视频接口v2 [ AdVideoUploadV2(clt *core.SDKClient, accessToken string, req *file.AdVideoUploadRequestV2) (*file.Video, error) ]
        - 获取视频信息get接口 [ AdVideoGet(clt *core.SDKClient, accessToken string, req *file.AdVideoGetRequest) ([]file.Video, error) ]
        - 查询视频信息list接口 [ AdVideoList(clt *core.SDKClient, accessToken string, req *file.AdVideoListRequest) (*file.AdVideoListResponse, error) ]
    - 视频库
        - 视频库-推送视频 [ AdVideoShare(clt *core.SDKClient, accessToken string, req *file.AdVideoShareRequest) ([]file.AdVideoShareDetail, error) ]
        - 视频库-批量更新视频功能 [ AdVideoUpdate(clt *core.SDKClient, accessToken string, req *file.AdVideoUpdateRequest) error ]
        - 视频库-删除视频标签 [ AdVideoTagDelete(clt *core.SDKClient, accessToken string, req *file.AdVideoTagDeleteRequest) error ]
        - 视频关联创意数查询 [ AdVideoRelateCreatives(clt *core.SDKClient, accessToken string, req *file.AdVideoRelateCreativesRequest) ([]file.AdVideoRelatedCreatives, error) ]
- 工具
    - 查询工具
        - 获取可选的深度转化目标 [ unit.OcpcConversionInfos(clt *core.SDKClient, accessToken string, req *unit.OcpcConversionInfosRequest) (*unit.OcpcConversionInfosResponse, error) ]
        - 获取可选的定向标签 [ tool.TargetingTagsList(clt *core.SDKClient, accessToken string, req *tool.TargetingTagsListRequest) (*tool.TargetingTag, error) ]
        - 获取可选的应用定向 [ tool.AppSearch(clt *core.SDKClient, accessToken string, req *tool.AppSearchRequest) (*tool.TargetingApp, error) ]
        - 获取可选的推荐封面 [ tool.KeyFrame(clt *core.SDKClient, accessToken string, req *tool.KeyFrameRequest) ([]string, error) ]
        - 获取可选的动态词包 [ tool.CreativeWordList(clt *core.SDKClient, accessToken string, advertiserID int64) ([]tool.CreativeWord, error) ]
        - 获取行动号召按钮 [ creative.ActionBarTextList(clt *core.SDKClient, accessToken string, req *creative.ActionBarTextListRequest) ([]string, error) ]
        - 获取可选的封面贴纸样式 [ tool.CreativeWordStyles(clt *core.SDKClient, accessToken string, advertiserID int64) ([]tool.CreativeWordStyle, error) ]
        - 获取可用的转化目标 [ tool.ConvertList(clt *core.SDKClient, accessToken string, req *tool.ConvertListRequest) (*tool.ConvertListResponse, error) ]
        - 获取可选白名单接口 [ advertiser.WhiteList(clt *core.SDKClient, accessToken string, advertiserID int64) (*advertiser.WhiteListResponse, error) ]
        - 获取地域定向 [ region.List(clt *core.SDKClient, accessToken string) (map[string]region.Region, error) ]
        - 获取商圈地域定向 [ region.DistrictList(clt *core.SDKClient, accessToken string, advertiserID int64) (map[string]region.District, error) ]
        - 获取可用咨询组件列表 [ lp.ConsultList(clt *core.SDKClient, accessToken string, req *lp.ConsultListRequest) (*lp.ConsultListResponse, error) ]
    - 功能名单
        - 获取创意分类标签白名单客户 [ advertiser.WhiteList(clt *core.SDKClient, accessToken string, advertiserID int64) (*advertiser.WhiteListResponse, error) ]
        - 获取联盟投放白名单 [ advertiser.WhiteList(clt *core.SDKClient, accessToken string, advertiserID int64) (*advertiser.WhiteListResponse, error) ]
    - 应用列表
        - 创建应用 [ file.AdAppCreate(clt *core.SDKClient, accessToken string, req *file.AdAppCreateRequest) (*file.App, error) ]
        - 修改应用 [ file.AdAppUpdate(clt *core.SDKClient, accessToken string, req *file.AdAppUpdateRequest) (*file.App, error) ]
        - 获取应用列表 [ file.AdAppList(clt *core.SDKClient, accessToken string, req *file.AdAppListRequest) (*file.AdAppListResponse, error) ]
    - 定向模版
        - 创建定向模板 [ target.TemplateCreate(clt *core.SDKClient, accessToken string, req *target.TemplateCreateRequest) (*target.Template, error) ]
        - 查询定向模板接口 [ target.TemplateList(clt *core.SDKClient, accessToken string, req *target.TemplateListRequest) (*target.TemplateListResponse, error) ]
        - 修改定向模板 [ target.TemplateUpdate(clt *core.SDKClient, accessToken string, req *target.TemplateUpdateRequest) (*target.Template, error) ]
        - 删除定向模板 [ target.TemplateDelete(clt *core.SDKClient, accessToken string, req *target.TemplateDeleteRequest) error ]
- DMP人群管理(api/dmp)
    - 人群包上传接口 [ PopulationUpload(clt *core.SDKClient, accessToken string, req *dmp.PopulationUploadRequest) (*dmp.Population, error) ]
    - 人群包更新接口 [ PopulationUpdate(clt *core.SDKClient, accessToken string, req *dmp.PopulationUpdateRequest) (*dmp.Population, error) ]
    - 人群列表查询接口 [ PopulationList(clt *core.SDKClient, accessToken string, req *dmp.PopulationListRequest) ([]dmp.Population, error) ]
    - 人群包删除接口 [ PopulationDelete(clt *core.SDKClient, accessToken string, req *dmp.PopulationDeleteRequest) error ]
    - 人群包跨账户推送 [ PopulationAccountsPush(clt *core.SDKClient, accessToken string, req *dmp.PopulationAccountsPushRequest) (*dmp.PopulationAccountsPushResponse, error) ]
    - 人群包上线接口 [ PopulationPush(clt *core.SDKClient, accessToken string, req *dmp.PopulationPushRequest) error ]
- 数据上报管理 (api/track)
    - 转化回传 [ Activate(req *track.ActivateRequest) error ]
    - 点击检测链接 [ Click(baseUrl string, fields []string) string ]

快手广告接口
