---
title: "Built in rtl8192cu* - has it ever worked for anyone?"
date: 2012-03-31
forum: Networking &amp; Wireless
---

### Post by mikewhatever on 2012-03-31
**Please note, this thread is for the built in driver only. If you downloaded a driver from Realtek, it's not for you.**

I've been trying to get the built in rtl8192cu driver work for about a year with various kernels and different distros, but to no avail. 

The device I have is as follows:
```
Bus 001 Device 002: ID 7392:7811 Edimax Technology Co., Ltd EW-7811Un 802.11n Wireless Adapter [Realtek RTL8188CUS]
```

It's been reported that rtl8192cu has been added to the mainline kernel as of 2.6.38.
[http://www.h-online.com/open/features/Kernel-Log-Coming-in-2-6-39-Part-1-Network-drivers-and-infrastructure-1227053.html](http://www.h-online.com/open/features/Kernel-Log-Coming-in-2-6-39-Part-1-Network-drivers-and-infrastructure-1227053.html)
> Kernel developers have merged the rtl8192cu WLAN driver for Realtek's RTL8192CU and RTL8188CU USB WLAN components (see e.g. 1, 2). 

...and indeed, as of 11.04 the APs around are visible, but it wouldn't connect to any of them.

Here is the bug report: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/852190](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/852190)

