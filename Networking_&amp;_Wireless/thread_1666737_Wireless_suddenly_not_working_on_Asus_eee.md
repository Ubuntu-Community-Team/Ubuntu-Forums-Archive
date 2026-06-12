---
title: "Wireless suddenly not working on Asus eee"
date: 2011-01-14
forum: Networking &amp; Wireless
---

### Post by RuneLacroix on 2011-01-14
Hey.
 
I have been using ubuntu troublefree for some month, but yesterday, suddenly the wireless internet connection stopped working. It happened after i used the turn off wireless network shortcut, now i cant turn it on again (usually this works fine).
 
The situation is now, that when i click on the tray icon showing connection it says, wired network disconnected (it never said this before), then if i click on the wireless shortcut it also says wireless disconnected... But if i click again it doesnt show connections, the disconnected sign just disappears...? 
 
Any suggestions to what i can do? Or what has happened?
I have a Eee pc 1008p with ubuntu 10.10.
 
Kind Regards, 
Rune Lacroix

---

### Post by amsterdamharu on 2011-01-14
What is the output of the following commands?

```
rfkill list
ifconfig
iwconfig
```
To execute the commands you can press alt + F2, type gnome-terminal and click run. Then copy the 3 command and paste it in the terminal (black screen that showed up after you clicked run). Use the mouse to paste commands in the terminal.
Then you can select all the text in the terminal, right click and select copy. When pasting it here please wrap it in &#91;code] &#91;/code] tags. In other words: &#91;code][COLOR=Red]Your pasted stuff[/COLOR]&#91;/code]

To see what wireless you are using could you post the output of:
```
lsusb
lspci -k
```

When pasting it here please wrap it in &#91;code] &#91;/code] tags. In other words: &#91;code][COLOR=Red]Your pasted stuff[/COLOR]&#91;/code]

---

### Post by RuneLacroix on 2011-01-14
Thank you.
Here it is:
 
 
```
 
runelacroix@Shakti:~$ rfkill list 
0: eeepc-wlan: Wireless LAN 
Soft blocked: yes 
Hard blocked: no 
runelacroix@Shakti:~$ ifconfig 
eth0 Link encap:Ethernet HWaddr e0:cb:4e:67:a7:a6 
UP BROADCAST MULTICAST MTU:1500 Metric:1 
RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
collisions:0 txqueuelen:1000 
RX bytes:0 (0.0 B) TX bytes:0 (0.0 B) 
Interrupt:45 


lo Link encap:Local Loopback 
inet addr:127.0.0.1 Mask:255.0.0.0 
inet6 addr: ::1/128 Scope:Host 
UP LOOPBACK RUNNING MTU:16436 Metric:1 
RX packets:216 errors:0 dropped:0 overruns:0 frame:0 
TX packets:216 errors:0 dropped:0 overruns:0 carrier:0 
collisions:0 txqueuelen:0 
RX bytes:16048 (16.0 KB) TX bytes:16048 (16.0 KB) 




runelacroix@Shakti:~$ iwconfig 
lo no wireless extensions. 


eth0 no wireless extensions. 


runelacroix@Shakti:~$ lsusb 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 001 Device 002: ID 13d3:5116 IMC Networks Integrated Webcam 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub 
runelacroix@Shakti:~$ lspci -k 
00:00.0 Host bridge: Intel Corporation N10 Family DMI Bridge 
Subsystem: ASUSTeK Computer Inc. Device 83ac 
Kernel driver in use: agpgart-intel 
Kernel modules: intel-agp 
00:02.0 VGA compatible controller: Intel Corporation N10 Family Integrated Graphics Controller 
Subsystem: ASUSTeK Computer Inc. Device 83ac 
Kernel driver in use: i915 
Kernel modules: i915 
00:02.1 Display controller: Intel Corporation N10 Family Integrated Graphics Controller 
Subsystem: ASUSTeK Computer Inc. Device 83ac 
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02) 
Subsystem: ASUSTeK Computer Inc. Device 8398 
Kernel driver in use: HDA Intel 
Kernel modules: snd-hda-intel 
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02) 
Kernel driver in use: pcieport 
Kernel modules: shpchp 
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02) 
Kernel driver in use: pcieport 
Kernel modules: shpchp 
00:1c.3 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 4 (rev 02) 
Kernel driver in use: pcieport 
Kernel modules: shpchp 
00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 02) 
Subsystem: ASUSTeK Computer Inc. Device 83ad 
Kernel driver in use: uhci_hcd 
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02) 
Subsystem: ASUSTeK Computer Inc. Device 83ad 
Kernel driver in use: uhci_hcd 
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02) 
Subsystem: ASUSTeK Computer Inc. Device 83ad 
Kernel driver in use: uhci_hcd 
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02) 
Subsystem: ASUSTeK Computer Inc. Device 83ad 
Kernel driver in use: uhci_hcd 
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02) 
Subsystem: ASUSTeK Computer Inc. Device 83ad 
Kernel driver in use: ehci_hcd 
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2) 
00:1f.0 ISA bridge: Intel Corporation NM10 Family LPC Controller (rev 02) 
Subsystem: ASUSTeK Computer Inc. Device 83ad 
00:1f.2 SATA controller: Intel Corporation N10/ICH7 Family SATA AHCI Controller (rev 02) 
Subsystem: ASUSTeK Computer Inc. Device 83ad 
Kernel driver in use: ahci 
Kernel modules: ahci 
01:00.0 Ethernet controller: Atheros Communications AR8132 Fast Ethernet (rev c0) 
Subsystem: ASUSTeK Computer Inc. Device 838a 
Kernel driver in use: atl1c 
Kernel modules: atl1c 
02:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01) 
Subsystem: Device 1a3b:1089 
Kernel modules: ath9k 
runelacroix@Shakti:~$ 

```

---

### Post by hansolo4949 on 2011-01-14
You somehow soft-blocked your wireless card. To unblock it, you need to type: 
sudo rfkill unblock 0

---

### Post by RuneLacroix on 2011-01-14
It doesnt help.. the only thing different is that i now get :
 
```
runelacroix@Shakti:~$ rfkill list 
0: eeepc-wlan: Wireless LAN 
Soft blocked: no
Hard blocked: no 

```
 
But that doesnt make the internet work.. and when i restart it says again :
 
```
runelacroix@Shakti:~$ rfkill list 
0: eeepc-wlan: Wireless LAN 
Soft blocked: yes 
Hard blocked: no 

```
 
??

---

### Post by hansolo4949 on 2011-01-14
Hmm...try using the shortcut again to enable the wireless card again. Then run Rfkill and see if you're wireless card isn't softblocked anymore. if it is, unblock it, then wait and see if you get any wireless access points withing the next souple of minutes. If not, reboot, and see if that works.

---

### Post by amsterdamharu on 2011-01-14
Try the following commands:

```
sudo rfkill unblock 0
sudo ifconfig wlan0 up
sudo ifconfig
```

Then see if your network applet detects any new wireless networks.

---

### Post by JPierreD on 2011-03-21
I had the same problem when my Kernel was updated by the update manager.

---

