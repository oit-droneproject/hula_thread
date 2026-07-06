
'''python
import pyhula
import cv2
import numpy as np
import time
import keyboard

api = pyhula.UserApi()
if not api.connect():
    print("connect error")
    exit()

print('connected')
print(f"battery={api.get_battery()}")

# ストリーム有効化（この順番が重要）
api.Plane_cmd_swith_rtp(0)
api.single_fly_flip_rtp()  # これが必要

#api.Plane_cmd_switch_QR(0)

time.sleep(6)  # SPS/PPSが届くまで待つ

print("映像取得開始...")

while True:
    #arry=api.single_fly_Anticipatory_recognition(0,20)
    #print(arry)
    #print(arry['y'])
    #print(api.single_fly_Optical_flow_recognition(0,20))
    #print(api.single_fly_Optical_flow_alignment(0,20,0))

    print(api.single_fly_Proactive_alignment(0))
    print(api.single_fly_getColor())

    
    if keyboard.is_pressed('q'):
        print("qが押されたので停止します")
        api.Plane_cmd_swith_rtp(1)
        break
'''
