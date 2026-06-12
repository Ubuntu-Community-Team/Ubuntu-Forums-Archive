---
title: "wireless network with DWL-G520+"
date: 2006-04-17
forum: Networking &amp; Wireless
---

### Post by Alain1 on 2006-04-17
Hello,

I'm a newbie on Linux... I installed Ubuntu 5.10. I have also XP on my PC. So, I'm working in dual boot.  
For the moment I'm trying to have a wireless connection.
I installed ndiswrapper and searched the inf-file (driver) 
Here is the result :
Installed ndis drivers:
gplus   driver present, hardware present
The problem is that I can not configure 
When I do lspci, I recieve this:
0000:00:00.0 Host bridge: VIA Technologies, Inc. VT8366/A/7 [Apollo KT266/A/333]0000:00:01.0 PCI bridge: VIA Technologies, Inc. VT8366/A/7 [Apollo KT266/A/333 AGP]
0000:00:05.0 Multimedia audio controller: C-Media Electronics Inc CM8738 (rev 10)
0000:00:0d.0 Network controller: Texas Instruments ACX 111 54Mbps Wireless Interface
0000:00:0f.0 Communication controller: Conexant HCF 56k Data/Fax/Voice Modem (rev 08)
0000:00:11.0 ISA bridge: VIA Technologies, Inc. VT8233A ISA Bridge
0000:00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
0000:00:11.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 23)
0000:00:11.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 23)
0000:01:00.0 VGA compatible controller: STMicroelectronics STG4000 [3D Prophet Kyro Series] (rev 01)

My iwconfig command give me this info :
alain@alainlinux:~$ iwconfig
lo        no wireless extensions.

wlan0     IEEE 802.11b+/g+  ESSID:"alainthuis"  Nickname:"acx100 v0.2.0pre8"
          Mode:Auto  Frequency:2.412 GHz  Access Point: 00:00:00:00:00:00
          Bit Rate=54 Mb/s   Tx-Power=15 dBm   Sensitivity=1/3
          Retry min limit:7   RTS thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.

sit0      no wireless extensions.

I can not connect. 
I**s there someone who can help me step by step**? 
Thanks...
Greetings,
Alain

Is there nobody who can help me please?

---

### Post by jml on 2006-04-17
Don't feel too bad.  Getting wireless networking going in Linux is one of the most difficult tasks I have ever encountered.  Judging by the number of different posts on this topic, a lot of people are experiencing the same type of problem.  here is a link to Ubuntu's wireless troubleshooting guide.  I hope it helps.

[https://wiki.ubuntu.com/WirelessTroubleshootingGuide](https://wiki.ubuntu.com/WirelessTroubleshootingGuide)

Joe

---

### Post by Alain1 on 2006-04-30
When I do the following command (lshw), I receive this... Maybe someone can help me further? 
 *-network
             description: Wireless interface
             product: ACX 111 54Mbps Wireless Interface
             vendor: Texas Instruments
             physical id: d
             bus info: pci@00:0d.0
             logical name: wlan0
             version: 00
             serial: 00:11:95:47:ae:10
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list ethernet physical wireless
             configuration: broadcast=yes driver=acx_pci multicast=yes wireless=IEEE 802.11b+/g+
             resources: iomemory:f6800000-f6801fff iomemory:f6000000-f601ffff irq:11
It looks to be recognized as an ACX 111 54 Mbps Wireless Interface
Can anyone help me please? :p

---

