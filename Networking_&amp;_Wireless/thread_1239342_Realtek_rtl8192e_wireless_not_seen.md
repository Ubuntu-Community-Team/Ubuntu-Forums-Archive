---
title: "Realtek rtl8192e wireless not seen"
date: 2009-08-13
forum: Networking &amp; Wireless
---

### Post by tonyps on 2009-08-13
**[B]Realtek rtl8192e wireless concerns**[/B] 			 			 			 		  		 		 			 			Here it is...
lspci -nn

**02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. Device [10ec:8192] (rev 01)**
03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 02)

So, I have read through and tried pretty much all of the suggestions/procedures for getting the wireless working, with no success...the wired works great....
If anyone has any other useful suggestions or success at getting this to work, I would greatly appreciate you chiming in here...

Thanks again,
Tony ...

---

### Post by valros on 2009-11-03
Bump, I just bought a brand new laptop, Toshiba L505-S5990. It comes with Realtek RTL8192E as a network card and it is not being recognized, please someone solve this.

---

### Post by mjerkovic on 2009-11-03
I am having the same problem.  I have also followed the numerous suggestions in other threads but I still cannot see the wireless card.

I am running the 64-bit version of 9.04.  My plan this weekend is to try and upgrade to 9.10 and follow the same process again to see if that fixes it.

I read somewhere that the kernel shipped with 9.10 has a driver in the staging area that might work with the 8192 chipset??

---

### Post by Dude-PWB- on 2009-11-12
I just got my 8192e wireless working with ndiswrapper and the windows xp drivers from the realtek site. They seem to work well.

Not what i really wanted but here's to hoping we can get this chipset supported in the linux community.

---

### Post by tonyps on 2009-11-12
Thanks for the response! I had tried this in the past with no success. I am running the 64bit version of Ubuntu 9.0.4, so I am wondering if this might have something to do with it. Maybe that and the fact that I am not knowledgable on how to correctly accomplish the ndiswrapper thing....
Were the drivers you used new ones? for 64 bit OS? Does it matter?

Thanks,

Tony ...

---

### Post by Dude-PWB- on 2009-11-12
Well, there wasn't an option to download 64bit drivers (that I recall). But, I was/am using the 32bit version of ubuntu booting off a live usb key.

The simplest way to explain it is that I installed ndiswrapper from the synaptic package manager, downloaded the appropriate windows drivers from the realtek site, extracted them to a folder on the desktop, opened ndiswrapper from System>Administration and simply clicked add driver, navigated to my folder on the desktop, located the windows xp driver and even though it popped up a couple errors, the wireless took right off and found all my nearby access points.

However, once I finally got online with my wireless, I sent an e-mail to realtek asking them if they had any future plans to support this adapter in linux.

And to my surprise, about 3 hours later, not only did I get a reply from realtek, but they attached the linux driver to the e-mail.

I haven't tried it yet, and not sure if we are allowed to attach drivers/files to the forum, but I am planning on trying them again tomorrow when I have more time. I will report back with my success/failures on that end.

Untill then, the windows xp driver and ndiswrapper are working fine.

---

### Post by Dude-PWB- on 2009-11-13
Well, unfortunately, the realtek supplied linux drivers did not work.

From what i have been able to find out so far, is that there is something new in the 2.6.31 kernel that does not allow the drivers to compile properly.

I have tried to get them to compile the only way my limited experience knows how.

Here are my errors, in case anyone else knows how to make this work for me. It was from a Live USB install.

```
ubuntu@ubuntu:~/Desktop/rtl8192e_linux_2.6.0008.0106.2009$ sudo make
make[1]: Entering directory `/usr/src/linux-headers-2.6.31-14-generic'
  CC [M]  /home/ubuntu/Desktop/rtl8192e_linux_2.6.0008.0106.2009/ieee80211/ieee80211_rx.o
  CC [M]  /home/ubuntu/Desktop/rtl8192e_linux_2.6.0008.0106.2009/ieee80211/ieee80211_softmac.o
  CC [M]  /home/ubuntu/Desktop/rtl8192e_linux_2.6.0008.0106.2009/ieee80211/ieee80211_tx.o
  CC [M]  /home/ubuntu/Desktop/rtl8192e_linux_2.6.0008.0106.2009/ieee80211/ieee80211_wx.o
/home/ubuntu/Desktop/rtl8192e_linux_2.6.0008.0106.2009/ieee80211/ieee80211_wx.c: In function ‘ieee80211_wx_get_encode_ext_rsl’:
/home/ubuntu/Desktop/rtl8192e_linux_2.6.0008.0106.2009/ieee80211/ieee80211_wx.c:846: warning: suggest parentheses around operand of ‘!’ or change ‘&’ to ‘&&’ or ‘!’ to ‘~’
  CC [M]  /home/ubuntu/Desktop/rtl8192e_linux_2.6.0008.0106.2009/ieee80211/ieee80211_module.o
/home/ubuntu/Desktop/rtl8192e_linux_2.6.0008.0106.2009/ieee80211/ieee80211_module.c: In function ‘alloc_ieee80211_rsl’:
/home/ubuntu/Desktop/rtl8192e_linux_2.6.0008.0106.2009/ieee80211/ieee80211_module.c:121: error: ‘struct net_device’ has no member named ‘hard_start_xmit’
make[2]: *** [/home/ubuntu/Desktop/rtl8192e_linux_2.6.0008.0106.2009/ieee80211/ieee80211_module.o] Error 1
make[1]: *** [_module_/home/ubuntu/Desktop/rtl8192e_linux_2.6.0008.0106.2009/ieee80211] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.31-14-generic'
make: *** [all] Error 2
```And:

```
ubuntu@ubuntu:~/Desktop/rtl8192e_linux_2.6.0008.0106.2009$ sudo su
root@ubuntu:/home/ubuntu/Desktop/rtl8192e_linux_2.6.0008.0106.2009# make
make[1]: Entering directory `/usr/src/linux-headers-2.6.31-14-generic'
  CC [M]  /home/ubuntu/Desktop/rtl8192e_linux_2.6.0008.0106.2009/ieee80211/ieee80211_module.o
/home/ubuntu/Desktop/rtl8192e_linux_2.6.0008.0106.2009/ieee80211/ieee80211_module.c: In function ‘alloc_ieee80211_rsl’:
/home/ubuntu/Desktop/rtl8192e_linux_2.6.0008.0106.2009/ieee80211/ieee80211_module.c:121: error: ‘struct net_device’ has no member named ‘hard_start_xmit’
make[2]: *** [/home/ubuntu/Desktop/rtl8192e_linux_2.6.0008.0106.2009/ieee80211/ieee80211_module.o] Error 1
make[1]: *** [_module_/home/ubuntu/Desktop/rtl8192e_linux_2.6.0008.0106.2009/ieee80211] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.31-14-generic'
make: *** [all] Error 2
```So unfortunately the realtek linux drivers will not work for me.

The windows drivers will work with ndiswrapper, but I would be much happier if there was a straight up linux driver for this wireless device. Using a windows driver in my linux install almost makes me feel dirty. :redface:

---

### Post by daxasasw on 2009-11-13
I think this is enough .....
I do agree with you. Those are the most effective way

---

### Post by BizCasFri on 2009-11-15
So I was able to get the XP64bit driver working in a manual ndiswrapper install. When I run a ndiswrapper -l check, I get the following message:
```
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
net819xp : driver installed
    device (10EC:8192) present
```I then ran, on the advice of the ndiswrapper wifidocs page:
```
sudo depmod -a
sudo modprobe ndiswrapper
```Nothing showed up in the terminal when I ran both commands and still there is no ath0 when I run iwconfig. I still get this:
```
lo        no wireless extensions.

eth0      no wireless extensions.
```I'm gonna try another driver but it's not looking good so far...
(EDIT: tried 32 bit with same steps with same results)

---

### Post by BizCasFri on 2009-11-16
So... I feel like an idiot. I shut down my laptop earlier today, and now upon booting it, my wireless works! 

