---
title: "bluetooth not working"
date: 2011-12-05
forum: Networking &amp; Wireless
---

### Post by ashwani kumar sharma on 2011-12-05
i am new to ubuntu and want to use my bluetooth inbuilt on my laptop ..... i previusly used xp in which there was a specail key p1 ........in which first i had to install the drivers for p1 key/utility then by pressing the p1 key i used to activate the bluetooth stack over which i installed the bluetooth drivers(bilinton or auz.. something like that).... but now i have swithed to ubuntu and unable to use my bluetooth it does not show icon only ......please help me

---

### Post by wildman4god on 2011-12-05
what's the model number of your bluetooth adapter?

---

### Post by ashwani kumar sharma on 2011-12-11
how to find that

---

### Post by nothingspecial on 2011-12-13
If you have no replies to your question after about 24 hours please bump your thread rather than making a new one.

I have closed all your other threads.

Do not make any more about this issue. Thank you.

---

### Post by ashwani kumar sharma on 2011-12-15
i am sorry about no of duplicate threds ..


i am having a hcl leaptop which shows "that there are no Bluetooth  adapters plugged in"..... now any one can help to solve this problem so  that i can run my bluetooth on linux

---

### Post by ashwani kumar sharma on 2011-12-15
please any one here for help

---

### Post by nothingspecial on 2011-12-15
You need to give some more information. Do you know what make your bluetooth device is?

---

### Post by ashwani kumar sharma on 2011-12-15
the pc shows no bluetooth adapter found 
i have tried    lsusb and  rfkill list and output was 
$ lsusb
Bus 004 Device 003: ID 12d1:140b Huawei Technologies Co., Ltd. EC1260 Wireless Data Modem HSD USB Card
Bus 004 Device 002: ID 1c4f:0003 SiGma Micro HID controller
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 004: ID eb1a:5060 eMPIA Technology, Inc. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 148f:2573 Ralink Technology, Corp. RT2501/RT2573 Wireless Adapter
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub



and 


$ rfkill list
0: phy1: Wireless LAN
	Soft blocked: no
	Hard blocked: yes



model number is 
HCL NOTEBOOK P38 PDC

---

### Post by ashwani kumar sharma on 2011-12-16
hey what next i should do i am not getting to fix it 


rfkill
Usage:    rfkill [options] command
Options:
    --version    show version (0.4-1 (Ubuntu))
Commands:
    help
    event
    list [IDENTIFIER]
    block IDENTIFIER
    unblock IDENTIFIER
where IDENTIFIER is the index no. of an rfkill switch or one of:
    <idx> all wifi wlan bluetooth uwb ultrawideband wimax wwan gps fm



 $ lsusb
Bus 004 Device 009: ID 12d1:140b Huawei Technologies Co., Ltd. EC1260 Wireless Data Modem HSD USB Card
Bus 004 Device 008: ID 1c4f:0003 SiGma Micro HID controller
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 004: ID eb1a:5060 eMPIA Technology, Inc. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 148f:2573 Ralink Technology, Corp. RT2501/RT2573 Wireless Adapter
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

---

