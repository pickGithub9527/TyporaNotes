### 0.Inception

涉及人员：学生、教职工、辅导员、导师、保卫处、学生处、学院、信息中心

涉及用例：每日疫情数据上报、出校、入校、人员申请出校表单、人员申请入校表单、查看疫情上报数据、提醒未上报人员、行为轨迹分析

![image-20210412195921028](/Users/samstephen/Library/Application Support/typora-user-images/image-20210412195921028.png)

### 1.「审核出入权限」

**用例UC1: 人员出校**

> **范围**：疫情防控系统
>
> **级别**：用户目标
>
> **主要参与者**：出入校园人员、安保人员
>
> **涉众及其关注点**：
>
> —出入校园人员：希望能够快速验证身份及出入权限，快速进出校园。
>
> —安保人员：希望能够快速核实进出人员身份，并且保证出入权限的正确性。
>
> —校方：希望人员的出入校园申请经核实，且保证未得到权限的人员不可出入校园。
>
> **前置条件**：出入校园人员必须经过申请确认及审核审批。
>
> **成功保证**：校园人员经审批后能正常出入校园。
>
> **主成功场景**：
>
> 1. 人员在申请出校权限成功后按需出校
> 2. 人脸识别系统识别人员身份
> 3. 后台数据查询确认出校权限
> 4. 权限确认成功，闸机自动打开，人员自行出校
>
> **拓展**：
>
> *a.恢复系统：
>
> ​	为了支持人员可以在系统瘫痪时能及时上报故障，应保证出入校园的地方随时有安保人员值班，向信息系统中心反馈情况
>
> ​	1.安保人员发现系统故障
>
> ​	2.重启系统
>
> ​		2a.系统重启，能够成功进行相应业务
>
> ​		2b.系统重启，业务仍无法正常进行
>
> ​			1.告知信息系统中心，通知回复故障
>
> ​			2.采用人工审核出校权限
>
> *b.人工审核：
>
> ​	为了支持人员可以在系统无法正常运行时正常出入校园，例如申请出入校园申请瘫痪、人脸识别系统瘫痪，应保证出入校园的地方随时有安保人员值班审核权限，提供正常的业务。
>
> ​	1.系统出错，无法正常自动进行人员审核和闸机开放
>
> ​	2.出校人员向安保人员展示出校权限身份
>
> ​	3.include 人工审核校园权限
>
> 2-4a.人脸识别系统无法识别通过人员的身份或权限返回无权限出入校园
>
> ​	1.返回权限确认失败
>
> ​	2.人员持权限文件（二维码或纸质文件）向安保人员展示
>
> ​	3.include [人工审核校园权限]

**用例UC2：人员申请表单出校**

> **范围**：疫情防控系统
>
> **级别**：用户目标
>
> **主要参与者**：出入校园人员、安保人员
>
> **涉众及其关注点**：
>
> —申请人员：希望能快速申请出入校园的权限，并且尽快得到权限确认。
>
> —审核人员：希望能够快速浏览申请内容及人员，快捷审核申请表单。
>
> —校方：希望人员的申请表单信息记录详尽，方便核实；审批通过符合规则流程。
>
> **前置条件**：申请表单人员必须填写相应的表单信息。
>
> **成功保证**：审批人员审批完成后修改相应出入权限。
>
> **主成功场景**：
>
> 1. 人员依据表单填写申请
> 2. 系统发送申请给审核人员
> 3. 审核人员确认申请
> 4. 系统修改权限，返回申请成功提醒
>
> **拓展**：
>
> *a.系统在任意时刻故障：
>
> ​	提醒申请人员目前不可申请，可直接持有相应的身份证件到出入处询问出入校园安排审核出入。
>
> 1a.表单未填写必须填写项
>
> ​	1.提醒「请填写所有必填项」，并将视图锁定到未填项
>
> ​	重复1内容，直到所有必填项填写完毕
>
> ​	2.系统发送表单给审批人员，并弹窗提醒填写完毕
>
> 2-4a.系统自行审批
>
> ​	1.依据表单内容，系统自行审核
>
> ​	2.修改权限，并返回申请成功提醒
>
> 3-4a.申请出入情况不符合学校安排
>
> ​	1.处理申请表单，不允许出入权限发放
>
> ​	2.系统返回申请失败提醒

**用例UC3：人工审核出校权限**

> **范围**：疫情防控系统
>
> **级别**：子功能
>
> **主要参与者**：出校人员、安保人员
>
> **涉众及其关注点**：
>
> —出入校园人员：希望能够快速验证身份及出校权限，快速出校。
>
> —安保人员：希望出示证件能够快速核实出校人员身份，并且保证权限正确性。
>
> **前置条件**：出校人员出示权限证件。
>
> **成功保证**：出校人员成功出校。
>
> **主成功场景**：
>
> 1. 出校人员向安保人员展示出校的权限证件
> 2. 安保人员对证件进行检查，出校权限可出校
> 3. 权限确认成功，安保打开闸机，人员出校
>
> **拓展**：
>
> 3a.权限不通过
>
> ​	1.出校人员证件绑定身份无出校权限
>
> ​	2.拒绝人员出校