The problem appears to be consistent with the other threads:
[http://ubuntuforums.org/showthread.php?t=1640199&page=4&highlight=edimax+7811](http://ubuntuforums.org/showthread.php?t=1640199&page=4&highlight=edimax+7811)
[http://ubuntuforums.org/showthread.php?t=1590873&highlight=edimax+7811](http://ubuntuforums.org/showthread.php?t=1590873&highlight=edimax+7811)
[http://ubuntuforums.org/showthread.php?t=1883600&highlight=edimax+7811](http://ubuntuforums.org/showthread.php?t=1883600&highlight=edimax+7811)
[http://ubuntuforums.org/showthread.php?t=1886342&highlight=edimax+7811](http://ubuntuforums.org/showthread.php?t=1886342&highlight=edimax+7811)
[http://ubuntuforums.org/showthread.php?t=1878827&highlight=edimax+7811](http://ubuntuforums.org/showthread.php?t=1878827&highlight=edimax+7811)
[http://ubuntuforums.org/showthread.php?t=1881780&highlight=edimax+7811](http://ubuntuforums.org/showthread.php?t=1881780&highlight=edimax+7811)

Has the built in driver worked for anyone?

Could it be that something is misconfigured?

```
lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu precise (development branch)
Release:	12.04
Codename:	precise

```

```
uname -a
Linux amu-laptop 3.2.0-20-generic #33-Ubuntu SMP Tue Mar 27 16:42:26 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

```

```
lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 7392:7811 Edimax Technology Co., Ltd EW-7811Un 802.11n Wireless Adapter [Realtek RTL8188CUS]
Bus 001 Device 003: ID eb1a:2771 eMPIA Technology, Inc. 
Bus 001 Device 004: ID 05e1:0100 Syntek Semiconductor Co., Ltd 802.11g + Bluetooth Wireless Adapter

```

```
~$ iwconfig
lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"amu"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:78:9E:FA:32:C8   
          Bit Rate=72.2 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-38 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.

```

```
dmesg | grep rtl
[    7.697491] rtl8192cu: MAC address: 00:1f:1f:e4:4e:38
[    7.697506] rtl8192cu: Board Type 0
[    7.832913] rtlwifi: rx_max_size 15360, rx_urb_num 8, in_ep 1
[    8.177409] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[    8.179072] usbcore: registered new interface driver rtl8192cu
[   16.987112] rtl8192cu: MAC auto ON okay!
[   17.020118] rtl8192cu: Tx queue select: 0x05
[   17.021044] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cufw.bin
[ 2586.100137] rtlwifi: reg 0x102, usbctrl_vendorreq TimeOut! status:0xffffffed value=0x7a520b90
[ 2586.100157] rtlwifi: reg 0x422, usbctrl_vendorreq TimeOut! status:0xffffffed value=0x7a520b90
[ 2586.100172] rtlwifi: reg 0x542, usbctrl_vendorreq TimeOut! status:0xffffffed value=0x7a520b90

```

```
~$ rfkill list all
1: phy1: Wireless LAN
	Soft blocked: no
	Hard blocked: no

```

---

### Post by kurt18947 on 2012-03-31
I'm typing this message on a Thinkpad with an Edimax adapter in use.  I had the same experience as you using the built-in driver. I downloaded the driver from Realtek's site. 

[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true)

The Readme file talks about kernel 2.6.38 and 3.x.  I don't know if this will work with Ubuntu distros earlier than 11.10 or not.  With Precise I just unpacked the driver and ran the installer. 

```
sudo bash install.sh
```Restarted and it worked. I kept the folder where I can find it.  Kernel upgrades will kill the adapter.  Rerunning the install script will bring it back.  This did not work with Mint12 which I think is the same underpinnings as Ubuntu 11.10.  I had to blacklist "rtl8192cu" in order for Mint12 to use the adapter.  I found this counter-intuitive  seeing as Precise lists the 8192cu module in use but blacklisting 'rtl8192cu' worked in Mint12 where just running the install script did not. I guess blacklisting prevents the built-in module from loading and conflicting with the Realtek version.

---

### Post by mikewhatever on 2012-03-31
I know that the driver from realtek.com works, but it's only available for 3.0.2 and earlier kernels, but not for 3.2 which is the default in Precise. 
The question is, Why include a driver that doesn't work?

---

### Post by Bucky Ball on 2012-03-31
So you are using 12.04 LTS???

And try switching of N. That has worked for some people. You will need to search for the command (unless you know how) as I've never had to use that one.

---

### Post by mikewhatever on 2012-03-31
Yes, I am trying to use the device with Precise now, but it doesn't really maqtter. I've also tested it with Natty, Oneiric and Open Suse 12 (kernel 3.1) and Fedora16 and the built in driver never worked, ever.

---

### Post by kurt18947 on 2012-03-31
> **mikewhatever said:**
> I know that the driver from realtek.com works, but it's only available for 3.0.2 and earlier kernels, but not for 3.2 which is the default in Precise. 
The question is, Why include a driver that doesn't work?

I know that Realtek only lists certain image versions.  I'm using the RealTek driver on Kernel 3.2.0-21, just installed a couple hours ago.  The kernel upgrade did kill it, running the install.sh script resurrected it. The adapter is blinking happily away.:guitar:  And I never had any success with the built-in driver either.  I got the infamous "re-enter your network key" error.  The same driver from RealTek works fine on Mint 12 & the latest Precise.

---

### Post by mikewhatever on 2012-03-31
> **kurt18947 said:**
> I know that Realtek only lists certain image versions.  I'm using the RealTek driver on Kernel 3.2.0-21, just installed a couple hours ago.  The kernel upgrade did kill it, running the install.sh script resurrected it. The adapter is blinking happily away.:guitar:  And I never had any success with the built-in driver either.  I got the infamous "re-enter your network key" error.  The same driver from RealTek works fine on Mint 12 & the latest Precise.

Well, the point of this thread is not to tell people, "Hey, the built in driver is broken, get one from realtek". I know you can do that, in fact, I've been using the device with Lucid for months. 

What I want to know is whether the builtin driver ever worked for anyone, because if not, I'll be asking the kernel devs to remove, or at least blacklist it.

---

### Post by anspfirst on 2012-03-31
Its not totaly ethical but have you tried looking for an ungaurded access point near your house. With a little help from a pringles can you might but on the internets in  no time.

---

### Post by mikewhatever on 2012-03-31
> **anspfirst said:**
> Its not totaly ethical but have you tried looking for an ungaurded access point near your house. With a little help from a pringles can you might but on the internets in  no time.

Yes, I have. The device wouldn't connect to any network, protected or open.

---

### Post by wildmanne39 on 2012-03-31
Hi, you can try this parameter to see if it will make it connect if it does we will need to make it permanent.
```
sudo modprobe -r rtl8192cu
sudo modprobe rtl8192cu swenc=1
```
Thanks

---

### Post by mikewhatever on 2012-03-31
The 'swenc=1' option didn't make any difference. Is there any other option to try?
Thanks.

---

### Post by kurt18947 on 2012-03-31
> **mikewhatever said:**
> Well, the point of this thread is not to tell people, "Hey, the built in driver is broken, get one from realtek". I know you can do that, in fact, I've been using the device with Lucid for months. 

What I want to know is whether the builtin driver ever worked for anyone, because if not, I'll be asking the kernel devs to remove, or at least blacklist it.

Ah, I did not understand that, thanks.  The built-in has never worked well for me.  The device's blue light would come on steady but I was seldom able to connect at all and never for more than a couple minutes.  I'd get the infamous 'enter your network key' or whatever the phrase is.

---

### Post by wildmanne39 on 2012-03-31
Hi, in 12.04 that is the only parameter available.

---

### Post by deckoff on 2012-04-05
I bought a really cheap USB dongle with this chip. I managed to installed it , using [this link]("http://www.r-statistics.com/2011/11/edimax-ew-7811un-usb-wireless-connecting-to-a-network-on-ubuntu-11-10/")

I use Ubuntu 11.10 kernel - 3.0.0.16. It connects and works, but sometimes connection slows down considerably. Dont know if this is because of my network or the adapter, but the other PC connect and download at much better speeds.
I would be happy if I find a fix these slows

---

### Post by mikewhatever on 2012-04-09
> **deckoff said:**
> I bought a really cheap USB dongle with this chip. I managed to installed it , using [this link]("http://www.r-statistics.com/2011/11/edimax-ew-7811un-usb-wireless-connecting-to-a-network-on-ubuntu-11-10/")

I use Ubuntu 11.10 kernel - 3.0.0.16. It connects and works, but sometimes connection slows down considerably. Dont know if this is because of my network or the adapter, but the other PC connect and download at much better speeds.
I would be happy if I find a fix these slows

In short, the built in module hasn't worked for you too.

---

### Post by deckoff on 2012-04-10
> **mikewhatever said:**
> In short, the built in module hasn't worked for you too.
YES!
This chip is the most probable reason(not sure on 100%) for the issues I have, yes. It performs better round her, though, slow-downs are noticeable 5% of the time, only. 
I am waiting for a better drivers from Realtek, too

---

### Post by iburroughs on 2012-04-13
I'm having a slightly different set of symptoms in 11.10.

From at cold boot wireless works perfectly but after return from hibernate it doesn't show up in network manager and 
***rfkill list*** just shows an empty list.

***nmcli nm status*** and ***lsmod ***give the same results before and after while ***dmesg | grep rtl*** after shows
```

[    8.759796] rtl8192cu: MAC address: 00:02:72:a1:78:2e
[    8.759799] rtl8192cu: Board Type 0
[    9.243607] rtl8192cu: rx_max_size 15360, rx_urb_num 8, in_ep 1
[    9.345478] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[    9.345857] usbcore: registered new interface driver rtl8192cu
[   15.585263] rtl8192cu: MAC auto ON okay!
[   15.618009] rtl8192cu: Tx queue select: 0x05
[   15.618766] rtl8192c: Loading firmware file rtlwifi/rtl8192cufw.bin
[ 2743.917404] rtl8192cu: MAC address: 00:02:72:a1:78:2e
[ 2743.917406] rtl8192cu: Board Type 0
[ 2743.917426] Modules linked in: bnep rfcomm bluetooth parport_pc ppdev vesafb binfmt_misc arc4 snd_hda_codec_hdmi snd_hda_codec_realtek snd_hda_intel snd_hda_codec snd_hwdep snd_pcm rtl8192cu rtl8192c_common rtlwifi mac80211 snd_seq_midi cfg80211 snd_rawmidi snd_seq_midi_event sp5100_tco snd_seq fglrx(P) snd_timer snd_seq_device snd soundcore snd_page_alloc i2c_piix4 shpchp k10temp wmi max6650 lp parport usbhid hid r8169 ahci libahci pata_atiixp
[ 2743.917473]  [<f8802637>] rtl92cu_init_sw_vars+0x57/0x1e0 [rtl8192cu]
[ 2743.917484]  [<f8797d58>] rtl_usb_probe+0x1b6/0x45e [rtlwifi]
[ 2743.917546] usb 1-5: firmware: rtlwifi/rtl8192cufw.bin will not be loaded
[ 2743.917640] rtl8192cu:rtl92cu_init_sw_vars():<0-0> Failed to request firmware!
[ 2743.917642] rtlwifi:rtl_usb_probe():<0-0> Can't init_sw_vars.

```

I tried **wildmanne39's** sugestion
> 	
Hi, you can try this parameter to see if it will make it connect if it does we will need to make it permanent.
Code:
sudo modprobe -r rtl8192cu
sudo modprobe rtl8192cu swenc=1
Thanks
 
except without the swenc=1 option.

This worked and wireless is back on line!

Sorry **wildmanne39** for not quoting you properly, I just couldn't figure out how to do it.

I joined this forum about two years ago and I can safely say that you folks are the most helpful on the Internet. 

):P Many thanks ):P

---

### Post by moeneim on 2012-04-28
Thanks to wildmanne39, this worked for me too on 12.04 with the latest kernel.

> sudo modprobe -r rtl8192cu
> sudo modprobe rtl8192cu swenc=1

---

### Post by wildmanne39 on 2012-04-28
Hi, glad it helped.
Enjoy

---

### Post by mikewhatever on 2012-05-03
This bug appears to be widespread. I've tested Fedora 17 beta (kernel 3.3) recently with the exact same results. 

Here are some Bugzilla bug reports:
[https://bugzilla.redhat.com/show_bug.cgi?id=806142](https://bugzilla.redhat.com/show_bug.cgi?id=806142)
[https://bugzilla.redhat.com/show_bug.cgi?id=789605](https://bugzilla.redhat.com/show_bug.cgi?id=789605)

I wonder, how long does it take for an updated driver from Realtek to make it into the Kernel?

---

### Post by Bucky Ball on 2012-05-03
Don't rely on Realtek to support Linux ... or anyone else for that matter! Not true; some do a great job ...

Why would an updated Realtek driver make it to any kernel? That is up to Realtek, not the Linux community, or even Canonical ...

---

### Post by TechZilla on 2012-07-29
> **Bucky Ball said:**
> Don't rely on Realtek to support Linux ... or anyone else for that matter! Not true; some do a great job ...

Why would an updated Realtek driver make it to any kernel? That is up to Realtek, not the Linux community, or even Canonical ...

Your incorrect, Realtek has done only slightly less than Ralink.  They allow the firmware to be redistributed, and provide a generally working vendor driver with source. This is actually better than most vendors, and their effort deserves some level of acknowledgment.

What they don't do, which is the reason for these issues, is support the Linux in-kernel developed driver.  Almost every vendor driver will have an incredibly difficult time getting accepted in-kernel, not to mention it would require an ongoing commitment to maintain.  It's worth mentioning,  The in-kernel drivers are helped by the existence of open source vendor drivers.  As the source can be used as a poor mans spec.  so the in-kernel driver is built to use mac80211, coded to kernel standards, and because of which often has built in injection. What the in-kernel driver misses, is all the in-house knowledge that only a vendor could acquire. 


So while you could arguably blame Realtek,for not supporting in-kernel driver development, they should not be singled out for their lack of support. Lets leave the shaming for vendors most deserving.  I also want to add, while canonical is not to blame for kernel problems, i'm unaware of even one driver they have created/improved. Last I checked, even Microsoft had a more kernel code contributed.  This criticism is coming from a Debian guy, who switched to Ubuntu at 6.04...  So not to bash them, but for being the most popular GNU/Linux distribution, they need to contribute more to the kernel source.

---

### Post by Bucky Ball on 2012-07-29
> **TechZilla said:**
> Your incorrect, Realtek has done only slightly less than Ralink.  They allow the firmware to be redistributed, and provide a generally working vendor driver with source. This is actually better than most vendors, and their effort deserves some level of acknowledgment.

+++1. Totally agree. Think you misread me. I maybe didn't make it clear enough I was quoting the opinion of another poster and replying with:

[QUOTE=Bucky Ball]Not true; some do a great job ...[/QUOTE]

I try to stick with Realtek then Broadcom. Just bought a USB TV tuner with  Realtek inside. Works a treat. Watching the Olympics on the desktop while working on the laptop right now! ;)

---

### Post by blueadept on 2012-08-11
> **wildmanne39 said:**
> Hi, you can try this parameter to see if it will make it connect if it does we will need to make it permanent.
```
sudo modprobe -r rtl8192cu
sudo modprobe rtl8192cu swenc=1
```
Thanks

Sadly this didn't help here, with 12.10

---

### Post by wbushey on 2012-08-11
Hi, I just wanted to throw in my experience, which is basically that the drivers available from Realtek's site work much better than the builtin rtl8192cu kernel drivers on my Ubuntu 12.04 amd64 machine.

I have an Asus USB-13N rev. B1, which has the Realtek 8192 chip, and which I bought specifically because of its linux support. For the week I have owned it I have tried to use the built in drivers, and generally had terrible performance. I was consistently getting download speeds of ~30KBps on a broadband connection that usually gets ~4MBps on any other machine in my house, or this same machine (with the USB-13N) in Windows. It would also often drop its connection with my router, and maybe a 1/3 of the time, I would get a never ending prompt for the network key.

Today I came across this thread and tried installing Realtek's 8192cu driver from its website. Now I finally have the wireless USB performance I expected when I bought the USB-13N. Thanks for pointing out that the built-in driver is basically useless =D>

---

### Post by Bucky Ball on 2012-08-12
> **blueadept said:**
> Sadly this didn't help here, with 12.10

12.10 not released and definitely testing. Please direct your issues to the appropriate Ubuntu +1 sub-forum. ;)

---

### Post by Placidia428 on 2012-08-12
Wbushey,

I just got the same Asus dongle that you have - USB-N13 - and the inbuilt drivers dont' work. Would you mind telling me exactly what you did to get yours working, or direct me to the relevant forum page?

Did you try the driver that came with the Asus or did you download from Realtek?

---

### Post by williamts99 on 2012-08-13
Just started using the Edimax EW-7811Un with this chipset on Ubuntu 12.04 using the built in rtl8192cu driver.  Plugged it in, connected to WPA2 network right away, no issues at all.

---

### Post by mikewhatever on 2012-09-07
I'll be testing 12.04.1, OpenSuse 12.2 and Quantal beta1 next time I get to use the device. It's been almost a year since [the bug]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/852190") was reported, if you are affected, please leave a comment there.

---

### Post by Oedipe on 2012-09-13
[Kubuntu 12.04 Precise]

Hi, i have a usb dongle [SIZE="3"]Netgear N150 WNA1000M[/SIZE] that use the infamous ship **[SIZE="3"]rtl8192cu[/SIZE]**. The built-in driver with **kernel 3.2.0-30** doesn't work at all... Disconnecting every 10 - 30 minutes... 

I don't understand why this rtl8192cu problem has not been resolved since one year ! (and why they build a kernel with such a buggy driver). :mad:

---

### Post by chili555 on 2012-09-13
> **Oedipe said:**
> I don't understand why this rtl8192cu problem has not been resolved since one year ! (and why they build a kernel with such a buggy driver). :mad:Do you think it's a buggy driver or a buggy Network Manager or a buggy wpa_supplicant or a buggy power management scheme or a buggy wireless-N implementation in your router? Or how any and all of them interact? I'm not sure.

---

### Post by mikewhatever on 2012-09-19
> **Oedipe said:**
> [Kubuntu 12.04 Precise]

Hi, i have a usb dongle [SIZE="3"]Netgear N150 WNA1000M[/SIZE] that use the infamous ship **[SIZE="3"]rtl8192cu[/SIZE]**. The built-in driver with **kernel 3.2.0-30** doesn't work at all... Disconnecting every 10 - 30 minutes... 

I don't understand why this rtl8192cu problem has not been resolved since one year ! (and why they build a kernel with such a buggy driver). :mad:

Yea, it is rather frustrating. Ideally, it should have been moved back into staging for improvements, this way, the developers would know that it's not done, and users wouldn't stumble over it, but the phylosophy is - release often and early, and so it's out, and broken.
As for getiing it fixed, that would probably never happen, at least not in the time frame that would matter to any of us. If there hadn't been a relatively easy workaround, then, may be, but Realtek provides a working driver, .

---

### Post by iburroughs on 2012-10-16
Mine disconnects at random intervals. 10 min to 10 days

---

### Post by waterloo2005 on 2012-12-21
In 12.04,when I use realtek driver, the system will dies.
In 12.10 , rtl8192cu within kernel is still NOT stable.

---

### Post by Bucky Ball on 2012-12-22
> **waterloo2005 said:**
> In 12.04,when I use realtek driver, the system will dies.
In 12.10 , rtl8192cu within kernel is still NOT stable.

If you have an issue, please post a new thread with a descriptive title in the appropriate sub-forum rather than attempting to get help on an old, inactive thread buried 34 posts deep.

This will improve your chance of getting help.

[I][B]Thread Closed

Reason: [/B][/I]Old thread put to bed ...

---

