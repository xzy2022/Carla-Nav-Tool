这是一个“点击目标点 + 自动驾驶 + 采集数据”的脚本，不是纯手动驾驶脚本。
核心流程在 data_collect.py (line 1033)、data_collect.py (line 1298)、data_collect.py (line 818)：
连接 CARLA，加载地图，生成自车 + 交通车 + 行人。
你在画面里鼠标左键点目标点，脚本用深度图把像素点转成世界坐标并 agent.set_destination(...)。
车辆由 BehaviorAgent/BasicAgent 自动开过去。
采集并保存到 _out/<episode>/：images/、inverse_matrix/、vehicle_positions.txt、target_positions.txt、command.txt、camera_intrinsic.npy。
页面打开后怎么控制（含车辆）
按键逻辑在 data_collect.py (line 274)：
鼠标左键：设定目标点并开始一次自动行驶。
第一次点会在终端弹 Enter Command:，你需要在终端输入文本并回车（不输入会像“卡住”）。
Esc 或 Ctrl+Q：退出。（似乎只有这个有效）
D：下一条 episode（下次点击会新建 episode 并重新输入 command）。
Z：删除当前 episode 并准备下一条。
R：重写当前 command.txt。
I：忽略保存（不记录数据）。