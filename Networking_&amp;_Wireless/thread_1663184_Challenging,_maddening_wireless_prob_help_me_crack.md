---
title: "Challenging, maddening wireless prob: help me crack the nut!"
date: 2011-01-09
forum: Networking &amp; Wireless
---

### Post by Bucky Ball on 2011-01-09
*** UPDATE: This card is now fixed in the 11.04 kernel. You can install that and Realtek have brought out a new driver for it, too. All is explained in post #24 here:
[http://ubuntuforums.org/showthread.php?p=11133342#post11133342](http://ubuntuforums.org/showthread.php?p=11133342#post11133342)


Hi all,
 
 I've been banging on about this periodically in another thread since I got my new machine and getting nowhere but I think I'm narrowing it down and things have changed enough to warrant this new thread. Today I decided I was going to fix this once and for all(!!!). Any help more than appreciated. Consider it a challenge cos it's got me stumped!

 **My specs:**
 Toshiba Satellite Pro L510
 Realtek RTL8191SEvB Wireless LAN Controller (rev 10)
           driver=rtl819xSE driverversion=0019.1207.2010
 Dual booting 10.10, kernel 2.6.35-24 with Windows 7
 One of four machines on home network using static IP's.
     
 The 2.6.35-** kernel is the only one I could get running on my machine, and that   after hours of research and tweaking, so please don't ask me to try another kernel. I've tried 'em from 2.6.32 to 2.6.37. :)


 **My issue:**
 I'm on the LAN and net no problem, can see websites, etc (so all ESSID, security key, channel, etc, are correct) but the signal strength swings from 100% to 50% for a few seconds at random, fluctuates unpredictably, then settles back around 97% - 100% for most of the time. I do speed tests on the following site using the 'Bandwidth' button when the page is loaded:
 
 [http://www.abc.net.au/iview/](http://www.abc.net.au/iview/)
   
 Whereas other speed test sites seem to fluctuate this one gives me consistent output. On the machine in question I am getting between 0.4 - 0.7Mbps, *regardless* of signal strength!  
 
 There are three other machines on our home network &#8211; two wireless and one wired - all running Ubuntu (two wireless 10.04 LTS, one wired 8.04 LTS), all achieving 10Mbps+ (including my studio box which is behind two walls and two doors using a USB wireless dongle!).   
 NOTE: Ethernet cable is fine on     the Toshiba in question; 10Mbps+, same as the rest. 

 **My explorations today:**
 Firstly I checked the speed in Windows 7. It was *exactly* the same: 0.4Mbps &#8211; 0.7. Hmm. Download speed the same on both OSs also, peaking at around 125kbps.
 
Realtek offers newer drivers for Windows and Linux than the ones I was running. Take note Windows users: Windows 7 did NOT pick this up when I tried 'Update Driver' from the Device Manager; I had to manually go to the site, download, and install. Both drivers here:
 
 [http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false)
 

 I boot into Windows, install the new, reboot, voila; 10Mbps+ like the other three machines.  
 
**My attempted Ubuntu fix:**
 So I'm figuring it's as easy as installing the updated Linux driver. I downloaded 0019.1207.2010, untarred, removed the old 0018 version, and installed the new one. Reboot and it's there, no problem. But wireless no different. And I mean absolutely *no* different. Signal strength and transfer rates unchanged.
 
 **My ideas:**  
 1/ Does this card and driver just not work with Maverick at the moment?
 2/ Is there something set incorrectly in the wireless/network config files?
 3/ Have I overlooked something glaringly obvious and simple for the last three months?
 
**My line of attack:**
 I have a side bet on #3, but I like #2, and that's where I'm going to start investigating. Reasoning? 

1/ The Ubuntu install on the Toshiba - the latest release on the newest machine &#8211; has totally different signal strength and transfer rate to the other installs on the other three machines. 
2/ Win7 is fine on the same laptop with transfer speeds matching all other OS installs on the other three machines (two dual booting with XP, one Ubuntu only). 
3/ Every other install is within about 0.75Mbps of each other and signal solid while the Toshiba is showing 0.4 - 0.7Mbps and signal erratic.  
 
This kinda rules out the router. It must be a setting on the Toshiba. But which?  
 
 I've researched my problem a *lot* and it seems to be kinda unique. For others with this card the connection seems to die completely. I've tried just about everything I could find and I'm guessing it's not the same issue for me; if the machine disconnects/connects a pop-up tells me so and I never need to manually reconnect (not even after suspend). No sign of a pop-up or dropped connection.
 
Anyone wanting to help crack this nut is more than welcome.  
 
 Below are various outputs. Any logs or other info required just ask. I have also attached a dmesg generated after a machine start (not restart). syslog was too big to upload. I have omitted the ESSID from the output, but trust me, it's the correct one. ;)
 
 Tnx in advance for *any* ideas anyone may have &#8230;
 

 ```
binky@tosher:~$ iwconfig  
 lo        no wireless extensions.  
 
 eth0      no wireless extensions.  
 
 wlan0     802.11bg  ESSID:"*****"  Nickname:"rtl8191SEVA2"  
           Mode:Managed  Frequency=2.437 GHz  Access Point: 00:1B:11:84:AF:26    
           Bit Rate=11 Mb/s    
           Retry:on   RTS thr:off   Fragment thr:off  
           Power Management:off  
           Link Quality=100/100  Signal level=-45 dBm  Noise level=-120 dBm  
           Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0  
           Tx excessive retries:0  Invalid misc:0   Missed beacon:0 
``` ```
binky@tosher:~$ iwlist wlan0 scan 
 wlan0     Scan completed :  
           Cell 01 - Address: 00:1B:11:84:AF:26  
                     ESSID:"*****" 
                     Protocol:IEEE802.11g  
                     Mode:Master  
                     Channel:6  
                     Encryption key:on  
                     Bit Rates:54 Mb/s  
                     Extra: Rates (Mb/s): 54  
                     Quality=100/100  Signal level=-45 dBm  Noise level=-120 dBm  
                     Extra: Last beacon: 5ms ago 
``` ```
binky@tosher:~$ iwlist wlan0 rate 
 wlan0     12 available bit-rates :  
       1 Mb/s  
       2 Mb/s  
       5.5 Mb/s  
       11 Mb/s  
       6 Mb/s  
       9 Mb/s  
       12 Mb/s  
       18 Mb/s  
       24 Mb/s  
       36 Mb/s  
       48 Mb/s  
       54 Mb/s  
           Current Bit Rate:11 Mb/s
``` From 'lshw -C network':
 
```
*-network  
        description: Wireless interface  
        product: RTL8191SEvB Wireless LAN Controller  
        vendor: Realtek Semiconductor Co., Ltd.  
        physical id: 0  
        bus info: pci@0000:03:00.0  
        logical name: wlan0  
        version: 10  
        serial: b4:82:fe:3c:ad:72  
        width: 32 bits  
        clock: 33MHz  
        capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless  
        configuration: broadcast=yes **driver=rtl819xSE driverversion=0019.1207.2010** firmware=63 ip=192.168.0.107 latency=0 link=yes multicast=yes wireless=802.11bg  
        resources: irq:17 ioport:2000(size=256) memory:d4000000-d4003fff
``` My driver is in bold; yes, the right one.
 
 In '/lib/firmware' I have 'RTL8192SE'.

---

### Post by Bucky Ball on 2011-01-09
Well, I just made another breakthrough of sorts. From Synaptics I added:

**linux-backports-modules-wireless-maverick-generic**

I did attempt to install linux-backports-modules-wireless-lucid-generic, a possible fix I found here:

[http://subbass.blogspot.com/2010/05/howto-ubuntu-1004-lucid-post-install.html](http://subbass.blogspot.com/2010/05/howto-ubuntu-1004-lucid-post-install.html)

... but could'nt figure out how.

After adding the Maverick wireless backports I then deleted my wireless connection and rebooted. 

Set up the wireless again on reboot. When I go to Edit Connections >Wireless, my wireless connection showed that it was in use NOW! It has only ever shown in use NEVER. Some progress but unfortunately I'm still wallowing at 0.04-0.07Mbps. Any suggestions?

I am closing in!!! :twisted:

---

### Post by Bucky Ball on 2011-01-09
Just followed the instructions for adding the Lucid backports here:

[https://help.ubuntu.com/community/UbuntuBackports#Enabling%20the%20entire%20repository]("https://help.ubuntu.com/community/UbuntuBackports#Enabling%20the%20entire%20repository")

After adding to my sources Synaptics tells me things have changed and to hit 'reload'. I did but the Lucid backports are nowhere to be seen. I have no idea if successfully installing the Lucid wireless backports is going to make any difference but I'm giving anything a go at this point. :confused:

From the link:

> After refreshing the package manager's cache, packages from the backport repositories will now be available for installation. They aren't.

---

### Post by Bucky Ball on 2011-01-10
Just one other thing of interest, another clue, and a bit of support for my theory of a dodgy setting (or the .35 kernel). The internet speed problem is exactly the same whether I use kernel 2.6.35-24 *or *2.6.35-**. They all seem to work but the internet issue remains unchanged.

---

### Post by chah on 2011-01-10
Hi, I had a similar (but not the same) problem that I managed to solve. I have an Edimax wifi USB card that has a realtek chipset in it. Apparently there are 2 possible driver sets for this chipset. In my case they were rt2870sta, which I think was written by realtek, and the other was rt2x00lib/rt2x00usb written by a third party (not certain who, this is from memory). I read somewhere that this was causing a conflict and very flaky wifi performance that I was experiencing. I tried blacklisting first the rt2870sta driver by adding it to the file /etc/modprobe.d/blacklist.conf and rebooting. That didn't improve the performance. I subsequently blacklisted the other driver set, and all my wifi problems went away.

I'm not sure if your poor performance is due to a similar cause. I suggest to execute lsmod and look for the realtek drivers loaded. If you have more than 1 set, search for them online, and see if you can find which ones belong together as a group and try blacklisting one set or the other. 

At any rate, from the symptoms you describe, I would suspect the wifi driver.

Hope you can solve your problem.

---

### Post by Bucky Ball on 2011-01-10
Chah, thanks for that. A new angle, exactly what I'm after. The output at the end of 'lsmod' was interesting:

```
r8169                  42254  0 
libahci                26052  1 ahci
mii                     5261  1 r8169
```Is that two loaded or two parts of the same? I'm unsure what this means.

---

### Post by chah on 2011-01-10
I just re-read your first post. If you are getting the same data transfer rates in Windows and in Ubuntu, I would suspect the hardware, or some settings that are embedded in the hardware (some hardware has non volatile memory that can retain settings even after the power is off). 

I would get it fixed in Windows first by sending it to Toshiba before trying to tackle it in Ubuntu.

---

### Post by grahammechanical on 2011-01-10
Hi

I do not have a laptop. I do have a motherboard with wireless built in. It came with a separate user guide for the wireless adapter. All the advice is for Windows. I do notice that with the program that is installed under Windows (I am only using Ubuntu), you can set the wireless node to either 802.11b or 802.11g/b

I think that Ubuntu switches from 802.b to 802.g without us needing to select a node. Is it possible to make sure that your wireless adapter is running at 802.g or 802.n speeds and not 802.b speeds?

Also I notice that you have a noise level. I do not know if -120 dBm is excessive. Is it?

Regards.

---

### Post by Bucky Ball on 2011-01-10
Hi grahammechanical, 

Thanks for the tip. How would I check?

Something strange has happened. A friend came around for a couple of hours and I switched my machine off. I booted it up three hours later and it is *definitely* faster and connecting with websites almost immediately whereas before it  was hanging for what was getting to be an unbearably long time (seemed  to be getting worse) and seems to be really zippy. 

But the plot thickens. The speed test is *identical* to what it was before; 0.4 - 0.7. So I tried the Speakeasy Speedtest, another I have been using for comparison. *Identical* to what it has always read (barely 1Mbps up and down). 

The network signal icon is strong and above 90% most of the time now but it still drops radically for no apparent reason. Now rarely.

I'm guessing that driver update maybe *did* do the trick - or at least made a difference - and I'm getting more consistent signal and better speeds even though its not showing that on the speed test (???) Youtube loads fast and plays 480 vids no prob. 

Or maybe it just feels fast because it was waiting for an age before connecting to a website before. Who knows? Maybe the world is an orange! Can't work it out, but ready and willing to check b/g settings. Will have a look and see what I can dig up on that. ;)

Thanks for your help so far, people.

---

### Post by Bucky Ball on 2011-01-10
Could be onto something. Connection information tells me:

> 802.11 Wifi (wlan0)A quick look here leads me to believe it should 803.11G?

[http://en.wikipedia.org/wiki/IEEE_802.11#802.11-1997_.28802.11_legacy.29](http://en.wikipedia.org/wiki/IEEE_802.11#802.11-1997_.28802.11_legacy.29)

Am I anywhere close? A discovery instigated by investigating your idea grahammechanical. Connection Info also tells me:

> Driver: rtl819xSE
Speed: 11Mb/s

This totally contradicts what the speed tests are telling.

---

### Post by Bucky Ball on 2011-01-10
This is also interesting: Why is "rtl8191SEVA2" the nickname when the card is the RTL8191SEvB? (Just discovered it makes no difference to config).
802.11b/g but what's it set to? Working on how to find that out.
Connection rate should probably be 54Mb/s as have a G router. (changed rate with 'iwconfig wlan0 rate 54M to match the setting on wireless G router)
Noise level has dropped which might explain why I'm not getting so many hangs.
I also changed mode with 'iwconfig wlan0 mode Managed'. 

```
binky@tosher:~$ iwconfig wlan0
wlan0     **802.11bg**  ESSID:"Slynn"  Nickname:**"rtl8191SEVA2"**
          Mode:Managed  Frequency=2.437 GHz  Access Point: 00:1B:11:84:AF:26   
          Bit Rate=**11 Mb/s **  
          Retry:on   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=93/100  Signal level=-48 dBm  Noise level=-**116 dBm**
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

Still doing the same as it was but not as much. Still hanging randomly but connecting to sites quicker and there's moments where it seems to be working perfectly, despite all details from speed tests and 'Network Tools'. There's still something not quite right, but getting closer. Thanks for your ideas to this point. I'm off to bed ...

---

### Post by Bucky Ball on 2011-01-11
Another day, another whole lot of wasted time waiting for pages to load. 

I am figuring just gonna have to wait for an update fix or a miracle. No real idea what I'm doing at this point as boot up this morning and bad as it's ever been. 'Edit Connections' shows me my wireless was last used two days ago and up s**t creek once more. 

I have no idea what's happening and doesn't seem like anyone else has either. If someone has any ideas whatsoever please chime in. Anything goes at this point.

Thanks for your ideas and help to this point folks but I'm starting to think that this machine with this wireless card and Maverick (and just about any other kernel I've tried) and the updated (or old) driver are, at the moment, a c**p match. Nothing I try is getting close to fixing. No-one I can find has this issue. Time for a bug report.

:-({|=

---

### Post by Bucky Ball on 2011-01-11
What do people think of this, from /var/log/messages?

```
binky@tosher:~$ tail -f /var/log/messages
Jan 12 03:47:07 tosher kernel: [  142.695815] rtl8192se_update_ratr_table: ratr_index=0 ratr_table=0x00000000
Jan 12 03:48:27 tosher kernel: [  222.611623] rtl8192se_update_ratr_table: ratr_index=0 ratr_table=0x00000000
Jan 12 03:50:07 tosher kernel: [  322.598834] rtl8192se_update_ratr_table: ratr_index=0 ratr_table=0x00000000
Jan 12 03:52:07 tosher kernel: [  442.457546] rtl8192se_update_ratr_table: ratr_index=0 ratr_table=0x00000000
Jan 12 03:54:07 tosher kernel: [  562.456816] rtl8192se_update_ratr_table: ratr_index=0 ratr_table=0x00000000
Jan 12 03:56:07 tosher kernel: [  682.464836] rtl8192se_update_ratr_table: ratr_index=0 ratr_table=0x00000000
Jan 12 03:58:07 tosher kernel: [  802.403540] rtl8192se_update_ratr_table: ratr_index=0 ratr_table=0x00000000
Jan 12 03:58:29 tosher rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="1222" x-info="http://www.rsyslog.com"] rsyslogd was HUPed, type 'lightweight'.
Jan 12 04:00:07 tosher kernel: [  922.292220] rtl8192se_update_ratr_table: ratr_index=0 ratr_table=0x00000000
Jan 12 04:02:07 tosher kernel: [ 1042.231529] rtl8192se_update_ratr_table: ratr_index=0 ratr_table=0x00000000
```

---

### Post by Bucky Ball on 2011-01-12
Okay, I am convinced this is a driver issue. I admit defeat and will have to live with a dodgy driver and wildly fluctuating unreliable wireless. I am going to install OpenSuse 11.3 and see if that makes any difference. Thanks for your help. 

I deleted my wireless connection in Network Manager, rebooted, and now Network Manager is showing the connection as used three minutes ago, so that bit seems to be working again but has made no difference whatever to my connection speed or reliability. Not overjoyed. :( :confused:

I did actually attempt to install the rtl8191SEVA2 driver, seeing as the machine wants to give it that nickname, but 'make install gives this error:

```
binky@tosher:~$ cd /home/binky/Downloads/RealtekDriver/VA2/rtl8192se_linux_2.6.0019.1207.2010/
binky@tosher:~/Downloads/RealtekDriver/VA2/rtl8192se_linux_2.6.0019.1207.2010$ sudo make
make[1]: Entering directory `/usr/src/linux-headers-2.6.35-24-generic'
  Building modules, stage 2.
  MODPOST 1 modules
make[1]: Leaving directory `/usr/src/linux-headers-2.6.35-24-generic'
binky@tosher:~/Downloads/RealtekDriver/VA2/rtl8192se_linux_2.6.0019.1207.2010$ sudo make install
make[1]: Entering directory `/usr/src/linux-headers-2.6.35-24-generic'
  Building modules, stage 2.
  MODPOST 1 modules
make[1]: Leaving directory `/usr/src/linux-headers-2.6.35-24-generic'
make[1]: Entering directory `/home/binky/Downloads/RealtekDriver/VA2/rtl8192se_linux_2.6.0019.1207.2010/HAL/rtl8192'
make -C /lib/modules/2.6.35-24-generic/build M= CC=gcc modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.35-24-generic'
  CHK     include/linux/version.h
  CHK     include/generated/utsrelease.h
make[3]: *** No rule to make target `kernel/bounds.c', needed by `kernel/bounds.s'.  Stop.
make[2]: *** [prepare0] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.35-24-generic'
make[1]: *** [modules] Error 2
make[1]: Leaving directory `/home/binky/Downloads/RealtekDriver/VA2/rtl8192se_linux_2.6.0019.1207.2010/HAL/rtl8192'
make: *** [install] Error 2

```

I did 'make' first, then 'make install', of course. The error message reminded me that I tried to install this driver about a month and a half ago and got the same message. Couldn't figure it out then either.

---

### Post by Bucky Ball on 2011-01-17
*** Further Update:

I have emailed Realtek to see if they can shed some light. Failing this, after three months of working on this off and on and attempting every fix known to human kind I give up! Hopefully there will be a Ubuntu update or Realtek update that may one day fix this problem. I am currently trying to set up the card in OpenSUSE to see if that makes any difference but having even less luck there ... :(

*** And further update!

To finish off this conversation with myself a point of interest: I installed the card in OpenSUSE and the signal strength is rock solid, not fluctuating at all, but the speed is exactly the same. 0.4-0.7Mbps.

---

### Post by Bucky Ball on 2011-06-13
Just to add:

I emailed Realtek back in February to find that the driver they supply is only intended  for use on 32bit systems and unpredictable on 64bit systems. With this  in mind, I finally had the time to install a 32bit Ubuntu on one of my  partitions. The install automatically supplied me with this driver:

driver=rtl819xSE driverversion=0015.0127.2010

Not the driver version I was using previously in the other install which  was the latest which starts with 0019. It worked straight away but the  speed was the same (although the connection is stable at 88%).

So no  different really. Around 1Mbs as opposed to around 10 on the cable. I am  about to email Realtek again. Their driver for Windows matches the  cable speed, for Linux, no. Once again Linux is the poor brother.

Maybe they mean it is for use on a 32bit machine, period. ***Not*** a 64bit machine running a 32bit OS. That would be incredibly unhelpful. What irks me is that these companies don't just get on the forums and make things clear to the community in the first place. Instead we have to waste hours fiddling about at a pointless exercise.

---

### Post by blitzit on 2011-07-22
Hi Bucky Ball,

I had similar problems like yours with my D-Link DWA525.
[LIST=1]
[*]Fluctuating signal strength for no apparent reason
[*]Couldn't find (seemingly) authentic drivers
[*]Unreliable operation of the connection
[/LIST]

I spent weeks trying to configure it as well, and it would start working. But again, in a period of a weeks, there would be a problem and it would come to a stop.

I have finally managed to get the thing work for now. But I totally agree with you, these companies should come out with releases about drivers so that we don't have to keep banging our heads trying to search for solutions.

---

### Post by Bucky Ball on 2011-07-22
> **Vijay Rao said:**
> ... I totally agree with you, these companies should come out with releases about drivers so that we don't have to keep banging our heads trying to search for solutions.

+12. Yep. How's this for irony. I now have a USB wireless dongle which has a Realtek wireless chip and using the 8189 (or 8187 depending on the install I'm running) that works out of the box! Plug it in, it's there!

I've switched off the internal wireless card. Blacklist. Couldn't be bothered ...

BTW: I have a couple of D-Link routers and they're great. At least so far but they've been around for some years now!

---

