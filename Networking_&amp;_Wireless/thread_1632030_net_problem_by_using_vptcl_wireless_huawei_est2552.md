---
title: "net problem by using vptcl wireless huawei est2552 in ubunut 10.10"
date: 2010-11-27
forum: Networking &amp; Wireless
---

### Post by humanaveed on 2010-11-27
hay 
i am new to ubuntu, i have installed ubunutu 10.10, i have vptcl wireless huawei est2552 set, i am unable to conncet to internet using this set, plz help me, n iam using 64 bit dell inspron,

When i attach the cable it gets detected as a  usb storage device and not as a usb modem i used this command to covert it,[INDENT]***sudo apt-get install usb-modeswitch***

it gives the following output
 Reading package lists... Done
    Building dependency tree       
    Reading state information... Done
    usb-modeswitch is already the newest version.
    0 upgraded, 0 newly installed, 0 to remove and 158 not upgraded.
    1 not fully installed or removed.
    After this operation, 0B of additional disk space will be used.
    Do you want to continue 
  
[/INDENT]thn i Unplug the modem and plug it back in. Use lsusb command to  see usb modem it gives folloowing output
   Bus 002 Device 004: ID 12d1:1010 Huawei Technologies Co., Ltd. 
    Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
    Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
    Bus 001 Device 012: ID 413c:8162 Dell Computer Corp. 
    Bus 001 Device 011: ID 413c:8161 Dell Computer Corp. 
    Bus 001 Device 010: ID 0a5c:4500 Broadcom Corp. BCM2046B1 USB 2.0 Hub (part of BCM2046 Bluetooth)
    Bus 001 Device 005: ID 0bda:0158 Realtek Semiconductor Corp. USB 2.0 multicard reader
    Bus 001 Device 004: ID 0c45:641d Microdia 
    Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
    Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
    i donot konw what to do further, and am i going in a correct way, plzzzzz help me in connecting net in ubuntu10.10

---

