---
title: "hauwei modem not detected mobile broadband device"
date: 2012-10-14
forum: Networking &amp; Wireless
---

### Post by ervinodsingh on 2012-10-14
Hi, in my freshly installed ubuntu my  hawei modem is not detected  as new devices in "set new broad band mobile connection." section. 
Please help me in this regard...i do not want to use windows only to use Internet

---

### Post by matt_symes on 2012-10-14
Hi

Can you post the model.

I have this problem and i am currently looking for a solution (I borrowed a stick from a friend). 

My stick (my friends stick :)) is not mode switching correctly and is throwing an error that is written to dmesg and syslog.

Do you have LED's on the stick ? If so, what colour are they flashing ? Are they even flashing ? Are they even on ?

What is displayed in dmesg when you insert the stick ?

I will be looking for a solution tomorrow evening when i have more time.

Kind regards

---

### Post by ervinodsingh on 2012-10-16
HI Matt,  thanks for your reply

MY datard model is Huawei E303C as mentioned in given link:  [http://www.flipkart.com/huawei-e303c-data-card/p/itmd7g4damu7gtez?pid=DATD7G4DXMPW8M7U&ref=5967e82d-eef6-4ba5-bb90-ca3185810919&srno=m_1_1&otracker=from-search](http://www.flipkart.com/huawei-e303c-data-card/p/itmd7g4damu7gtez?pid=DATD7G4DXMPW8M7U&ref=5967e82d-eef6-4ba5-bb90-ca3185810919&srno=m_1_1&otracker=from-search)


Msg shown:  mobile partner -- open with files or eject (same msg as wen i connect my pendrive)

It is blinking blue and detected today. But its detection is very random, i cant predict whether it will be detected or not. 


 My lsusb output:--
vinod@vinod:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 004: ID 058f:a014 Alcor Micro Corp. 
Bus 001 Device 005: ID 0cf3:3005 Atheros Communications, Inc. AR3011 Bluetooth
Bus 002 Device 004: ID 12d1:1506 Huawei Technologies Co., Ltd. E398 LTE/UMTS/GSM Modem/Networkcard

---

