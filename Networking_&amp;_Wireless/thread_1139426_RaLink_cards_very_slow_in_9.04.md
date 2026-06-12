---
title: "RaLink cards very slow in 9.04"
date: 2009-04-27
forum: Networking &amp; Wireless
---

### Post by lacibaci on 2009-04-27
I have two RaLink based cards:

EDIMAX EW-7128G (RaLink RT61)
Foxconn WLL-3350 (RaLink RT2500)

Both of them are really slow.  The transfer rate is in the 1Mbps range no matter what the status shows.  I noticed there were some issues in 8.10 and I was hoping that they would be resolved in 9.04.

Lac

---

### Post by mizunoX on 2009-04-28
> **lacibaci said:**
> I have two RaLink based cards:

EDIMAX EW-7128G (RaLink RT61)
Foxconn WLL-3350 (RaLink RT2500)

Both of them are really slow.  The transfer rate is in the 1Mbps range no matter what the status shows.  I noticed there were some issues in 8.10 and I was hoping that they would be resolved in 9.04.

Lac

I think the driver included with 9.04 is for wireless G only or something... my max connection speed is 54Mb/s since switching to 9.04.

---

### Post by cottfcfan on 2009-04-28
I`m having the same problem with my edimax ew7318usg card.
Strangely though I start off with a download speed of between 5-6mbps, then it quickly fades to less than 1.
This never happened in 8.10, only since i upgraded to 9.04.
May have to downgrade.

---

### Post by lacibaci on 2009-04-28
Is this at least something being looked at?  Both cards show in the fully supported list.  As far as I can tell the default drivers included in Jaunty don't work at all.  As somebody pointed out above, the transfer rate (as measured not what is displayed in network info applet) starts out great but then quickly degrades to sub 1Mbps range.
I did see a hodgepodge of suggestions and howtos but nothing definite.  I don't think using ndis wrapper or building drivers from source is an acceptable solution.

Lac

---

### Post by cottfcfan on 2009-04-28
I wonder if anyone in the know, could tell us whether these network cards should work by default or not in 9.04?
 And if not does anyone know what we need to do?
 Also is it possible to revert back to 8.10 without a full reinstall?
 Any comments would be appreciated.

---

### Post by lacibaci on 2009-04-28
Don't know about reverting to 8.10.  As far as I can tell the last release these cards were working reliably was 8.04.

Lac

---

### Post by ktechman on 2009-04-28
Hve you tried setting the bitrate?

---

### Post by lacibaci on 2009-04-28
Yes I did.  It makes no difference.  I shows (in info 54M) but the real speed is more like 1Mbps.

Lac

---

### Post by ktechman on 2009-04-28
I was afraid of that I am going to abandon 9.04 now for my customers they will get intrepid on the desk and I am trying 8.04 for a laptop to see if the cisco card I have will download any faster.  I believe this is an issue that hasn't gotten much attention, My laptop a Toshiba about a year old went @8 months without wireless because of the ath9k driver needed much work. But in this case the laptop is from 2003, wired works great but...


Regards Ktechman

---

### Post by Mars73 on 2009-04-28
Looks like may have somewhat of the same problem.
I have a Belkin USB G+ adapter (rt73 I believe) and was working great with 8.04 and 8.10 and with a fresh install of 9.04 it seems it's working at 1/4 of the normal speed.
I used to get 10-15Mbps upstairs but now have 1-2 and nothing have changed since 8.04. Changing the channels, burst ack, qos etc doesn't matter.
I'll wait just a little of there will be an update or solution, but if it takes too long I might go back to 8.10.

---

### Post by dolman25 on 2009-04-29
I have a Broadcom Corporation BCM4328 802.11a/b/g/n (rev 03), same problem here.

---

### Post by cottfcfan on 2009-04-29
I Think ive solved my problem.
Initially I upgraded from 8.10 to 9.04. Last night I did a clean install of 9.04 and let it update. It seems to have solved the problem.
This morning I got a constant download rate of 5mbps, which is what I had before.
Its early yet but ill monitor it and post the outcome.

---

### Post by Mars73 on 2009-04-29
> **cottfcfan said:**
> I Think ive solved my problem.
Initially I upgraded from 8.10 to 9.04. Last night I did a clean install of 9.04 and let it update. It seems to have solved the problem.
This morning I got a constant download rate of 5mbps, which is what I had before.
Its early yet but ill monitor it and post the outcome.

Mine was a fresh install as well but speeds are way lower then normal. I will probably install a fresh 8.10 this evening to see if speeds are higher again. Maybe it's got something to do with a newer kernel?

---

### Post by cottfcfan on 2009-04-29
I`ve had a new install now for the last 24hrs and all seems well.
Even now at peak time download speed is steady at about 5mbps. 
 Pleased I haven`t had to regress back to 8.10.
Still can`t really understand the problem but it seems many people on here are having similar issues.

