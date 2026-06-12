---
title: "Asus Bluetooth Dongle Installation - need driver or inf file"
date: 2010-11-02
forum: Networking &amp; Wireless
---

### Post by BobTheMailMan on 2010-11-02
The bluetooth manager does not detect a bluetooth dongle 
trying to use ndiswrapper to fix
I installed device manager and the results are shown below
i downloaded the windows driver suite. It has 4 .exe self extracting driver archives and a setupconfig.ini. The .ini file is below. I was able to extract one of the 32bit archives on a windows machine and it had about 8 .inf files that are titled weird and would not install properly using ndiswrapper probably because im using the 64-bit architecture. there are 2 64bit .exe's in the driver download, but how can i extract them in ubuntu and do i really need to install all 8 .inf files.

any help on the situation would be wonderful. also do i actually need to make a .inf file? if so how?

Asus - BT211 mini bluetooth dongle
```
http://usa.asus.com/product.aspx?P_ID=GfCNjYFw5rZAov3S - windows driver under download section. 
```Device manager 
```
Model: Unknown model (id =0x3000)
Vendor: atheros Communications, inc
revision: 2.00
connection: USB
USB Version: ??
Connected at ??
remote wake up: no
bus powered: yes
Max power: 100ma
```SetupConfig.ini
```
[PVID] 
PID=1783 
vid=0b05 
[setup] 
DeviceType="dongle"
```

---

### Post by BobTheMailMan on 2010-11-03
Solved! - i happended to be using 10.4 lts. i was moving the os to a raid 0/ more permanent setup and i installed 10.10 with the usb in the computer and it picked up the bluetooth right off the batt

---

### Post by jeukel on 2011-05-23
So far I get 2 ID's from this dongle.

When it works on 10.04, the ID its ASUSTEK something... When not, the same as BobTheMailMan.

On 10.10 it works just fine with the athero's ID one.Im using the lastest precompiled kernel by canonical for ubuntu AMD64.

---

