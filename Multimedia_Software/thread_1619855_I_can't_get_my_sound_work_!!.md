---
title: "I can't get my sound work !!"
date: 2010-11-12
forum: Multimedia Software
---

### Post by AluCarD_v8 on 2010-11-12
hello everybody 

I cannot hear any of my music or video files. 
but I have windows xp and it's working will !!

can anyone help me ?? :( 


this is the output of **lspci** : 

[COLOR=Blue]00:00.0 Host bridge: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller (rev 10)
00:01.0 PCI bridge: Intel Corporation 82G33/G31/P35/P31 Express PCI Express Root Port (rev 10)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 01)
00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 IDE interface: Intel Corporation N10/ICH7 Family SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 01)
01:00.0 VGA compatible controller: nVidia Corporation G96 [GeForce 9400 GT] (rev a1)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)
serious@ubuntu:~$ lspci
00:00.0 Host bridge: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller (rev 10)
00:01.0 PCI bridge: Intel Corporation 82G33/G31/P35/P31 Express PCI Express Root Port (rev 10)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 01)
00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 IDE interface: Intel Corporation N10/ICH7 Family SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 01)
01:00.0 VGA compatible controller: nVidia Corporation G96 [GeForce 9400 GT] (rev a1)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)[/COLOR]



[SIZE=4]pleaseeeeee help me :confused:[/SIZE]

---

### Post by tajiknomi on 2010-11-12
[I][SIZE=2]1st of all..

Go to >system>preferences>sound...and check whether it is mute..?
[/SIZE][/I]

---

### Post by AluCarD_v8 on 2010-11-12
Thank you for your reply ....

when I try to open it it says : Waiting for sound system to respond 


??

---

### Post by Yellow Pasque on 2010-11-12
Your pulseaudio is screwed up. Try:
```
rm -rf ~/.pulse*
```
Log out and back in.

---

### Post by AluCarD_v8 on 2010-11-13
I've typed it in the terminal but nothing happend ?

---

### Post by AluCarD_v8 on 2010-11-13
help meeeeeee

---

### Post by tajiknomi on 2010-11-13
[SIZE=2]Go to Preferences>Startup-application's>Startup programe's tab..

click Add
[/SIZE]Name: **Pulseaudio daemon**
Command:**/usr/bin/pulseaudio**
Comment: **Start the sound daemon**

Now logout, then login again

->Fixed
[]("http://ubuntuforums.org/showthread.php?t=1495061")

---

### Post by AluCarD_v8 on 2010-11-13
Thank you brother for your reply
unfortunately, still can't solve this :(

---

### Post by tajiknomi on 2010-11-13
See the same thread...Focus on Comments...may it help....

[http://www.ubuntugeek.com/ubuntu-10-04-tip-how-to-fix-waiting-for-sound-system-to-respond-problem.html](http://www.ubuntugeek.com/ubuntu-10-04-tip-how-to-fix-waiting-for-sound-system-to-respond-problem.html)

---

