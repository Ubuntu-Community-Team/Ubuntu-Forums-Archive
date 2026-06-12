---
title: "Realteck drivers and 11.04"
date: 2011-05-15
forum: Networking &amp; Wireless
---

### Post by Grisk13 on 2011-05-15
Greetings  I posted a few weeks ago about my wireless card not working.  I was able to fix it (under Natty) for a while, but I am having some issues and my fixes are not even close to functioning anymore.    To fix the problem, I originally downloaded this driver  [http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=1&PFid=1&Level=6&Conn=5&DownTypeID=3&GetDown=false&Downloads=true#RTL8185L](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=1&PFid=1&Level=6&Conn=5&DownTypeID=3&GetDown=false&Downloads=true#RTL8185L)    and, though I occasionally had to re- &quot;make-install&quot; it, it worked.      Last night, I did the system updates Ubuntu suggested and this morning, my WiFi is not functioning :(  Here are the &quot;common commands&quot; and stuff I have used so far to try to debug the problem.    lspci:  1a/b/g Wireless LAN Controller (rev 20) 0c:03.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306/7/8 [Fire II(M)] IEE    iwconfig:    wlan0     IEEE 802.11bg  ESSID:&quot;***** ******&quot;             Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated              Tx-Power=20 dBm              Retry  long limit:7   RTS thr:off   Fragment thr:off           Power Management:off    I am slightly confused as to why my Wireless LAN Controller doesn't come up as my Realtek 8185, but I think that may be issue number 1.   The next bit of confusion comes from the fact that wlan0 is shown as connected to the correct SSID, even showing a frequency, but is not, infact, sending or receiving from that source.     As I have said before, I just really nee WiFi to work.  I was having issues with my sound and graphics cards, so I ran the update manager, but I wasn't expecting it to break my drivers!    It is also worth noting that I have actually tried to recompile my drivers and re-install them, they don't seem to be working, for some reason.  Thank you for reading!

---

### Post by chili555 on 2011-05-15
> I am slightly confused as to why my Wireless LAN Controller doesn't come up as my Realtek 8185, but I think that may be issue number 1.I am more than slightly confused because your question is all run together with hardly any punctuation and no paragraph breaks to make things more readable.

The reason your wireless doesn't come up as your Realtek is that you are looking at the wrong line. If you re-run:```
lspci -nn
```I am quite confident your Realtek is shown. 

Your complaint or question seems to be:> my WiFi is not functioning :(In what way is it not functioning? When you click the Network Manager icon, do you see your network? When you click your network, does it try to connect?> iwconfig: wlan0 
IEEE 802.11bg ESSID:***** ******
Mode:Managed Frequency:2.412 GHz Access Point: Not-Associated Tx-Power=20 dBm 
Retry long limit:7 RTS thr:off Fragment thr:off Power Management:off If your drivers were not functioning, you wouldn't see a wireless interface wlan0.

When you recompiled, did you include 'make clean' in your steps? Did you reboot?

---

### Post by Grisk13 on 2011-05-15
Believe it or not, that OP did actually have formatting...  I have edited it several times to try to regain it, but every time I hit save it runs together in that horrible paragraph.  I think it may have something to do with the fact that I copied the output of the two commands from a file with Unix line tags, but that is another question for another day.

I apologize for not being clear, I thought the output of "iwconfig" was enough to show that I could view wireless networks in my network applet, but I was clearly wrong (hardly the first time)!

Here is the output of the command you requested:

```
00:00.0 Host bridge [0600]: Intel Corporation Core Processor DMI [8086:d131] (rev 11)
00:03.0 PCI bridge [0604]: Intel Corporation Core Processor PCI Express Root Port 1 [8086:d138] (rev 11)
00:08.0 System peripheral [0880]: Intel Corporation Core Processor System Management Registers [8086:d155] (rev 11)
00:08.1 System peripheral [0880]: Intel Corporation Core Processor Semaphore and Scratchpad Registers [8086:d156] (rev 11)
00:08.2 System peripheral [0880]: Intel Corporation Core Processor System Control and Status Registers [8086:d157] (rev 11)
00:08.3 System peripheral [0880]: Intel Corporation Core Processor Miscellaneous Registers [8086:d158] (rev 11)
00:10.0 System peripheral [0880]: Intel Corporation Core Processor QPI Link [8086:d150] (rev 11)
00:10.1 System peripheral [0880]: Intel Corporation Core Processor QPI Routing and Protocol Registers [8086:d151] (rev 11)
00:1a.0 USB Controller [0c03]: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller [8086:3b3c] (rev 06)
00:1b.0 Audio device [0403]: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio [8086:3b56] (rev 06)
00:1c.0 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 [8086:3b42] (rev 06)
00:1c.4 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 5 [8086:3b4a] (rev 06)
00:1c.5 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 6 [8086:3b4c] (rev 06)
00:1c.6 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 7 [8086:3b4e] (rev 06)
00:1c.7 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 8 [8086:3b50] (rev 06)
00:1d.0 USB Controller [0c03]: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller [8086:3b34] (rev 06)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 PCI Bridge [8086:244e] (rev a6)
00:1f.0 ISA bridge [0601]: Intel Corporation 5 Series Chipset LPC Interface Controller [8086:3b02] (rev 06)
00:1f.2 IDE interface [0101]: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA IDE Controller [8086:3b20] (rev 06)
00:1f.3 SMBus [0c05]: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller [8086:3b30] (rev 06)
00:1f.5 IDE interface [0101]: Intel Corporation 5 Series/3400 Series Chipset 2 port SATA IDE Controller [8086:3b26] (rev 06)
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc Barts XT [ATI Radeon HD 6800 Series] [1002:6738]
01:00.1 Audio device [0403]: ATI Technologies Inc Barts HDMI Audio [Radeon HD 6800 Series] [1002:aa88]
03:00.0 SATA controller [0106]: JMicron Technology Corp. JMB362/JMB363 Serial ATA Controller [197b:2363] (rev 03)
03:00.1 IDE interface [0101]: JMicron Technology Corp. JMB362/JMB363 Serial ATA Controller [197b:2363] (rev 03)
05:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 03)
06:00.0 PCI bridge [0604]: PLX Technology, Inc. PEX 8608 8-lane, 8-Port PCI Express Gen 2 (5.0 GT/s) Switch [10b5:8608] (rev ba)
07:01.0 PCI bridge [0604]: PLX Technology, Inc. PEX 8608 8-lane, 8-Port PCI Express Gen 2 (5.0 GT/s) Switch [10b5:8608] (rev ba)
07:05.0 PCI bridge [0604]: PLX Technology, Inc. PEX 8608 8-lane, 8-Port PCI Express Gen 2 (5.0 GT/s) Switch [10b5:8608] (rev ba)
07:07.0 PCI bridge [0604]: PLX Technology, Inc. PEX 8608 8-lane, 8-Port PCI Express Gen 2 (5.0 GT/s) Switch [10b5:8608] (rev ba)
07:09.0 PCI bridge [0604]: PLX Technology, Inc. PEX 8608 8-lane, 8-Port PCI Express Gen 2 (5.0 GT/s) Switch [10b5:8608] (rev ba)
08:00.0 USB Controller [0c03]: NEC Corporation uPD720200 USB 3.0 Host Controller [1033:0194] (rev 03)
09:00.0 IDE interface [0101]: Marvell Technology Group Ltd. Device [1b4b:91a0] (rev 12)
0c:02.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller [10ec:8185] (rev 20)
0c:03.0 FireWire (IEEE 1394) [0c00]: VIA Technologies, Inc. VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller [1106:3044] (rev c0)

