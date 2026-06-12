---
title: "Realtek RTL8191SE"
date: 2009-09-16
forum: Networking &amp; Wireless
---

### Post by fositen on 2009-09-16
Hi there.

I recently purchased a laptop Toshiba L500-13W.
I have installed Ubuntu on it and i have ony one problem for now.

It's Realtek RTL8191SE wireless lan isn't recognized by Ubuntu.

On a desperate try to put it working i've made the upgrade to the new Ubuntu version 9.10(its still in beta) but i couldn't put it to work.

I was hopping for a bit of help regarding this.

Ty for your time.

---

### Post by mattmc on 2009-10-29
You and me both. I can't get the card to work for the life of me. I have the Toshiba l500-02H with the Realtek RTL8191SE WIRELESS CARD PCI-E NIC. I do not have the wifi card with the Bluetooth.
 
I have tried ndiswrapper on 9.04 and no luck there, I have downloaded 9.10 today "not the RC" and ifconfig wlan0 up  says there is no device. I an not new to the bash and ndiswrapper install but can't figure this one out.
 
Anyone have any ideas?

---

### Post by FatherDale on 2009-11-13
Same issue. I have a new Toshiba T115 with Realtek RTL8191SE. Guess this is a windows box....

---

### Post by Aurawin on 2009-11-16
I have a Toshiba T135-S1309 with the same Wireless chip integrated.  I guess I'm stuck with Windows Seven ...
 
Ubuntu needs a driver task force IMO.

---

### Post by Dude-PWB- on 2009-11-16
Check out this thread at launchpad: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/401126](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/401126)

It is for the rtl8192se chipset, but someone in there reported it worked for the 8191se chipset as well.

Alternatively, send an e-mail to realtek and give them your network device info, and the version of ubuntu you are running and they will send you the proper driver.

I just went through all of this with an rtl8192e chipset and they were extremely fast at sending me a driver for it.

---

### Post by bjsmith307 on 2009-12-07
[FONT=Arial]I have a Toshiba Satellite L505 and here is what worked for me: run terminal and type [/FONT]
"sudo apt-get install ndisgtk" [FONT=Arial]and after that is done go [here]("http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=48&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#RTL8192SE") and get the win2k driver.
Then I just unzipped the driver file into the download file. Then I clicked 
system-administration-windows wireless driver, and searched for
for downloads - rtl8191 (the file that you unzipped)-91_92_SE_Driver-win2k-net8192se.inf 
and click install and close. Worked for me hope it works for you! I had to use WPA Personal
and tkip algorithms to make it all work, but it is working good for me.[/FONT]

---

### Post by collegeKid28 on 2009-12-19
Worked for me!!! 

Thank you, bjsmith307 :)


> **bjsmith307 said:**
> [FONT=Arial]I have a Toshiba Satellite L505 and here is what worked for me: run terminal and type [/FONT]
"sudo apt-get install ndisgtk" [FONT=Arial]and after that is done go [here]("http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=48&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#RTL8192SE") and get the win2k driver.
Then I just unzipped the driver file into the download file. Then I clicked 
system-administration-windows wireless driver, and searched for
for downloads - rtl8191 (the file that you unzipped)-91_92_SE_Driver-win2k-net8192se.inf 
and click install and close. Worked for me hope it works for you! I had to use WPA Personal
and tkip algorithms to make it all work, but it is working good for me.[/FONT]

---

### Post by Aurawin on 2009-12-23
I recieved the drivers direct from realtek.  I had to compile them but as soon as I ran make and make install and rebooted it worked.  Anyone need driver source?  I cannot attach source since it's larger than the quota.
 
But I'm using my wireless every day with this version.  It's pretty stable unless you have to switch hotspots.  That may lead to a system hang.  But that hang even happens on Windows 7.

---

### Post by kieran_ole on 2009-12-23
If you can, please, do, i'm on the same boat, i've tried a few different drivers, etc, i've tried the linux drivers on their page to no sucsess, so if you have it i'll take it, thanks...

do you want my email so you can send it??

---

### Post by A_M_S on 2009-12-27
I'm interested!!!


Do you want my email so you can send it??

---

### Post by lukus on 2009-12-27
Yes please, drivers would be fantastic if that's at all possible? I wouldnt mind hosting them on a few sites I admin if its useful at all.  I really need drivers for this chipset pretty quickly.  Cheers

---

### Post by AdeHall on 2009-12-29
Hi Aurawin

Please let me know how I can get this driver - I have emailed Realtek but they are out until the 4th!

Can you send it to me?

Regards

---

### Post by Snow Pickles on 2009-12-29
I'm no expert but I managed to get it working on my Toshiba l505.

