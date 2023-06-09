# Smart light box
โปรเจคนี้มีชื่อว่า "Smart light box" หรือ "กล่องเปิด-ปิดไฟอัจฉริยะ" ทำขึ้นเพื่อทดลองสร้างวงจรไฟฟ้าเพื่อควบคุมการเปิด-ปิดหลอดไฟ โดยในโปรเจคนี้จะใช้ microcontroller ESP32 เป็นตัวควบคุม และใช้วงจร Op-amp comparator และ Transistor as a switch

![alt text](https://github.com/tsunafield1/Smart_light_box/blob/main/Example.PNG?raw=true)

อุปกรณ์ที่ใช้
- ESP32
- สายไฟ
- Photoboard
- IC LM358 (Op-amp)
- Resistor 1KΩ และ 10KΩ
- Potentiometer 100K
- LDR sensor
- Electret microphone condenser
- 7 Segment
- Transistor NPN 2N2222
- Relay SY-12-K
- Diode 1N4001
- หลอดไฟ
- Infrared sensor
- Adapter 12V 1A
- Button

การทำงานของกล่องเปิด-ปิดไฟอัจฉริยะ จะมีการทำงานทั้งหมด 4 โหมด 
- Infrared โหมดนี้จะใช้ Infrared sensor เป็นตัวแปรในการเปิด-ปิดไฟ เมื่อมีวัตถุเข้าใกล้เซนเซอร์ถึงระยะที่กำหนด หลอดไฟจะเปลี่ยนสถานะ (เปิด หรือ ปิด)
- ความเข้มแสง โหมดนี้จะใช้ LDR sensor เป็นตัวแปรในการเปิด-ปิดไฟ เมื่อเซนเซอร์วัดความเข้มแสงได้สูงกว่าที่กำหนด หลอดไฟจะปิด ในทางกลับกัน เมื่อเซนเซอร์วัดความเข้มแสงได้ต่ำกว่าที่กำหนด หลอดไฟจะเปิด
- เสียง โหมดนี้จะใช้ Electret microphone condenser เป็นตัวแปรในการเปิด-ปิดไฟ เมื่อมีเสียงดังถึงระดับที่กำหนด หลอดไฟจะเปลี่ยนสถานะ
- ปุ่ม โหมดนี้เป็นเหมือนหลอดไฟปกติ คือกดปุ่มทางซ้ายของกล่อง เพื่อเปลี่ยนสถานะของหลอดไฟ

โดยสามารถเปลี่ยนโหมดได้ด้วยการกดปุ่มทางขวาของกล่อง นอกจากนี้ยังสามารถควบคุมโหมด และสถานะของหลอดไฟผ่าน web browser ได้อีกด้วย โดยจะต้องเชื่อมต่อเครือข่ายเดียวกับ ESP32 หรือเชื่อมต่อ Hotspot ของ ESP32 แล้วเข้า web browser ด้วย IP ที่แสดงบน Serial monitor (สามารถเปลี่ยน ssid และ password ของเครือข่ายที่ ESP32 เชื่อมต่อ และ Hotspot ได้ใน Esp32AllWiFiVIR.ino บรรทัดที่ 7-10)

คลิปนำเสนอผลงาน: https://youtu.be/8XGPrZlh8J8

-----------------------------------------------------------------------------------------------------------------------------------------------------------------------

ใน src จะมี 1 ไฟล์
- Esp32AllWiFiVIR.ino คือ ไฟล์ที่อัพโหลดลง ESP32

ใน Circuit model จะมี 8 ไฟล์
- IR Active.PNG คือ รูปจำลองของวงจร Infrared ขณะหลอดไฟเปิด
- IR Non-Active.PNG คือ รูปจำลองของวงจร Infrared ขณะหลอดไฟปิด
- LDR Active.PNG คือ รูปจำลองของวงจร LDR sensor ขณะหลอดไฟเปิด
- LDR Non-Active.PNG คือ รูปจำลองของวงจร LDR sensor ขณะหลอดไฟปิด
- Mic Active.PNG คือ รูปจำลองของวงจร Electret microphone condenser ขณะหลอดไฟเปิด
- Mic Non-Active.PNG คือ รูปจำลองของวงจร Electret microphone condenser ขณะหลอดไฟปิด
- Transistor Active.PNG คือ รูปจำลองของวงจร Transistor ขณะหลอดไฟเปิด
- Transistor Non-Active.PNG คือ รูปจำลองของวงจร Transistor ขณะหลอดไฟปิด

โปรเจคนี้เป็นส่วนหนึ่งของวิชา Circuits and Electronics ภาควิชาวิศวกรรมคอมพิวเตอร์ คณะวิศวกรรมศาสตร์ สถาบันเทคโนโลยีพระจอมเกล้าเจ้าคุณทหารลาดกระบัง