---

### Post by Mars73 on 2009-04-30
Installed 8.10 again yesterday, incl. all updates and connection was a little better but not that much.
I saw it also installed an update for Network Manager, so I removed it and installed WICD and that got me going. Wireless speeds are back to normal again and I'm getting 16/17Mbps upstairs. And it's stable, with 9.04 after some time I got disconnected.
Don't know what the problem is with 9.04, the kernel or network manager or driver but it doesn't like my rt73usb (Belkin G+ usb adapter).

---

### Post by cottfcfan on 2009-05-01
Update...
3 days since fresh install, and old problem is back.
This morning my browser could hardly open my home page, and download speeds are non-existant.
 Works fine wired & windows XP.
This is definately an Ubuntu wireless problem.
 And judging by the amount of posts many people are having the same problem and not just on Jaunty.
 Just hope I don`t have to go back to the dreaded Windows again.

---

### Post by ags0082 on 2009-05-04
Hello,

I'm experiencing the same problem although I'm using a Linksys WMP54G wireless card which utilizes the same RT2500 module.

Initially I had to reset it to 54Mbs and it seemed to work great after a reboot.  But as soon I started download some files, it dropped pretty bad.

My signal strength varies from 68-88 although I have a wireless laptop sitting right next to my PC and its download rates are pretty consistent around: 6684 kbps.  Not very impressive considering my wired desktop downstairs gets around 16000 kbps.

I'm using the speed test out at speakeasy.net.  Here  the rates I'm getting at the moment on my desktop:

Download Speed: 13160 kbps (1645 KB/sec transfer rate)
Upload Speed: 7834 kbps (979.3 KB/sec transfer rate)

This is pretty darn good but it won't last.  The download rate will drop to around 800 if I start up bittorrent.

So I'm pretty curious whats going on with the RT2500 module.  :confused:

---

### Post by davidmohammed on 2009-05-05
network manager still doesn't cope with RT2500 cards very well -

Use synaptic and install wicd.

---

### Post by gocek on 2009-05-05
I have TP-Link TL-WN321G and it actually worked quite ok about a week ago (although it was slow, sometimes pages wouldn't even load, while on Windows Vista everything worked like a charm). Now I'm on LiveCD and it doesn't even connect (doesn't get any DHCP offers). I haven't changed much, only my router's firmware, for a newer one, dunno if it has any impact.

Don't you think it might be connected with the IPv6 thing? Not sure what was it's status in 8.10. Just a thought for experts ;)

BTW: I also have a card on realtek chipset (rtl8180) and it works well, despite weak signal in my room.

---

### Post by daaxix on 2009-05-05
I have a rt2561/rt61 chipset linksys PCI card and after an update last week this started happening to me on Hardy as well.

I had problems in the past, but if I used iwconfig to reset the rate and then the connection I could get normal speeds for awhile.

Now, even that does not work, the connection is stuck at around 1 Mbps no matter what I do.  I even tried reverting to an earlier kernel and it did not fix it.

Any help would be greatly appreciated!  After reading some of the launchpad bugs it seems like this is a chronic issue for the serialmonkey drivers, and they probably will not be backported, which is a shame.  In fact, it seems this issue was fixed a couple of times, then somehow regression kept happening.  Now, it seems to be an issue again in Jaunty.


I guess what I am going to try right now is to use ndiswrapper and blacklist the serialmonkey driver.


iwconfig

> lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"FitchResearch"  
          Mode:Managed  Frequency:2.452 GHz  Access Point: 00:0F:B5:6E:39:9A   
          Bit Rate=54 Mb/s   Tx-Power=16 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality=32/100  Signal level:-68 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


lspci

> 00:00.0 Host bridge: Intel Corporation 82P965/G965 Memory Controller Hub (rev 02)
00:01.0 PCI bridge: Intel Corporation 82P965/G965 PCI Express Root Port (rev 02)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 02)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HB/HR (ICH8/R) LPC Interface Controller (rev 02)
00:1f.2 RAID bus controller: Intel Corporation 82801 SATA RAID Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation G71 [GeForce 7300 GS] (rev a1)
03:00.0 SATA controller: JMicron Technologies, Inc. JMB361 AHCI/IDE (rev 02)
03:00.1 IDE interface: JMicron Technologies, Inc. JMB361 AHCI/IDE (rev 02)
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)
05:00.0 Network controller: RaLink RT2561/RT61 802.11g PCI
05:01.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 05)
05:01.1 Input device controller: Creative Labs SB Live! Game Port (rev 05)
05:04.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 80)

dmesg | grep wlan

 > 169.340617] wlan0: associated
[  216.608121] wlan0: authenticate with AP 00:0f:b5:6e:39:9a
[  216.751803] wlan0: authenticated
[  216.751810] wlan0: associate with AP 00:0f:b5:6e:39:9a
[  216.950809] wlan0: associate with AP 00:0f:b5:6e:39:9a
[  217.128475] wlan0: RX ReassocResp from 00:0f:b5:6e:39:9a (capab=0x401 status=0 aid=4)

---

### Post by mrg201 on 2009-05-12
I have had the same problems for all the recent Ubuntu distributions. It used to be easy to work around (before the serial monkey rt2500 driver was incorporated into the kernel):

All you had to do was install the daily rt2500 CVS tarball, uninstall network manager and install either Wicd or Rutilt and everything would be fine.

Therefore, I thought the fix for this would be as simple as uninstalling network manager and installing either of Wicd or Rutilt, however, neither of them do any better - they all give roughly 50-70% connection strength and ~25Kb download speeds on an 8MB connection.

Thus it would seem that network manager has finally been sorted and now the driver included in the kernel is the problem? But I am unsure how to change the driver now.

---

### Post by bj0 on 2009-06-15
I was trying to figure out this problem recently.

The setup I have is:  A wired network with my main desktop (ubuntu 9.04) with a wireless router and a wireless media PC (kubuntu 8.04 lts).

The media PC has a pci ralink card using the rt61pci module.  I've never had any problems sending files from my desktop to the media pc, it transfers fast (MB/s), but when I try to transfer something from the media PC to my desktop, I was getting 80kB/s.  This is ridiculously slow for a local network

I tried searching for info, but this thread is the only relevant thing I've come across so far.  Has anyone figured out what is causing this yet? 

I've tried installing WICD, but it had no effect on the transfer speeds.

I've been using iperf to measure bandwidth between the two computers, and I get ~ 9 Mbit/s in one direction and 700Kbit/s in the other.

Progress:
Ok I found a thread saying that ubuntu automatically sets the "rate" setting of ralink wireless cards to 1m/s, and I noticed (iwconfig wlan0) that the rate was currently set to that.

I manually set it with  "sudo iwconfig wlan0 rate 54M" (or 11M).

And that gave me a little speed boost.  Now, with iperf, I get 12 Mbit/s in one direction and 5 Mbit/s in the other.  It is definitely better than before, but I still don't understand why one direction is half the speed of the other...

Any news on this issue?

EDIT: I tried the same speed tests on a wireless laptop using Ubuntu 9.04 and:
Network controller: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection (rev 05) 
using ipw2200

It got 20Mbit/s both directions, so I'm fairly certain there's nothing wrong with the network...

---

### Post by RavanH on 2009-07-12
> **lacibaci said:**
> I have two RaLink based cards:

EDIMAX EW-7128G (RaLink RT61)
Foxconn WLL-3350 (RaLink RT2500)

Both of them are really slow.  The transfer rate is in the 1Mbps range no matter what the status shows.  I noticed there were some issues in 8.10 and I was hoping that they would be resolved in 9.04.

Lac

Please check out my fix on [http://ubuntuforums.org/showthread.php?p=7605785#post7605785](http://ubuntuforums.org/showthread.php?p=7605785#post7605785) which involves switching to Wicd plus a small pre-connection script! 

Let me know if it works or not :)

---