The driver can be found [here.](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=9&PFid=9&Level=6&Conn=5&DownTypeID=3&GetDown=false&Downloads=true#RTL8192E)

Then follow the standard install procedure found [here](http://www.linuxquestions.org/linux/answers/Networking/NdisWrapper_The_Ultimate_Guide/)

Then reboot. Great success!

---

### Post by Dude-PWB- on 2009-11-16
Another update of sorts for this chipset.

I replied to realtek with my issues with the last driver they sent me, dated 0106.2009 and included my errors from the terminal, and my research into why that particular driver would not compile. 

They have now replied back with a new driver attached dated 1029.2009. Hopefully this one will compile properly and work so that we can get away from ndiswrapper. They seem very eager to help and support this chipset in linux.

I will give this driver a try today and report back with my results.

---

### Post by Dude-PWB- on 2009-11-16
Success!

The new driver from realtek works fine, and better than the windows driver through ndiswrapper.

The file size is too large to upload here so I'm not sure what avenues I can take to get this driver to anyone that needs/wants it. If a mod or admin can tell me where I can/should upload this driver, please reply or send me a PM.

I may just set up a rapidshare link or something if there is no better option.

I will post back later with the link to download, depending on what I figure out.

---

### Post by Dude-PWB- on 2009-11-16
Ok, I have uploaded it to rapidshare for the time being. Unfortunately I don't have a rapidshare account so their site says it can be downloaded 10 times.

Hopefully that will be enough to find somewhere more permanent to host the file for those that need it.

Link: [http://rapidshare.com/files/307935870/rtl8192e_linux_2.6.0011.1029.2009.tar.gz.html](http://rapidshare.com/files/307935870/rtl8192e_linux_2.6.0011.1029.2009.tar.gz.html)

MD5: 379F53A4B81A478506A64E49FDBC8126 


And, for anyone that would like to know the steps I went through to compile and install the driver, here is what I did. Not sure if I made too many steps or not enough, but my experience is still limited with linux. It worked for me, hopefully it will work for everyone else.

First, I downloaded the file and extracted it to a folder.

Then since I was using the windows wireless driver with ndiswrapper, I opened network manager, and disconnected from my router.

Then I opened ndsiwrapper and removed the windows driver. Then went to synaptic and removed the three entries for ndsiwrapper. I marked them for complete removal so there was no chance of the ndiswrapper driver hanging on to the wireless device.

Then rebooted and and checked to make sure my wireless was no longer detected.

Then open a terminal, and cd to the folder where the driver is extracted.

Then.

```
sudo make
```then it compiled, but 'sudo make install' gave errors, so i did.

```
sudo su
```and that gave me a root prompt, then.

```
make install
```Then rebooted again.

When it rebooted, it didn't detect my wireless, but lspci -vv showed my wireless device using the new driver. So, after a few attempts at trying to start up the wireless, I finally, from a terminal, cd to the driver directory again, then.

```
sudo ./wlan0up
```And away it went. Connected and working.

Haven't tried another reboot yet to see if it will automatically detect it on subsequent  boots, but that will be the next order of business.

Good luck everyone!

---

### Post by tonyps on 2009-11-17
Evening,
Toshiba A505D-S6958
RTL8192e
AMD Turion X2
ATI Radeon
4GB RAM
Ubuntu 9.0.4

Thanks!! I downloaded it, followed your instructions and it seems to be doing well. Ony a few questions though...
1. My RTL8192e is seen as WLAN1 when I run iwconfig:
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

wlan1     802.11bgn  Nickname:"rtl8192E"
          Mode:Managed  Frequency=2.422 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   
          Retry:on   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=10/100  Signal level=0 dBm  Noise level=-100 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

Should I set the wireless config for Ad hoc or Infrastructure?  ON my home network it connects with WEP and is set to infrastructure...When I tried it at work, connections were very hard to maintain even thoug there was a strong signal. Our wireless guest network there does not use security but is limited with what you can access...
Thanks again, looking forward to hearing more good news!!
Tony ...

---

### Post by Dude-PWB- on 2009-11-17
Don't have an answer for why it is wlan1 instead of wlan0, but I don't think it really matters as long as it works. It could possibly be that ndiswrapper may still have ahold of wlan0.

I think the ad-hoc/infrastructure setting is more of a router side setting rather than a driver setting, however i'm not completely clear on that.

My wireless wouldn't automatically start on boot and I had to start it manually every time. I have since installed wicd from the repositories and it in turn removes network manager, I'm hoping that will solve my isseue.

---

### Post by BizCasFri on 2009-11-18
I shall try this on my Toshiba u500 later today and give you an update.

---

### Post by Dude-PWB- on 2009-11-18
OK! Figured it out!

Once the driver is installed, to get the wireless to start on boot you need to edit your /etc/modules file.

```
sudo gedit /etc/modules
```

Then simply add r8192e_pci on a line and save the file.

```
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.
r8192e_pci
```

When you reboot, your wireless should start automatically.

---

### Post by BizCasFri on 2009-11-18
So, I'm having some problems with it. The driver installed, following the instructions, and having to do a ./wlan0up each time, but when I do, it doesn't find any networks where I know there are some. Also adding that line to the modules file does not do anything for me, and I have to do a ./wlan0up each time, and it doesn't find any networks anyways.

Back to ndiswrapper for me I guess...

---

### Post by Dude-PWB- on 2009-11-18
I wonder if it has to do with you using 64bit and this is the 32bit driver?

Did you make sure you removed ndiswrapper (complete removal) and reboot so ndiswrapper lets go of the device?

I also removed network manager and installed wicd in an earlier step, wonder of that would help?

You might want to do like me and e-mail realtek and see if they have a 64 bit driver, that might be the issue on its own.

It should work, I'm sure we can find a way.

---

### Post by mltriebe on 2009-11-18
> **Dude-PWB- said:**
> 

Link: [http://rapidshare.com/files/307935870/rtl8192e_linux_2.6.0011.1029.2009.tar.gz.html](http://rapidshare.com/files/307935870/rtl8192e_linux_2.6.0011.1029.2009.tar.gz.html)

MD5: 379F53A4B81A478506A64E49FDBC8126 




File will not download any more, says it was downloaded to many times.  Can you upload it again.  That is what it said you need to do.

Thanks, Mike

---

### Post by Dude-PWB- on 2009-11-18
> **mltriebe said:**
> File will not download any more, says it was downloaded to many times.  Can you upload it again.  That is what it said you need to do.

Thanks, Mike

Here you go, 10 more times I guess. :)

[http://rapidshare.com/files/309017559/rtl8192e_linux_2.6.0011.1029.2009.tar.gz.html](http://rapidshare.com/files/309017559/rtl8192e_linux_2.6.0011.1029.2009.tar.gz.html)


 MD5: 379F53A4B81A478506A64E49FDBC8126

---

### Post by mltriebe on 2009-11-20
Thanks, driver works great but I still had an issue with the computer locking up after a few minutes of wifi use.  I got this from a google search.

This is a common issue on x86_64 with >4GB memory mapped for doing 32 bit DMA transfers using an IOMMU (can be emulated via software like in your case [intel], or via hardware[amd]) when some driver leak memory.

And the fix was to add the following to grub.

One more tip, your problem will dissapear completely if boot your system with "mem=4G iommu=off". Of course, your system will have only ~3.3GB of RAM instead of 8G.

Mike

---

### Post by pcdragon on 2009-11-21
Thanks Dude for posting this and sharing the driver.  I have it working with the following:

Kubuntu 9.10 32-Bit
Toshiba L500 laptop

Needed to uninstall network-manager. I don't have wicd installed.

Because I have WPA-PSK (TKIP) setup on my router I installed the standard kubuntu wpasupplicant package and copied /usr/share/doc/wpasupplicant/examples/wpa-psk-tkip.conf to /etc/wpa_supplicant/wpa_supplicant.conf then edited it to suit.

I added the following lines to /etc/network/interfaces:

```

auto wlan0
iface wlan0 inet dhcp
wpa-driver wext
wpa-conf /etc/wpa_supplicant/wpa_supplicant.conf

```


Added the following line to /etc/modules:
```

r8192e_pci

```

Rebooted and it worked fine. Thanks again for solving this issue.

cheers

---

### Post by yutani on 2009-11-24
Hello Dude,

I just bought a Samsung N120 with the Realtek RTL8192E and can't get
the WLAN to work under Ubuntu.
Can you please upload the driver for me.
I have my own FTP-Site, so you can (if you want) upload it to:

[ftp://magica.selfip.net/incoming](ftp://magica.selfip.net/incoming)

Thanks a lot!!!

Regards

yutani

---

### Post by tonyps on 2009-11-24
I must be seeing something different with this Toshiba. I cannot seem to get the 8192e to come up reliably, even using that latest Linux driver, following the instructions. My home router uses WEP, if that makes a difference.
Also, not that I am sure this matters, but my WLAN keeps getting seen as WLAN1....when it can be seen...
I was attempting to use NDIS but had no luck there....
Toshiba A505D-S6958
AMD Tuion-X2
4GB RAM
Realtek 8192e wireless (b/g/n)
ATI Radeon 3100
Ubuntu 9.1.0 64 bit(recent upgrade)
 
Any assistance greatly appreciated...
 
Tony ...

---

### Post by northd_tech on 2009-11-24
Hi Tony.  I haven't been able to get the Realtek 8192E to work with 64 bit Windows drivers (or by compiling the source code either) on a relative's Toshiba Satellite P505D laptop.  I was able to get it to install using the older 32-bit drivers under 32-bit Ultimate Ubuntu 2.3 (based on 9.04 Jackalope).  Here is what I posted on another thread here:

[http://ubuntuforums.org/showpost.php?p=8173982&postcount=3](http://ubuntuforums.org/showpost.php?p=8173982&postcount=3)

Unfortunately, his Linux install got corrupted somehow on a dual-boot Vista, so we just upgraded to the newer Ultimate Ubuntu 2.4 (based on ubuntu 9.10) in 64-bit, and now I can't get the WiFi to work with the newer 64-bit OS either.  This new kernel is listed as:
2.6.31-15-generic #50-Ubuntu SMP Tue Nov 10 14:53:52 UTC 2009 x86_64 GNU/Linux

I did briefly see device "wlan0", but it said it was disabled when I ran an "iwconfig" command.  The source code method is described on this Samsung N120 thread:

[http://ubuntuforums.org/showthread.php?t=1191590](http://ubuntuforums.org/showthread.php?t=1191590)

As near as I can tell, this is only/mainly? a problem for the 64-bit OS and drivers (the 32-bit Ubuntu wireless worked great for weeks in the new P505D Toshiba).  I've found some newer Vista and Windows 7 drivers, and I may try to mix and match something there (but I remember that being a good way to freeze a 64-bit Linux when we experimented before).

Good Luck (esp. if it's a 64-bit version).

EDIT:  The 8192**SE **source code was throwing error messages at me when I tried compiling that earlier, so I'm not convinced those chipsets are compatible.  The 8192 **E** sourcecode from this German site did eventually compile (but still no 64-bit wireless "wlan0" device functioning- it showed "disabled" and then disappeared after a reboot).

[http://forum.ubuntuusers.de/topic/samsung-n510-und-ubuntu/3/#post-2247165](http://forum.ubuntuusers.de/topic/samsung-n510-und-ubuntu/3/#post-2247165)

This looks to be the fix, thanks to chili555:

[http://ubuntuforums.org/showthread.php?t=1329254](http://ubuntuforums.org/showthread.php?t=1329254)

More good tips for Realtek WiFi are here:

[http://forum.novatech.co.uk/showthread.php?t=15068](http://forum.novatech.co.uk/showthread.php?t=15068)

---

### Post by mtah on 2009-12-04
> **Dude-PWB- said:**
> Here you go, 10 more times I guess. :)

[http://rapidshare.com/files/309017559/rtl8192e_linux_2.6.0011.1029.2009.tar.gz.html](http://rapidshare.com/files/309017559/rtl8192e_linux_2.6.0011.1029.2009.tar.gz.html)


 MD5: 379F53A4B81A478506A64E49FDBC8126

Link's down again. Could you perhaps upload the driver again to a more available location - at least just attach it here if possible? :)

---

### Post by Dude-PWB- on 2009-12-09
The file is too large to upload here. But here is a new link again.

Remember this is the 32bit version of the driver, you will have to e-mail realtek for the 64bit version.

[http://rapidshare.com/files/318722694/rtl8192e_linux_2.6.0011.1029.2009.tar.gz.html](http://rapidshare.com/files/318722694/rtl8192e_linux_2.6.0011.1029.2009.tar.gz.html)


 MD5: 379F53A4B81A478506A64E49FDBC8126

---

### Post by chellrose on 2009-12-11
Dude-PWB-,

I downloaded the driver and followed your instructions.  No errors when I do
```
sudo ./wlan0up
```
but no connections either.  There is no wlan0 listed by iwconfig, and when I tried to set the essid using
```

sudo iwconfig wlan0 essid <ESSID>

```
it gave me the error:
```

Error for wireless request "Set ESSID" (8B1A) :
    SET failed on device wlan0 ; No such device.

```

The link is for a 32 bit driver, correct?  I've tried ndiswrapper also with no success.  I have a Realtek 8172 on a Toshiba T135-S1309, running Ubuntu 9.10 32-bit.  Extensive Googling has revealed nothing for the 8172 except that it's _supposed_ to work with the 8192e drivers.  Do you have any other suggestions?

I've never done this before -- on my old laptop (Atheros card) the wireless worked out of the box.

Thanks! =)

---

### Post by Dude-PWB- on 2009-12-12
> **Sissy13 said:**
> Dude-PWB-,

I downloaded the driver and followed your instructions.  No errors when I do
```
sudo ./wlan0up
```but no connections either.  There is no wlan0 listed by iwconfig, and when I tried to set the essid using
```

sudo iwconfig wlan0 essid <ESSID>

```it gave me the error:
```

Error for wireless request "Set ESSID" (8B1A) :
    SET failed on device wlan0 ; No such device.

```The link is for a 32 bit driver, correct?  I've tried ndiswrapper also with no success.  I have a Realtek 8172 on a Toshiba T135-S1309, running Ubuntu 9.10 32-bit.  Extensive Googling has revealed nothing for the 8172 except that it's _supposed_ to work with the 8192e drivers.  Do you have any other suggestions?

I've never done this before -- on my old laptop (Atheros card) the wireless worked out of the box.

Thanks! =)

If you are absolutely sure about which wireless device you have, I would e-mail realtek and ask them for the driver, that's all I did, and they were quite quick about it too.

However, that card seems to be one that I have not yet seen. Make sure you check the networking section of 'lspci -vv' closely to determine the proper chipset.

---

### Post by chellrose on 2009-12-12
> **Dude-PWB- said:**
> If you are absolutely sure about which wireless device you have, I would e-mail realtek and ask them for the driver, that's all I did, and they were quite quick about it too.

However, that card seems to be one that I have not yet seen. Make sure you check the networking section of 'lspci -vv' closely to determine the proper chipset.

Thanks!  I'd been doing lspci without the '-vv', and it wasn't all that informative.

Can someone tell me how to pull the chipset information out of this mess?  Here is the relevant section of 'lspci -vv':

```

08:00.0 Network controller: Realtek Semiconductor Co., Ltd. Device 8172 (rev 10)
    Subsystem: Realtek Semiconductor Co., Ltd. Device 8181
    Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Interrupt: pin A routed to IRQ 5
    Region 0: I/O ports at 3000 [disabled] [size=256]
    Region 1: Memory at c0100000 (32-bit, non-prefetchable) [disabled] [size=16K]
    Capabilities: [40] Power Management version 3
        Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=375mA PME(D0+,D1+,D2+,D3hot+,D3cold-)
        Status: D0 PME-Enable- DSel=0 DScale=0 PME-
    Capabilities: [50] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
        Address: 0000000000000000  Data: 0000
    Capabilities: [70] Express (v1) Legacy Endpoint, MSI 00
        DevCap:    MaxPayload 256 bytes, PhantFunc 0, Latency L0s <512ns, L1 <64us
            ExtTag- AttnBtn- AttnInd- PwrInd- RBE+ FLReset-
        DevCtl:    Report errors: Correctable- Non-Fatal- Fatal- Unsupported-
            RlxdOrd+ ExtTag- PhantFunc- AuxPwr- NoSnoop-
            MaxPayload 128 bytes, MaxReadReq 512 bytes
        DevSta:    CorrErr+ UncorrErr- FatalErr- UnsuppReq+ AuxPwr- TransPend-
        LnkCap:    Port #0, Speed 2.5GT/s, Width x1, ASPM L0s L1, Latency L0 <512ns, L1 <64us
            ClockPM- Suprise- LLActRep- BwNot-
        LnkCtl:    ASPM L0s L1 Enabled; RCB 64 bytes Disabled- Retrain- CommClk+
            ExtSynch- ClockPM- AutWidDis- BWInt- AutBWInt-
        LnkSta:    Speed 2.5GT/s, Width x1, TrErr- Train- SlotClk+ DLActive- BWMgmt- ABWMgmt-
    Capabilities: [100] Advanced Error Reporting <?>
    Capabilities: [140] Virtual Channel <?>
    Capabilities: [160] Device Serial Number 00-e0-4c-ff-fe-22-55-88

```

Thanks! =)

---

### Post by Dude-PWB- on 2009-12-12
> **Sissy13 said:**
> Thanks!  I'd been doing lspci without the '-vv', and it wasn't all that informative.

Can someone tell me how to pull the chipset information out of this mess?  Here is the relevant section of 'lspci -vv':

```

08:00.0 Network controller: Realtek Semiconductor Co., Ltd. Device 8172 (rev 10)
    Subsystem: Realtek Semiconductor Co., Ltd. Device 8181
    Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Interrupt: pin A routed to IRQ 5
    Region 0: I/O ports at 3000 [disabled] [size=256]
    Region 1: Memory at c0100000 (32-bit, non-prefetchable) [disabled] [size=16K]
    Capabilities: [40] Power Management version 3
        Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=375mA PME(D0+,D1+,D2+,D3hot+,D3cold-)
        Status: D0 PME-Enable- DSel=0 DScale=0 PME-
    Capabilities: [50] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
        Address: 0000000000000000  Data: 0000
    Capabilities: [70] Express (v1) Legacy Endpoint, MSI 00
        DevCap:    MaxPayload 256 bytes, PhantFunc 0, Latency L0s <512ns, L1 <64us
            ExtTag- AttnBtn- AttnInd- PwrInd- RBE+ FLReset-
        DevCtl:    Report errors: Correctable- Non-Fatal- Fatal- Unsupported-
            RlxdOrd+ ExtTag- PhantFunc- AuxPwr- NoSnoop-
            MaxPayload 128 bytes, MaxReadReq 512 bytes
        DevSta:    CorrErr+ UncorrErr- FatalErr- UnsuppReq+ AuxPwr- TransPend-
        LnkCap:    Port #0, Speed 2.5GT/s, Width x1, ASPM L0s L1, Latency L0 <512ns, L1 <64us
            ClockPM- Suprise- LLActRep- BwNot-
        LnkCtl:    ASPM L0s L1 Enabled; RCB 64 bytes Disabled- Retrain- CommClk+
            ExtSynch- ClockPM- AutWidDis- BWInt- AutBWInt-
        LnkSta:    Speed 2.5GT/s, Width x1, TrErr- Train- SlotClk+ DLActive- BWMgmt- ABWMgmt-
    Capabilities: [100] Advanced Error Reporting <?>
    Capabilities: [140] Virtual Channel <?>
    Capabilities: [160] Device Serial Number 00-e0-4c-ff-fe-22-55-88

```Thanks! =)

Hmm, don't see the wireless listed there at all.

What is the output of lsusb? Maybe you have a usb wireless adapter?

---

### Post by chellrose on 2009-12-12
That's not my wireless card?  Hmm... I have an Atheros device too, but it's listed as an ethernet adapter, which I'm guessing means wired internet.

Edit: I finally figured out how to find the information in Windoze (my laptop is dual-boot Ubuntu and Win7).  Windows tells me that I have a "Realtek RTL8191SE Wireless LAN 802.11n PCI-E NIC".  Hmm... maybe I should be looking for an 8191 driver rather than the 8192 provided here?

lsusb yields

```

Bus 002 Device 005: ID 0781:7450 SanDisk Corp. Sansa C250
Bus 002 Device 003: ID 04f2:b19a Chicony Electronics Co., Ltd 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 002: ID 093a:2510 Pixart Imaging, Inc. 
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```Right now I have an mp3 player plugged in (the SanDisk) and a mouse, so those explain two of the entries...

---

### Post by Dude-PWB- on 2009-12-13
> **Sissy13 said:**
> That's not my wireless card?  Hmm... I have an Atheros device too, but it's listed as an ethernet adapter, which I'm guessing means wired internet.

Edit: I finally figured out how to find the information in Windoze (my laptop is dual-boot Ubuntu and Win7).  Windows tells me that I have a "Realtek RTL8191SE Wireless LAN 802.11n PCI-E NIC".  Hmm... maybe I should be looking for an 8191 driver rather than the 8192 provided here?

lsusb yields

```

Bus 002 Device 005: ID 0781:7450 SanDisk Corp. Sansa C250
Bus 002 Device 003: ID 04f2:b19a Chicony Electronics Co., Ltd 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 002: ID 093a:2510 Pixart Imaging, Inc. 
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```Right now I have an mp3 player plugged in (the SanDisk) and a mouse, so those explain two of the entries...

Ahh, ok, the SE adapter, that explains why the drivers were not working.

Check out this link here.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/401126](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/401126)

---

### Post by chellrose on 2009-12-14
\\:D/ Hurray!!! Wireless seems to be working now, finally.  Thank you for your help!

Two small questions...
1. I installed the WinXP driver using ndiswrapper.  The .inf and .sys files are currently sitting on my desktop.  Can I move or delete them, or would that seriously screw things up?

2. I prefer to use the command line to connect rather than the network manager, if possible.  I know that I need to add wlan0 and the essid to /etc/network/interfaces.  Do I need to add anything in any other location in order to do that?

Thanks again! :D

---

### Post by lukasz__20 on 2009-12-21
> **Dude-PWB- said:**
> The file is too large to upload here. But here is a new link again.

[http://rapidshare.com/files/318722694/rtl8192e_linux_2.6.0011.1029.2009.tar.gz.html](http://rapidshare.com/files/318722694/rtl8192e_linux_2.6.0011.1029.2009.tar.gz.html)

 MD5: 379F53A4B81A478506A64E49FDBC8126

Link's down again. Could you upload the driver again or send to my email [email]lukasz__17@interia.pl[/email]?

---

### Post by lotharmat on 2009-12-22
I emailed Realtek on Friday and asked them for the 32 and 64 bit drivers.

They emailed be back on Monday with both drivers!

When I get home - I'll upload them to my webspace (NTLworld - So fingers crossed)

---

### Post by Eduardo Mercovich on 2009-12-26
> **lotharmat said:**
> I emailed Realtek on Friday and asked them for the 32 and 64 bit drivers. They emailed be back on Monday with both drivers!

Did you uploaded somewhere? Realtek's site seems down right now...

I have the same issue here: Samsung N130, UNR 9.1, doesn't see the wireless card, Realtek driver from Samsung doesn't work, and  working now with a wired link to my router (already saw what seems to be all threads until today, 26/12/09).

Just for the records, it seems this Samsung has a Realtek 8192 rev 0.1.

lspci -vv says>
[QUOTE]02:00.0 Network controller: Realtek Semiconductor Co., Ltd. Device 8192 (rev 01)
	Subsystem: Askey Computer Corp. Device 7160
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 11
	Region 0: I/O ports at 2000 [size=256]
	Region 1: Memory at f0100000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: [40] Power Management version 3
		Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=375mA PME(D0-,D1+,D2+,D3hot+,D3cold-)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-
	Capabilities: [50] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
		Address: 0000000000000000  Data: 0000
	Capabilities: [70] Express (v1) Legacy Endpoint, MSI 00
		DevCap:	MaxPayload 256 bytes, PhantFunc 0, Latency L0s <128ns, L1 <2us
			ExtTag- AttnBtn- AttnInd- PwrInd- RBE+ FLReset-
		DevCtl:	Report errors: Correctable- Non-Fatal- Fatal- Unsupported-
			RlxdOrd+ ExtTag- PhantFunc- AuxPwr- NoSnoop-
			MaxPayload 128 bytes, MaxReadReq 512 bytes
		DevSta:	CorrErr+ UncorrErr- FatalErr- UnsuppReq+ AuxPwr- TransPend-
		LnkCap:	Port #0, Speed 2.5GT/s, Width x1, ASPM L0s L1, Latency L0 <512ns, L1 <64us
			ClockPM+ Suprise- LLActRep- BwNot-
		LnkCtl:	ASPM L0s L1 Enabled; RCB 64 bytes Disabled- Retrain- CommClk+
			ExtSynch- ClockPM+ AutWidDis- BWInt- AutBWInt-
		LnkSta:	Speed 2.5GT/s, Width x1, TrErr- Train- SlotClk+ DLActive- BWMgmt- ABWMgmt-
	Capabilities: [100] Advanced Error Reporting <?>
	Capabilities: [140] Virtual Channel <?>
	Capabilities: [160] Device Serial Number 00-26-b6-ff-fe-25-49-84

Thanks a lot for sharing, regards... :-)

--
EM

---

### Post by Eduardo Mercovich on 2009-12-27
Ok guys, just solved. :-)

Today Realtek site was up, so I got the few 8192 drivers that saw there, and tried them with a standard ndiswrapper install of UNR (ubuntu netbook remix) 9.10, installing with the ndiswrapper GUI, ndisgtk.

The first one worked, even if it says that it can't see if the hardware is present. :-)

I am uploading it to 
[http://mercovich.net/ubuntu/819xP_WindowsDriver_1677.1.0708.2009.zip](http://mercovich.net/ubuntu/819xP_WindowsDriver_1677.1.0708.2009.zip) 
so we all have it available while we need it. 

Of course, a native driver would be better, but in the meantime, we can enjoy and work.

Best regards...


PD: since some people still have troubles, I don't mark the thread as solved. Is this OK?&#777;
--
EM

---

### Post by Tigerbright on 2009-12-31
Hi Guys,

Long time lurker, first time poster.

As a proviso I should state that I am more of a mac than Linux aficionado so please don't think I'm a Linux expert. I am learning what I can though ;)

I started looking for a solution to the wifi problem after installing Linux (Kubuntu) on my Uk model Samsung N140 and seeing that the wifi card didn't work. 

I didn't like the ndiswrapper solution so in the end I contacted the manufacturer (RealTek) and was pleasantly surprised to receive a reply and driver within a few hours.

Below is the latest driver that they have for the RealTek rtl8192e.

I have uploaded it to my premier rapidshare account, so it can be downloaded an unlimited amount of times:

[http://rapidshare.com/files/327460823/rtl8192e_linux_2.6.0012.1210.2009.tar.gz](http://rapidshare.com/files/327460823/rtl8192e_linux_2.6.0012.1210.2009.tar.gz)

These were the steps I think I took to install.

First, I downloaded the file and extracted it to a folder on the desktop.

Then I opened a terminal, and cd'd to the folder where the driver is extracted.

Then:

sudo su

Then:

make install

When I rebooted, it detected the wifi card and I was able to connect!

Hurrah! No more win 7 :)

I hope people will find this driver useful and admins please feel free to edit this post if I have missed out any stages in the install process.

---

### Post by tonyps on 2010-01-02
Thanks for the info!! I will certainly try this latest one, providing I can get the download as a non member. Seems their servers have been awfully busy lately (for non members)...

Tony ...

---

### Post by armanox on 2010-01-02
Tigerbright,

That did the trick for me.  Someone should make a deb package for the driver.

---

### Post by tonyps on 2010-01-04
Morning,

Is there a special trick to get the download? I have been trying for the past few days, at different times, still with no success...suggestions welcome!!

Tony ...

---

### Post by Tigerbright on 2010-01-04
> **armanox said:**
> Tigerbright,

That did the trick for me.  Someone should make a deb package for the driver.

Excellent! Very glad its working for people. From the RS stats, its had over 50 downloads so far :)

---

### Post by Tigerbright on 2010-01-04
> **tonyps said:**
> Morning,

Is there a special trick to get the download? I have been trying for the past few days, at different times, still with no success...suggestions welcome!!

Tony ...

No trick. RS usually lets you download whether you are a premium member or not.

I got your PM and will email it to you asap....

---

### Post by tonyps on 2010-01-06
Ok, thanks for the drivers!!
I got it installed with no errors, but the wireless still does not seem to work..
iwconfig shows:
wlan1     802.11bgn  Nickname:"rtl8192E"
          Mode:Managed  Access Point: Not-Associated   Bit Rate:1 Mb/s   
          Retry:on   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=10/100  Signal level=0 dBm  Noise level=-100 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
lspci shows:
02:00.0 Network controller: Realtek Semiconductor Co., Ltd. Device 8192 (rev 01)
ifconfig wlan1 up produces this error:
SIOCSIFFLAGS: Operation not permitted

Any other info I can offer, just let me know. Thanks in advance for any assistance!
Tony ...

---

### Post by idavidmiller on 2010-01-10
The following procedure worked without any issues with a Samsung N130 Netbook and the Linux Realtek r8192e driver using Ubuntu 9.10, 32-bit version. From a shell terminal session do:

0. Need headers and source packages:

$ sudo apt-get install linux-source linux-headers-`uname -r`

1. Download Realtek r8192e driver archive from: 

    [http://rapidshare.com/files/327944041/rtl8192e_linux_2.6.0012.1210.2009.tar.gz.html](http://rapidshare.com/files/327944041/rtl8192e_linux_2.6.0012.1210.2009.tar.gz.html)

Note: Click the "Free User" button under the left speedometer and wait for the countdown timer to end. Then click Download button. Save file.

2. After downloading is complete, change to the download folder and extract driver archive to a working folder:

$ cd "~/your/download/folder" # (whatever your pathname is)

$ tar -xvjf rtl8192e_linux_2.6.0012.1210.2009.tar.gz


3. Installing the kernel source package (step 0. above) puts an archive file only in    /usr/src. Need to extract the source archive to /usr/src.

First,  get the source package version number:

$ dpkg -p linux-source | grep Depends:

This gives the version number of the source package. Use the version numbers only in the the following command. Example: for output of

 "Depends: linux-source-2.6.31"

use 2.6.31 for the "$your_version_number" below:

$ sudo tar -C /usr/src -xvjf /usr/src/linux-source-$your_version_ number.tar.bz2


4. Build and install driver.

Change into the rtl8192e_linux_2.6.0012.1210.2009 folder:

$ cd rtl8192e_linux_2.6.0012.1210.2009

$ sudo make

IMPORTANT NOTE: Must be superuser (sudo -s) for next command to make install without errors!

$ sudo -s make install

5. Add module to kernel and check module info:

$ sudo modprobe r8192e_pci

$ modinfo r8192e_pci

Module should be fired up at this point. You should get an output listing from modinfo that includes something like the following:

filename:       /lib/modules/2.6.31-17-generic/kernel/drivers/net/wireless/r8192e_pci.ko
license:        GPL
version:        0012.1210.2009
author:         Copyright(c) 2008 - 2010 Realsil Semiconductor Corporation <wlanfae@realtek.com>
description:    Linux driver for Realtek RTL819x WiFi cards

$ lspci -vv 

This should show info about all the drivers attached to PCI devices in the listing produced. Scroll through the listing. Should show under "Network controller:"

Kernel driver in use: rtl819xE
Kernel modules: r8192e_pci


6. You now have to configure a wireless connection for your wireless setup using Network Connections from System menu: SSID, DHCP or fixed IP, security settings (WEP, key, etc.), Infrastucture or Ad Hoc, auto-connect, etc. Be sure to connect to this setup. You may find an auto SSID name already listed there. If so, edit this auto connection.

7. Check network configuration:

$ iwconfig wlan0

Note: if wlan0 does not work try wlan1 or just omit this and use iwconfig only.

If the wireless is connected, your wireless SSID will show up in the output as ESSID as well as other wireless connection data:

wlan0     802.11bg ESSID:"your_wireless_SSID"  Nickname:"rtl8192E"

The exact output may be different on your system: wlan1 instead of wlan0, 802.11bgn instead of 802.11bg, etc., but these elements should all be present in this essential form.

6. Edit /etc/modules (gksudo gedit /etc/modules,  sudo vim /etc/modules, sudo nano /etc/modules or whatever editor you use) and add line:

r8192e_pci


This will install the module at boot time.

An addtional note. This wireless driver seems to cause problems with the power manager sleep (suspend) and hibernate modes. There is a fix for this that worked on my netbook. Edit /usr/lib/pm-utils/sleep.d/55NetworkManager to read as shown below adding the lies in bold:

case "$1" in
    hibernate|suspend)
        **modprobe -r r8192e_pci**
        suspend_nm
        ;;
    thaw|resume)
        **modprobe r8192e_pci**
        resume_nm
        ;;
    *) exit $NA
        ;;
esac


These lines remove the driver on supsend/hibernate and activate it again when waking up from suspend or hibernate.

See the following for details:

[http://www.backports.ubuntuforums.org/showpost.php?p=8574835&postcount=3](http://www.backports.ubuntuforums.org/showpost.php?p=8574835&postcount=3)

---

### Post by tonyps on 2010-01-11
Morning,

Things seem to go fine until:
modinfo r8192_pci
ERROR: modinfo: could not find module r8192_pci
However, if I change it to:
modinfo r8192e_pci then I get the following:
filename:       /lib/modules/2.6.31-17-generic/kernel/drivers/net/wireless/r8192e_pci.ko
license:        GPL
version:        0012.1210.2009
author:         Copyright(c) 2008 - 2010 Realsil Semiconductor Corporation <wlanfae@realtek.com>
description:    Linux driver for Realtek RTL819x WiFi cards
srcversion:     7CABA7BCE31A29AA9AF783E
alias:          pci:v000007AAd00000047sv*sd*bc*sc*i*
alias:          pci:v000007AAd00000044sv*sd*bc*sc*i*
alias:          pci:v000010ECd00008192sv*sd*bc*sc*i*
depends:        
vermagic:       2.6.31.6 SMP mod_unload modversions 
parm:           ifname: Net interface name, wlan%d=default (charp)
parm:           hwwep: Try to use hardware WEP support(default use hw. set 0 to use software security) (int)
parm:           channels: Channel bitmask for specific locales. NYI (int)

The output of lspci -vv shows:
02:00.0 Network controller: Realtek Semiconductor Co., Ltd. Device 8192 (rev 01)
    Subsystem: Realtek Semiconductor Co., Ltd. Device 8182
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Interrupt: pin A routed to IRQ 16
    Region 0: I/O ports at 6000 [size=256]
    Region 1: Memory at e7200000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: rtl819xE
    Kernel modules: r8192e_pci

Looking in System Menu, Network Connections, shows no wireless networks available, though there is a very strong one, with no encryption required.
Output of iwconfig shows:
wlan1     802.11bgn  Nickname:"rtl8192E"
          Mode:Managed  Access Point: Not-Associated   Bit Rate:1 Mb/s   
          Retry:on   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=10/100  Signal level=0 dBm  Noise level=-100 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

I added r8192e_pci to the /etc/modules using
sudo gedit /etc/modules
Here is the file:
lp
rtc
r8192e_pci

Rebooted and still no success....

Thanks in advance for any assistance!!
Tony ...

---

### Post by idavidmiller on 2010-01-11
> **tonyps said:**
> Morning,

Things seem to go fine until:
modinfo r8192_pci
ERROR: modinfo: could not find module r8192_pci
However, if I change it to:
modinfo r8192e_pci then I get the following:
filename:       /lib/modules/2.6.31-17-generic/kernel/drivers/net/wireless/r8192e_pci.ko
license:        GPL
version:        0012.1210.2009
author:         Copyright(c) 2008 - 2010 Realsil Semiconductor Corporation <wlanfae@realtek.com>
description:    Linux driver for Realtek RTL819x WiFi cards
srcversion:     7CABA7BCE31A29AA9AF783E
alias:          pci:v000007AAd00000047sv*sd*bc*sc*i*
alias:          pci:v000007AAd00000044sv*sd*bc*sc*i*
alias:          pci:v000010ECd00008192sv*sd*bc*sc*i*
depends:        
vermagic:       2.6.31.6 SMP mod_unload modversions 
parm:           ifname: Net interface name, wlan%d=default (charp)
parm:           hwwep: Try to use hardware WEP support(default use hw. set 0 to use software security) (int)
parm:           channels: Channel bitmask for specific locales. NYI (int)

The output of lspci -vv shows:
02:00.0 Network controller: Realtek Semiconductor Co., Ltd. Device 8192 (rev 01)
    Subsystem: Realtek Semiconductor Co., Ltd. Device 8182
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Interrupt: pin A routed to IRQ 16
    Region 0: I/O ports at 6000 [size=256]
    Region 1: Memory at e7200000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: rtl819xE
    Kernel modules: r8192e_pci

Looking in System Menu, Network Connections, shows no wireless networks available, though there is a very strong one, with no encryption required.
Output of iwconfig shows:
wlan1     802.11bgn  Nickname:"rtl8192E"
          Mode:Managed  Access Point: Not-Associated   Bit Rate:1 Mb/s   
          Retry:on   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=10/100  Signal level=0 dBm  Noise level=-100 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

I added r8192e_pci to the /etc/modules using
sudo gedit /etc/modules
Here is the file:
lp
rtc
r8192e_pci

Rebooted and still no success....

Thanks in advance for any assistance!!
Tony ...

Re: 
However, if I change it to:
modinfo r8192e_pci then I get the following:

You are correct. this line should read:

modinfo r8192e_pci

and not
modinfo r8192_pci

Sorry! Typo.

It appears to me that the driver is installed, otherwise you would not see:

Kernel driver in use: rtl819xE
    Kernel modules: r8192e_pci

However I don't see any SSID (ESSID) for your wireless access device in the output from iwconfig. This should show:

wlan1     802.11bgn ESSID:"your_wireless_SSID"  Nickname:"rtl8192E"

where your_wireless_SSID is whatever name your local wireless access device uses. So this is a clue.

Did you do the  sudo modprobe r8192e_pci step?

I had a network setup for my wireless SSID already in the Network Manager using known settings.
When I did the modprobe r8192e_pci I got a network connection automatically after that.
I knew this happened because the NetworkManager Applet "pinwheel" icon at the top panel started spinning and voila ... connected with the signal bars icon then.

I have to tell you I worked the better part of a day getting this procedure patched together from about ten different Google search windows
opened in my browser. I ran into one roadblock after the other. By trial and error I finally was able to get this to work using information from
various sources. I am not sure why it is not working for you. Sorry. I do know that I had to try different driver downloads and this was the only one
that worked. Make sure that your netbook is using the chip for the r8192e driver. You can email Realtek with your model number and they should send you the correct drivers, if that is the problem.

I would check to make sure first that you have the wireless connection information correct using the Network Connection tool. If this is not correct you
will not get a connection. However you should get the SSID to show up in that tool as "auto your_SSID" if the driver is working correctly.

Make sure to remove or disable ndiswrapper if you have that set up to use a Windows driver. I tried that and could not get it to work. This may conflict with your Linux installed driver module.

---

### Post by tonyps on 2010-01-11
Thanks for the response.. I sorta figured it was a typo....but it still is not working for me.....
Thanks!!

---

### Post by tonyps on 2010-01-12
HI all,

Just as a follow up.....I have been busting my B@#*&^ trying to get this to work under x64 Ubuntu, not really paying any attention to trying the x86 version....(why, because I wanted to be stubborn and use the 64bit power of my laptop...). anyhow, has anyone had success getiing the rtl8192e to work under the 32bit version of 9.10??

Thanks!!
Tony ...

---

### Post by idavidmiller on 2010-01-12
tonyps RE:#51 

FYI:

#47 refers to 9.10, 32-bit version with Linux rtl8192e wireless driver on Samsung N130 netbook.

I feel your pain!

I looked on the Realtek website for their driver download link. There is no Linux/Unix driver listed for the rtl8192e device. Evidently Realtek sent this driver to an individual via email and they posted it to Rapidshare -- kind of odd for Realtek to keep this a secret it seems since this driver seems to work okay for me and the person that posted the driver to Rapidshare. They do have a Linux driver for the rtl8192se chip. I read the technical docs for both and there is some language there about:

"The RTL8192SE provides simple legacy and 20MHz/40MHz co-existence mechanisms to ensure backward and network compatibility."

I am not sure if this means the rtl8192se driver will work with the rtl8192e chip or not. It can't hurt to try I guess. The download link is:

[http://www.realtek.com/downloads/downloadsView.aspx?Langid=1&PNid=48&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#RTL8192SE](http://www.realtek.com/downloads/downloadsView.aspx?Langid=1&PNid=48&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#RTL8192SE)

If all else fails, email Realtek tech support and ask if they have a  driver for the rtl8192e chip for 64-bit Linux 2.6 kernels.

On the web page below for the rtl8192e chip driver is also shown a Windows7 64-bit driver for the rtl8192u chip:

[http://www.realtek.com/downloads/downloadsView.aspx?Langid=1&PNid=9&PFid=9&Level=6&Conn=5&DownTypeID=3&GetDown=false&Downloads=true#RTL8192E](http://www.realtek.com/downloads/downloadsView.aspx?Langid=1&PNid=9&PFid=9&Level=6&Conn=5&DownTypeID=3&GetDown=false&Downloads=true#RTL8192E)

There is no 64-bit driver of any sort shown for the rtl8192e. So I suspect that the rtl8192e hardware may not support 64-bit OS. FYI I tried the ndiswrapper solution with 32-bit Windows XP driver and it did not work for me, but others seem to have success with this approach of using Windows drivers. You might try this approach with the 64-bit Windows7 drivers. I am on shaky ground here, since I am not super familiar with the compatibility and limitation issues of ndiswrapper. If you are going to try ndiswrapper see my post at:

[http://www.backports.ubuntuforums.org/showpost.php?p=8655233&postcount=4](http://www.backports.ubuntuforums.org/showpost.php?p=8655233&postcount=4)

I am not sure why this driver would build and show in use by the kernel using modprobe and modinfo on you system if it was incompatible with the 64-bit OS on your box. I would think that at some point in the process of #47 above that you would get an error of some kind thrown back at you. So I am not convinced that the driver is the culprit here. Maybe someone with more Linux savvy will read this thread and shed some light on that idea. 

David Miller

---

### Post by unicag on 2010-01-16
The RS links are not working.
Could you please upload it again?
I have premium account and I can upload the drivers after I get them.

---

### Post by chili555 on 2010-01-16
There are 32- and 64-bit tarballs here: [http://www.thinkwiki.org/wiki/ThinkPad_11b/g/n_Wireless_LAN_Mini-PCI_Express_Adapter_II](http://www.thinkwiki.org/wiki/ThinkPad_11b/g/n_Wireless_LAN_Mini-PCI_Express_Adapter_II)

I don't have the card, so I haven't tested it.

---

### Post by Dude-PWB- on 2010-01-16
The 32bit version works fine for me on my laptop, and since I am playing around on a USB install of ubuntu, and I like to tinker, I have installed the driver a few times, with NO problems, provided the instructions are followed properly.

The E and SE drivers are NOT the same. If you don't have or can't find the proper driver, then send an e-mail to realtek. Seriously, they sent me the driver within hours. Initially, they sent me the wrong driver, not their fault as I didn't tell them what version of Ubuntu I was running, and they sent me the driver for the older kernel. I replied back to them with my dilemma, and the proper information, and had the proper driver the next day. No other manufacturer that I have dealt with in the past has come close to being as accommodating as realtek was. 

If the install procedure is not working for you, then you are missing a step, or you have the wrong driver for your kernel version. It took me a few tries before I finally got it right. Follow the instructions in posts #13 and #17 of this thread. The install instructions int he readme from realtek are not clear enough to install it properly if you have limited experience with linux.

Here is another link for the 8192e driver for 9.10. This is the 32bit driver, not 64bit.

[http://rapidshare.com/files/336365402/rtl8192e_linux_2.6.0011.1029.2009.tar.gz](http://rapidshare.com/files/336365402/rtl8192e_linux_2.6.0011.1029.2009.tar.gz)

---

### Post by Satori80 on 2010-01-17
> **Dude-PWB- said:**
> 
Here is another link for the 8192e driver for 9.10. This is the 32bit driver, not 64bit.

[http://rapidshare.com/files/336365402/rtl8192e_linux_2.6.0011.1029.2009.tar.gz](http://rapidshare.com/files/336365402/rtl8192e_linux_2.6.0011.1029.2009.tar.gz)

No offence meant here, but giving out the URL to this file repeatedly isn't going to help those of us who aren't paying users. The site has been "too busy" to allow free downloads for over a week now. Though I certainly do appreciate your willingness to, and contributions toward, helping your fellow Linux users. 

I finally gave up and emailed Realtek. I find it frustrating that they won't just make it publicly available themselves. I'm going to have to strongly suggest they do that if/when I get a reply.

It really makes me wish I still had my servers online. The only thing I could do now to offer to help would be to post it to Usenet -- but that's not a solution as not everybody knows how to access it.

I did notice somebody offered to put it on his FTP server though... that seems like a reasonable solution if he's still up for it. :)

---

### Post by unicag on 2010-01-17
> **Dude-PWB- said:**
> Follow the instructions in posts #13 and #17 of this thread. The install instructions int he readme from realtek are not clear enough to install it properly if you have limited experience with linux.

Here is another link for the 8192e driver for 9.10. This is the 32bit driver, not 64bit.

[http://rapidshare.com/files/336365402/rtl8192e_linux_2.6.0011.1029.2009.tar.gz](http://rapidshare.com/files/336365402/rtl8192e_linux_2.6.0011.1029.2009.tar.gz)

Thanks, it worked.

I was using ndiswrapper and I had issues while connecting to a WPA2 wlan. Usually it wasn't connecting.

Now it works good with our WPA2 security enabled wlan.

---

### Post by Satori80 on 2010-01-19
nvm this post. I made a big mistake but now I can't delete this post. :(

---

### Post by evatw001 on 2010-01-19
its almost always a driver issue when something like this happens to me.

---

### Post by nostradamuz on 2010-01-19
I am very happy to report that my wireless works great!!!
After a ndiswrapper ****.. is this a breeze .. :)

---

### Post by ssam on 2010-01-19
you could also try using the lucid kernel which has the driver 
[http://ubuntuforums.org/showthread.php?t=1383446&highlight=8192](http://ubuntuforums.org/showthread.php?t=1383446&highlight=8192)

---

### Post by Dude-PWB- on 2010-01-19
> **Satori80 said:**
> **No offence meant here, but giving out the URL to this file repeatedly isn't going to help those of us who aren't paying users.** The site has been "too busy" to allow free downloads for over a week now. Though I certainly do appreciate your willingness to, and contributions toward, helping your fellow Linux users. 

I finally gave up and emailed Realtek. I find it frustrating that they won't just make it publicly available themselves. I'm going to have to strongly suggest they do that if/when I get a reply.

It really makes me wish I still had my servers online. The only thing I could do now to offer to help would be to post it to Usenet -- but that's not a solution as not everybody knows how to access it.

I did notice somebody offered to put it on his FTP server though... that seems like a reasonable solution if he's still up for it. :)

I'm only trying to help as that is the only solution I could come up with for the time being. The latest link is a full time dedicated link now so it should not expire.

---

### Post by liamgh on 2010-01-31
I got this card working under 32bit Ubuntu Lucid (haven't tried 64 bit Lucid, although did not get very far with 64 bit Karmic) on the Samsung R580. The Lucid kernel has a driver for the rtl8192e built in, but it does not yet have firmware. I obtained the firmware and put it in the right place using the method described in this post:
[http://ubuntuforums.org/showthread.php?p=8752410](http://ubuntuforums.org/showthread.php?p=8752410)

---

### Post by moaoci on 2010-02-03
Toshiba Satellite L505D-S6947 - Turion X2 RM-74 64bit  with RTL8192E card **successfully working**.

Ubuntu 9.10 64bit
Linux kernel 2.6.31.17 

I have a standard dual-boot installation of Ubuntu 9.10 Karmic 64bit, all automatic updates had been done, and then I applied the driver's easy instructions to install and start it.  No fussy changes to apply.

The only odd thing is that my cursor becomes invisible if I move it over the antenna icon before the connection is completed. I can sure live with that. 

The driver I used is **rtl8192e_linux_2.6.0013.0127.2010.tar.gz** and I obtained it simply by e-mailing [EMAIL="wlanfae@realtek.com"]wlanfae@realtek.com[/EMAIL] to get the latest status for RTL8192E driver for linux 64bit systems.
 
On my first e-mail to realtek, I was sent file rtl8192e_linux_2.6.0012.1210.2009.tar.gz which did NOT work for me.  So I sent back the output of DMESG, lspci, and a md5sum of the firmware files to realtek and asked for help. 
 
The next day, I received this new file:  **rtl8192e_linux_2.6.0013.0127.2010.tar.gz**  
 
I recompiled it, rebooted and my network came in automaticly. (WEPA2 encription)
 
The morale: don't hesitate like me to e-mail realtek to get your drivers file, they seemed quite happy to help me.
 
Special thanks to  [EMAIL="kidman@realtek.com"]kidman@realtek.com[/EMAIL]

---

### Post by find.karl on 2010-02-05
moaoci thanks for the update, any chance you can upload that file some place like [http://rapidshare.com/index.html](http://rapidshare.com/index.html)

I am currently waiting for a response to my request from RealTek for the latest driver and a link to some place that we may look for future updates

---

### Post by moaoci on 2010-02-05
Keep your driver files at hand reach.  
 
**The driver needs to be re-installed ( sudo su + make clean + make + make install + reboot ) whenever the Linux kernel number changes.  **
 
Last night, the update manager updated my system and the Linux Kernel 2.6.31.19 was installed and I lost my wifi immediately at reboot.  I had to reinstall the RTL8192E driver  (sudo su + make clean +  make + make install + reboot ) and everything was back to normal.

---

### Post by moaoci on 2010-02-05
You are welcomed to make it available elsewhere if you want, when you'll get the driver from realtek.  
 
The best solution would be from Realtek download site...  I requested it and I don't know if they are seriously thinking of doing so.  If they start receiving too many e-mail driver requests, they might...  But they might be OK with e-mail distribution until Linux Kernel supports it.  
 
Let us know if and when you decide to distribute the RTL8192E driver (and it's updates).

---

### Post by chili555 on 2010-02-05
> The driver needs to be re-installed ( make + make install + reboot ) whenever the Linux kernel number changes.I suggest:```
sudo su
[COLOR="Red"]make clean[/COLOR]
make
make install
reboot
```'make clean' removes any files created in your previous 'make' done against the old kernel. You are quite correct that the process needs to be re-run every time a new kernel, known in Ubuntu-speak as linux-image, is installed. The clue will be when your wireless conks out with no warning.

---

### Post by ebb3771 on 2010-02-06
I just bought a Toshiba Satellite L555D-S7005, and installed Ubuntu 9.10 32 bit on it.  The wireless network card does not work out of the box.  I fixed it with the following protocol:

1.  Go to device manager in Windows 7 (preloaded on this laptop) and see what driver is installed for the wireless card.  In my case, it says "Realtek RTL8191SE".

2.  Go to the Realtek web page and download the driver for the IEEE 802.11b/g/n chipset that matches the name of the driver Windows 7 was using.  The Realtek page is here: [http://152.104.125.41/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false](http://152.104.125.41/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false) 

3.  Unpack the archive, and execute the following in the unpacked directory in a terminal window (exactly as in Dude-PWB-'s instructions):
> sudo make
sudo su
make install


That's it.  I actually ran "./wlan0up" after "make install", like Dude-PWB recommends, but I'm not convinced it's necessary.  The wireless card worked immediately, without logging out or rebooting.  I didn't have to modify any system files to make it load after rebooting either.

Cheers,
E

---

### Post by jcanini on 2010-02-08
I followed Dude-PWB advice and got hold of the rtl8192e_linux_2.6.0012.1210.2009 file and installed it with the make and make install commands and and wireless device worked after reboot on my N140 notepad running Ubuntu notebook remix. Thanks Dude your help is very much appreciated.
Today I installed automatic updates with the 2.6.31.19 kernel and the wireless device did not work.
When I reboot with the 2.6.31.17 kernel the device works perfectly, so just wanted to post this to alert people to possible issues with the new kernel.

Just read moaoci comment above about reinstalling the driver every kernel update, not an ideal situation but at least it works.

---

### Post by pirxter on 2010-02-22
Greetings,

I have a Samsung R463 notebook bought in Shanghai, which apparently seems to be otherwise sold in Russia only, at least this is my impression after extensive googling.

The Realtek 8192e inside works fine under Windows XP out of the box, whereas Windows 7 needs the driver from the Realtek website.

Ubuntu 9.10 64-bit identified the device correctly, but no driver from the Realtek website worked after correct compilation. 

I had a great response from Realtek about the issue, phantastic support. They e-mailed me the updated 64-bit driver source after a few days. This driver worked on an updated version of Ubuntu 9.10 64 bit, however, it required manual start every time.

After extensive experimenting resulting in a clean install of Ubuntu 9.10 64-bit, it now works flawlessly.

e-mail Realtek support for the driver.

---

### Post by AeroRange on 2010-03-31
My Ubuntu 9.10 (64-bit) crashed and error when booted with wireless turned on after I installed the windows driver with ndiswrapper.
While I haven't receive email reply from realtek yet.

---

### Post by mcguire on 2010-04-16
Realtek (kidman) sends me today the driver v14 which works on 64 bits (tested on lucid).
On my Samsung R580 laptop, it disconnects often but it is usable. When it disconnects, sometimes, it can not reconnect automatically so I have to unload the module and reload it, then it works again for some time.

I've uploaded it to my personal server so that everybody can download it :
[http://ftp.jdsystem.info/rtl8192e_linux_2.6.0014.0401.2010.tar.gz](http://ftp.jdsystem.info/rtl8192e_linux_2.6.0014.0401.2010.tar.gz)

Hope this help

EDIT : I've also attached this driver to [bug 508746]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/508746") on Launchpad.

---

### Post by s32ialx on 2010-04-22
If you have not got it working yet [http://ubuntuforums.org/showthread.php?t=1460038](http://ubuntuforums.org/showthread.php?t=1460038) is how to get it working for x86 and x64 of the newest release 10.04 x86 and x64

---

### Post by andydch on 2010-06-10
i got error when compile the source

WARNING: Symbol version dump /usr/src/linux-2.6.34/Module.symvers
           is missing; modules will have no dependencies and modversions.

  Building modules, stage 2.
  MODPOST 1 modules
/bin/sh: scripts/mod/modpost: not found
make[2]: *** [__modpost] Error 127
make[1]: *** [modules] Error 2
make[1]: Leaving directory `/usr/src/linux-2.6.34'
make: *** [all] Error 2

whats wrong with my process?

thanks

---

### Post by austen on 2010-09-15
#10 didn't work for me, ndiswrapper saw the device but would error out, however that may have been due to the fact that I neglected to copy the firmware included with the RTL8192U Linux drivers. That ship has sailed, however...

Compiling the latest Linux kernel (2.6.35.4 in my case) with the RTL8192U staging drivers (and copying firmware to /lib/firmware) works perfectly.

God, I *love* this OS!

---

### Post by chris_jh on 2010-10-09
I have been struggling with this for a few days now, and finally got it working on a Samsung R780 using Ubuntu 10.04.1 x86_64.

The rtl8192e_linux_2.6.0014.0401.2010 does not work properly.

I have tried several version of this driver, none worked.

This one worked for me, thanks to Dirk Hoeschen.

[http://www.dirk-hoeschen.de/temp/rtl819Xe.tar.gz](http://www.dirk-hoeschen.de/temp/rtl819Xe.tar.gz)

---

### Post by IBBoard on 2010-10-20
Just a quick note to say thanks for the instructions in post #47. With Ubuntu Netbook Edition on a Samsung N150 then the wireless works fine *until* you suspend/restart, at which point it won't work. I didn't need any of the install instructions, but the changes to the power management script have made it work.

If only this all worked smoother. My wife is half cursing me for making her think that Linux would be better than Windows. The UI is a better size, but documentation is poor and we're just hitting too many of these niggly problems.

---

### Post by IBBoard on 2010-10-31
Correction - that fix works a bit. With the changes then the machine hibernates and restores correctly, but 90% of the time then it fails to reconnect to the network. A clean startup is generally okay, but a wake-up sits trying to connect, then pops up the password for the wireless, then sits, then asks for the password. The only way to fix it is to remove and re-add the drivers (again) and it'll normally connect straight away.

Now, if only the drivers didn't seem to drop packets/resend a lot. One of my wife's apps keeps dropping its connection because of retransmits, but doesn't do it on a wired connection. The same app to the same router on another laptop (also on UNE 10.10) doesn't have that problem. It seems that the r8192 drivers just generally need a bit of work.

---

### Post by drspikes on 2010-11-07
> **pcdragon said:**
> Thanks Dude for posting this and sharing the driver.  I have it working with the following:

Kubuntu 9.10 32-Bit
Toshiba L500 laptop

Needed to uninstall network-manager. I don't have wicd installed.

Because I have WPA-PSK (TKIP) setup on my router I installed the standard kubuntu wpasupplicant package and copied /usr/share/doc/wpasupplicant/examples/wpa-psk-tkip.conf to /etc/wpa_supplicant/wpa_supplicant.conf then edited it to suit.

I added the following lines to /etc/network/interfaces:

```

auto wlan0
iface wlan0 inet dhcp
wpa-driver wext
wpa-conf /etc/wpa_supplicant/wpa_supplicant.conf

```
Added the following line to /etc/modules:
```

r8192e_pci

```Rebooted and it worked fine. Thanks again for solving this issue.

cheers

This method fixed the problem for me.  Thank you very much:guitar:

---

### Post by schmoken on 2010-11-07
My Samsung N130 and I have been going round and round with the same issue.
I'm running 10.10 w/kernel 2.6.35-22.

I sent realtek an email on Saturday, and got a reply on **Sunday** with the correct drivers. 

email & link:

> Dear Sir,               

Thanks for your email.

Please find the attached for latest RTL8192E 32bit and 64bit Linux driver which is the updated one different from the one you used.

Just kindly remind, please install by the below steps.

The following is the installing steps:
1. Change to the driver directory
2. sudo su
3. make
4. make install
5.reboot
6. ./wlan0up or ./wlan1up

     Note: 1. if permission denied, change perperty with `chmod 777 wlan0up`
           2. or enable driver with `ifconfig wlanx up`(wlanx denote wlan interface name).

 
If your OS is 64bit, maybe there is kernel self driver for RTL8192E, you should delet it first before install:

    1) cd /lib/modules/2.6.3x.xx.xx/
    2) find -name "r8192e_pci.ko"
    3) delet all the r8192e_pci.ko
    4) install our RTL8192E driver
    5) reboot.

if there&#8217;s still any other problem, please let us know.

   Thanks a lot

Regards,

Kidman


[http://www.box.net/shared/v1bpr94j8k](http://www.box.net/shared/v1bpr94j8k)

---

### Post by charleyllabete on 2011-03-18
Thank you!  That solution worked fine for me.

---

### Post by anipet on 2011-04-18
thank you so much schmoken for your info, it was just what solved my problem and got me finally back on ubuntu, from which I'm posting this reply :D

THANK YOU!

---

### Post by choper81 on 2011-05-13
GREAT!
Thank you very much worked perfectly on my N130!!!
P.S. wonder why ubuntu developers do not fix this?...

---

### Post by quicky2g on 2012-10-08
I have an [Acer Veriton Nettop]("http://www.newegg.com/Product/Product.aspx?Item=N82E16883103629") running Debain 6.0.6 with a Realtek RTL8192DE wireless card. I downloaded the Unix/Linux driver from the Realtek website but compiling the module from source kept failing. The README file mentioned using [compat-wireless]("http://linuxwireless.org/en/users/Download/stable/"). The versions of compat-wireless seemed to be organized based on kernel versions. Debian is currently running 2.6.32-5. I tried compat-wireless v2.6 but it didn't work. After extracting the tar.bz2 file and going through the README file, there's a command showing the wireless cards it supports:
```
./scripts/driver-select
```v2.6 didn't have the right driver available. I downloaded v3.5 and it did:
```

Supported 802.11 drivers:
        ath5k
        ath9k
        ath9k_ap
        ath9k_htc
        carl9170
        ath6kl
        b43
        zd1211rw
        rt2x00
        wl1251
        wl12xx
        brcmsmac
        brcmfmac

Supported Ethernet drivers:
        atl1
        atl2
        atl1e
        atl1c
        alx

Supported group drivers:
        atheros <  ath5k ath9k carl9170 zd1211rw ath6kl >
        ath <  ath5k ath9k carl9170 ath6kl >
        brcm80211 <  brcmsmac brcmfmac >
        intel <  iwlwifi, iwlegacy >
        rtl818x <  rtl8180 rtl8187 >
        rtlwifi <  rtl8192ce >
        ti <  wl1251 wl12xx (SPI and SDIO)>

Supported group drivers: Bluetooth & Ethernet:
        atlxx <  atl1 atl2 atl1e alx>
        bt <  Linux bluetooth drivers >

```gcc, kernel headers, and all the other usual software for compiling packages should be installed. I compiled the driver successfully using the instructions in the README file. Pay attention to output after the scripts finish installing the kernel modules. There are a few extra commands needed to load the drivers into the kernel and reboot, but I can't remember what they are. I'm using the rtlwifi driver with no problems. Hope this helps!

---

