---
title: "No WiFi Ubuntu 11.04 on Thinkpad T61"
date: 2012-08-02
forum: Networking &amp; Wireless
---

### Post by paffenbutler on 2012-08-02
Hello, I have installed Ubuntu 11.04 on my Thinkpad t61 laptop.

I am not able to create any wireless connections.  I have not tried wired.  I need some driver tips I think.  Any out there?

---

### Post by praseodym on 2012-08-02
Please show the terminal outputs of:

```
lspci -nnk | grep -iA2 net
uname -a
lsusb
iwconfig
rfkill list
```

---

### Post by paffenbutler on 2012-08-02
mike@mike-ThinkPad-T61:~$ lspci -nnk | grep -iA2 net 
00:19.0 Ethernet controller [0200]: Intel Corporation 82566MM Gigabit Network Connection [8086:1049] (rev 03) 
	Subsystem: Lenovo ThinkPad T61 [17aa:20b9] 
	Kernel driver in use: e1000e 
-- 
03:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection [8086:4230] (rev 61) 
	Subsystem: Intel Corporation Lenovo ThinkPad T51 [8086:1110] 
	Kernel driver in use: iwlagn 
mike@mike-ThinkPad-T61:~$ uname -a 
Linux mike-ThinkPad-T61 2.6.35-24-generic #42-Ubuntu SMP Thu Dec 2 01:41:57 UTC 2010 i686 GNU/Linux 
mike@mike-ThinkPad-T61:~$ lsusb 
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 006 Device 002: ID 17ef:1003 Lenovo Integrated Smart Card Reader 
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub 
mike@mike-ThinkPad-T61:~$ iwconfig 
lo        no wireless extensions. 
 
eth0      no wireless extensions. 
 
wlan0     IEEE 802.11abg  ESSID:off/any   
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off    
          Retry  long limit:7   RTS thr:off   Fragment thr:off 
          Power Management:off 
           
mike@mike-ThinkPad-T61:~$ rfkill list 
0: phy0: Wireless LAN 
	Soft blocked: yes 
	Hard blocked: yes 
1: tpacpi_bluetooth_sw: Bluetooth 
	Soft blocked: yes 
	Hard blocked: yes 
mike@mike-ThinkPad-T61:~$ ^C 
mike@mike-ThinkPad-T61:~$

---

### Post by praseodym on 2012-08-03
Try 

> sudo rfkill unblock all
rfkill list
Any button/switch/key/key combination (e.g. Fn+F2)? Tried to reset the BIOS?

---

### Post by paffenbutler on 2012-08-03
I'm quite new at this.  Can you tell me what these steps will do?
Thanks.:)

---

### Post by praseodym on 2012-08-03
> mike@mike-ThinkPad-T61:~$ rfkill list
0: phy0: Wireless LAN
Soft blocked: yes
Hard blocked: yes
1: tpacpi_bluetooth_sw: Bluetooth
Soft blocked: yes
Hard blocked: yes 
Hopefully, it will unblock the wifi

---

### Post by paffenbutler on 2012-08-03
Thanks so much.  Tried the Unblock and found the soft block off but hard lock still on.  That got me thinking (finally), and I looked for a hardware switch for the wifi.  Its on the front of the thinkpad, and it was pushed to 'off'.  

Thanks for the leads.  I feel stupid, but happy.

---

### Post by josil on 2012-09-30
I am about to switch from Fedora 14 to ubuntu 11.04 on my Thinkpad T61. What the performance of the machine with ubuntu? Is it fast and smooth? Thanks for the feedback

---