```

Well, this is interesting.  I attempted to do a "sudo make install clean" on the driver I posted earlier and now my Ubutnu instillation fails to boot.  I can choose Ubuntu in my bootloader, but I get nothing but a black screen after that.  A fantastic way to start the afternoon :(
Thank you!

---

### Post by chili555 on 2011-05-15
> Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller [10ec:8185] (rev 20)Thar she blows!

I don't understand why some manufacturers confuse us all by characterizing a wireless device as Ethernet controller. Realtek is hardly alone in this.

I think the whole r8185 and r8187 series are pretty poor. They are troublesome and there are tons of posts complaining that they can't connect, can't stay connected, can't do WPA2, etc. Frankly, if I were buying a laptop today, an 8185 or 8187 would be a deal-breaker. I do realize that we sometimes convert an older lappy to Ubuntu and have few choices.

I suggest you rebuild the driver:```
cd Downloads/or/wherever
sudo su
make clean 
make
make install
rmmod -f r8180
modprobe r8180
exit
```Substitute your details as needed.

Post back if you have more trouble.

---

### Post by imnotrich on 2011-06-08
Solved - delete 11.04 and reinstall Ubuntu 9.04, it recognizes and works flawlessly with this (forgive the editorial comment) very common wireless card.

In the past I've had some success (when there are hardware issues with the current Ubuntu release) is to install a previous release that actually did support the hardware and then run the "upgrades" until I reached the version I wanted. Most of the time, somehow, the Ubuntu upgrade realizes that hey I need to keep support for this hardware. But today I noticed that between 9.04 and 9.10 Ubuntu broke just about everything else (touch pad, video, and sound) on my less than 5 year old laptop so the crazy bald headed guy from Mexico's upgrade method does not always work. Just an idea.

---