I got the driver from [http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&ProdID=226&DownTypeID=3&GetDown=false&Downloads=true#2281](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&ProdID=226&DownTypeID=3&GetDown=false&Downloads=true#2281)
in the RTL8191SE-VA2 section.
Then I did
```

sudo su
make
make install
reboot

```For some reason way beyond my understanding  just "sudo make install" won't work and gives some error about "No rule to make target `kernel/bounds.c', needed by `kernel/bounds.s' ."
Hope this helps

---

### Post by mdalacu on 2009-12-30
yes it's working but only for a short period of time ... :(
After 1 min or so , the wifi connection is dead. My card is in a Asus EeePC 1201N netbook.
i also get this error during boot: *ACPI: I/O resource nForce2_smbus [0x4e00-0x4e3f] conflicts with ACPI region SM00* i don't know if they are related. Anyway, my wifi card does not work properly with the latest Realtek drivers. .:(

---

### Post by Infil on 2010-01-01
I thought I would share my experiences. I have a Clevo W760 with RTL8191SE running 9.10.

I first tried the official Realtek driver and it installed without hassle. However I couldn't connect to anything, even unencrypted networks. 

Then I downloaded file I found [here]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/401126/comments/5") (it's from the bug report linked to previously). Now I can connent to unencrypted networks and it seems it even discovers more networks. But when I try to connect to a WAP network I can't use the regular password, but I have to use the long encryption key which I copied from the connection settings from another computer. A bit annoying.

---

### Post by qwerty123321 on 2010-01-01
> **Snow Pickles said:**
> I'm no expert but I managed to get it working on my Toshiba l505.

I got the driver from [http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&ProdID=226&DownTypeID=3&GetDown=false&Downloads=true#2281](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&ProdID=226&DownTypeID=3&GetDown=false&Downloads=true#2281)
in the RTL8191SE-VA2 section.
Then I did
```

sudo su
make
make install
reboot

```For some reason way beyond my understanding  just "sudo make install" won't work and gives some error about "No rule to make target `kernel/bounds.c', needed by `kernel/bounds.s' ."
Hope this helps
OMG thank you so much!! my wireless now works !!! thank you!

---

### Post by AdeHall on 2010-01-02
No such luck for me I'm afraid. I tried the latest downloaded drivers and followed the same instructions as above but it's still not working.

Here's the output from the lshw command:


*-network UNCLAIMED
       description: Ethernet controller
       product: Atheros AR8132 / L1c Gigabit Ethernet Adapter
       vendor: Attansic Technology Corp.
       physical id: 0
       bus info: pci@0000:07:00.0
       version: c0
       width: 64 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=0
       resources: memory:b6000000-b603ffff ioport:2000(size=128)
  *-network
       description: Wireless interface
       product: Realtek Semiconductor Co., Ltd.
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: wlan3
       version: 10
       serial: 00:e0:4c:81:92:68
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl819xSE driverversion=0013.1127.2009 firmware=74 latency=0 multicast=yes wireless=802.11bgn
       resources: irq:17 ioport:3000(size=256) memory:b6100000-b6103fff


As you can see the wired ethernet card is not working either making it difficult to apply changes!

Does anyone have any ideas please?

---

### Post by mdalacu on 2010-01-02
> **AdeHall said:**
> No such luck for me I'm afraid. I tried the latest downloaded drivers and followed the same instructions as above but it's still not working.

Here's the output from the lshw command:


*-network UNCLAIMED
       description: Ethernet controller
       product: Atheros AR8132 / L1c Gigabit Ethernet Adapter
       vendor: Attansic Technology Corp.
       physical id: 0
       bus info: pci@0000:07:00.0
       version: c0
       width: 64 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=0
       resources: memory:b6000000-b603ffff ioport:2000(size=128)
  *-network
       description: Wireless interface
       product: Realtek Semiconductor Co., Ltd.
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: wlan3
       version: 10
       serial: 00:e0:4c:81:92:68
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl819xSE driverversion=0013.1127.2009 firmware=74 latency=0 multicast=yes wireless=802.11bgn
       resources: irq:17 ioport:3000(size=256) memory:b6100000-b6103fff


As you can see the wired ethernet card is not working either making it difficult to apply changes!

Does anyone have any ideas please?

Do you have Asus 1201N notebook? I have one, and i got my ethernet working by booting with acpi=off parameter (one problem: no touchpad). After that it was no longer required. With the latest drives my wifi is working aprox. for one minute only...:-(

---

### Post by AdeHall on 2010-01-02
I have a Toshiba T130 laptop

---

### Post by Taburn on 2010-01-03
My connection also works for a couple of minutes then dies out. I have a Toshiba Satellite L500. This happens when I install the drivers with the make install command as well as when I copy the firmware to the Kernel (method 2 from the realtek readme file). Is anyone having this problem with Ubuntu 32 bits? (I'm using 64 bits).

---

### Post by mdalacu on 2010-01-04
> **Taburn said:**
> My connection also works for a couple of minutes then dies out. I have a Toshiba Satellite L500. This happens when I install the drivers with the make install command as well as when I copy the firmware to the Kernel (method 2 from the realtek readme file). Is anyone having this problem with Ubuntu 32 bits? (I'm using 64 bits).

Exactly the same on Asus 1201N! (64 and 32 bits)

---

### Post by c1tlr340 on 2010-01-22
Hello all,

Same problem here, Asus 1201n too.

Drops connection every minute or so.

Would love help with this.

---

### Post by c1tlr340 on 2010-01-23
I seem to have found a solution to my problem, so thought I would share.

Having looked at the files installed by driver, it had copied the firmware to the /lib/firmware/2.6.31-17-generic/RTL8192SE folder.

Normally I put firmware files directly into /lib/firmware

So I copied both files into this folder and rebooted, all seems to be fine now.

Hope this helps someone else.:)

---

### Post by vcallas on 2010-01-23
> **c1tlr340 said:**
> I seem to have found a solution to my problem, so thought I would share.

Having looked at the files installed by driver, it had copied the firmware to the /lib/firmware/2.6.31-17-generic/RTL8192SE folder.

Normally I put firmware files directly into /lib/firmware

So I copied both files into this folder and rebooted, all seems to be fine now.

Hope this helps someone else.:)


When you say both files which to files are you talking about? When I list the files in /lib/firmware/2.6.31-17-generic/rtl8192se_linux_2.6.0013.1204.2009 I have 18 things listed.

Looking forward to the reply as am finding this frustrating.
Am running Ubuntu 9.10 64 bit on a Toshiba L450-01M.

---

### Post by Taburn on 2010-01-24
> **vcallas said:**
> When you say both files which to files are you talking about? When I list the files in /lib/firmware/2.6.31-17-generic/rtl8192se_linux_2.6.0013.1204.2009 I have 18 things listed.

Looking forward to the reply as am finding this frustrating.
Am running Ubuntu 9.10 64 bit on a Toshiba L450-01M.

 The files that C1tlr340 is talking about are the ones located in the ../rtl8192se_linux_2.6.0013.1204.2009/firmware/RTL8192se directory. (they are called rtl8192sfw.bin and rtl8192sfw492.bin.  I tried this solution myself and it does not really help anything. Connection still drops every few minutes and I occasionally get asked for my WPA key. I'll keep fiddling around and keep you posted in case of success.

---

### Post by c1tlr340 on 2010-01-24
> **Taburn said:**
> The files that C1tlr340 is talking about are the ones located in the ../rtl8192se_linux_2.6.0013.1204.2009/firmware/RTL8192se directory. (they are called rtl8192sfw.bin and rtl8192sfw492.bin.  I tried this solution myself and it does not really help anything. Connection still drops every few minutes and I occasionally get asked for my WPA key. I'll keep fiddling around and keep you posted in case of success.

Sorry for the false alarm, mine is back to dropping connection.

The BIOS on my 1201n always needs reconfigured on reboot too.

I'm having to use windows just now, as I am finding the problem very annoying.

I am using the latest bios version from Asus, 318.

Now not sure if problem is driver or bios related.:(:(:(

---

### Post by c1tlr340 on 2010-01-24
I normally use a Broadcom card, copy over the firmware and am up and running in about 5 min.

I am considering buying a half size pci-e card and installing it, requires opening it up though.

---

### Post by jdwannam on 2010-01-25
Here is what I used to get a stable wireless driver running on the 1201n.  Many thanks to [David Woo]("https://launchpad.net/~wooshwu") of on launchpad for posting all of the information [here]("https://bugs.launchpad.net/ubuntu/%2Bsource/linux/%2Bbug/401126") that I needed to get it working.  And thanks to the [Phoronix review of the 1201n]("http://www.phoronix.com/scan.php?page=article&item=asus_eee_1201n&num=3") that had the above link.

I've installed the 64-bit version of Ubuntu 9.10, but there are instructions within the bug report for getting it working on the 32-bit version as well.

32-bit Driver:
[http://launchpadlibrarian.net/33927923/rtl8192se_linux_2.6.0010.1012.2009.tar.gz](http://launchpadlibrarian.net/33927923/rtl8192se_linux_2.6.0010.1012.2009.tar.gz)

64-bit Driver:
[http://launchpadlibrarian.net/34090326/rtl8192se_linux_2.6.0010.1012.2009_64bit.tar.gz](http://launchpadlibrarian.net/34090326/rtl8192se_linux_2.6.0010.1012.2009_64bit.tar.gz)

Prerequisites:
```

sudo apt-get install build-essentials
sudo apt-get install linux-headers-`uname -r`

```

[1] Extract the driver using 'tar zxvf <filename>'
[2] CD into the folder and run make
[3] Then run 'make install'
[4] If make install succeeds, reboot and it should be working

If the make install fails (as it did for me) you can manually install the driver using these steps:

[1] Copy the target module in HAL/rtl8192/rt8192se_pci.ko to /lib/modules/`uname -r`/kernel/drivers/net/wireless/
[2] Copy rtl8192se firmware folder to /lib/firmware/`uname -r`
[3] Run the command of `depmod -a`
[4] Run the command of 'modprobe rtl8192se_pci', or reboot.
[5] Check the NetworkManager, and see whether there's network list show out?

Best of luck!

Duncan

---

### Post by joeyy on 2010-01-26
> **Aurawin said:**
> I recieved the drivers direct from realtek.  I had to compile them but as soon as I ran make and make install and rebooted it worked.  Anyone need driver source?  I cannot attach source since it's larger than the quota.
 
But I'm using my wireless every day with this version.  It's pretty stable unless you have to switch hotspots.  That may lead to a system hang.  But that hang even happens on Windows 7.

hey man i need tht could i pm you my email so u could send it?
tht would help me soo much pleas and thank you.

---

### Post by tomazo on 2010-01-27
I bought Msi Wind Top AE2220M yesterday. Installed Ubuntu 9.10 x64, but can't get the wifi working :/ Spent hours trying to make it work.
[img]http://i49.tinypic.com/25je89s.png[/img]

I see my network, but it just won't connect at all. I also tried to change WEP/WPA encryption, didn't help either. This just makes me want to get rid of Ubuntu. Any ideas?

---

### Post by ClosAttack on 2010-01-27
I have an Asus 1201n with the realtek 1892se wirless card.  After much hassle I found this: [http://dillernet.com/apple/2010/01/10/eee-1201n-wifi-working-in-karmic-ubuntu](http://dillernet.com/apple/2010/01/10/eee-1201n-wifi-working-in-karmic-ubuntu)

which has instructions for using ndiswrapper to get it working.
Hope it helps.

Also this is with 9.10, not sure about anything else.

---

### Post by tomazo on 2010-01-28
Well, I was still playing with the previously installed driver. Managed to connect to my network now, but it's just totally unusable.
Looks almost fine when there's no network traffic:
```
64 bytes from 192.168.1.1: icmp_seq=4 ttl=255 time=47.4 ms
64 bytes from 192.168.1.1: icmp_seq=5 ttl=255 time=6.58 ms
64 bytes from 192.168.1.1: icmp_seq=6 ttl=255 time=34.6 ms
64 bytes from 192.168.1.1: icmp_seq=7 ttl=255 time=20.8 ms
64 bytes from 192.168.1.1: icmp_seq=8 ttl=255 time=14.7 ms
64 bytes from 192.168.1.1: icmp_seq=10 ttl=255 time=12.5 ms
64 bytes from 192.168.1.1: icmp_seq=11 ttl=255 time=11.0 ms
64 bytes from 192.168.1.1: icmp_seq=12 ttl=255 time=5.66 ms
64 bytes from 192.168.1.1: icmp_seq=13 ttl=255 time=14.5 ms
64 bytes from 192.168.1.1: icmp_seq=14 ttl=255 time=7.33 ms
64 bytes from 192.168.1.1: icmp_seq=17 ttl=255 time=30.9 ms
64 bytes from 192.168.1.1: icmp_seq=18 ttl=255 time=15.6 ms
64 bytes from 192.168.1.1: icmp_seq=19 ttl=255 time=17.6 ms
64 bytes from 192.168.1.1: icmp_seq=20 ttl=255 time=38.3 ms
```

But it just gets TOTALLY unusable right in the moment I do anything on the network - this is when I opened firefox and tried to load a page:
```
64 bytes from 192.168.1.1: icmp_seq=29 ttl=255 time=1492 ms
64 bytes from 192.168.1.1: icmp_seq=30 ttl=255 time=926 ms
64 bytes from 192.168.1.1: icmp_seq=34 ttl=255 time=1068 ms
64 bytes from 192.168.1.1: icmp_seq=38 ttl=255 time=433 ms
64 bytes from 192.168.1.1: icmp_seq=41 ttl=255 time=128 ms
64 bytes from 192.168.1.1: icmp_seq=43 ttl=255 time=560 ms
64 bytes from 192.168.1.1: icmp_seq=44 ttl=255 time=1253 ms
64 bytes from 192.168.1.1: icmp_seq=45 ttl=255 time=794 ms
64 bytes from 192.168.1.1: icmp_seq=48 ttl=255 time=323 ms
64 bytes from 192.168.1.1: icmp_seq=53 ttl=255 time=340 ms
64 bytes from 192.168.1.1: icmp_seq=54 ttl=255 time=462 ms
64 bytes from 192.168.1.1: icmp_seq=56 ttl=255 time=1487 ms
64 bytes from 192.168.1.1: icmp_seq=58 ttl=255 time=1335 ms
64 bytes from 192.168.1.1: icmp_seq=59 ttl=255 time=432 ms
64 bytes from 192.168.1.1: icmp_seq=62 ttl=255 time=1665 ms
64 bytes from 192.168.1.1: icmp_seq=64 ttl=255 time=1807 ms
64 bytes from 192.168.1.1: icmp_seq=65 ttl=255 time=1671 ms
```

That windows driver is gonna work with 64bit Ubuntu too?

---

### Post by ClosAttack on 2010-01-28
Not sure if the ndiswrapper solution will work for 64bit, I'm running 32bit, but it's worth a try as it works flawlessly on 32bit.

---

### Post by tomazo on 2010-01-28
Tried that Windows driver, but no success.
```
azo@azo-desktop-sk:~/Downloads$ ndiswrapper -l
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
net8192se : driver installed
	device (10EC:8172) present (alternate driver: r8192se_pci)
azo@azo-desktop-sk:~/Downloads$ sudo depmod -a
azo@azo-desktop-sk:~/Downloads$ sudo modprobe ndiswrapper
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
azo@azo-desktop-sk:~/Downloads$ ifconfig
eth0      Link encap:Ethernet  HWaddr 40:61:86:5c:46:17  
          inet addr:192.168.1.10  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::4261:86ff:fe5c:4617/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:7293 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6809 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:6662850 (6.6 MB)  TX bytes:1302140 (1.3 MB)
          Interrupt:30 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:14 errors:0 dropped:0 overruns:0 frame:0
          TX packets:14 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:808 (808.0 B)  TX bytes:808 (808.0 B)

```

---

### Post by ClosAttack on 2010-01-28
The instructions might not mention that you need to add the line

ndiswrapper

to the /etc/modules file.  Also be sure to restart after applying the ndiswrapper solution.

---

### Post by tony conroy on 2010-01-28
after installing 9.10 on my toshiba latop i have battled continuously with the the rtl8192 wireless adapter. i am using the native linux drivers. after several iterations of testing, i can verify the following:
- i can successfully connect with wpa enabled, and run a continous ping of my wireless router without error. 
- i can open a very simple web page (i.e. google.com) with no issues either. 
- opening any webpage containing flash or other embedded media causes the wireless session to drop the connection.
- at the same time that connection dropped, the ping "session" (still running in the background) switched from ms response times to "destination host unreachable."
- once the connection has been dropped, the error seems to be unrecoverable. the only way to restore the connection is to reboot.
 
any expert opinions on what would cause this type of behavior? at first i was cursing the adapter, but now i'm not so sure.

---

### Post by tomazo on 2010-01-29
> **ClosAttack said:**
> The instructions might not mention that you need to add the line

ndiswrapper

to the /etc/modules file.  Also be sure to restart after applying the ndiswrapper solution.Made no difference :(

---

### Post by w1ll15 on 2010-02-06
> **jdwannam said:**
> Here is what I used to get a stable wireless driver running on the 1201n.  Many thanks to [David Woo]("https://launchpad.net/~wooshwu") of on launchpad for posting all of the information [here]("https://bugs.launchpad.net/ubuntu/%2Bsource/linux/%2Bbug/401126") that I needed to get it working.  And thanks to the [Phoronix review of the 1201n]("http://www.phoronix.com/scan.php?page=article&item=asus_eee_1201n&num=3") that had the above link.

I've installed the 64-bit version of Ubuntu 9.10, but there are instructions within the bug report for getting it working on the 32-bit version as well.

32-bit Driver:
[http://launchpadlibrarian.net/33927923/rtl8192se_linux_2.6.0010.1012.2009.tar.gz](http://launchpadlibrarian.net/33927923/rtl8192se_linux_2.6.0010.1012.2009.tar.gz)

64-bit Driver:
[http://launchpadlibrarian.net/34090326/rtl8192se_linux_2.6.0010.1012.2009_64bit.tar.gz](http://launchpadlibrarian.net/34090326/rtl8192se_linux_2.6.0010.1012.2009_64bit.tar.gz)

Prerequisites:
```

sudo apt-get install build-essentials
sudo apt-get install linux-headers-`uname -r`

```

[1] Extract the driver using 'tar zxvf <filename>'
[2] CD into the folder and run make
[3] Then run 'make install'
[4] If make install succeeds, reboot and it should be working

If the make install fails (as it did for me) you can manually install the driver using these steps:

[1] Copy the target module in HAL/rtl8192/rt8192se_pci.ko to /lib/modules/`uname -r`/kernel/drivers/net/wireless/
[2] Copy rtl8192se firmware folder to /lib/firmware/`uname -r`
[3] Run the command of `depmod -a`
[4] Run the command of 'modprobe rtl8192se_pci', or reboot.
[5] Check the NetworkManager, and see whether there's network list show out?

Best of luck!

Duncan
Thank you so much !! My wireless is now working great on asus 1201n karmic 64bit

ONE NOTE no s needed on build-essential   and make install comand must be done as su

"sudo su"

thank you again

---

### Post by w1ll15 on 2010-02-06
one more thing ...
it did not work right after restart...

I went to System > Admin...> hardware drivers ..then deactivated driver then reactivated it and it started working!!!!:D

---

### Post by Taburn on 2010-02-08
Hello all!
I seem to have finally figured out what was not working with my card. I fiddled around with some of the ideas posted here for a while, but never actually got to somewhere where my connection wouldn't drop every so often. Now, when my connection would drop, I would get asked for my WPA key phrase, that sent me on the right track. I went into my rtl8192se_linux_2.6.0013.1204.2009 folder and open the file wpal.conf. In there, I replaced what they had for the SSID with my network ID and put my key into the psk line. I saved, then deactivated my wireless by right clicking on the network manager. I reactivated it and it has been working ever since. There seem to still be some fluctuation in the signal strength, but it always comes back whereas it used to completely drop before.:D

---

### Post by w1ll15 on 2010-02-10
> **tomazo said:**
> I bought Msi Wind Top AE2220M yesterday. Installed Ubuntu 9.10 x64, but can't get the wifi working :/ Spent hours trying to make it work.
[img]http://i49.tinypic.com/25je89s.png[/img]

I see my network, but it just won't connect at all. I also tried to change WEP/WPA encryption, didn't help either. This just makes me want to get rid of Ubuntu. Any ideas?
The same thing is happening to me...it works now but...I have to deactivate and reactivate the driver everytime i reboot...:(

---

### Post by girlette on 2010-03-05
> **bjsmith307 said:**
> [FONT=Arial]I have a Toshiba Satellite L505 and here is what worked for me: run terminal and type [/FONT]
"sudo apt-get install ndisgtk" [FONT=Arial]and after that is done go [URL="http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=48&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#RTL8192SE"]here[,/URL] and get the win2k driver.
Then I just unzipped the driver file into the download file. Then I clicked 
system-administration-windows wireless driver, and searched for
for downloads - rtl8191 (the file that you unzipped)-91_92_SE_Driver-win2k-net8192se.inf 
and click install and close. Worked for me hope it works for you! I had to use WPA Personal
and tkip algorithms to make it all work, but it is working good for me.[/FONT]

tried this on my 1201N-dual boot (w7&karmic), and it works!
thanks, bjsmith307

---

### Post by tomazo on 2010-03-13
> **w1ll15 said:**
> The same thing is happening to me...it works now but...I have to deactivate and reactivate the driver everytime i reboot...:(You're right :O I just gave it a try again, installed new drivers and was happy that it worked. Until I rebooted ... but as you say, deactivating and activating the driver helps. Weird.

---

### Post by Tovam on 2010-03-14
> **jdwannam said:**
> Here is what I used to get a stable wireless driver running on the 1201n.  Many thanks to [David Woo]("https://launchpad.net/~wooshwu") of on launchpad for posting all of the information [here]("https://bugs.launchpad.net/ubuntu/%2Bsource/linux/%2Bbug/401126") that I needed to get it working.  And thanks to the [Phoronix review of the 1201n]("http://www.phoronix.com/scan.php?page=article&item=asus_eee_1201n&num=3") that had the above link.

I've installed the 64-bit version of Ubuntu 9.10, but there are instructions within the bug report for getting it working on the 32-bit version as well.

32-bit Driver:
[http://launchpadlibrarian.net/33927923/rtl8192se_linux_2.6.0010.1012.2009.tar.gz](http://launchpadlibrarian.net/33927923/rtl8192se_linux_2.6.0010.1012.2009.tar.gz)

64-bit Driver:
[http://launchpadlibrarian.net/34090326/rtl8192se_linux_2.6.0010.1012.2009_64bit.tar.gz](http://launchpadlibrarian.net/34090326/rtl8192se_linux_2.6.0010.1012.2009_64bit.tar.gz)

Prerequisites:
```

sudo apt-get install build-essentials
sudo apt-get install linux-headers-`uname -r`

```

[1] Extract the driver using 'tar zxvf <filename>'
[2] CD into the folder and run make
[3] Then run 'make install'
[4] If make install succeeds, reboot and it should be working

If the make install fails (as it did for me) you can manually install the driver using these steps:

[1] Copy the target module in HAL/rtl8192/rt8192se_pci.ko to /lib/modules/`uname -r`/kernel/drivers/net/wireless/
[2] Copy rtl8192se firmware folder to /lib/firmware/`uname -r`
[3] Run the command of `depmod -a`
[4] Run the command of 'modprobe rtl8192se_pci', or reboot.
[5] Check the NetworkManager, and see whether there's network list show out?

Best of luck!

Duncan

Going fine until I do 'sudo make install', then I just get...

```
make[1]: Entering directory `/usr/src/linux-headers-2.6.31-20-generic'
  Building modules, stage 2.
  MODPOST 1 modules
make[1]: Leaving directory `/usr/src/linux-headers-2.6.31-20-generic'
make[1]: Entering directory `/home/tomas/Desktop/rtl8192se_linux_2.6.0010.1020.2009_64bit/HAL/rtl8192'
make -C /lib/modules/2.6.31-20-generic/build M= CC=gcc modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.31-20-generic'
  CHK     include/linux/version.h
  CHK     include/linux/utsrelease.h
  SYMLINK include/asm -> include/asm-x86
make[3]: *** No rule to make target `kernel/bounds.c', needed by `kernel/bounds.s'.  Stop.
make[2]: *** [prepare0] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.31-20-generic'
make[1]: *** [modules] Error 2
make[1]: Leaving directory `/home/tomas/Desktop/rtl8192se_linux_2.6.0010.1020.2009_64bit/HAL/rtl8192'
make: *** [install] Error 2

```

This with a Toshiba Satellite P500, the Realtek RTL8191SE wireless network card and Ubuntu 9.10 64-bit.

Does anyone know what this is, or how to solve it?

Thanks in advance.

---

### Post by jdwannam on 2010-03-14
> **Tovam said:**
> Going fine until I do 'sudo make install', then I just get...

```
make[1]: Entering directory `/usr/src/linux-headers-2.6.31-20-generic'
  Building modules, stage 2.
  MODPOST 1 modules
make[1]: Leaving directory `/usr/src/linux-headers-2.6.31-20-generic'
make[1]: Entering directory `/home/tomas/Desktop/rtl8192se_linux_2.6.0010.1020.2009_64bit/HAL/rtl8192'
make -C /lib/modules/2.6.31-20-generic/build M= CC=gcc modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.31-20-generic'
  CHK     include/linux/version.h
  CHK     include/linux/utsrelease.h
  SYMLINK include/asm -> include/asm-x86
make[3]: *** No rule to make target `kernel/bounds.c', needed by `kernel/bounds.s'.  Stop.
make[2]: *** [prepare0] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.31-20-generic'
make[1]: *** [modules] Error 2
make[1]: Leaving directory `/home/tomas/Desktop/rtl8192se_linux_2.6.0010.1020.2009_64bit/HAL/rtl8192'
make: *** [install] Error 2

```

This with a Toshiba Satellite P500, the Realtek RTL8191SE wireless network card and Ubuntu 9.10 64-bit.

Does anyone know what this is, or how to solve it?

Thanks in advance.

This is common, did you try the manual steps I posted?  make install fails for me as well.. but the manual install works every time.

Duncan

---

### Post by Dude-PWB- on 2010-03-14
The one common problem with the realtek instructions are that you need to extract the drivers, then:

```
sudo su
```to get to a root shell, then:

```
make
make install

```
Read the instructions we went through [HERE]("http://ubuntuforums.org/showthread.php?t=1239342") to get the drivers to function properly.

Make sure you edit the /etc/modules file to load the driver at startup

```
sudo gedit /etc/modules
```Hope this helps.

Edit: This was for the 32bit rtl8192e driver, so make the necessary changes for the se and/or 64bit driver.

---

### Post by tracyandskye on 2010-03-21
I have a 1201n with the same in & out wireless problems (after loading the linux driver).  So I'm trying to do this:

> 
Quote:
Originally Posted by jdwannam View Post
Here is what I used to get a stable wireless driver running on the 1201n. Many thanks to David Woo of on launchpad for posting all of the information here that I needed to get it working. And thanks to the Phoronix review of the 1201n that had the above link.

I've installed the 64-bit version of Ubuntu 9.10, but there are instructions within the bug report for getting it working on the 32-bit version as well.

32-bit Driver:
[http://launchpadlibrarian.net/339279...12.2009.tar.gz](http://launchpadlibrarian.net/339279...12.2009.tar.gz)

64-bit Driver:
[http://launchpadlibrarian.net/340903...9_64bit.tar.gz](http://launchpadlibrarian.net/340903...9_64bit.tar.gz)

Prerequisites:
Code:

sudo apt-get install build-essentials
sudo apt-get install linux-headers-`uname -r`

[1] Extract the driver using 'tar zxvf <filename>'
[2] CD into the folder and run make
[3] Then run 'make install'
[4] If make install succeeds, reboot and it should be working

If the make install fails (as it did for me) you can manually install the driver using these steps:

[1] Copy the target module in HAL/rtl8192/rt8192se_pci.ko to /lib/modules/`uname -r`/kernel/drivers/net/wireless/
[2] Copy rtl8192se firmware folder to /lib/firmware/`uname -r`
[3] Run the command of `depmod -a`
[4] Run the command of 'modprobe rtl8192se_pci', or reboot.
[5] Check the NetworkManager, and see whether there's network list show out?

Best of luck!

Duncan
Thank you so much !! My wireless is now working great on asus 1201n karmic 64bit

ONE NOTE no s needed on build-essential and make install comand must be done as su

"sudo su"


but I'm having problems with the first part.  I did:

```
sudo apt-get install build-essential
```

and it told me I already had the latest version.  OK, so I did:

```
sudo apt-get install linux-headers-'beautybooty -r'
```

and it told me that it couldn't find package linux-headers-beautybooty -r.  I assume my syntax is wrong but I don't know how.  I tried it without the ' symbols but that appeared to be incorrect.

---

### Post by chili555 on 2010-03-21
> sudo apt-get install linux-headers-'beautybooty -r'Indeed the syntax is wrong; in several respects. First of all, if you, and the others here, install headers only for your running kernel version `uname -r` then the headers will not get updated when a newer kernel is installed. For example, when linux-image-2.6.31-21-generic comes out, you will *not* automatically get the matching headers.

When a newer kernel comes out and you boot into it, your compiled-from-source driver will not work. You must then do:```
cd Desktop/driver_file
sudo su
make clean
make
make install
modprobe rt8192se_pc
exit
```No headers for x-21? No joy.

The correct method is to install headers as follows:```
sudo apt-get install linux-headers-generic
```If you wanted to intentionally error and install the wrong thing:```
sudo apt-get install linux-headers-`uname -r`
```uname -r means whatever my currently running kernel is. Those tickmarks are on the left side of my US keyboard with ~.

---

### Post by tracyandskye on 2010-03-21
Ahh, obviously I thought uname was supposed to be my username.

What you are saying about the headers makes sense.  I guess I can do that and then the rest of the steps to try & get this wireless working.  Does that mean that when the updates install a new kernal that it will break the wireless again?

Actually, looking at the directions, I realize that I have already done the make & make install thing so this doesn't get me to a working wireless adapter.  This is really frustrating because there is a linux driver for this card.  It seems that it should work in Ubuntu...

Thx-

---

### Post by chili555 on 2010-03-21
> updates install a new kernal that it will break the wireless again?
Yes, but just follow the steps I outlined above. In fact, just try them now and let me know if your wireless springs to life.

---

### Post by tracyandskye on 2010-03-21
Modprobe brings back an error that the module is not found.

---

### Post by chili555 on 2010-03-21
Man, oh man! I gotta scrape a few layers of grime off of these trifocals!```
sudo modprobe r8192se_pc[COLOR="Red"]i[/COLOR]
```If the prompt says nothing, then it has loaded successfully. Then, hopefully, connect with Network Manager.

---

### Post by tracyandskye on 2010-03-21
The prompt said nothing but the behaviour is the same.  The wireless seems to work for a minute, then drops out.  It shows a good signal & says that it's active, but it's not really working.

---

### Post by chili555 on 2010-03-21
> **tracyandskye said:**
> The prompt said nothing but the behaviour is the same.  The wireless seems to work for a minute, then drops out.  It shows a good signal & says that it's active, but it's not really working.Please post:```
iwconfig
ifconfig
```Is the wired ethernet disconnected when it tries to connect? Thanks.

---

### Post by tracyandskye on 2010-03-21
This is with the network cable unplugged & the wireless enabled & with a good signal

```
beautybooty@BeautyBooty:~$ iwconfig
lo        no wireless extensions.

wlan0     802.11bgn  ESSID:"VooDooNet"  Nickname:"rtl8191SEVA1"
          Mode:Managed  Frequency=2.417 GHz  Access Point: 00:1E:58:27:AC:2B   
          Bit Rate=150 Mb/s   
          Retry:on   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=88/100  Signal level=-53 dBm  Noise level=-114 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.

pan0      no wireless extensions.

beautybooty@BeautyBooty:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr e0:cb:4e:97:43:5f  
          inet6 addr: fe80::e2cb:4eff:fe97:435f/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:20980304 errors:0 dropped:0 overruns:0 frame:0
          TX packets:597 errors:0 dropped:0 overruns:0 carrier:2
          collisions:0 txqueuelen:1000 
          RX bytes:475315 (475.3 KB)  TX bytes:114201 (114.2 KB)
          Interrupt:27 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:10 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:662 (662.0 B)  TX bytes:662 (662.0 B)

wlan0     Link encap:Ethernet  HWaddr 1c:4b:d6:60:a3:bf  
          inet addr:192.168.0.197  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::1e4b:d6ff:fe60:a3bf/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:570 errors:0 dropped:0 overruns:0 frame:0
          TX packets:686 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:136676 (136.6 KB)  TX bytes:75802 (75.8 KB)
          Interrupt:19 Memory:f81c8000-f81c8100
```

---

### Post by chili555 on 2010-03-21
Man! Those are some great looking settings! I notice the card wants to do N speeds:> Bit Rate=150 Mb/s Does your router support N speeds? Will it stay connected if you drop it down to G?```
sudo iwconfig wlan0 rate 54M
```N is a bit twitchy in Linux right now.

---

### Post by tracyandskye on 2010-03-21
It's working!!!  I changed the router settings to G only.

Really sucks that Ubuntu/N is not quite there.  I've had a D-Link DIR 655 router for a while & was so excited to finally get a laptop with N...

Thanks so much!  If it were not for people like you, Ubuntu would not be an option for people like me.  I need to get over to the absolute beginner forums & start helping.

Peace-

---

### Post by MartinuxP on 2010-03-24
Hi,
I'm using Lucid, I have an Asus EEE 1201t and this wifi adapter.
It work only with revision -15 of the kernel, -16 and -17 (the actual) seems not to like my board; iwconfig sees the card but the scan sees no networks.
Any ideas about that?
Is this a known bug?

Bye!

---

### Post by kitarof on 2010-03-25
bonjour

ça marche pour moi
j'ai téléchargé le pilote depuis [**ce lien**]("http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=41&PFid=9&Level=6&Conn=5&DownTypeID=3&GetDown=false")

j'utilise ubuntu 9.10
Realtek RTL8191SE 802.11n PCI-E NIC

--- TRANSLATION ---
hello

it  works for me
I downloaded  the driver from[** this link**]("http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=41&PFid=9&Level=6&Conn=5&DownTypeID=3&GetDown=false")

I use Ubuntu 9.10
Realtek  RTL8191SE 802.11n PCI-E NIC

---

### Post by ivosir on 2010-03-26
Hi folks,

Sorry for crossposting... but after a sleepless night I managed to make my connection working and stable. :-)

Running Ubuntu Karmic (9.10) 64bit on Asus EEE 1201N with rtl8192se wifi interface.

A few days ago I bought a new wifi router, 802.11n capable. Since that time the connection was a nightmare. Drop-outs every few minutes, kernel panics, cold resets. I tried many driver versions from both [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/401126](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/401126) and [http://www.realtek.com.tw/downloads/](http://www.realtek.com.tw/downloads/), no joy. Ndiswrapper does not work for this network interface on the 64bit OS.

Finally, switching the router from WPA2 to WPA did the magic. Now running the latest driver from the Realtek web site,tThe connection has been rock stable, about 30 hours without a single drop-out, 150 Mbps.

Either the WPA2 implementation must be faulty in the device driver or there is a coincidence of the WPA2 and the 802.11n standard.

Cheers!
Ivo

---

### Post by MartinuxP on 2010-04-03
Hi,

I've just tried the file you suggested but with rev. 17 of Lucid Kernel still no wireless network on my laptop :(

Here a part of my dmesg:
```
Apr  4 07:51:54 martino-eee kernel: [  231.348310] Linux kernel driver for RTL8192 based WLAN cards
Apr  4 07:51:54 martino-eee kernel: [  231.348314] Copyright (c) 2007-2008, Realsil Wlan Driver
Apr  4 07:51:54 martino-eee kernel: [  231.348889] rtl819xSE 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Apr  4 07:51:54 martino-eee kernel: [  231.349741] Adapter(8192SE) is found - DeviceID=8171
Apr  4 07:51:54 martino-eee kernel: [  231.410118] rtl819xSE 0000:02:00.0: firmware: requesting RTL8192SE/rtl8192sfw.bin
Apr  4 07:51:54 martino-eee kernel: [  231.531929] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
Apr  4 07:51:54 martino-eee kernel: [  231.542583] ===>rtllib_start_scan()
Apr  4 07:51:54 martino-eee kernel: [  231.548954] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Apr  4 07:52:01 martino-eee kernel: [  238.540104] ----------->rtl8192se_check_hw_scan()
Apr  4 07:52:01 martino-eee kernel: [  238.540114] FW Scan long time without stop, stop hw scan
Apr  4 07:52:01 martino-eee kernel: [  238.541135] <-----------rtl8192se_check_hw_scan()
Apr  4 07:52:08 martino-eee kernel: [  245.560083] ----------->rtl8192se_check_hw_scan()
Apr  4 07:52:08 martino-eee kernel: [  245.560092] FW Scan long time without stop, stop hw scan
Apr  4 07:52:08 martino-eee kernel: [  245.561111] <-----------rtl8192se_check_hw_scan()
Apr  4 07:52:22 martino-eee kernel: [  259.048751] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
Apr  4 07:52:29 martino-eee kernel: [  266.050081] ----------->rtl8192se_check_hw_scan()
Apr  4 07:52:29 martino-eee kernel: [  266.050092] FW Scan long time without stop, stop hw scan
Apr  4 07:52:29 martino-eee kernel: [  266.051115] <-----------rtl8192se_check_hw_scan()
Apr  4 07:52:52 martino-eee kernel: [  289.048262] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
Apr  4 07:52:59 martino-eee kernel: [  296.060160] ----------->rtl8192se_check_hw_scan()
Apr  4 07:52:59 martino-eee kernel: [  296.060178] FW Scan long time without stop, stop hw scan
Apr  4 07:52:59 martino-eee kernel: [  296.061217] <-----------rtl8192se_check_hw_scan()
Apr  4 07:53:32 martino-eee kernel: [  329.047323] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
Apr  4 07:53:39 martino-eee kernel: [  336.060053] ----------->rtl8192se_check_hw_scan()
Apr  4 07:53:39 martino-eee kernel: [  336.060064] FW Scan long time without stop, stop hw scan
Apr  4 07:53:39 martino-eee kernel: [  336.061086] <-----------rtl8192se_check_hw_scan()
Apr  4 07:54:22 martino-eee kernel: [  379.048305] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
Apr  4 07:54:29 martino-eee kernel: [  386.050099] ----------->rtl8192se_check_hw_scan()
Apr  4 07:54:29 martino-eee kernel: [  386.050107] FW Scan long time without stop, stop hw scan
Apr  4 07:54:29 martino-eee kernel: [  386.051129] <-----------rtl8192se_check_hw_scan()
```

It keeps on scanning without results...

---

### Post by MartinuxP on 2010-04-06
same with rev 19, both drivers.

---

### Post by c0ppelius on 2010-04-07
I am having the same problem with a Lenovo x200 running Lucid beta 1. I can initially connect upon boot but am disconnected after a few minutes and can no longer reconnect. The card scans without results.

---

### Post by internalkernel on 2010-04-08
Im running an eeepc 1201N, realtek 8192SE - this fix worked for me... 

share the love: 

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/530275](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/530275)

---

### Post by MartinuxP on 2010-04-15
Even with the package in the Matt Price ppa my card is not working, can't see any network and dmesg says:
```
dmesg | grep -i rtl
[   14.660675] rtllib_crypt: registered algorithm 'NULL'
[   14.660681] rtllib_crypt: registered algorithm 'TKIP'
[   14.660684] rtllib_crypt: registered algorithm 'CCMP'
[   14.660686] rtllib_crypt: registered algorithm 'WEP'
[   14.660689] Linux kernel driver for RTL8192 based WLAN cards
[   14.665184] rtl819xSE 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   14.665301] rtl819xSE 0000:02:00.0: setting latency timer to 64
[   19.236956] rtl819xSE 0000:02:00.0: firmware: requesting RTL8192SE/rtl8192sfw.bin
[   19.246503] rtl819xSE:request firmware fail!
[   19.246559] rtl819xSE:Firmware Download Fail!!a
[   19.290385] rtl819xSE 0000:02:00.0: firmware: requesting RTL8192SE/rtl8192sfw.bin
[   19.302244] rtl819xSE:request firmware fail!
[   19.302300] rtl819xSE:Firmware Download Fail!!a
[   19.331993] rtl819xSE 0000:02:00.0: firmware: requesting RTL8192SE/rtl8192sfw.bin
[   19.339400] rtl819xSE:request firmware fail!
[   19.339457] rtl819xSE:Firmware Download Fail!!a
[   19.360502] rtl819xSE 0000:02:00.0: firmware: requesting RTL8192SE/rtl8192sfw.bin
[   19.364399] rtl819xSE:request firmware fail!
[   19.364455] rtl819xSE:Firmware Download Fail!!a
[   19.381323] rtl819xSE 0000:02:00.0: firmware: requesting RTL8192SE/rtl8192sfw.bin
[   19.387500] rtl819xSE:request firmware fail!
[   19.387555] rtl819xSE:Firmware Download Fail!!a
[   19.407630] rtl819xSE 0000:02:00.0: firmware: requesting RTL8192SE/rtl8192sfw.bin
[   19.423819] rtl819xSE:request firmware fail!
[   19.423874] rtl819xSE:Firmware Download Fail!!a
[   19.442310] rtl819xSE 0000:02:00.0: firmware: requesting RTL8192SE/rtl8192sfw.bin
[   19.453238] rtl819xSE:request firmware fail!
[   19.453294] rtl819xSE:Firmware Download Fail!!a
[   19.480083] rtl819xSE 0000:02:00.0: firmware: requesting RTL8192SE/rtl8192sfw.bin
[   19.486011] rtl819xSE:request firmware fail!
[   19.486067] rtl819xSE:Firmware Download Fail!!a
[   19.502519] rtl819xSE 0000:02:00.0: firmware: requesting RTL8192SE/rtl8192sfw.bin
[   19.505484] rtl819xSE:request firmware fail!
[   19.505539] rtl819xSE:Firmware Download Fail!!a
[   19.538926] rtl819xSE 0000:02:00.0: firmware: requesting RTL8192SE/rtl8192sfw.bin
[   19.548814] rtl819xSE:request firmware fail!
[   19.548869] rtl819xSE:Firmware Download Fail!!a
[   19.574114] rtl819xSE 0000:02:00.0: firmware: requesting RTL8192SE/rtl8192sfw.bin
[   19.583599] rtl819xSE:request firmware fail!
[   19.583656] rtl819xSE:Firmware Download Fail!!a
[   19.583660] rtl819xSE:ERR!!! _rtl8192_sta_up(): initialization is failed!
[  230.198814] rtl819xSE 0000:02:00.0: PCI INT A disabled
[  230.201145] rtllib_crypt: unregistered algorithm 'TKIP'
[  230.201156] rtllib_crypt: unregistered algorithm 'CCMP'
[  230.201162] rtllib_crypt: unregistered algorithm 'WEP'
[  230.201168] rtllib_crypt: unregistered algorithm 'NULL' (deinit)
```

---

### Post by MartinuxP on 2010-04-17
With the new kernel (rev. 21) it worked without any changes (using the dkms system to compile the driver automatically).

Happy :D

---

### Post by ales85 on 2010-04-30
Hello everybody,

well I have, as many of you, problem with wireless on Ubuntu 10.04 LTS. I installed it yesterday and can't get wireless to work. I tried instructions on net to install rtl8192se_pci module and it worked with 9.10 but not now.

I also tried packet from here [https://launchpad.net/~matt-price/+archive/mattprice](https://launchpad.net/~matt-price/+archive/mattprice) but it doesn't help.

I have Asus 1201N and I get these messages from dmesg:

[   18.229017] rtl819xSE 0000:07:00.0: firmware: requesting RTL8192SE/rtl8192sfw.bin
[   18.237657] rtl819xSE:request firmware fail!
[   18.237662] 
[   18.237672] rtl819xSE:Firmware Download Fail!!a
[   18.237675] 
[   18.244934] rtl819xSE 0000:07:00.0: firmware: requesting RTL8192SE/rtl8192sfw.bin
[   18.245325] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:08.0/input/input9
[   18.253868] rtl819xSE:request firmware fail!
[   18.253873] 
[   18.253882] rtl819xSE:Firmware Download Fail!!a
repeatedly...

lspci outputs this:

07:00.0 Network controller: Realtek Semiconductor Co., Ltd. Device 8171 (rev 10)
	Subsystem: Device 1a3b:1107
	Flags: bus master, fast devsel, latency 0, IRQ 19
	I/O ports at d800 [size=256]
	Memory at fbefc000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: rtl819xSE
	Kernel modules: r8192se_pci

But I'm not able to get any connection or even to see an available wireless network. The icon is with exclamation mark all the time.

I also installed the proposed updates (kernel rev. 22) but no change.

What else can I try?

---

### Post by chili555 on 2010-04-30
> rtl819xSE 0000:07:00.0: firmware: requesting RTL8192SE/rtl8192sfw.bin
rtl819xSE:request firmware fail!Please see here: [http://ubuntuforums.org/showpost.php?p=9187347&postcount=5](http://ubuntuforums.org/showpost.php?p=9187347&postcount=5)

Please download the attachment to your desktop. Right click and select Extract Here. Now open a terminal and do:```
cd /lib/firmware/`uname -r` && ls
```Those tickmarks are on the upper left of my US keyboard on the same key with ~. Do you see a file called RTL8192SE? If so, do:```
cp ~/Desktop/rtl8192sfw.bin RTL8192SE
cd RTL8192SE
sudo chmod 755 *
sudo chown root:root *
```If you do not have such a file, create one:```
sudo mkdir RTL8192SE
```Now proceed with the steps above to copy over the firmware, give it the correct permissions and owner.

After a reboot, you should be working. If not, let us see:```
dmesg | grep -i rtl819
```

---

### Post by Ayreonic on 2010-04-30
I also have an 1201N netboot and it looks like my wireless card has a sleeping disorder..
This is what I get after installing Matt price wireless driver.

```
[  222.053904] rtl8192_hw_wakeup(): RF Change in progress! schedule wake up task again
[  222.056761] rtl8192_hw_wakeup(): RF Change in progress! schedule wake up task again
[  244.430582] ===>rtl8192se_link_change():ieee->iw_mode is 2
[  245.954085] ===>rtl8192se_link_change():ieee->iw_mode is 2
[  270.064035] rtl8192_hw_wakeup(): RF Change in progress! schedule wake up task again
[  302.067824] rtl8192_hw_sleep_down(): RF Change in progress!
[  304.072041] rtl8192_hw_wakeup(): RF Change in progress! schedule wake up task again
[  316.069046] rtl8192_hw_wakeup(): RF Change in progress! schedule wake up task again
[  344.430121] ===>rtl8192se_link_change():ieee->iw_mode is 2
[  345.950100] ===>rtl8192se_link_change():ieee->iw_mode is 2
[  390.072858] rtl8192_hw_sleep_down(): RF Change in progress!
[  440.068725] rtl8192_hw_sleep_down(): RF Change in progress!
[  442.072038] rtl8192_hw_wakeup(): RF Change in progress! schedule wake up task again
[  464.435355] ===>rtl8192se_link_change():ieee->iw_mode is 2
[  465.954091] ===>rtl8192se_link_change():ieee->iw_mode is 2
[  570.078494] rtl8192_hw_sleep_down(): RF Change in progress!
[  572.080050] rtl8192_hw_wakeup(): RF Change in progress! schedule wake up task again
[  584.435380] ===>rtl8192se_link_change():ieee->iw_mode is 2
[  585.954124] ===>rtl8192se_link_change():ieee->iw_mode is 2
[  616.078802] rtl8192_hw_sleep_down(): RF Change in progress!
[  620.074352] rtl8192_hw_sleep_down(): RF Change in progress!
[  672.076578] rtl8192_hw_wakeup(): RF Change in progress! schedule wake up task again
[  704.435701] ===>rtl8192se_link_change():ieee->iw_mode is 2
[  705.954081] ===>rtl8192se_link_change():ieee->iw_mode is 2
[  712.074981] rtl8192_hw_sleep_down(): RF Change in progress!
[  718.080055] rtl8192_hw_wakeup(): RF Change in progress! schedule wake up task again
[  760.077038] rtl8192_hw_wakeup(): RF Change in progress! schedule wake up task again
[  804.075577] rtl8192_hw_sleep_down(): RF Change in progress!
[  806.080041] rtl8192_hw_wakeup(): RF Change in progress! schedule wake up task again
[  824.435884] ===>rtl8192se_link_change():ieee->iw_mode is 2
[  825.954064] ===>rtl8192se_link_change():ieee->iw_mode is 2
[  868.080029] rtl8192_hw_sleep_down(): RF Change in progress!
[  898.083045] rtl8192_hw_sleep_down(): RF Change in progress!
[  944.434962] ===>rtl8192se_link_change():ieee->iw_mode is 2
[  945.954578] ===>rtl8192se_link_change():ieee->iw_mode is 2
[  998.085036] rtl8192_hw_wakeup(): RF Change in progress! schedule wake up task again
[ 1022.088668] rtl8192_hw_sleep_down(): RF Change in progress!
[ 1064.435093] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 1065.966051] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 1184.435142] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 1185.955582] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 1246.092038] rtl8192_hw_wakeup(): RF Change in progress! schedule wake up task again
[ 1304.431966] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 1305.950070] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 1308.090071] rtl8192_hw_sleep_down(): RF Change in progress!
[ 1338.093079] rtl8192_hw_wakeup(): RF Change in progress! schedule wake up task again
[ 1368.096116] rtl8192_hw_sleep_down(): RF Change in progress!
[ 1424.434836] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 1425.958608] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 1432.095719] rtl8192_hw_sleep_down(): RF Change in progress!
[ 1500.088878] rtl8192_hw_sleep_down(): RF Change in progress!
[ 1532.092595] rtl8192_hw_wakeup(): RF Change in progress! schedule wake up task again
[ 1544.435167] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 1545.954103] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 1624.094519] rtl8192_hw_sleep_down(): RF Change in progress!
[ 1626.096032] rtl8192_hw_wakeup(): RF Change in progress! schedule wake up task again
[ 1628.088103] rtl8192_hw_sleep_down(): RF Change in progress!
[ 1664.435607] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 1665.954071] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 1748.100699] rtl8192_hw_sleep_down(): RF Change in progress!
[ 1774.109590] rtl8192_hw_sleep_down(): RF Change in progress!
[ 1778.103168] rtl8192_hw_sleep_down(): RF Change in progress!
[ 1784.432775] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 1785.954053] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 1788.100035] rtl8192_hw_wakeup(): RF Change in progress! schedule wake up task again
[ 1844.104040] rtl8192_hw_wakeup(): RF Change in progress! schedule wake up task again
[ 1848.105040] rtl8192_hw_wakeup(): RF Change in progress! schedule wake up task again
[ 1878.108037] rtl8192_hw_wakeup(): RF Change in progress! schedule wake up task again
[ 1904.435085] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 1905.954056] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 1936.105340] rtl8192_hw_sleep_down(): RF Change in progress!
[ 1966.108371] rtl8192_hw_sleep_down(): RF Change in progress!
[ 2024.435485] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 2025.958890] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 2030.107988] rtl8192_hw_sleep_down(): RF Change in progress!
[ 2032.109041] rtl8192_hw_wakeup(): RF Change in progress! schedule wake up task again
[ 2040.105052] rtl8192_hw_wakeup(): RF Change in progress! schedule wake up task again
[ 2086.120423] rtl8192_hw_sleep_down(): RF Change in progress!
[ 2120.117027] rtl8192_hw_sleep_down(): RF Change in progress!
[ 2144.435777] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 2145.962565] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 2172.135981] rtl8192_hw_sleep_down(): RF Change in progress!
[ 2174.137038] rtl8192_hw_wakeup(): RF Change in progress! schedule wake up task again
[ 2236.135647] rtl8192_hw_sleep_down(): RF Change in progress!
[ 2264.435548] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 2265.954056] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 2300.135256] rtl8192_hw_sleep_down(): RF Change in progress!
[ 2384.435390] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 2385.954056] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 2428.134449] rtl8192_hw_sleep_down(): RF Change in progress!
[ 2488.140476] rtl8192_hw_sleep_down(): RF Change in progress!
[ 2504.434785] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 2505.954069] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 2514.149927] rtl8192_hw_sleep_down(): RF Change in progress!
[ 2520.148037] rtl8192_hw_wakeup(): RF Change in progress! schedule wake up task again
[ 2528.140563] rtl8192_hw_wakeup(): RF Change in progress! schedule wake up task again
[ 2578.149508] rtl8192_hw_sleep_down(): RF Change in progress!
[ 2588.144476] rtl8192_hw_wakeup(): RF Change in progress! schedule wake up task again
[ 2608.152543] rtl8192_hw_sleep_down(): RF Change in progress!
[ 2614.149031] rtl8192_hw_wakeup(): RF Change in progress! schedule wake up task again
[ 2624.430717] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 2625.954106] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 2744.434011] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 2745.954585] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 2830.154384] rtl8192_hw_sleep_down(): RF Change in progress!
[ 2832.157037] rtl8192_hw_wakeup(): RF Change in progress! schedule wake up task again
[ 2836.161032] rtl8192_hw_wakeup(): RF Change in progress! schedule wake up task again
[ 2864.434480] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 2865.954170] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 2948.180048] rtl8192_hw_wakeup(): RF Change in progress! schedule wake up task again
[ 2984.432155] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 2985.962096] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 3042.189581] rtl8192_hw_wakeup(): RF Change in progress! schedule wake up task again
[ 3104.431915] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 3105.970078] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 3122.198190] rtl8192_hw_sleep_down(): RF Change in progress!
[ 3148.207761] rtl8192_hw_sleep_down(): RF Change in progress!
[ 3152.201299] rtl8192_hw_sleep_down(): RF Change in progress!
[ 3154.205075] rtl8192_hw_wakeup(): RF Change in progress! schedule wake up task again
[ 3178.210824] rtl8192_hw_sleep_down(): RF Change in progress!
[ 3218.208513] rtl8192_hw_wakeup(): RF Change in progress! schedule wake up task again
[ 3224.431105] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 3225.955101] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 3278.212042] rtl8192_hw_wakeup(): RF Change in progress! schedule wake up task again
[ 3336.213563] rtl8192_hw_sleep_down(): RF Change in progress!
[ 3344.435629] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 3345.958054] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 3376.205030] rtl8192_hw_wakeup(): RF Change in progress! schedule wake up task again
[ 3430.216407] rtl8192_hw_sleep_down(): RF Change in progress!
[ 3444.209049] rtl8192_hw_wakeup(): RF Change in progress! schedule wake up task again
[ 3464.213072] rtl8192_hw_sleep_down(): RF Change in progress!
[ 3464.435485] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 3465.954080] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 3504.217037] rtl8192_hw_wakeup(): RF Change in progress! schedule wake up task again
[ 3528.212708] rtl8192_hw_sleep_down(): RF Change in progress!
[ 3534.217031] rtl8192_hw_wakeup(): RF Change in progress! schedule wake up task again
[ 3538.208034] rtl8192_hw_wakeup(): RF Change in progress! schedule wake up task again
[ 3568.208534] rtl8192_hw_wakeup(): RF Change in progress! schedule wake up task again
[ 3584.434661] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 3585.962059] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 3628.213034] rtl8192_hw_wakeup(): RF Change in progress! schedule wake up task again
[ 3688.221041] rtl8192_hw_wakeup(): RF Change in progress! schedule wake up task again
[ 3704.431340] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 3705.962083] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 3824.432047] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 3825.962641] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 3846.229058] rtl8192_hw_wakeup(): RF Change in progress! schedule wake up task again
[ 3872.229054] rtl8192_hw_wakeup(): RF Change in progress! schedule wake up task again
[ 3944.435606] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 3945.954061] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 4022.245038] rtl8192_hw_wakeup(): RF Change in progress! schedule wake up task again
[ 4064.435158] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 4065.954064] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 4112.260035] rtl8192_hw_wakeup(): RF Change in progress! schedule wake up task again
[ 4138.264037] rtl8192_hw_wakeup(): RF Change in progress! schedule wake up task again
[ 4172.268035] rtl8192_hw_wakeup(): RF Change in progress! schedule wake up task again
[ 4184.435283] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 4185.954262] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 4196.266770] rtl8192_hw_sleep_down(): RF Change in progress!
[ 4304.435432] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 4305.954093] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 4348.288035] rtl8192_hw_wakeup(): RF Change in progress! schedule wake up task again
[ 4378.289041] rtl8192_hw_wakeup(): RF Change in progress! schedule wake up task again
[ 4408.292041] rtl8192_hw_wakeup(): RF Change in progress! schedule wake up task again
[ 4424.435544] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 4425.954058] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 4466.293838] rtl8192_hw_sleep_down(): RF Change in progress!
[ 4476.293036] rtl8192_hw_wakeup(): RF Change in progress! schedule wake up task again
[ 4498.304046] rtl8192_hw_wakeup(): RF Change in progress! schedule wake up task again
[ 4544.434183] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 4545.954081] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 4548.315719] rtl8192_hw_sleep_down(): RF Change in progress!
[ 4638.324731] rtl8192_hw_sleep_down(): RF Change in progress!
[ 4664.430393] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 4665.950070] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 4668.327753] rtl8192_hw_sleep_down(): RF Change in progress!
[ 4698.330755] rtl8192_hw_sleep_down(): RF Change in progress!
[ 4784.429449] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 4785.950058] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 4802.325040] rtl8192_hw_wakeup(): RF Change in progress! schedule wake up task again
[ 4826.329937] rtl8192_hw_sleep_down(): RF Change in progress!
[ 4856.332948] rtl8192_hw_sleep_down(): RF Change in progress!
[ 4904.434728] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 4905.954084] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 4920.332543] rtl8192_hw_sleep_down(): RF Change in progress!
[ 4988.325698] rtl8192_hw_sleep_down(): RF Change in progress!
[ 5024.435190] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 5025.954050] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 5118.328043] rtl8192_hw_wakeup(): RF Change in progress! schedule wake up task again
[ 5144.429756] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 5145.950068] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 5180.324480] rtl8192_hw_sleep_down(): RF Change in progress!
[ 5182.328035] rtl8192_hw_wakeup(): RF Change in progress! schedule wake up task again
[ 5244.324085] rtl8192_hw_sleep_down(): RF Change in progress!
[ 5246.325028] rtl8192_hw_wakeup(): RF Change in progress! schedule wake up task again
[ 5264.434791] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 5265.954080] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 5274.327085] rtl8192_hw_sleep_down(): RF Change in progress!
[ 5276.328033] rtl8192_hw_wakeup(): RF Change in progress! schedule wake up task again
[ 5384.430533] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 5385.950065] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 5402.326287] rtl8192_hw_sleep_down(): RF Change in progress!
[ 5432.329292] rtl8192_hw_sleep_down(): RF Change in progress!
[ 5466.325879] rtl8192_hw_sleep_down(): RF Change in progress!
[ 5496.328890] rtl8192_hw_sleep_down(): RF Change in progress!
[ 5504.435653] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 5505.954064] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 5594.325019] rtl8192_hw_wakeup(): RF Change in progress! schedule wake up task again
[ 5624.435799] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 5625.954069] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 5744.434898] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 5745.954069] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 5752.327264] rtl8192_hw_sleep_down(): RF Change in progress!
[ 5766.925042] rtl8192_hw_wakeup(): RF Change in progress! schedule wake up task again
[ 5782.330271] rtl8192_hw_sleep_down(): RF Change in progress!
[ 5812.333297] rtl8192_hw_sleep_down(): RF Change in progress!
[ 5864.434993] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 5865.954078] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 5876.332883] rtl8192_hw_sleep_down(): RF Change in progress!
[ 5880.326457] rtl8192_hw_sleep_down(): RF Change in progress!
[ 5882.329030] rtl8192_hw_wakeup(): RF Change in progress! schedule wake up task again
[ 5984.435828] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 5985.954073] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 6104.435601] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 6105.954068] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 6168.332036] rtl8192_hw_wakeup(): RF Change in progress! schedule wake up task again
[ 6206.328033] rtl8192_hw_wakeup(): RF Change in progress! schedule wake up task again
[ 6224.435448] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 6225.954077] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 6344.435006] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 6345.954065] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 6358.326633] rtl8192_hw_wakeup(): RF Change in progress! schedule wake up task again
[ 6458.328041] rtl8192_hw_wakeup(): RF Change in progress! schedule wake up task again
[ 6464.429090] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 6465.950068] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 6518.332033] rtl8192_hw_wakeup(): RF Change in progress! schedule wake up task again
[ 6546.331879] rtl8192_hw_sleep_down(): RF Change in progress!
[ 6584.435628] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 6585.954059] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 6704.434502] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 6705.958053] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 6708.327653] rtl8192_hw_sleep_down(): RF Change in progress!
[ 6768.333659] rtl8192_hw_sleep_down(): RF Change in progress!
[ 6824.435222] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 6825.954089] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 6832.333268] rtl8192_hw_sleep_down(): RF Change in progress!
[ 6900.326443] rtl8192_hw_sleep_down(): RF Change in progress!
[ 6926.335867] rtl8192_hw_sleep_down(): RF Change in progress!
[ 6944.435580] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 6945.954068] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 6960.332454] rtl8192_hw_sleep_down(): RF Change in progress!
[ 7058.328622] rtl8192_hw_sleep_down(): RF Change in progress!
[ 7060.337028] rtl8192_hw_wakeup(): RF Change in progress! schedule wake up task again
[ 7064.434818] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 7065.954057] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 7088.331617] rtl8192_hw_sleep_down(): RF Change in progress!
[ 7118.334639] rtl8192_hw_sleep_down(): RF Change in progress!
[ 7122.328209] rtl8192_hw_sleep_down(): RF Change in progress!
[ 7124.329047] rtl8192_hw_wakeup(): RF Change in progress! schedule wake up task again
[ 7158.328045] rtl8192_hw_wakeup(): RF Change in progress! schedule wake up task again
[ 7184.435414] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 7185.954065] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 7304.434857] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 7305.954101] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 7340.336411] rtl8192_hw_sleep_down(): RF Change in progress!
[ 7350.333042] rtl8192_hw_wakeup(): RF Change in progress! schedule wake up task again
[ 7374.332993] rtl8192_hw_sleep_down(): RF Change in progress!
[ 7376.337037] rtl8192_hw_wakeup(): RF Change in progress! schedule wake up task again
[ 7406.336038] rtl8192_hw_wakeup(): RF Change in progress! schedule wake up task again
[ 7424.435987] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 7425.958073] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 7444.336034] rtl8192_hw_wakeup(): RF Change in progress! schedule wake up task again
[ 7502.332170] rtl8192_hw_sleep_down(): RF Change in progress!
[ 7544.430535] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 7545.950070] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 7626.337802] rtl8192_hw_sleep_down(): RF Change in progress!
[ 7658.344029] rtl8192_hw_wakeup(): RF Change in progress! schedule wake up task again
[ 7664.435183] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 7665.954073] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 7780.346361] rtl8192_hw_sleep_down(): RF Change in progress!
[ 7782.348041] rtl8192_hw_wakeup(): RF Change in progress! schedule wake up task again
[ 7784.434490] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 7785.954110] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 7816.352039] rtl8192_hw_wakeup(): RF Change in progress! schedule wake up task again
[ 7870.355371] rtl8192_hw_sleep_down(): RF Change in progress!
[ 7904.431018] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 7905.966626] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 7998.355756] rtl8192_hw_sleep_down(): RF Change in progress!
[ 8024.436012] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 8025.954064] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 8102.349041] rtl8192_hw_wakeup(): RF Change in progress! schedule wake up task again
[ 8144.434979] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 8145.954056] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 8158.360039] rtl8192_hw_wakeup(): RF Change in progress! schedule wake up task again
[ 8190.353318] rtl8192_hw_sleep_down(): RF Change in progress!
[ 8222.361039] rtl8192_hw_wakeup(): RF Change in progress! schedule wake up task again
[ 8264.430936] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 8265.950063] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 8340.368356] rtl8192_hw_sleep_down(): RF Change in progress!
[ 8384.435434] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 8385.958076] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 8464.373959] rtl8192_hw_sleep_down(): RF Change in progress!
[ 8466.377047] rtl8192_hw_wakeup(): RF Change in progress! schedule wake up task again
[ 8504.435931] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 8505.966049] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 8558.376593] rtl8192_hw_sleep_down(): RF Change in progress!
[ 8622.376200] rtl8192_hw_sleep_down(): RF Change in progress!
[ 8624.429189] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 8625.954051] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 8636.368736] rtl8192_hw_wakeup(): RF Change in progress! schedule wake up task again
[ 8658.376036] rtl8192_hw_wakeup(): RF Change in progress! schedule wake up task again
[ 8690.369391] rtl8192_hw_sleep_down(): RF Change in progress!
[ 8692.372041] rtl8192_hw_wakeup(): RF Change in progress! schedule wake up task again
[ 8696.372037] rtl8192_hw_wakeup(): RF Change in progress! schedule wake up task again
[ 8720.372415] rtl8192_hw_sleep_down(): RF Change in progress!
[ 8722.373114] rtl8192_hw_wakeup(): RF Change in progress! schedule wake up task again
[ 8744.435575] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 8745.954079] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 8810.381611] rtl8192_hw_sleep_down(): RF Change in progress!
[ 8864.434903] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 8865.955567] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 8908.378120] rtl8192_hw_sleep_down(): RF Change in progress!
[ 8972.377939] rtl8192_hw_sleep_down(): RF Change in progress!
[ 8984.434844] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 8985.970051] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 9032.384143] rtl8192_hw_sleep_down(): RF Change in progress!
[ 9034.389556] rtl8192_hw_wakeup(): RF Change in progress! schedule wake up task again
[ 9068.384535] rtl8192_hw_wakeup(): RF Change in progress! schedule wake up task again
[ 9104.433755] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 9105.958061] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 9194.380485] rtl8192_hw_sleep_down(): RF Change in progress!
[ 9196.381057] rtl8192_hw_wakeup(): RF Change in progress! schedule wake up task again
[ 9220.390007] rtl8192_hw_sleep_down(): RF Change in progress!
[ 9224.435381] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 9225.954068] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 9258.380285] rtl8192_hw_sleep_down(): RF Change in progress!
[ 9260.385556] rtl8192_hw_wakeup(): RF Change in progress! schedule wake up task again
[ 9284.389819] rtl8192_hw_sleep_down(): RF Change in progress!
[ 9344.435423] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 9345.954043] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 9464.431781] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 9465.974062] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 9584.434155] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 9585.959083] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 9588.414481] rtl8192_hw_sleep_down(): RF Change in progress!
[ 9648.420718] rtl8192_hw_sleep_down(): RF Change in progress!
[ 9704.435390] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 9705.958114] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 9824.429083] rtl8192_hw_wakeup(): RF Change in progress! schedule wake up task again
[ 9824.429185] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 9825.950076] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 9896.432709] rtl8192_hw_wakeup(): RF Change in progress! schedule wake up task again
[ 9928.436048] rtl8192_hw_wakeup(): RF Change in progress! schedule wake up task again
[ 9944.431844] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 9945.966093] ===>rtl8192se_link_change():ieee->iw_mode is 2
[10020.438739] rtl8192_hw_sleep_down(): RF Change in progress!
[10064.434266] rtl8192_hw_wakeup(): RF Change in progress! schedule wake up task again
[10064.434370] ===>rtl8192se_link_change():ieee->iw_mode is 2
[10065.955582] ===>rtl8192se_link_change():ieee->iw_mode is 2
[10088.432116] rtl8192_hw_sleep_down(): RF Change in progress!
[10184.435833] ===>rtl8192se_link_change():ieee->iw_mode is 2
[10185.954087] ===>rtl8192se_link_change():ieee->iw_mode is 2
[10208.444517] rtl8192_hw_sleep_down(): RF Change in progress!
[10210.445545] rtl8192_hw_wakeup(): RF Change in progress! schedule wake up task again
[10298.453804] rtl8192_hw_wakeup(): RF Change in progress! schedule wake up task again
[10304.434388] ===>rtl8192se_link_change():ieee->iw_mode is 2
[10305.954515] ===>rtl8192se_link_change():ieee->iw_mode is 2
[10392.456721] rtl8192_hw_sleep_down(): RF Change in progress!
[10398.452546] rtl8192_hw_wakeup(): RF Change in progress! schedule wake up task again
[10424.428751] ===>rtl8192se_link_change():ieee->iw_mode is 2
[10425.970556] ===>rtl8192se_link_change():ieee->iw_mode is 2
[10544.434740] ===>rtl8192se_link_change():ieee->iw_mode is 2
[10545.955065] ===>rtl8192se_link_change():ieee->iw_mode is 2
[10552.460579] rtl8192_hw_wakeup(): RF Change in progress! schedule wake up task again
[10582.465053] rtl8192_hw_wakeup(): RF Change in progress! schedule wake up task again
[10620.461046] rtl8192_hw_wakeup(): RF Change in progress! schedule wake up task again
[10664.434645] ===>rtl8192se_link_change():ieee->iw_mode is 2
[10665.954395] ===>rtl8192se_link_change():ieee->iw_mode is 2
[10672.473563] rtl8192_hw_wakeup(): RF Change in progress! schedule wake up task again
[10726.484444] rtl8192_hw_sleep_down(): RF Change in progress!
[10782.497061] rtl8192_hw_sleep_down(): RF Change in progress!
[10784.434133] ===>rtl8192se_link_change():ieee->iw_mode is 2
[10785.970121] ===>rtl8192se_link_change():ieee->iw_mode is 2
[10818.497047] rtl8192_hw_wakeup(): RF Change in progress! schedule wake up task again
[10872.506371] rtl8192_hw_sleep_down(): RF Change in progress!
[10874.508266] rtl8192_hw_wakeup(): RF Change in progress! schedule wake up task again
[10904.434793] ===>rtl8192se_link_change():ieee->iw_mode is 2
[10905.978056] ===>rtl8192se_link_change():ieee->iw_mode is 2
[10958.522057] rtl8192_hw_sleep_down(): RF Change in progress!
[10960.524038] rtl8192_hw_wakeup(): RF Change in progress! schedule wake up task again
[11022.522143] rtl8192_hw_sleep_down(): RF Change in progress!
[11024.433048] ===>rtl8192se_link_change():ieee->iw_mode is 2
[11025.958111] ===>rtl8192se_link_change():ieee->iw_mode is 2
[11108.537527] rtl8192_hw_sleep_down(): RF Change in progress!
[11144.433661] ===>rtl8192se_link_change():ieee->iw_mode is 2
[11145.962066] ===>rtl8192se_link_change():ieee->iw_mode is 2
[11258.553051] rtl8192_hw_sleep_down(): RF Change in progress!
[11264.435134] ===>rtl8192se_link_change():ieee->iw_mode is 2
[11265.955628] ===>rtl8192se_link_change():ieee->iw_mode is 2
[11324.560426] rtl8192_hw_wakeup(): RF Change in progress! schedule wake up task again
[11378.565475] rtl8192_hw_sleep_down(): RF Change in progress!
[11380.569061] rtl8192_hw_wakeup(): RF Change in progress! schedule wake up task again
[11384.435919] ===>rtl8192se_link_change():ieee->iw_mode is 2
[11385.966057] ===>rtl8192se_link_change():ieee->iw_mode is 2
[11388.561074] rtl8192_hw_wakeup(): RF Change in progress! schedule wake up task again
[11500.581040] rtl8192_hw_wakeup(): RF Change in progress! schedule wake up task again
[11504.434807] ===>rtl8192se_link_change():ieee->iw_mode is 2
[11505.955629] ===>rtl8192se_link_change():ieee->iw_mode is 2
[11520.593819] rtl8192_hw_sleep_down(): RF Change in progress!
[11524.587384] rtl8192_hw_wakeup(): RF Change in progress! schedule wake up task again
[11530.585058] rtl8192_hw_wakeup(): RF Change in progress! schedule wake up task again
[11590.592038] rtl8192_hw_wakeup(): RF Change in progress! schedule wake up task again
[11620.592548] rtl8192_hw_wakeup(): RF Change in progress! schedule wake up task again
[11624.434913] ===>rtl8192se_link_change():ieee->iw_mode is 2
[11625.962073] ===>rtl8192se_link_change():ieee->iw_mode is 2
[11648.593573] rtl8192_hw_sleep_down(): RF Change in progress!
[11658.588545] rtl8192_hw_wakeup(): RF Change in progress! schedule wake up task again
[11678.596525] rtl8192_hw_sleep_down(): RF Change in progress!
[11744.434966] ===>rtl8192se_link_change():ieee->iw_mode is 2
[11745.962138] ===>rtl8192se_link_change():ieee->iw_mode is 2
[11776.592999] rtl8192_hw_wakeup(): RF Change in progress! schedule wake up task again
[11802.602566] rtl8192_hw_sleep_down(): RF Change in progress!
[11806.600452] rtl8192_hw_wakeup(): RF Change in progress! schedule wake up task again
[11806.601469] rtl8192_hw_wakeup(): RF Change in progress! schedule wake up task again
[11840.592821] rtl8192_hw_sleep_down(): RF Change in progress!
[11864.431968] ===>rtl8192se_link_change():ieee->iw_mode is 2
[11865.951093] ===>rtl8192se_link_change():ieee->iw_mode is 2
[11896.605427] rtl8192_hw_wakeup(): RF Change in progress! schedule wake up task again
[11930.602126] rtl8192_hw_sleep_down(): RF Change in progress!
[11960.605252] rtl8192_hw_sleep_down(): RF Change in progress!
[11984.434656] ===>rtl8192se_link_change():ieee->iw_mode is 2
[11985.955573] ===>rtl8192se_link_change():ieee->iw_mode is 2
[11990.608335] rtl8192_hw_sleep_down(): RF Change in progress!
[12090.613568] rtl8192_hw_wakeup(): RF Change in progress! schedule wake up task again
[12104.435097] ===>rtl8192se_link_change():ieee->iw_mode is 2
[12105.962603] ===>rtl8192se_link_change():ieee->iw_mode is 2
[12196.636455] rtl8192_hw_wakeup(): RF Change in progress! schedule wake up task again
[12224.434996] ===>rtl8192se_link_change():ieee->iw_mode is 2
[12225.954340] ===>rtl8192se_link_change():ieee->iw_mode is 2
[12256.642651] rtl8192_hw_wakeup(): RF Change in progress! schedule wake up task again
[12286.645781] rtl8192_hw_wakeup(): RF Change in progress! schedule wake up task again
[12344.431480] ===>rtl8192se_link_change():ieee->iw_mode is 2
[12345.950291] ===>rtl8192se_link_change():ieee->iw_mode is 2
[12384.642270] rtl8192_hw_sleep_down(): RF Change in progress!
[12448.642019] rtl8192_hw_sleep_down(): RF Change in progress!
[12464.435235] ===>rtl8192se_link_change():ieee->iw_mode is 2
[12465.955646] ===>rtl8192se_link_change():ieee->iw_mode is 2
[12478.645149] rtl8192_hw_sleep_down(): RF Change in progress!
[12480.649047] rtl8192_hw_wakeup(): RF Change in progress! schedule wake up task again
[12512.641838] rtl8192_hw_sleep_down(): RF Change in progress!
[12576.641581] rtl8192_hw_wakeup(): RF Change in progress! schedule wake up task again
[12584.435485] ===>rtl8192se_link_change():ieee->iw_mode is 2
[12585.955055] ===>rtl8192se_link_change():ieee->iw_mode is 2
[12612.645053] rtl8192_hw_wakeup(): RF Change in progress! schedule wake up task again
[12628.660638] rtl8192_hw_sleep_down(): RF Change in progress!
[12634.661056] rtl8192_hw_wakeup(): RF Change in progress! schedule wake up task again
[12704.434539] ===>rtl8192se_link_change():ieee->iw_mode is 2
[12705.959925] ===>rtl8192se_link_change():ieee->iw_mode is 2
[12726.657084] rtl8192_hw_wakeup(): RF Change in progress! schedule wake up task again
[12774.682550] rtl8192_hw_sleep_down(): RF Change in progress!
[12824.431402] ===>rtl8192se_link_change():ieee->iw_mode is 2
[12825.950060] ===>rtl8192se_link_change():ieee->iw_mode is 2
[12838.682383] rtl8192_hw_sleep_down(): RF Change in progress!
[12840.684088] rtl8192_hw_wakeup(): RF Change in progress! schedule wake up task again
[12944.431011] ===>rtl8192se_link_change():ieee->iw_mode is 2
[12945.986064] ===>rtl8192se_link_change():ieee->iw_mode is 2
[12956.705041] rtl8192_hw_wakeup(): RF Change in progress! schedule wake up task again
[13010.713777] rtl8192_hw_sleep_down(): RF Change in progress!
[13012.721058] rtl8192_hw_wakeup(): RF Change in progress! schedule wake up task again
[13064.430743] ===>rtl8192se_link_change():ieee->iw_mode is 2
[13065.974065] ===>rtl8192se_link_change():ieee->iw_mode is 2
[13106.720035] rtl8192_hw_wakeup(): RF Change in progress! schedule wake up task again
[13130.726129] rtl8192_hw_sleep_down(): RF Change in progress!
[13162.732551] rtl8192_hw_wakeup(): RF Change in progress! schedule wake up task again
[13184.434711] ===>rtl8192se_link_change():ieee->iw_mode is 2
[13185.962594] ===>rtl8192se_link_change():ieee->iw_mode is 2
[13228.722586] rtl8192_hw_sleep_down(): RF Change in progress!
[13264.720042] rtl8192_hw_wakeup(): RF Change in progress! schedule wake up task again
[13288.728750] rtl8192_hw_wakeup(): RF Change in progress! schedule wake up task again
[13294.724049] rtl8192_hw_wakeup(): RF Change in progress! schedule wake up task again
[13304.434729] ===>rtl8192se_link_change():ieee->iw_mode is 2
[13305.963098] ===>rtl8192se_link_change():ieee->iw_mode is 2
[13348.734933] rtl8192_hw_wakeup(): RF Change in progress! schedule wake up task again
[13352.728559] rtl8192_hw_sleep_down(): RF Change in progress!
[13408.741117] rtl8192_hw_wakeup(): RF Change in progress! schedule wake up task again
[13424.431164] ===>rtl8192se_link_change():ieee->iw_mode is 2
[13425.951055] ===>rtl8192se_link_change():ieee->iw_mode is 2
[13466.761536] rtl8192_hw_wakeup(): RF Change in progress! schedule wake up task again
[13544.435199] ===>rtl8192se_link_change():ieee->iw_mode is 2
[13545.966103] ===>rtl8192se_link_change():ieee->iw_mode is 2
[13560.765029] rtl8192_hw_wakeup(): RF Change in progress! schedule wake up task again
[13582.773038] rtl8192_hw_wakeup(): RF Change in progress! schedule wake up task again
[13664.434974] ===>rtl8192se_link_change():ieee->iw_mode is 2
[13665.958102] ===>rtl8192se_link_change():ieee->iw_mode is 2
[13784.433226] ===>rtl8192se_link_change():ieee->iw_mode is 2
[13785.954088] ===>rtl8192se_link_change():ieee->iw_mode is 2
[13904.434851] ===>rtl8192se_link_change():ieee->iw_mode is 2
[13905.962068] ===>rtl8192se_link_change():ieee->iw_mode is 2
[13926.781025] rtl8192_hw_sleep_down(): RF Change in progress!
[13928.780421] rtl8192_hw_wakeup(): RF Change in progress! schedule wake up task again
[13956.784101] rtl8192_hw_sleep_down(): RF Change in progress!
[13958.785041] rtl8192_hw_wakeup(): RF Change in progress! schedule wake up task again
[13986.787183] rtl8192_hw_sleep_down(): RF Change in progress!
[14024.431922] ===>rtl8192se_link_change():ieee->iw_mode is 2
[14025.966063] ===>rtl8192se_link_change():ieee->iw_mode is 2
[14046.793289] rtl8192_hw_sleep_down(): RF Change in progress!
[14048.796033] rtl8192_hw_wakeup(): RF Change in progress! schedule wake up task again
[14056.792043] rtl8192_hw_wakeup(): RF Change in progress! schedule wake up task again
[14076.796398] rtl8192_hw_sleep_down(): RF Change in progress!
[14078.796036] rtl8192_hw_wakeup(): RF Change in progress! schedule wake up task again
[14086.796040] rtl8192_hw_wakeup(): RF Change in progress! schedule wake up task again

```

Any idea how to solve this? I have stable connection with my router but I can't surf the internet. :confused:

---

### Post by ales85 on 2010-04-30
chili555 I could kiss you :) I knew that I had to copy the firmware that was included in realtek driver somewhere but had no idea which was the directory. That did the trick. However, I still get the red exclamation mark... Any idea why? I have to research what could it mean and where are explanations...

I just hope that the connection will be stable.

BR Aleš

---

### Post by meles on 2010-04-30
I do have the RTL8192SE folder in lib/firmware, as well as the rtl8192sfw.bin file in the folder, but the wireless card is stil not working (dropping connections, etc.)

I wish there was a way to install the Realtek restricted driver on Lucid as well. It worked perfectly on Karmic. But I can't install it on Lucid anymore, no matter what (an upgrade from Karmic to Lucid will just delete it and replace it with the useless Ubuntu driver)

---

### Post by jdcf on 2010-05-03
Hi people, I'm new in the forum.
I'm writing because I was having that problem that cause the RTL8192SE WiFi card to fail after one or  two minutes in my Toshiba Satellite L500 with Ubuntu 10.04 64 bits and I have just solved it  (don't know if the solution works in any other platform). I'll try to explain every step I took to get there:

[LIST=1]
[*]Install build-essential, and surely you need linux-headers-`uname -r` too.
[*]Download the driver from the [Realtek site]("http://www.realtek.com"). I got it [here]("http://www.realtek.com/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true").
[*]Uncompress it, and, with the shell in the new dir, type:
```
sudo su
make
make install
reboot # I'm not sure it's necessary now, but I did it... 
```
[*]At this point, while trying to do something to make it work, I decided to add some parameters to the module to see if it had some effect. I think it's not necessary actually, but I left it unchanged and it works. As root, I created a /etc/modprobe.d/r8192se_pci.conf file with the next content (notice the RTL8191SE is my wlan0 interface, and yes, the module name is r8192se_pci, there is no misspelling):
```
alias wlan0 r8192se_pci
r8192se_pci option ifname=wlan0 hwwep=1
```
[*]Here comes the trick. The real problem is that the r8192se_pci module the system loads on boot is not the new one we have just compiled, but another one within Ubuntu. To solve this, do:
```
sudo su
cd /lib/modules/2.6.32-21-generic/kernel/ubuntu/rtl8192se/
mv r8192se_pci.ko r8192se_pci.ko.bak
ln -s ../../drivers/net/wireless/r8192se_pci.ko
```
[*]Reboot.
[/LIST]
And that's all, I think. I hope this will be useful to somebody. Please tell me if there is any problem.

---

### Post by zorro123 on 2010-05-04
I have the rtl8191se hardware and after upgrading the kernel to 2.6.32-22-generic my wireless lan started working without problems.
See [http://ubuntuforums.org/showthread.php?t=1464448&highlight=rtl8191se+lucid&page=2](http://ubuntuforums.org/showthread.php?t=1464448&highlight=rtl8191se+lucid&page=2)

HTH,

Regards Theo

---

### Post by Alex71854 on 2010-05-04
I have a Samsung N140 netbook and have also rtl8192se issues. I finally got wireless to work using ndiswrapper and the xp wireless driver from the Samsung website. I initially upgraded to 2.6.32-22.33. An update to 2.6.32-21 came through today, and I decided to revert back to 2.6.32-21. Everything still works fine. This may not be as desirable as the native driver, but until I have connectivity problems, I don't plan to change anything.

---

### Post by randuyoung on 2010-05-05
Thanks jdcf for this information. I followed it to the letter and my wireless connection is still not functioning. 

the output of iwconfig is:

wlan0     802.11bgn  Nickname:"rtl8191SEVA1"
          Mode:Managed  Frequency=2.417 GHz  Access Point: Not-Associated   
          Bit Rate:135 Mb/s   
          Retry:on   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=10/100  Signal level=0 dBm  Noise level=-100 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

The output of lssh -C network  is:

  *-network               
       description: Ethernet interface
       product: JMC260 PCI Express Fast Ethernet Controller
       vendor: JMicron Technology Corp.
       physical id: 0.5
       bus info: pci@0000:01:00.5
       logical name: eth0
       version: 02
       serial: 00:30:1b:be:e2:d9
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm pciexpress msix msi bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=jme driverversion=1.0.5 duplex=full ip=192.168.1.38 latency=0 link=yes multicast=yes port=MII speed=100MB/s
       resources: irq:27 memory:feaf8000-feafbfff ioport:dc00(size=128) ioport:d800(size=256)
  *-generic
       description: Wireless interface
       product: Illegal Vendor ID
       vendor: Illegal Vendor ID
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: ff
       serial: 70:1a:04:bc:63:43
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master vga_palette cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl819xSE driverversion=0015.0127.2010 firmware=62 latency=255 link=no maxlatency=255 mingnt=255 multicast=yes wireless=802.11bgn
       resources: irq:17 ioport:e800(size=256) memory:febfc000-febfffff

and the output of ifconfig is:

eth0      Link encap:Ethernet  HWaddr 00:30:1b:be:e2:d9  
          inet addr:192.168.1.38  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::230:1bff:febe:e2d9/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:842 errors:0 dropped:0 overruns:0 frame:0
          TX packets:729 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:963629 (963.6 KB)  TX bytes:118889 (118.8 KB)
          Interrupt:27 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:480 (480.0 B)  TX bytes:480 (480.0 B)

wlan0     Link encap:Ethernet  HWaddr 70:1a:04:bc:63:43  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 Memory:f8400000-f8400100

Any clues as to what I should do next to get the wireless connection to work?

Thanks

---

### Post by chili555 on 2010-05-05
> Any clues as to what I should do next to get the wireless connection to work?First, Network Manager is designed to NOT allow a wireless connection if wired is active; yours is:> eth0 Link encap:Ethernet HWaddr 00:30:1b:be:e2:d9
inet addr:192.168.1.38 Please detach the wire. Next, please do:```
sudo gedit /etc/NetworkManager/nm-system-settings.conf 
```If managed = false, please change it to true. Reboot.

Now is it working?

---

### Post by randuyoung on 2010-05-05
Still not working. Managed was set to false and it is now true. when I click on the wireless icon (which has a red exclamation point in it) I do not see a list of available routers that I can connect to. With the ethernet cable removed, here is the new output:

mlds@mlds-desktop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: JMC260 PCI Express Fast Ethernet Controller
       vendor: JMicron Technology Corp.
       physical id: 0.5
       bus info: pci@0000:01:00.5
       logical name: eth0
       version: 02
       serial: 00:30:1b:be:e2:d9
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=jme driverversion=1.0.5 latency=0 multicast=yes
       resources: irq:27 memory:feaf8000-feafbfff ioport:dc00(size=128) ioport:d800(size=256)
  *-generic
       description: Wireless interface
       product: Illegal Vendor ID
       vendor: Illegal Vendor ID
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: ff
       serial: 70:1a:04:bc:63:43
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master vga_palette cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl819xSE driverversion=0015.0127.2010 firmware=62 latency=255 maxlatency=255 mingnt=255 multicast=yes wireless=802.11bgn
       resources: irq:17 ioport:e800(size=256) memory:febfc000-febfffff
mlds@mlds-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     802.11bgn  Nickname:"rtl8191SEVA1"
          Mode:Managed  Frequency=2.417 GHz  Access Point: Not-Associated   
          Bit Rate:135 Mb/s   
          Retry:on   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=10/100  Signal level=0 dBm  Noise level=-100 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

mlds@mlds-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:30:1b:be:e2:d9  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:27 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:480 (480.0 B)  TX bytes:480 (480.0 B)

wlan0     Link encap:Ethernet  HWaddr 70:1a:04:bc:63:43  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 Memory:f83d0000-f83d0100

---

### Post by AllTiger on 2010-05-05
Am also having problems with trl8191se i followed many of the post advices but I have two problems, first they mentioned to use ./configure and there is no configure file in the drivers i downloaded from the links people have posted.
the other issue is that people mention a manual installation and there is a part about to copy a r8191se_pci.ko file. there is no any .ko file if somebody can help me with this i would appreciate, thanks.

---

### Post by chili555 on 2010-05-05
@randuyoung --

May we please see:```
dmesg | grep -e wlan -e 819
```Thanks.

---

### Post by chili555 on 2010-05-05
> **AllTiger said:**
> Am also having problems with trl8191se i followed many of the post advices but I have two problems, first they mentioned to use ./configure and there is no configure file in the drivers i downloaded from the links people have posted.
the other issue is that people mention a manual installation and there is a part about to copy a r8191se_pci.ko file. there is no any .ko file if somebody can help me with this i would appreciate, thanks.Please give me a link to the file you downloaded so I can download it and help you.

---

### Post by AllTiger on 2010-05-05
Chili555 here is the link
i tried from 2 sources

[http://launchpadlibrarian.net/34090326/rtl8192se_linux_2.6.0010.1012.2009_64bit.tar.gz](http://launchpadlibrarian.net/34090326/rtl8192se_linux_2.6.0010.1012.2009_64bit.tar.gz)

[ftp://WebUser:2mG8dBW@202.134.71.21/cn/wlan/rtl8192se_linux_2.6.0015.0127.2010.tar.gz](ftp://WebUser:2mG8dBW@202.134.71.21/cn/wlan/rtl8192se_linux_2.6.0015.0127.2010.tar.gz)

second link i think a log is need with with the first both happened the same thing one is 64 bit as my pc is and the second is supposed to be newer

I use make comand and i get the following 

make[1]: Entering directory `/lib/modules/2.6.31.12-0.2-desktop/build'
make[1]: *** No rule to make target `modules'.  Stop.
make[1]: Leaving directory `/lib/modules/2.6.31.12-0.2-desktop/build'
make: *** [all] Error 2

And i dont have a .ko file that is supposed to be needed

thanks for your help

---

### Post by chili555 on 2010-05-05
Have you updated to Lucid, version 10.04 yet? The module is already built in.

Do you have linux-headers and build-essential installed? These are required to compile these things.

If your system is 64-bit, you will definitely need the 64-bit package.

Finally, you will not find a .ko file until you *successfully* complete make and make install with no nada zero errors. Also, if you use Method 1 from the readme.txt, which I recommend, there is no need to copy over the .ko file. Do not do some of method 1 and some of method 2; it will lead to unexpected results.

---

### Post by qwerty123321 on 2010-05-05
Hi, I recently installed ubuntu 10.04 and wireless does work right out  of the box however it doesn't show all the available networks..it  appears that only some shows up :/ and some others dont..including my  own home network and my neighbours unsecure network lol..
Ive tried installing the driver that made wireless work in 9.10 but it  does not appear to fix the problem :/
heres my iwconfig 
```

howard@user681:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     802.11bgn  Nickname:"rtl8191SEVA2"
          Mode:Managed  Frequency=2.457 GHz  Access Point:  Not-Associated   
          Bit Rate:300 Mb/s   
          Retry:on   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=10/100  Signal level=0 dBm  Noise level=-100 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

howard@user681:~$ 

```

---

### Post by AllTiger on 2010-05-06
Thanks for the .ko hint i will forget that point, I think is probably a devel_c_c++ issue am not sure, linux-header and build-essential am supposed to have since I read that kernel-source is the equivalent so if i have that package i will have linux header and the essential, am using kubuntu 10.04 but am trying to do the same thing with open SuSe i think it doesnt change actually so i can do the same things.

---

### Post by randuyoung on 2010-05-06
Thanks for your help chili555, I really appreciate it....

Here is the output you requested:

[57934.186297] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
[57934.220298] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[57934.220308] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[57934.333954] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[57934.333964] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[57934.445954] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[57934.445963] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[57934.557949] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[57934.557958] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[57934.669951] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[57934.669961] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[57934.781950] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[57934.781959] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[57934.893973] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[57934.893982] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[57935.005954] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[57935.005964] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[57935.117955] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[57935.117965] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[57935.229948] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[57935.229957] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[57935.341952] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[57935.341961] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[57994.186309] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
[57994.220291] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[57994.220301] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[57994.333954] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[57994.333963] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[57994.445956] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[57994.445965] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[57994.557949] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[57994.557959] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[57994.669953] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[57994.669962] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[57994.781948] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[57994.781958] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[57994.893973] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[57994.893982] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[57995.005954] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[57995.005964] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[57995.117954] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[57995.117964] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[57995.229949] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[57995.229958] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[57995.341950] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[57995.341959] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58054.186107] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
[58054.220091] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58054.220101] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58054.333950] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58054.333960] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58054.445953] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58054.445962] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58054.557948] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58054.557957] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58054.669951] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58054.669960] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58054.781948] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58054.781957] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58054.893959] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58054.893968] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58055.005951] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58055.005960] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58055.117954] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58055.117963] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58055.229951] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58055.229961] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58055.341950] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58055.341960] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58114.186246] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
[58114.220224] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58114.220234] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58114.333950] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58114.333959] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58114.445955] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58114.445964] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58114.557949] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58114.557959] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58114.669951] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58114.669960] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58114.781947] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58114.781956] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58114.893959] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58114.893969] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58115.005955] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58115.005964] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58115.117954] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58115.117964] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58115.229952] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58115.229961] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58115.341948] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58115.341958] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58174.186268] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
[58174.220260] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58174.220271] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58174.333950] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58174.333960] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58174.445953] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58174.445962] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58174.557949] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58174.557958] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58174.669951] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58174.669960] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58174.781948] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58174.781957] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58174.893974] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58174.893984] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58175.005954] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58175.005963] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58175.117954] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58175.117963] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58175.229955] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58175.229964] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58175.341950] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58175.341959] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58191.686679] pwrdown, 0x6(BIT6)=ff
[58193.686682] pwrdown, 0x6(BIT6)=ff
[58195.686683] pwrdown, 0x6(BIT6)=ff
[58197.686680] pwrdown, 0x6(BIT6)=ff
[58199.686681] pwrdown, 0x6(BIT6)=ff
[58234.186055] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
[58234.220040] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58234.220050] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58234.333950] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58234.333959] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58234.445953] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58234.445962] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58234.557947] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58234.557957] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58234.669949] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58234.669958] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58234.781952] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58234.781961] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58234.893973] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58234.893982] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58235.005957] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58235.005967] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58235.117953] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58235.117963] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58235.229951] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58235.229960] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58235.341949] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58235.341958] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58294.186257] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
[58294.220239] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58294.220250] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58294.333950] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58294.333960] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58294.445953] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58294.445963] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58294.557949] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58294.557958] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58294.669953] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58294.669962] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58294.781951] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58294.781960] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58294.893960] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58294.893970] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58295.005953] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58295.005963] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58295.117952] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58295.117962] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58295.229951] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58295.229960] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58295.341949] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58295.341959] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58354.186263] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
[58354.220244] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58354.220254] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58354.333951] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58354.333960] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58354.445953] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58354.445962] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58354.557949] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58354.557958] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58354.669949] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58354.669958] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58354.781950] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58354.781959] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58354.893958] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58354.893968] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58355.005953] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58355.005962] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58355.117953] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58355.117962] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58355.229952] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58355.229961] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58355.341947] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58355.341956] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58414.186264] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
[58414.220245] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58414.220256] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58414.333953] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58414.333962] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58414.445953] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58414.445962] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58414.557949] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58414.557958] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58414.669949] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58414.669958] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58414.781950] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58414.781959] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58414.893973] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58414.893983] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58415.005955] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58415.005964] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58415.117953] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58415.117962] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58415.229952] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58415.229961] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58415.341948] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58415.341958] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58474.186283] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
[58474.220276] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58474.220286] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58474.333953] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58474.333963] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58474.445951] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58474.445960] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58474.557948] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58474.557957] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58474.669948] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58474.669957] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58474.781950] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58474.781959] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58474.893958] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58474.893969] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58475.005954] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58475.005963] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58475.117950] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58475.117960] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58475.229953] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58475.229962] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58475.341953] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58475.341962] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58534.186278] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
[58534.220259] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58534.220269] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58534.333953] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58534.333962] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58534.445951] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58534.445960] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58534.557949] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58534.557957] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58534.669948] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58534.669957] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58534.781953] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58534.781962] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58534.893958] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58534.893969] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58535.005957] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58535.005966] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58535.117955] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58535.117965] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58535.229952] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58535.229961] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58535.341951] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58535.341960] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58594.186284] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
[58594.220277] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58594.220287] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58594.333954] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58594.333964] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58594.445952] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58594.445961] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58594.557950] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58594.557959] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58594.669950] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58594.669959] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58594.781951] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58594.781960] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58594.893957] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58594.893967] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58595.005955] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58595.005964] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58595.117955] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58595.117964] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58595.229950] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58595.229959] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58595.341951] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58595.341960] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58654.186288] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
[58654.220276] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58654.220286] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58654.333953] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58654.333962] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58654.445953] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58654.445962] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58654.557949] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58654.557958] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58654.669947] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58654.669956] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58654.781951] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58654.781960] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58654.893959] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58654.893968] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58655.005954] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58655.005964] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58655.117957] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58655.117967] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58655.229949] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58655.229959] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58655.341951] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58655.341960] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58714.186261] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
[58714.220242] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58714.220252] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58714.333953] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58714.333962] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58714.445950] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58714.445959] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58714.557949] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58714.557958] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58714.669951] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58714.669960] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58714.781951] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58714.781959] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58714.893960] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58714.893970] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58715.005952] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58715.005962] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58715.117955] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58715.117964] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58715.229949] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58715.229959] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58715.341951] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58715.341960] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58774.186285] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
[58774.220276] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58774.220286] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58774.333954] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58774.333963] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58774.445949] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58774.445959] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58774.557951] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58774.557960] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58774.669952] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58774.669961] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58774.781950] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58774.781959] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58774.893974] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58774.893984] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58775.005952] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58775.005961] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58775.117956] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58775.117966] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58775.229949] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58775.229959] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58775.341952] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58775.341961] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58819.686680] pwrdown, 0x6(BIT6)=ff
[58834.186297] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
[58834.220294] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58834.220304] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58834.333954] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58834.333963] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58834.445949] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58834.445958] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58834.557950] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58834.557959] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58834.669953] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58834.669962] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58834.781949] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58834.781958] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58834.893975] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58834.893984] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58835.005952] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58835.005961] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58835.117954] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58835.117964] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58835.229951] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58835.229961] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58835.341951] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58835.341960] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58894.186049] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
[58894.220030] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58894.220040] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58894.333956] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58894.333965] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58894.445952] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58894.445961] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58894.557951] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58894.557961] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58894.669952] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58894.669961] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58894.781949] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58894.781958] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58894.893960] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58894.893969] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58895.005951] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58895.005961] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58895.117953] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58895.117963] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58895.229949] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58895.229958] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58895.341951] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58895.341960] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58954.186309] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
[58954.220290] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58954.220300] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58954.333951] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58954.333960] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58954.445948] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58954.445957] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58954.557950] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58954.557959] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58954.669951] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58954.669960] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58954.781950] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58954.781959] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58954.893959] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58954.893969] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58955.005951] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58955.005960] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58955.117954] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58955.117964] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58955.229953] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58955.229962] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58955.341951] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[58955.341960] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59014.186152] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
[59014.220139] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59014.220149] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59014.333951] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59014.333960] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59014.445949] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59014.445958] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59014.557949] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59014.557958] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59014.669951] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59014.669960] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59014.781949] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59014.781958] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59014.893976] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59014.893986] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59015.005951] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59015.005960] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59015.117954] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59015.117964] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59015.229952] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59015.229961] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59015.341949] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59015.341958] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59074.186204] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
[59074.220190] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59074.220200] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59074.333950] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59074.333960] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59074.445954] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59074.445963] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59074.557951] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59074.557960] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59074.669952] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59074.669961] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59074.781949] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59074.781958] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59074.893976] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59074.893986] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59075.005953] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59075.005962] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59075.117956] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59075.117966] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59075.229953] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59075.229962] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59075.341950] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59075.341959] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59134.186249] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
[59134.220229] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59134.220240] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59134.333950] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59134.333960] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59134.445952] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59134.445961] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59134.557950] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59134.557959] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59134.669953] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59134.669962] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59134.781951] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59134.781960] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59134.893977] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59134.893987] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59135.005955] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59135.005964] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59135.117952] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59135.117962] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59135.229951] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59135.229960] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59135.341950] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59135.341959] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59194.186248] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
[59194.220229] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59194.220239] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59194.333953] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59194.333962] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59194.445952] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59194.445961] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59194.557950] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59194.557959] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59194.669951] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59194.669960] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59194.781951] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59194.781960] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59194.893957] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59194.893967] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59195.005953] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59195.005962] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59195.117952] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59195.117961] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59195.229952] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59195.229961] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59195.341948] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59195.341957] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59254.186246] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
[59254.220228] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59254.220238] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59254.333949] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59254.333958] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59254.445954] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59254.445963] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59254.557949] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59254.557959] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59254.669951] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59254.669960] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59254.781952] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59254.781961] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59254.893974] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59254.893984] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59255.005953] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59255.005962] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59255.117952] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59255.117962] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59255.229952] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59255.229961] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59255.341949] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59255.341958] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59314.186258] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
[59314.220240] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59314.220250] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59314.333953] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59314.333962] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59314.445950] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59314.445960] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59314.557950] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59314.557959] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59314.669949] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59314.669958] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59314.781951] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59314.781960] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59314.893973] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59314.893983] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59315.005955] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59315.005964] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59315.117952] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59315.117962] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59315.229954] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59315.229963] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59315.341948] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59315.341957] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59374.186207] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
[59374.220192] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59374.220203] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59374.333953] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59374.333962] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59374.445949] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59374.445958] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59374.557949] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59374.557958] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59374.669948] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59374.669957] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59374.781950] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59374.781959] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59374.893959] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59374.893969] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59375.005956] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59375.005965] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59375.117950] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59375.117960] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59375.229954] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59375.229964] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59375.341951] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59375.341960] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59434.186150] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
[59434.220131] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59434.220141] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59434.333952] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59434.333961] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59434.445949] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59434.445958] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59434.557952] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59434.557961] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59434.669975] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59434.669985] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59434.781954] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59434.781963] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59434.893973] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59434.893983] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59435.005956] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59435.005965] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59435.117951] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59435.117960] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59435.229952] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59435.229962] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59435.341951] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59435.341960] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59494.186198] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
[59494.220180] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59494.220190] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59494.333953] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59494.333963] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59494.445950] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59494.445959] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59494.557950] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59494.557959] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59494.669949] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59494.669958] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59494.781950] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59494.781959] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59494.893960] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59494.893970] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59495.005956] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59495.005965] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59495.117954] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59495.117964] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59495.229976] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59495.229986] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59495.341956] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59495.341966] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59554.186199] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
[59554.220181] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59554.220191] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59554.333953] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59554.333962] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59554.445948] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59554.445957] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59554.557950] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59554.557959] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59554.669950] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59554.669959] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59554.781951] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59554.781961] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59554.893959] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59554.893969] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59555.005955] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59555.005964] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59555.117953] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59555.117963] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59555.229949] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59555.229959] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59555.341951] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59555.341960] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59614.186310] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
[59614.220290] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59614.220300] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59614.333953] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59614.333962] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59614.445949] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59614.445958] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59614.557950] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59614.557959] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59614.669948] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59614.669957] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59614.781952] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59614.781961] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59614.893958] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59614.893968] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59615.005952] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59615.005961] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59615.117955] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59615.117964] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59615.229949] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59615.229959] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59615.341952] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59615.341961] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59674.186309] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
[59674.220290] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59674.220300] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59674.333952] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59674.333962] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59674.445947] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59674.445956] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59674.557950] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59674.557959] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59674.669951] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59674.669960] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59674.781951] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59674.781960] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59674.893973] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59674.893983] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59675.005953] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59675.005962] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59675.117955] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59675.117965] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59675.229952] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59675.229961] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59675.341954] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59675.341963] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59734.186280] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
[59734.220278] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59734.220288] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59734.333955] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59734.333965] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59734.445952] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59734.445961] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59734.557951] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59734.557960] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59734.669951] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59734.669960] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59734.781949] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59734.781958] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59734.893975] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59734.893985] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59735.005952] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59735.005961] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59735.117955] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59735.117964] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59735.229948] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59735.229957] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59735.341950] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59735.341959] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59794.186291] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
[59794.220295] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59794.220305] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59794.333953] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59794.333962] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59794.445953] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59794.445962] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59794.557950] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59794.557960] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59794.669952] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59794.669961] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59794.781948] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59794.781957] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59794.893959] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59794.893969] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59795.005953] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59795.005963] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59795.117954] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59795.117964] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59795.229948] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59795.229957] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59795.341950] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59795.341959] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59819.686687] pwrdown, 0x6(BIT6)=ff
[59854.186298] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
[59854.220278] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59854.220288] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59854.333954] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59854.333963] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59854.445952] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59854.445961] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59854.557952] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59854.557961] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59854.669950] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59854.669959] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59854.781948] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59854.781957] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59854.893959] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59854.893969] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59855.005953] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59855.005962] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59855.117955] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59855.117964] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59855.229949] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59855.229959] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59855.341952] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59855.341961] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59914.186097] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
[59914.220079] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59914.220090] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59914.333950] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59914.333960] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59914.445953] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59914.445962] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59914.557951] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59914.557960] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59914.669951] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59914.669960] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59914.781948] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59914.781958] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59914.893959] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59914.893969] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59915.005951] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59915.005960] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59915.117954] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59915.117963] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59915.229953] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59915.229962] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59915.341953] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59915.341962] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59974.186298] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
[59974.220276] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59974.220286] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59974.333949] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59974.333958] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59974.445970] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59974.445979] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59974.557951] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59974.557961] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59974.669951] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59974.669960] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59974.781950] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59974.781959] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59974.893959] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59974.893969] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59975.005955] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59975.005964] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59975.117955] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59975.117965] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59975.229955] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59975.229965] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59975.341949] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[59975.341958] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[60034.186309] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
[60034.220291] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[60034.220301] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[60034.333951] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[60034.333960] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[60034.445950] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[60034.445959] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[60034.557951] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[60034.557961] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[60034.669952] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[60034.669961] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[60034.781950] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[60034.781959] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[60034.893958] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[60034.893968] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[60035.005953] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[60035.005962] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[60035.117953] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[60035.117963] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[60035.229952] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[60035.229962] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[60035.341949] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[60035.341958] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[60094.186300] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
[60094.220281] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[60094.220291] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[60094.333950] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[60094.333959] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[60094.445955] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[60094.445964] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[60094.557949] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[60094.557959] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[60094.669953] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[60094.669962] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[60094.781951] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[60094.781960] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[60094.893959] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[60094.893969] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[60095.005954] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[60095.005964] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[60095.117952] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[60095.117962] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[60095.229952] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[60095.229961] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[60095.341949] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[60095.341958] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[60154.186299] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
[60154.220279] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[60154.220289] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[60154.333950] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[60154.333959] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[60154.445950] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[60154.445959] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[60154.557953] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[60154.557963] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[60154.669952] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[60154.669961] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[60154.781951] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[60154.781960] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[60154.893976] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[60154.893986] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[60155.005955] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[60155.005964] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[60155.117952] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[60155.117962] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[60155.229952] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[60155.229961] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[60155.341950] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[60155.341959] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[60214.186310] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
[60214.220291] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[60214.220301] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[60214.333951] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[60214.333960] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[60214.445952] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[60214.445961] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[60214.557952] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[60214.557962] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[60214.669950] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[60214.669959] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[60214.781951] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[60214.781960] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[60214.893959] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[60214.893969] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[60215.005954] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[60215.005963] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[60215.117953] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[60215.117963] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[60215.229952] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[60215.229962] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[60215.341950] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[60215.341959] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[60274.186301] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
[60274.220282] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[60274.220293] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[60274.333953] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[60274.333962] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[60274.445951] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[60274.445960] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[60274.557951] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[60274.557960] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[60274.669950] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[60274.669959] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[60274.781951] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[60274.781960] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[60274.893959] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[60274.893968] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[60275.005954] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[60275.005964] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[60275.117952] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[60275.117962] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[60275.229953] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[60275.229963] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[60275.341948] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[60275.341957] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[60334.186313] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
[60334.220295] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[60334.220305] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[60334.333952] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[60334.333962] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[60334.445949] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[60334.445958] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[60334.557953] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[60334.557962] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[60334.669950] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[60334.669959] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[60334.781953] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[60334.781962] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[60334.893956] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[60334.893966] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[60335.005954] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[60335.005963] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[60335.117949] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[60335.117959] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[60335.229952] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[60335.229961] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[60335.341950] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[60335.341959] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[60394.186431] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
[60394.220579] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[60394.220590] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[60394.333982] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[60394.333994] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[60394.445976] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[60394.445987] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[60394.557983] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[60394.557995] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[60394.669976] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[60394.669986] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[60394.781983] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[60394.781995] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[60394.893976] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[60394.893986] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[60395.005989] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[60395.006000] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[60395.118006] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[60395.118017] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[60395.229979] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[60395.229990] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[60395.341984] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a
[60395.341996] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a

---

### Post by chili555 on 2010-05-06
> rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2aI am Googling this and so far have no hits. You might email Realtek and ask them what it means.

In the future, once you get past five repeats, you can omit lines 6-1000 and simply say there are many repeats.

---

### Post by blckz28 on 2010-05-06
I don't know if this will help but I was having the same problem with my rtl8191SEVA2 where it was recognized but didn't see any wireless networks.  I just installed all the newest updates and I can now see and connect to all my wireless networks.

---

### Post by AllTiger on 2010-05-06
Guys I was able to make the wireless work, it was a matter of installing/updating Gcc_c_C++ and i erased build folder (i think i created myself) but now once i connect i lose connection in a couple of minutes.

i think i have read that if somebody knows the solution very thankful from my part, i will keep investigating though

---

### Post by Chetwynds on 2010-05-07
> **jdcf said:**
> Hi people, I'm new in the forum.
I'm writing because I was having that problem that cause the RTL8192SE WiFi card to fail after one or  two minutes in my Toshiba Satellite L500 with Ubuntu 10.04 64 bits and I have just solved it  (don't know if the solution works in any other platform). I'll try to explain every step I took to get there:

[LIST=1]
[*]Install build-essential, and surely you need linux-headers-`uname -r` too.
[*]Download the driver from the [Realtek site]("http://www.realtek.com"). I got it [here]("http://www.realtek.com/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true").
[*]Uncompress it, and, with the shell in the new dir, type:
```
sudo su
make
make install
reboot # I'm not sure it's necessary now, but I did it... 
```
[*]At this point, while trying to do something to make it work, I decided to add some parameters to the module to see if it had some effect. I think it's not necessary actually, but I left it unchanged and it works. As root, I created a /etc/modprobe.d/r8192se_pci.conf file with the next content (notice the RTL8191SE is my wlan0 interface, and yes, the module name is r8192se_pci, there is no misspelling):
```
alias wlan0 r8192se_pci
r8192se_pci option ifname=wlan0 hwwep=1
```
[*]Here comes the trick. The real problem is that the r8192se_pci module the system loads on boot is not the new one we have just compiled, but another one within Ubuntu. To solve this, do:
```
sudo su
cd /lib/modules/2.6.32-21-generic/kernel/ubuntu/rtl8192se/
mv r8192se_pci.ko r8192se_pci.ko.bak
ln -s ../../drivers/net/wireless/r8192se_pci.ko
```
[*]Reboot.
[/LIST]
And that's all, I think. I hope this will be useful to somebody. Please tell me if there is any problem.

THANK YOU!
Toshiba satellite A500 Ubuntu10.04 64bit win7 64bit (realtek rtl8191se)
I am fairly new to Ubuntu. dipped my toe in with 8 and 9. decided to dual boot my laptop with the new 10lts to make sure I go in head first. Unfortunately the wireless did not work

I am assuming step 1 was to install Ubuntu?
Had already done step 2 and 3.
It kept saying connection established but I could not browse. It was the same before I downloaded the driver.
didn't do 4
step 5 sorted it all out. Wireless connection as we speak (or as I type)
Thank you again.
:D

---

### Post by yostral on 2010-05-07
Have you tried the last realtek driver packaged in [this PPA]("https://launchpad.net/~matt-price/+archive/mattprice/+packages") ? It worked for me. And Network-Manager CAN connect to wifi while connected to a wired network.

The only thing I have to do to make my wifi work with this driver is to uncheck Wireless Coonection from Network-Manager, then turn my wifi switch button on, then re-activate Wireless Connection in Network-Manager.

If Wireless Connection is activated in NM, when I switch my wifi on, it doesn't work.

---

### Post by randuyoung on 2010-05-18
Well, I still don't have my wireless issue fixed. Realtek sent me a new driver. Now they are telling me that I need to turn the radio on. The Shuttle X50V2 All-in-one touchscreen pc does dot have a switch to turn the wireless radio on or off. How to I turn on/off the radio from a standard keyboard or via software config? How can I tell if the radio is on or off?

Thanks in advance for your help!

---

### Post by chellrose on 2010-05-18
> **randuyoung said:**
> Well, I still don't have my wireless issue fixed. Realtek sent me a new driver. Now they are telling me that I need to turn the radio on. The Shuttle X50V2 All-in-one touchscreen pc does dot have a switch to turn the wireless radio on or off. How to I turn on/off the radio from a standard keyboard or via software config? How can I tell if the radio is on or off?

Thanks in advance for your help!

There should be a hotkey for turning wireless on/off.  On my Toshiba Satellite it's Fn+F8.

---

### Post by wedderburn on 2010-06-13
i just got a Toshiba A500 with this wireless chip, using the 0017 driver i can get to the point where i can see the wireless access points but can't connect to them even with the correct password. any advice?

---

### Post by tjose on 2010-06-30
Hi,

I am using Thinkpad T410i with r8192se_pci for the thewireless. After updating the kernel to 2.6.32.22 the driver failed to load. Then I followed the steps given by jdcf and made the driver load. However, the wlan0 interface is not load automatically. Even after I load it using (sudo ifconfig wlan0 up), it is not able to display any wireless accesspoints around (iwlist wlan0 scan  reports wlan0     Scan completed :). Can you please help me to solve this problem. ?

TIA
jt

---

### Post by tjose on 2010-06-30
Hi

Refering jdcf mail

Hi people, I'm  new in the forum.
I'm writing because I was having that problem that cause the RTL8192SE  WiFi card to fail after one or  two minutes in my Toshiba Satellite L500  with Ubuntu 10.04 64 bits and I have just solved it  (don't know if the  solution works in any other platform). I'll try to explain every step I  took to get there:

[LIST=1]
[*]Install build-essential, and  surely you need linux-headers-`uname -r` too.
[*]Download the driver from the [Realtek site]("http://www.realtek.com/"). I got it [here]("http://www.realtek.com/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true").
[*]Uncompress it, and, with the shell in the new dir, type:
 	Code:
 	sudo su
make
make install
reboot # I'm not sure it's necessary now, but I did it... 
[*]At this point, while trying to do something to make it work, I  decided to add some parameters to the module to see if it had some  effect. I think it's not necessary actually, but I left it unchanged and  it works. As root, I created a /etc/modprobe.d/r8192se_pci.conf file  with the next content (notice the RTL8191SE is my wlan0 interface, and  yes, the module name is r8192se_pci, there is no misspelling):
 	Code:
 	alias wlan0 r8192se_pci
r8192se_pci option ifname=wlan0 hwwep=1 
[*]Here comes the trick. The real problem is that the r8192se_pci  module the system loads on boot is not the new one we have just  compiled, but another one within Ubuntu. To solve this, do:
 	Code:
 	sudo su
cd /lib/modules/2.6.32-21-generic/kernel/ubuntu/rtl8192se/
mv r8192se_pci.ko r8192se_pci.ko.bak
ln -s ../../drivers/net/wireless/r8192se_pci.ko 
[*]Reboot.
[/LIST]
And that's all, I think. I hope this will be useful to somebody.  Please tell me if there is any problem.
 		                   		  		  		  		  		 		 			 				 				* 					 						Last edited by jdcf; May 4th, 2010 at 02:47 PM..  					 					 				* 			


After following the steps (except, the kernel change from 2.6.32.21 to 2.6.32.22) every this was successful on my Lenovo Thinkpad T410i.  But again no wireless :-)

/var/log/syslog gives the following message

Jun 30 09:58:41 jose kernel: [ 1048.568098] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jun 30 09:58:46 jose NetworkManager: <info>  (wlan0): supplicant interface state:  starting -> ready
Jun 30 09:58:46 jose NetworkManager: <info>  (wlan0): device state change: 2 -> 3 (reason 42)


Please help me to solve the problem

TIA
jt

---

### Post by poli5681 on 2010-07-22
> **randuyoung said:**
> Well, I still don't have my wireless issue fixed. Realtek sent me a new driver. Now they are telling me that I need to turn the radio on. The Shuttle X50V2 All-in-one touchscreen pc does dot have a switch to turn the wireless radio on or off. How to I turn on/off the radio from a standard keyboard or via software config? How can I tell if the radio is on or off?

Thanks in advance for your help!

Maybe it´s a bit late, but probably will help others with the same issue. I had a call with Shuttle today;
They told me they are aware of this issue and preparing a bios update for the X50V2 which will be released in a few days.
 This will give you the ability to enable the RF permanently.
The driver itself seems to work fine - as much as i can say without RF.

---

### Post by Tinamies on 2010-08-30
Hey!

Any news on that bios update? How is it flashable Ubuntu installed?

EDIT:

Ok.. I have the same problems even after doing a lot of stuff explained on this and many other threads.

- updated Shuttle X50v2 firmware and wlan is now "Always on"
- driver "rtl8192se_linux_2.6.0017.0705.2010" built and installed
- new firmware in firmware folder
- added module to modprobe.d

```

dmesg | grep -i rtl
[  515.346186] =====>rtl8192_set_chan()====ch:1
[  515.356142] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a queuelen=0
[  515.356158] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a queuelen=0
[  515.464029] =====>rtl8192_set_chan()====ch:2
[  515.473997] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a queuelen=0
[  515.474012] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a queuelen=0
[  515.580026] =====>rtl8192_set_chan()====ch:3
[  515.589984] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a queuelen=0
[  515.589995] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a queuelen=0
[  515.692032] =====>rtl8192_set_chan()====ch:4
[  515.702013] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a queuelen=0
[  515.702024] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a queuelen=0
[  515.808038] =====>rtl8192_set_chan()====ch:5
[  515.817999] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a queuelen=0
[  515.818015] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a queuelen=0
[  515.924050] =====>rtl8192_set_chan()====ch:6
[  515.934006] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a queuelen=0
[  515.934017] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a queuelen=0
[  516.036066] =====>rtl8192_set_chan()====ch:7
[  516.046026] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a queuelen=0
[  516.046039] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a queuelen=0
[  516.152027] =====>rtl8192_set_chan()====ch:8
[  516.161990] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a queuelen=0
[  516.162000] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a queuelen=0
[  516.264044] =====>rtl8192_set_chan()====ch:9
[  516.273996] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a queuelen=0
[  516.274007] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a queuelen=0
[  516.380029] =====>rtl8192_set_chan()====ch:10
[  516.389991] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a queuelen=0
[  516.390004] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a queuelen=0
[  516.496057] =====>rtl8192_set_chan()====ch:11
[  516.506009] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a queuelen=0
[  516.506020] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x2a queuelen=0
[  516.612048] =====>rtl8192_set_chan()====ch:12
[  516.728031] =====>rtl8192_set_chan()====ch:13
[  516.945861] rtl819xSE:[FW CMD] Set FW Cmd fail!!

```

I'm also puzzled about this feedbacl from modprobe:
```

root@magicQ:/home/magicq/Lataukset/rtl8192se_linux_2.6.0017.0705.2010# modprobe -v r8192se_pci
WARNING: /etc/modprobe.d/r8192se_pci.conf line 2: ignoring bad line starting with 'r8192se_pci'

```

And, if I understood correctly according to lsmod the module r8192se_pci is not being used:
```

lsmod | grep r8192
r8192se_pci           462816  0

```

```

uname -r
2.6.32-24-generic

```

---

### Post by Tinamies on 2010-08-31
I also checked rtl8139-diag and gives me the following report:

"Found a RealTek (unknown chip type) adapter at 0xe800.
 * A recognized chip has been found, but it does not appear to exist in
 * I/O space."

I would be so pleased to get some help..

---

### Post by Tinamies on 2010-09-08
Bump

---

### Post by thejpster on 2010-10-23
I just thought I'd add my experiences.

I have a Toshiba Satellite L500-1XC, with a Core i3-330M and a Realtek 8191SEvB. For maximum compatibility my router (an O2 Wireless Box IV) is set to WPA, not WPA2.

The symptoms are that I can make a connection and keep a ping going, but after using the network heavily - e.g. downloading a file - the network fails. At first, the ping keeps going but I can't browse any pages in my browser or do any DNS lookups. Usually the ping fails sometime after. /var/log/kern.log doesn't show up anything when the connection fails but it does say "===>rtl8192se_link_change():ieee->iw_mode is 2" a lot.

If I download a 2GB test file from my local webserver I can get anywhere between 20MB and 1500MB before the connection breaks. wget doesn't stop, it just sits there receiving 0 bytes per second.

Dropping the network connection and restarting it using NetworkManager brings it all back to life (although I have to restart wget), at least until the next drop out.

In terms of drivers, I have tried version 10 (10.12.2009) , 15 (01.27.2010), 17 (05.07.2010), 17 (07.05.2010) and 18 (the one that came with Maverick). Version 15 seems to last the longest before falling over, but that might just be randomness at play.

Very frustrating.

---

### Post by faketp on 2010-10-31
> **thejpster said:**
> I just thought I'd add my experiences.

I have a Toshiba Satellite L500-1XC, with a Core i3-330M and a Realtek 8191SEvB. For maximum compatibility my router (an O2 Wireless Box IV) is set to WPA, not WPA2.

The symptoms are that I can make a connection and keep a ping going, but after using the network heavily - e.g. downloading a file - the network fails. At first, the ping keeps going but I can't browse any pages in my browser or do any DNS lookups. Usually the ping fails sometime after. /var/log/kern.log doesn't show up anything when the connection fails but it does say "===>rtl8192se_link_change():ieee->iw_mode is 2" a lot.

If I download a 2GB test file from my local webserver I can get anywhere between 20MB and 1500MB before the connection breaks. wget doesn't stop, it just sits there receiving 0 bytes per second.

Dropping the network connection and restarting it using NetworkManager brings it all back to life (although I have to restart wget), at least until the next drop out.

In terms of drivers, I have tried version 10 (10.12.2009) , 15 (01.27.2010), 17 (05.07.2010), 17 (07.05.2010) and 18 (the one that came with Maverick). Version 15 seems to last the longest before falling over, but that might just be randomness at play.

Very frustrating.

I have the same problem!

The wireless works great, but randomly, the receiving rate down to 0 kbps but the wireless keep connected.
I only get network back to normal after reloading the module: sudo modprobe r8192se_pci. Then the network reconnect and back to normal.

I using the driver available on the Realtek site, Ubuntu 10.10 32bit, kernel 2.6.35-22-generic on my Asus EEE PC 1201N

Tks for any help!

---

### Post by jromma on 2010-11-22
yep, I have the same problem. Strangely enough, my wireless works fine when i set the router to only broadcast in 802.11b, but when it broadcasts in 802.11b/g/n it gets full signal but won't load anything. any ideas as to what this could be?

---

### Post by clarkac on 2010-11-27
Same for me - just changed my router to an N class router and now I can connect to the internet for about 5 minutes and after that it's gone.  This is Ubuntu 10.10 on a Toshiba L650-10G. This was using the native drivers in 10.10.  Then tried the drivers downloaded from Realtek a few months ago, same result.  Love to see this one fixed - it's kinda vital!

---

### Post by clarkac on 2010-11-27
Just tried latest driver from Realtek website (2.6.0018.1025.2010 - same result, wireless stays connected, internet access dies after 5-10 mins.  Disconn/reconn wireless & internet access comes back, for a bit...

---

### Post by Marko8855 on 2010-11-27
Same problem here. Wifi works fine and then all of a sudden there is no network activity (though it stays connected) and I start to see these messages looping in messages:

```
Nov 26 20:30:23 t510 kernel: [ 1332.641614] Linking with kellysspot,channel:6, qos:0, myHT:0, networkHT:0, mode:6 cur_net.flags:0x406
Nov 26 20:30:23 t510 kernel: [ 1332.641629] Linking with kellysspot,channel:6, qos:0, myHT:0, networkHT:0, mode:6 cur_net.flags:0x406
Nov 26 20:30:23 t510 kernel: [ 1332.641665] ===>rtllib_associate_procedure_wq(), chan:6
Nov 26 20:30:23 t510 kernel: [ 1332.641669] HTSetConnectBwMode():pHTInfo->bCurBW40MHz:0
Nov 26 20:30:23 t510 kernel: [ 1332.641671] =====>rtl8192_set_chan()====ch:6
Nov 26 20:30:23 t510 kernel: [ 1332.656558] rtl8192_SetWirelessMode(), wireless_mode:4, bEnableHT = 0
Nov 26 20:30:23 t510 kernel: [ 1332.659241] Associated successfully
Nov 26 20:30:23 t510 kernel: [ 1332.659243] normal associate
Nov 26 20:30:23 t510 kernel: [ 1332.659252] Using G rates:108
Nov 26 20:30:23 t510 kernel: [ 1332.659253] Successfully associated, ht not enabled(0, 0)
Nov 26 20:30:23 t510 kernel: [ 1332.659255] ===>rtl8192se_link_change():ieee->iw_mode is 2
Nov 26 20:30:23 t510 kernel: [ 1332.659259] rtl8192_update_cap(): WLAN_CAPABILITY_LONG_PREAMBLE
Nov 26 20:30:23 t510 kernel: [ 1332.659862] RX: IEEE802.1X EAPOL frame!
Nov 26 20:30:24 t510 kernel: [ 1333.653821] RX: IEEE802.1X EAPOL frame!
Nov 26 20:30:25 t510 kernel: [ 1334.654460] RX: IEEE802.1X EAPOL frame!
Nov 26 20:30:25 t510 kernel: [ 1334.744977] intel ips 0000:00:1f.6: MCP power or thermal limit exceeded
Nov 26 20:30:26 t510 kernel: [ 1335.651248] RX: IEEE802.1X EAPOL frame!
Nov 26 20:30:27 t510 kernel: [ 1336.647875] ==========>received disassoc/deauth(c0) frame, reason code:f
Nov 26 20:30:27 t510 kernel: [ 1336.647891] notify_wx_assoc_event(): Tell user space disconnected
Nov 26 20:30:27 t510 kernel: [ 1336.647900] ===========>RemovePeerTS,00:16:b6:14:c8:c8
Nov 26 20:30:27 t510 kernel: [ 1336.647934] ===>rtl8192se_link_change():ieee->iw_mode is 2
Nov 26 20:30:27 t510 kernel: [ 1336.763150] =====>rtl8192_set_chan()====ch:1
Nov 26 20:30:28 t510 kernel: [ 1336.876903] =====>rtl8192_set_chan()====ch:2
Nov 26 20:30:28 t510 kernel: [ 1336.990180] =====>rtl8192_set_chan()====ch:3
Nov 26 20:30:28 t510 kernel: [ 1337.100468] =====>rtl8192_set_chan()====ch:4
Nov 26 20:30:28 t510 kernel: [ 1337.213764] =====>rtl8192_set_chan()====ch:5
Nov 26 20:30:28 t510 kernel: [ 1337.325515] =====>rtl8192_set_chan()====ch:6
Nov 26 20:30:28 t510 kernel: [ 1337.435790] =====>rtl8192_set_chan()====ch:7
Nov 26 20:30:28 t510 kernel: [ 1337.549097] =====>rtl8192_set_chan()====ch:8
Nov 26 20:30:28 t510 kernel: [ 1337.659660] =====>rtl8192_set_chan()====ch:9
Nov 26 20:30:29 t510 kernel: [ 1337.771165] =====>rtl8192_set_chan()====ch:10
Nov 26 20:30:29 t510 kernel: [ 1337.883890] =====>rtl8192_set_chan()====ch:11
Nov 26 20:30:29 t510 kernel: [ 1337.996231] =====>rtl8192_set_chan()====ch:12
Nov 26 20:30:29 t510 kernel: [ 1338.107954] =====>rtl8192_set_chan()====ch:13
Nov 26 20:30:29 t510 kernel: [ 1338.220667] Linking with kellysspot,channel:6, qos:0, myHT:0, networkHT:0, mode:6 cur_net.flags:0x406
```

And this starts repeating in debug log:

```

Nov 27 13:58:06 hitchcock-eeepc kernel: [ 2280.952033] rtl819xSE:No more TX desc@1, ring->idx = 0,idx = 0, skblen = 0x9b queuelen=0
Nov 27 13:58:07 hitchcock-eeepc kernel: [ 2281.962348] rtl819xSE:No more TX desc@1, ring->idx = 0,idx = 0, skblen = 0x9b queuelen=0
Nov 27 13:58:09 hitchcock-eeepc kernel: [ 2284.549746] rtl819xSE:No more TX desc@1, ring->idx = 0,idx = 0, skblen = 0x9b queuelen=0
Nov 27 13:58:10 hitchcock-eeepc kernel: [ 2285.534075] rtl819xSE:No more TX desc@1, ring->idx = 0,idx = 0, skblen = 0x9b queuelen=0
Nov 27 13:58:11 hitchcock-eeepc kernel: [ 2286.538925] rtl819xSE:No more TX desc@1, ring->idx = 0,idx = 0, skblen = 0x9b queuelen=0
Nov 27 13:58:12 hitchcock-eeepc kernel: [ 2287.530828] rtl819xSE:No more TX desc@1, ring->idx = 0,idx = 0, skblen = 0x9b queuelen=0

```

Disabling/Enabling networking and/or wireless doesn't solve the problem, nor does logging out and logging in. I have to reboot.

---

### Post by qrees on 2010-12-06
I also have problems with r8192se_pci module, it disconnects randomly. Only think I've found to bring it back to life is (apart from rebooting):

```
rmmod r8192se_pci
modproble r8192se_pci
```

But it would be nice if someone fixed this...

---

### Post by Vincent_Lin on 2010-12-06
After the download and compilation of this driver, I still have no wifi connection.  As a matter of fact, the device is not seen at all.

The modprobe r8192se_pci command gives 

FATAL error: inserting r8192se_pci (/lib/modules/2.6.35-23-generic-pae/kernel/dirvers/net/wireless/r8192se_pci.ko): Invalid argument.

Trying to run the wlan0up script inside realtek driver sourse folder gives the same error.

Could there be anything I did wrong while running "sudo su; make;make install" ?  Does pae kernel matter?  It was installed automatically when I did update etc....  

What else I can do to correct this to make wifi work?

Thanks.


Vincent
x201 running 32bit kernel (after all other tries for 64bit kernel, wifi does not work no matter what)

---

### Post by Vincent_Lin on 2010-12-08
Hi Guys,

Sort of embrassing, but I have to let everyone know, that, my problem was resolved.

It was due to the off setting of wlreless lan/interface card setting in BIOS.

I read it here about rfkill command and others, and someone mentioned that BIOS settting. This prompted me to check the setting in BIOS. So it was off.

Reboot, Set it back to on, and it boots into working wireless - compiled r8192se_pci stuff. Who knows, maybe the original rtl8192se driver came with ubuntu would work as well.

And this survives a reboot. And it has been working for over an hour now.  I think I am all set.

Thanks all.

Cheers,

Vincent

---

### Post by julian.neil on 2010-12-14
I spent a couple of days sorting out wireless on a MSI wind top ae2020 and thought this might help others who've been having similar problems with the wireless card: Realtek Semiconductor Co., Ltd. RTL8191SEvB Wireless LAN Controller (rev 10)

The native r8192se_pci drivers that ship with 32-bit 10.10 seem to work at first glance, but the wireless is unstable and drops out periodically, and occasionally causes hangs.  There are several threads (this one included) and launchpad bugs reporting this issue.

The newer linux drivers from [www.realtek.com.tw](www.realtek.com.tw) dont seem to help much.  They improved my wireless stability, but only marginally.

The newer windows xp drivers from realtek dont work with ndiswrapper..

I ended up downloading the (somewhat outdated ) windows realtek drivers from the msi website  [http://www.msi.com/index.php?func=downloaddetail&type=driver&maincat_no=654&prod_no=1952](http://www.msi.com/index.php?func=downloaddetail&type=driver&maincat_no=654&prod_no=1952) 
and used ndiswrapper to install the [COLOR="Red"]Win2k[/COLOR] drivers buried in the driver pack.

I followed the very good instructions at [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

Everything seems to be working now.  no dropouts.  no strange repeated messages in my syslog.

---

### Post by thejpster on 2010-12-23
I've just tried a 32-bit 10.10 LiveCD and ndiswrapper with the MSI version of the Realtek drivers linked above. I watched 20 minutes of Youtube, which was enough to convince me it fixed the issue. It would never pre-buffer more than a minute or two before.

I was sufficiently satisfied in fact, that I've just replaced my 64-bit 10.10 install with a 32-bit one.

It would still be useful if Realtek fixed their drivers, but this is enough to stop me booting Windows 7 every time I want to browse the web.

---

### Post by andytiedye on 2011-01-11
"Missed by that much&#8230;"

Alas, that link now just goes to the main MSI page, presumably because the old W2K driver has been scrubbed from the site.   Searching their site for "Realtek" or "RTL" gets nothing.
It's gone from the realtek site too,  only versions left are Vista/XP and Windoze 7.

Any other place a working driver can be found anymore?

---

### Post by SeePU on 2011-01-14
So, there's no 'realtek-firmware' in the non-free repositories that will work or provide the driver????

There's such firmware in a non-free repo in Debian Squeeze but I can't test for you as I don't own a wifi adapter with this chipset.  

I was considering a nano style adapter that has a similar Realtek 8188SE chipset that uses 8188SU firmware.  I think it would use the same firmware package as the 8192 but it sounds like it's not a good idea at the moment since the support is so poor.

Anyway, if no firmware you find is available or it doesn't work, here's the website where you can download the driver.   I think you have to compile it, though.

[http://www.realtek.com/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false](http://www.realtek.com/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false)

'Hope that helps but don't blame me if it doesn't.  That's the only info I can find so far.

---

### Post by thejpster on 2011-01-16
> **SeePU said:**
> So, there's no 'realtek-firmware' in the non-free repositories that will work or provide the driver????


There is a driver for the 8192SE / 8191SEvB but on the latter chipset at least, it appears to be unreliable as it keeps dropping the wifi connection.

Firmware usually describes code that runs within the processor of the accessory. The driver is what runs on the host computer.

I believe (looking at a random example) that Realtek's driver code is licensed under the GPL and shipped entirely as source, but the binary firmware image they load into the wifi processor is not.

> **SeePU said:**
> 
There's such firmware in a non-free repo in Debian Squeeze but I can't test for you as I don't own a wifi adapter with this chipset.


That's probably Realtek's driver, but this is an Ubuntu forum. Ubuntu supply a driver with the kernel in their distribution, which, for some of us, doesn't work. Realtek also supply the same (but newer) driver on their website which again, for some of us, doesn't work.

> **SeePU said:**
> 
I was considering a nano style adapter that has a similar Realtek 8188SE chipset that uses 8188SU firmware.  I think it would use the same firmware package as the 8192 but it sounds like it's not a good idea at the moment since the support is so poor.


They run on a different driver and, as I understand it, do not suffer this issue.

> **SeePU said:**
> 
Anyway, if no firmware you find is available or it doesn't work, here's the website where you can download the driver.   I think you have to compile it, though.

[http://www.realtek.com/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false](http://www.realtek.com/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false)


We've tried almost all the drivers on that page, but thanks for the suggestion. Actually, on checking it appears there is a new one available with specific 11N WEP / TKIP fixes, so I might try that and report back.

---

### Post by thejpster on 2011-01-16
While rtl8192se_linux_2.6.0019.1207.2010 was gloriously fast for a few minutes, a quick trip to Youtube.com soon killed the connection stone dead, just like all the previous versions.

Back to ndiswrapper. As you were.

---

### Post by thejpster on 2011-01-16
Bah. Stupid double post.

---

### Post by thenendo on 2011-01-18
> **thejpster said:**
> 
Back to ndiswrapper. As you were.

Thejpster, any chance you could post those MSI drivers that work with ndiswrapper? The link on the previous page no longer works.

PM me if you don't have a server to put them on -- I could host them.

---

### Post by thejpster on 2011-01-19
I didn't realise you could post attachments. Try this.

---

### Post by milesmonk on 2011-02-12
Any luck since, anyone? Thejpster?

---

### Post by thejpster on 2011-02-12
Yes, what?

I'm still running with ndiswrapper. Seems to take a little while to connect sometimes, but once it's connected it's reliable.

---

### Post by emtdan on 2011-02-15
My internet is completely out now. Connects for less than a minute.  I have no idea how to use ndiswapper (sp) and but I do have the newest realtek driver installed. My internet used to stay up for 2-3 days now less than a minute... Back to windows unless one of you can help

---

### Post by milesmonk on 2011-02-19
> **thejpster said:**
> Yes, what?

I'm still running with ndiswrapper. Seems to take a little while to connect sometimes, but once it's connected it's reliable.

I'm running a 64-bit version of Ubuntu, and the available Realtek drivers (the ones you've attached) don't work since they're 32-bit. Even on the [Realtek website]("http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=48&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true") the 64-bit drivers don't seem to be available. 

(Also, sometimes
```
sudo modprobe r8192se_pci
```
makes the system hang.  

This happens almost always if /lib/modules/2.6.35-25-generic/kernel/drivers/net/wireless/ does not contain a symlink called r8192se_pci.ko -> /lib/modules/2.6.35-25-generic/kernel/ubuntu/rtl8192se/r8192se_pci.ko and happens once in a while if that symlink is present.  The solution seems to be to turn off the "Enable Networking" check mark, physically switch off the wifi switch on my Thinkpad, then run:
```
sudo rmmod r8192se_pci && sleep 2 && sudo modprobe r8192se_pci
```

And then put wifi switch to on again, and then click on "Enable Networking" again.)

---

### Post by thejpster on 2011-02-25
> **milesmonk said:**
> I'm running a 64-bit version of Ubuntu, and the available Realtek drivers (the ones you've attached) don't work since they're 32-bit. Even on the [Realtek website]("http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=48&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true") the 64-bit drivers don't seem to be available. 


I had to replace my 64-bit install with a 32-bit one specifically to use ndiswrapper with those drivers.

---

### Post by ikonitas on 2011-04-08
....

---

### Post by ikonitas on 2011-04-08
sudo apt-get install linux-backports-modules-wireless-2.6.35-22-generic

---

### Post by thejpster on 2011-04-21
I tried the wireless backports, but all I got was a r8192se_pci module that wouldn't load due to missing symbols.

I'm back on ndiswrapper again.

---

### Post by lucipacurar on 2011-05-03
Hi guys,

I have a Toshiba Satellite L655 with Realtek 8191SE WLAN card and I'm using Ubuntu 11.04. My problem is that I can't connect to a D-Link 615 wireless router with WPA Personal ecryption at work. At home I have the same router but with WPA2 Personal ecryption and it works fine. Is this a known issue?

Thanks

---

### Post by thejpster on 2011-05-08
> 
I have a Toshiba Satellite L655 with Realtek 8191SE WLAN card and I'm using Ubuntu 11.04. My problem is that I can't connect to a D-Link 615 wireless router with WPA Personal ecryption at work. At home I have the same router but with WPA2 Personal ecryption and it works fine. Is this a known issue?


My wireless was equally unreliable in WPA and WPA2, so I usually leave it in the latter. Is there perhaps some other configuration difference between the two?

I've just tried 11.04 AMD64 via Wubi, to avoid damaging my (working) 10.10 install. The install failed half way through on two occasions: once it locked up and all my fans went up to full speed, the second time threw me to a text console showing an r8192se_pci call stack trace. I have given up.

Is anyone having better luck with r8192se_pci in 11.04?

---

### Post by milesmonk on 2011-05-12
> **thejpster said:**
> Is anyone having better luck with r8192se_pci in 11.04?

I did an upgrade (not fresh install) to 11.04, didn't help. I removed old kernels, didn't help. I activated ubuntu-proposed repository, and installed linux-kernel 2.6.38-9 (which someone had suggested solves the problem), didn't help. I removed old symlinks, didn't help. I created new symlink (pointing /lib/modules/2.6.38-9-generic/kernel/net/wireless/r8192se_pci.ko -> /lib/modules/2.6.38-9-generic/kernel/ubuntu/rtl8192se/r8192se_pci.ko), didn't help.

---

### Post by bhuvan on 2011-05-23
I faced this issue in maverick (10.10) release. Reloading r8192se_pci kernel module had helped.

$ sudo rmmod r8192se_pci
$ sudo modprobe r8192se_pci

---

### Post by Richardarkless on 2011-05-25
Hi guys for anyone still having problems with the rtl8191se chipset I think I have found a solution, this has been tested on my sister's Advent Quantum q200 which is running the RTL8191SEvA chipset

What I did was install these 3 packages which will install the 2.6.39 kernel 

linux-headers-2.6.39-3 
linux-headers-2.6.39-3-generic 
linux-image-2.6.39-3-generic 

and then removed any backport modules or any other things I attempted before trying this and then restarted, so far its been 5 minutes and been great

Below is the command if you want to do it through the terminal

sudo apt-get install linux-headers-2.6.39-3 linux-headers-2.6.39-3-generic linux-image-2.6.39-3-generic

I dunno if this will fix the problems people are having with the rtl8192se chipset but its worth a try

EDIT: Restarted again and then it broke

---

### Post by GiladGressel on 2011-05-30
HI guys,

I upgraded my asus1201n to natty 11.04 on a fresh install

i downloaded a livecd and ran from USB. (upgrading in 10.10 was broken...)

The wifi signals all appear to be strong and connect very fast (compared to the wrapper i was using in 10.10)

however it's still broken.  It worked really fast for about 20 minutes, but I left it downloading a torrent and when I came back it had stopped working.  The signal is still there (it doesn't continually ask for password etc) but there is no activity when you try to browse or download

please note -- this problem appears to only exist in WPA password networks.  Right now I'm on a cafe wifi with no problems 

so... still broken.  will probably go to ndswrapper later on.
also of interest is that the asus1201n has an annoying error with the NVidia graphics.  This error might be more than annoying if I was to play any serious 3d games.  
[https://bugs.launchpad.net/ubuntu/+source/jockey/+bug/771788](https://bugs.launchpad.net/ubuntu/+source/jockey/+bug/771788)

-gilad

---

### Post by paralia20105 on 2011-06-13
> **qwerty123321 said:**
> OMG thank you so much!! my wireless now works !!! thank you!

 For me too. Thank you so much !!

---

### Post by hackwater on 2011-06-27
I too am struggling with this issue in Natty (64-bit Kubuntu; I did a fresh install rather than upgrade my Lucid install). I've tried compiling the module from the source available on the Realtek site to no avail. The rmmod/modprobe combination can successfully force the wireless back into operation, but it isn't a permanent fix, as it will go down again.

I note in the release notes from Realtek that the version of the driver publicly available is good for kernels 2.6.27 - 2.6.37; I suppose it's possible that they are not supporting 2.6.38 yet. I also note that this driver seems to be the same driver as for the 8192SE; I'm wondering if that's an issue.

In Windows, my laptop warns about interference from Bluetooth and the wireless card; since I wasn't using Bluetooth, I disabled it in Windows and attempted to disable it in Kubuntu, though I'm not 100% certain I succeeded. (I disabled the Powered option in the Bluetooth settings and stopped the bluetooth service.) This does not seem to affect the wireless's behavior.

I am now trying to contact Realtek to see if there's a driver for Natty/11.04 and/or the 2.6.38 Linux kernel; I will update with their response if any.

---

### Post by neo1786 on 2011-06-27
i had similar problems... mine was 8192ce tho

[http://ubuntuforums.org/showthread.php?t=1790306](http://ubuntuforums.org/showthread.php?t=1790306)

---

### Post by hackwater on 2011-06-28
While waiting for Realtek to get back to me, I installed the 3.0 kernel (aka 2.6.40). I've been running using this kernel for around 9 hours with no problems. So the good news is that this will likely be fixed by the time Oneiric comes out. The not-so-bad news is that right now, I'm running on release candidate 4 of that particular Linux kernel, so they've had 3 candidates to review. I suspect this kernel is close to stable. The not-so-good-news is that these test kernels are not meant for every day use. I won't be getting kernel updates unless I add the kernels PPA to my APT repos, which is a scary idea. If this is the only way to go forward, so be it. But I'm going to test an alternative, which is the latest drivers from Realtek.

Yep, five hours after I e-mailed them, Realtek came back with a zipped package containing the March 29, 2011 driver source. Ignore the date in the filename; I base my date on the Readme and the Release note, which, incidentally, mentions fixing the "crash issue caused by LPS ps-poll and null tx desc wrong," this last being a staple of my syslog when the wireless goes down.

I haven't tried it yet, but that's my next attempt: 2.6.38 with the 0620.2011/March 29, 2011 Realtek drivers. Hopefully that will take care of things until Oneiric releases. I've attached the drivers in case they are helpful to others having the same issue.

---

### Post by hsoulen on 2011-06-28
> **hackwater said:**
> While waiting for Realtek to get back to me, I installed the 3.0 kernel (aka 2.6.40). I've been running using this kernel for around 9 hours with no problems. So the good news is that this will likely be fixed by the time Oneiric comes out. The not-so-bad news is that right now, I'm running on release candidate 4 of that particular Linux kernel, so they've had 3 candidates to review. I suspect this kernel is close to stable. The not-so-good-news is that these test kernels are not meant for every day use. I won't be getting kernel updates unless I add the kernels PPA to my APT repos, which is a scary idea. If this is the only way to go forward, so be it. But I'm going to test an alternative, which is the latest drivers from Realtek.

Yep, five hours after I e-mailed them, Realtek came back with a zipped package containing the March 29, 2011 driver source. Ignore the date in the filename; I base my date on the Readme and the Release note, which, incidentally, mentions fixing the "crash issue caused by LPS ps-poll and null tx desc wrong," this last being a staple of my syslog when the wireless goes down.

I haven't tried it yet, but that's my next attempt: 2.6.38 with the 0620.2011/March 29, 2011 Realtek drivers. Hopefully that will take care of things until Oneiric releases. I've attached the drivers in case they are helpful to others having the same issue.

I am also having the same issue with an RTL8192SE since moving to Natty. I also wrote to Realtek and they sent me the same driver... And then the *real *fun began!

The zip contains driver source for several cards so be very careful when using "make install" as it will add driver modules for cards you do not have present.

So... You can edit the makefiles to trim out all but your drivers, or just delete the other sub-dirs and deal with the compile warnings/errors.

But for me, after successfully compiling this driver and getting it installed I get kernel panics on every boot. I have to boot to recovery kernel and get into single user mode, then manually rm the driver to be able to boot again. Sent logs to RT but have not heard back for a solution.

So for me the problem persists. Realtek drivers have been working pretty stable for me through 10.10 but on upgrade to 11.04 neither the Ubuntu kernel driver nor the Realtek driver are in any way reliable.

A beer for anyone who can get this card stable!

Hank

---

### Post by hackwater on 2011-06-28
> **hsoulen said:**
> I am also having the same issue with an RTL8192SE since moving to Natty. I also wrote to Realtek and they sent me the same driver... And then the *real *fun began!

The zip contains driver source for several cards so be very careful when using "make install" as it will add driver modules for cards you do not have present.

So... You can edit the makefiles to trim out all but your drivers, or just delete the other sub-dirs and deal with the compile warnings/errors.

Thanks for the warning. I'm going to try editing the main makefile under the theory that if it can't call the sub-directory's makefiles from that one, I should be OK for compilation purposes.
> But for me, after successfully compiling this driver and getting it installed I get kernel panics on every boot. I have to boot to recovery kernel and get into single user mode, then manually rm the driver to be able to boot again. Sent logs to RT but have not heard back for a solution.I will hope that the June 20, 2011 date is somehow meaningful (i.e., they haven't updated their documentation in the Readme/Release notes), but if kernel panics ensue, I will continue using the 3.0 kernel and keep myself up-to-date as judiciously as possible, but sadly, manually.
>  So for me the problem persists. Realtek drivers have been working pretty stable for me through 10.10 but on upgrade to 11.04 neither the Ubuntu kernel driver nor the Realtek driver are in any way reliable.

A beer for anyone who can get this card stable!Somebody must have; it definitely works for me and one other guy using the 3.0 kernel. See [this bug]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/588822"). He installed from the [daily builds]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/daily/current/"); I went more conservative and installed from the [RC4 mainline build]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v3.0-rc4-oneiric/"). I also had to update my [module init tools]("http://packages.ubuntu.com/oneiric/module-init-tools") with the Oneiric deb. So 4 debs total: the two header debs, the kernel imagte, and the module init tools, essentially following the recipe on the [MainlineBuilds wiki page]("https://wiki.ubuntu.com/Kernel/MainlineBuilds?action=show&redirect=KernelTeam%2FMainlineBuilds#Installing_Mainline_Kernels").

I've only had a couple of minor issues with 3.0 so far: it seems slower than 2.6.38, and I couldn't get it to see my printer until I powered the printer down, unplugged the USB cable, and plugged it back in on a different USB port, powering it back on. But the wireless has been going strong, so there's a half-baked solution there (certainly beats kernel panics).

Will report back later (or perhaps sooner, if kernel panic ensues) the results of compiling the driver I posted.

---

### Post by hsoulen on 2011-06-28
Thanks "hackwater".

Looks like your driver was actually newer then the one I got a week or so ago, must have been some changes since I sent in my feedback.


Edited the makefile to only look for RTL8192se

```

sudo su
make clean (force of habit)
make
make install

```

Compile went fine (no errors), module installed and after an init 6 it came up and sure enough wireless was enabled.

But... Now the box freezes up after a few seconds to a minute, before I can even connect to a network.

dmesg has no reference to what happens when it freezes, just stops logging, as the only change was this driver I am back to the drawing board. Hacking the driver out now :(

Appreciate the effort, hopefully you will have better luck. I am on an Asus 1201n BTW.

Cheers,

Hank

---

### Post by hackwater on 2011-06-28
I booted back into the 2.6.38 kernel and put some load on my connection until it went down halfway through a 12 minute YouTube video. I then opened a terminal and```
cd Downloads/realtek/kernel-module-source-directory
sudo su
rmmod r8192se_pci
make
make install
modprobe rtl8192se
```Note the name change for the module. No kernel panics so far, and I've successfully watched various trailers on YouTube for execrable entertainment (the things I'll do for testing), as this sort of load has proven most successful in the past in bringing down my connection. Connection is still up. Gonna try a reboot and some more tests (aka YouTube vids).

---

### Post by hsoulen on 2011-06-28
Ok so decided not to give up on the new driver!

Hacked it out and went back to the drawing board.

Re-compiled, brought the driver up and did a bit of surfing. Rebooted (actually powered down) and it seems stable so far with no further freezes.

One thing I did do, I killed conky. I know this sounds strange but after watching when the freezing was happening I started to think it might be when conky started probing wlan0. Nothing empirical, simply a guess but so far so good.

Will report back should anything change, but for the moment it seems the driver that hackwater posted is working for me with kernel 2.6.38.

Thanks a bunch for the post, seems that RT took my kernel panics seriously!

Cheers,

Hank

---

### Post by hackwater on 2011-06-28
> **hsoulen said:**
> Thanks "hackwater".Call me Jose.> Looks like your driver was actually newer then the one I got a week or so ago, must have been some changes since I sent in my feedback.I was hoping this would be the case. Watching videos on ESPN to test my connection. No kernel panics on the way in to the desktop; none so far.> Edited the makefile to only look for RTL8192se

Compile went fine (no errors), module installed and after an init 6 it came up and sure enough wireless was enabled.

But... Now the box freezes up after a few seconds to a minute, before I can even connect to a network.First thing I've been firing up after boot (but before I connect to the Internet) is the terminal, live-tailing (tail -f) the syslog and dmesg. Messages in both logs have been sparse compared to when I was using the r8192se_pci module, which was a lot chattier, showing channels attempted and lots of benign AP connection info. I'm wondering if the new module is not as verbose or is diverting output elsewhere...> dmesg has no reference to what happens when it freezes, just stops logging, as the only change was this driver I am back to the drawing board. Hacking the driver out now :(Anything in syslog?> Appreciate the effort, hopefully you will have better luck. I am on an Asus 1201n BTWI'm on a Toshiba Satellite A500 from January 2010. Sounds like whatever change they made to the kernel module is conflicting with some other module. Wanna give the 3.0 kernel a go? Or post lspci -nnv, though with no dmesg/syslog output, I'm not sure how valuable that would be...

Best,

Jose

---

### Post by hackwater on 2011-06-28
Hank, fantastic news! Completely disregard my last message, which was obsoleted by your post three minutes before I posted. That's interesting about conky; I'm not sure where I'd file that bug, but a few revs of Ubuntu ago (maybe around Hardy or so), I ran into an issue where running powertop would freeze one of my machines. I shrugged and stopped trying to use it (bad developer; should have reported the bug...), but this sounds like something in the driver doesn't like external monitoring.

Best,

Jose

---

### Post by hsoulen on 2011-06-28
> **hackwater said:**
> Hank, fantastic news! Completely disregard my last message, which was obsoleted by your post three minutes before I posted. That's interesting about conky; I'm not sure where I'd file that bug, but a few revs of Ubuntu ago (maybe around Hardy or so), I ran into an issue where running powertop would freeze one of my machines. I shrugged and stopped trying to use it (bad developer; should have reported the bug...), but this sounds like something in the driver doesn't like external monitoring.

Best,

Jose

Thanks Jose, yeah I agree this driver is way less "chatty" I am not seeing all the channel and re-sync messages either.

So far so good without conky, I am going to have a look at the probing code to see if I can find anything funky, maybe the rate is too high but I am now 90% sure conky is the issue. I am going to take the monitor for wlan out and start it up again to see what happens.

For anyone using the rt8192se, give the driver Jose posted a go, seems to be a solid fix for now and much appreciated.

Cheers,

Hank

:guitar:

---

### Post by infinitylx on 2011-06-28
Hi Jose.

I have same problems with this shitty realtek (05:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8191SEvB Wireless LAN Controller (rev 10)).

I try to use your driver but i feild to compile it 

> /home/infinitylx/Downloads/rtl_92ce_92se_92de_linux_mac80211_0003.0620.2011 # make
make -C /lib/modules/2.6.39.1-33-desktop/build M=/home/infinitylx/Downloads/rtl_92ce_92se_92de_linux_mac80211_0003.0620.2011 modules
make[1]: Entering directory `/usr/src/linux-2.6.39.1-33-obj/x86_64/desktop'
make -C ../../../linux-2.6.39.1-33 O=/usr/src/linux-2.6.39.1-33-obj/x86_64/desktop/. modules
  CC [M]  /home/infinitylx/Downloads/rtl_92ce_92se_92de_linux_mac80211_0003.0620.2011/base.o
/home/infinitylx/Downloads/rtl_92ce_92se_92de_linux_mac80211_0003.0620.2011/base.c: In function &#8216;rtl_action_proc&#8217;:
/home/infinitylx/Downloads/rtl_92ce_92se_92de_linux_mac80211_0003.0620.2011/base.c:840:25: error: &#8216;RX_FLAG_TSFT&#8217; undeclared (first use in this function)
/home/infinitylx/Downloads/rtl_92ce_92se_92de_linux_mac80211_0003.0620.2011/base.c:840:25: note: each undeclared identifier is reported only once for each function it appears in
make[4]: *** [/home/infinitylx/Downloads/rtl_92ce_92se_92de_linux_mac80211_0003.0620.2011/base.o] Error 1
make[3]: *** [_module_/home/infinitylx/Downloads/rtl_92ce_92se_92de_linux_mac80211_0003.0620.2011] Error 2
make[2]: *** [sub-make] Error 2
make[1]: *** [all] Error 2
make[1]: Leaving directory `/usr/src/linux-2.6.39.1-33-obj/x86_64/desktop'
make: *** [all] Error 2
linux-zn6d:/home/infinitylx/Downloads/rtl_92ce_92se_92de_linux_mac80211_0003.0620.2011 # 
Can you please help?

PS my kenrel is 2.6.39.1-33-desktop

---

### Post by hackwater on 2011-06-28
Custom kernel, eh?

According to [this thread]("http://www.linuxquestions.org/questions/slackware-14/make-error-wireless-realtek-driver-883400/") on linuxquestions.com, you're facing an incompatibility of the source code and your kernel version. The driver code is only good for kernels from 2.6.35 to 2.6.38, but to compile against the 2.6.39 (according to that thread), try```
# sed -i 's|RX_FLAG_TSFT|RX_FLAG_MACTIME_MPDU|g' base.c rtl8192{ce,se,de}/trx.c
``` before attempting to make the code. As it looks like you have the exact same chipset as me, you probably don't want to bother building the ce or de variants of the driver; you can edit the Makefile to accomplish this, or let me know and I can upload my modified Makefile. I have no idea if there are other kernel incompatibilities, but the thread I linked to seems to indicate this worked out OK.

Good luck!

Jose

---

### Post by infinitylx on 2011-06-28
> **hackwater said:**
> According to [this thread]("http://www.linuxquestions.org/questions/slackware-14/make-error-wireless-realtek-driver-883400/") on linuxquestions.com, you're facing an incompatibility of the source code and your kernel version. The driver code is only good for kernels from 2.6.35 to 2.6.38, but to compile against the 2.6.39 (according to that thread), try```
# sed -i 's|RX_FLAG_TSFT|RX_FLAG_MACTIME_MPDU|g' base.c rtl8192{ce,se,de}/trx.c
``` before attempting to make the code.

Good luck!

thx... seems to work now.

---

### Post by arif-ali on 2011-06-28
> **hackwater said:**
> While waiting for Realtek to get back to me, I installed the 3.0 kernel (aka 2.6.40). I've been running using this kernel for around 9 hours with no problems. So the good news is that this will likely be fixed by the time Oneiric comes out. The not-so-bad news is that right now, I'm running on release candidate 4 of that particular Linux kernel, so they've had 3 candidates to review. I suspect this kernel is close to stable. The not-so-good-news is that these test kernels are not meant for every day use. I won't be getting kernel updates unless I add the kernels PPA to my APT repos, which is a scary idea. If this is the only way to go forward, so be it. But I'm going to test an alternative, which is the latest drivers from Realtek.

Yep, five hours after I e-mailed them, Realtek came back with a zipped package containing the March 29, 2011 driver source. Ignore the date in the filename; I base my date on the Readme and the Release note, which, incidentally, mentions fixing the "crash issue caused by LPS ps-poll and null tx desc wrong," this last being a staple of my syslog when the wireless goes down.

I haven't tried it yet, but that's my next attempt: 2.6.38 with the 0620.2011/March 29, 2011 Realtek drivers. Hopefully that will take care of things until Oneiric releases. I've attached the drivers in case they are helpful to others having the same issue.

Nice one, I will give this a go on my laptop this evening, and will report back. Maybe worth creating a dkms modules for this so that we don't have to keep compiling it for kernel upgrades that natty will bring later as well.

FYI, I have been using natty with the 3.0.0 rc4 kernel from mainline, and that has been working really well for me.

---

### Post by hsoulen on 2011-06-28
Ahhhh well I spoke too soon.

About an hour after my last successful session, box locked up hard again.

Going through the logs to see if I can find the culprit but as this box was stable a few hours before the RT drivers I am going to assume the worst.

My quest for stable wireless in Natty continues. Gotta tell ya, this is one of those things, even if everything else is working it makes no difference if I have to hang a bloody USB dongle off the side of my laptop.

Distro-hunting continues until a solution is found. I might just have to live with yum (yuck).

**Edit**: Sure enough syslog shows NetworkManager wlan0 roamed from the BSSID and when it tried to reconnect BAM! hard-lock. After this first hard-lock the only way for me to get back to a proper boot (hard-lock within several seconds both in X and cli) is to turn off the card with the physical switch. Going to continue to debug and see where it gets me.

Cheers,

Hank

---

### Post by arif-ali on 2011-06-28
> **hsoulen said:**
> Ahhhh well I spoke too soon.

About an hour after my last successful session, box locked up hard again.

Going through the logs to see if I can find the culprit but as this box was stable a few hours before the RT drivers I am going to assume the worst.

My quest for stable wireless in Natty continues. Gotta tell ya, this is one of those things, even if everything else is working it makes no difference if I have to hang a bloody USB dongle off the side of my laptop.

Distro-hunting continues until a solution is found. I might just have to live with yum (yuck).

**Edit**: Sure enough syslog shows NetworkManager wlan0 roamed from the BSSID and when it tried to reconnect BAM! hard-lock. After this first hard-lock the only way for me to get back to a proper boot (hard-lock within several seconds both in X and cli) is to turn off the card with the physical switch. Going to continue to debug and see where it gets me.

Cheers,

Hank

You could instead try the kernel 3.0.0-0300rc4-generic from mainline in the meantime, which I have been using for a few weeks now without any problems (for me anyway), This has the relevant drivers already compiled in.

The only thing is that you will probably need a new version of module-init-tools, but it seems to work really well

---

### Post by hsoulen on 2011-06-28
> **arif-ali said:**
> You could instead try the kernel 3.0.0-0300rc4-generic from mainline in the meantime, which I have been using for a few weeks now without any problems (for me anyway), This has the relevant drivers already compiled in.

The only thing is that you will probably need a new version of module-init-tools, but it seems to work really well

Did you install the mainline from some PPA, from the debs or from source? I am in dependency hell from the updated module-init-tools.

Cheers,

Hank

---

### Post by arif-ali on 2011-06-28
> **hsoulen said:**
> Did you install the mainline from some PPA, from the debs or from source? I am in dependency hell from the updated module-init-tools.

Cheers,

Hank

I downloaded the module-init-tools from the following URL

[http://ftp.heanet.ie/pub/ubuntu/pool/main/m/module-init-tools/](http://ftp.heanet.ie/pub/ubuntu/pool/main/m/module-init-tools/)

and then the relevant 3 files from

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.0-rc4-oneiric/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.0-rc4-oneiric/)

i.e. 
linux-headers
linux-headers-generic
linux-image

Install all 4, and reboot, and it should work

Note: other 3rd party drivers had issues, so I would try to test the kernel on it's own entity first, and then  try any 3rd party drivers

---

### Post by kozimodo on 2011-06-28
> **hackwater said:**
> While waiting for Realtek to get back to me, I installed the 3.0 kernel (aka 2.6.40). I've been running using this kernel for around 9 hours with no problems. So the good news is that this will likely be fixed by the time Oneiric comes out. The not-so-bad news is that right now, I'm running on release candidate 4 of that particular Linux kernel, so they've had 3 candidates to review. I suspect this kernel is close to stable. The not-so-good-news is that these test kernels are not meant for every day use. I won't be getting kernel updates unless I add the kernels PPA to my APT repos, which is a scary idea. If this is the only way to go forward, so be it. But I'm going to test an alternative, which is the latest drivers from Realtek.

Yep, five hours after I e-mailed them, Realtek came back with a zipped package containing the March 29, 2011 driver source. Ignore the date in the filename; I base my date on the Readme and the Release note, which, incidentally, mentions fixing the "crash issue caused by LPS ps-poll and null tx desc wrong," this last being a staple of my syslog when the wireless goes down.

I haven't tried it yet, but that's my next attempt: 2.6.38 with the 0620.2011/March 29, 2011 Realtek drivers. Hopefully that will take care of things until Oneiric releases. I've attached the drivers in case they are helpful to others having the same issue.

The attached drivers compile and load fine but cannot get a connection. I also tried the 3.0 kernel (rc1 since that is what is in the ppa) and get a panic on boot.

---

### Post by kozimodo on 2011-06-28
Ah, I see that there are more recent rc's.  rc5 seems to be working great for me so far.  Will know more tomorrow.

---

### Post by hsoulen on 2011-06-29
> **arif-ali said:**
> I downloaded the module-init-tools from the following URL

[http://ftp.heanet.ie/pub/ubuntu/pool/main/m/module-init-tools/](http://ftp.heanet.ie/pub/ubuntu/pool/main/m/module-init-tools/)

and then the relevant 3 files from

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.0-rc4-oneiric/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.0-rc4-oneiric/)

i.e. 
linux-headers
linux-headers-generic
linux-image

Install all 4, and reboot, and it should work

Note: other 3rd party drivers had issues, so I would try to test the kernel on it's own entity first, and then  try any 3rd party drivers

Thanks a bunch.

Will have a look, probably need the newest Nvidia drivers from the oneiric PPA otherwise not too many custom drivers.

I have to think about other distros to be honest, I realize this is not Ubuntu's "fault" but the fact that I had stable wireless for several versions and then all of a sudden I don't is frustrating, especially considering that the drivers were added to the kernel but apparently with little testing outside a WEP connection at 54Mb.

I'll keep posting as I go and let you all know my results.

Thanks for all the support.

Hank

---

### Post by kozimodo on 2011-06-29
I can confirm that the 3.0 rc4 and rc5 kernels work much better but I still regularly, although less frequently, get deauths so that instead if being unusable, it is now only annoying.

The 3.0 kernel has other problems for me.  There are some boot up warnings/errors and mounting USB drives is broken.

Toshiba L675-S7107.

---

### Post by thejpster on 2011-07-02
I am currently using the driver from compat-wireless-3.0-rc4-1.tar.bz2. It passes the YouTube test and I've been happily surfing for a few hours without issue.

```

me@laptop:~$ modinfo rtl8192se
filename:       /lib/modules/2.6.38-8-generic/updates/drivers/net/wireless/rtlwifi/rtl8192se/rtl8192se.ko
firmware:       rtlwifi/rtl8192sefw.bin
description:    Realtek 8192S/8191S 802.11n PCI wireless
license:        GPL
author:         Realtek WlanFAE	<wlanfae@realtek.com>
author:         lizhaoming	<chaoming_li@realsil.com.cn>
srcversion:     937F4C8CF0D06038BBDF950

me@laptop:~$ uname -a
Linux Satellite-L500 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:50 UTC 2011 i686 i686 i386 GNU/Linux

```

---

### Post by hsoulen on 2011-07-06
Just thought I would post my final results.

Anyone out there with a draft n router (in my case Belkin) you WILL have issues with the 8192/92se cards in Linux.

After countless hours wasted the Belkin/Realtek combo just does not work. I can get a more stable connection if I set my router to WPA Personal TKIP (not WPA2 AES) and to a/b/g (no n) but still flaky, not to mention the Belkin will ONLY connect at n speeds if you use WPA2/AES anyway...

Solution for me was to grab an old Linksys 54g router, load dd-wrt on it and run it in bridge mode to my Belkin, that way all my other n devices can connect to the Belkin SSID and get full n speed and my Linux box can connect at g speeds to the Linksys on another SSID.

Crappy solution to be sure as the same card in Windows connects at n with no issues or drops, my opinion is that draft n (not sure about n in general) with the WPA/AES combo is just not stable in Linux but this is conjecture.

Also decided to move to another Distro on this box, not just because of this issue but a few others as well. But have no fear you are all still stuck with me anyway as I have four other Ubuntu boxes in the house.

Cheers,

Hank

---

### Post by kozimodo on 2011-07-06
> **thejpster said:**
> I am currently using the driver from compat-wireless-3.0-rc4-1.tar.bz2. It passes the YouTube test and I've been happily surfing for a few hours without issue.

So far so good with compat-wireless-3.0-rc4-1.tar.bz2 as well.

---

### Post by milesmonk on 2011-07-09
> **kozimodo said:**
> So far so good with compat-wireless-3.0-rc4-1.tar.bz2 as well.

Can confirm that this has worked great for me so far.  

However, I did need to add an entry saying "modprobe rtl8192se" to /etc/modules to make it load automatically.

---

### Post by GiladGressel on 2011-07-15
Hi,
glad to hear something is working again.
Can someone give me easy to follow directions for how to use the driver found in that tarbal?

i browsed the compat site and am more confused than before.  

thanks
-gilad

---

### Post by chili555 on 2011-07-15
> **GiladGressel said:**
> Hi,
glad to hear something is working again.
Can someone give me easy to follow directions for how to use the driver found in that tarbal?

i browsed the compat site and am more confused than before.  

thanks
-giladWould you please start a new thread? I'm working a hunch here and, if it doesn't work out, we can build compat-wireless pretty easily. Please post in your thread:```
lspci -nn | grep 0280
```

---

### Post by thejpster on 2011-07-16
Performed some updates and rebooted to find I had no wifi. Oh, look, a kernel update. Here we go again.

cd ~/compat-wireless-3.0-rc4-1
make clean
make
sudo make install
sudo modprobe -r rtl8192se
sudo modprobe rtl8192se

Phew. Good job I didn't delete that tarball ;) Can't wait until this driver goes mainstream.

Using this driver I haven't had any drop outs in the last two weeks, and it's much faster and more reliable at connecting than ndiswrapper was.

---

### Post by Glowbeard on 2011-08-07
I have the RTL8191SEvB chip and after upgrading to the most recent Realtek drivers and switching my routers security from WPA to WEP authentication I was able to get the wireless working.

Y-A-Y

---

### Post by thejpster on 2011-10-15
Just to add, the driver baked into to Kernel 3.0.0 in Ubuntu 11.10 works fine. No more backports for me.

---

