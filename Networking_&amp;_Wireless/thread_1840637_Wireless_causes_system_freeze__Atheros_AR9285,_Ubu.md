---
title: "Wireless causes system freeze:  Atheros AR9285, Ubuntu 11.04 64-bit, Acer Aspire 5250"
date: 2011-09-07
forum: Networking &amp; Wireless
---

### Post by Zanazabar on 2011-09-07
Hello all.  Just got a new laptop (Acer Aspire 5250) and decided to install Ubuntu for the first time.  Grabbed the 11.04 64-bit edition and did a clean install, and then all upgrades through Synaptic Package Manager.  I found my built-in wireless PCIe card, an Atheros AR9285 (rev1) is responsible for system freezes (kernel panic).

Conditions: e If I have the ethernet cable plugged in, everything is fine.  If I take out the ethernet cable, the system freezes in 5-15 seconds forcing a hard shutdown.  If I boot up without the cable plugged in the system will freeze during boot-up or at the log-in screen.  While the ethernet cable is plugged in, the system does connect to the wireless router successfully.  I know this because after unplugging the ethernet cable, during the very short window I have gotten HTTP traffic through.  Also, logging into the router from a different box, I can see the laptop as a client with the MAC address of the wireless card.

So far, I have read many threads on these forums and others and tried many things including:
   - disabling wireless encryption
   - installing a new kernel 
   - installing the compat-wireless package

Nothing was successful, so I have now done a complete reinstallation of Ubuntu 11.04 64-bit and want to give a fresh try following suggestions.

Here follows the requested output from the How-to-post Guide:

**1 ) Machine Brand and Model (PC/Laptop)**:
```
Acer Aspire 5250
```**2 ) Wireless Brand, Model and Wireless Chipset:**
```
steven@zanazabar:~$ lspci -nn | grep "Atheros"
06:00.0 Ethernet controller [0200]: Atheros Communications AR8152 v2.0 Fast Ethernet [1969:2062] (rev c1)
07:00.0 Network controller [0280]: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) [168c:002b] (rev 01)
```**3 ) check interface:**[INDENT]```
steven@zanazabar:~$ iwconfig wlan0
wlan0     IEEE 802.11bgn  ESSID:"xxxxxx"  
          Mode:Managed  Frequency:2.422 GHz  Access Point: xx:xx:xx:xx:xx:xx   
          Bit Rate=54 Mb/s   Tx-Power=9 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=53/70  Signal level=-57 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:33   Missed beacon:0
```[/INDENT][B]

4 ) Check for modules:[/B]

```
[INDENT]steven@zanazabar:~$ lsmod | grep "ath"
ath9k                 118238  0 
mac80211              294370  1 ath9k
ath9k_common           13851  1 ath9k
ath9k_hw              323077  2 ath9k,ath9k_common
ath                    23773  2 ath9k,ath9k_hw
cfg80211              178528  3 ath9k,mac80211,ath
[/INDENT]
```
**5 ) Kernel boot messages**
```
steven@zanazabar:~$ dmesg | grep "ath"
[    2.031646] device-mapper: multipath: version 1.2.0 loaded
[    2.031660] device-mapper: multipath round-robin: version 1.0.0 loaded
[   17.946436] ath9k 0000:07:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[   17.946462] ath9k 0000:07:00.0: setting latency timer to 64
[   17.998894] ath: EEPROM regdomain: 0x65
[   17.998901] ath: EEPROM indicates we should expect a direct regpair map
[   17.998910] ath: Country alpha2 being used: 00
[   17.998915] ath: Regpair used: 0x65
[   18.045067] ieee80211 phy0: Selected rate control algorithm 'ath9k_rate_control'
[   18.047035] Registered led device: ath9k-phy0::radio
[   18.047238] Registered led device: ath9k-phy0::assoc
[   18.047432] Registered led device: ath9k-phy0::tx
[   18.047555] Registered led device: ath9k-phy0::rx
``` 
**6 ) Network configuration**
```
steven@zanazabar:~$ sudo lshw -C wlan0
PCI (sysfs)  
```**7 ) Scan for networks:**
```
steven@zanazabar:~$ iwlist scan wlan0
wlan0     Scan completed :
          Cell 01 - Address: xx:xx:xx:xx:xx:xx
                    Channel:3
                    Frequency:2.422 GHz (Channel 3)
                    Quality=51/70  Signal level=-59 dBm  
                    Encryption key:on
                    ESSID:"xxxxxx"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000fb59cd188
                    Extra: Last beacon: 70340ms ago
                    IE: Unknown: 000B4372797374616C53686970
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030103
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD06001018020100

```[B]


8 ) Ubuntu Version: [/B]
```
steven@zanazabar:~$ lsb_release -d
Description:    Ubuntu 11.04
```
**9 ) Kernel/architecture (including 32 vs. 64 bit): **
```
steven@zanazabar:~$ uname -mr
2.6.38-11-generic x86_64
```
**10 ) Restarting the network:**
```
[INDENT]steven@zanazabar:~$ sudo /etc/init.d/networking restart
 * Running /etc/init.d/networking restart is deprecated because it may not enable again some interfaces
 * Reconfiguring network interfaces...                                          Ignoring unknown interface eth0=eth0.
Ignoring unknown interface wlan0=wlan0.
                                                                         [ OK ]
[/INDENT]
```

---

### Post by wildmanne39 on 2011-09-07
Hi, here is a link that fixes that problem for most people.
[http://ubuntuforums.org/showthread.php?t=1811178](http://ubuntuforums.org/showthread.php?t=1811178)
Thank you

---

### Post by SpaceQuadrant on 2011-09-07
Hello, there seems to be a bit of a bug with Atheros wireless at the moment. [http://ubuntuforums.org/showthread.php?t=1835190&page=1](http://ubuntuforums.org/showthread.php?t=1835190&page=1) try checking out a few suggestions there, mine will not work at all.

---

### Post by wildmanne39 on 2011-09-07
Hi, most of the time that bug does not keep you from having a good connection.
Thank you

---

### Post by Zanazabar on 2011-09-08
Unfortunately in my case, reordering the boot order (putting network boot first in BIOS) does not help the situation.

When I tried this I lost any ability to connect to the wireless at all, but it still froze up the system if I unplugged the network cable.  I followed the links and it looks like the original solution worked for someone with a Broadcom wireless card.  This fix may also work for some people with Atheros, but it did not work for me.

I have also tried the nohwcrypt option and other little tweaks, but nothing has done the trick.

---

### Post by wildmanne39 on 2011-09-08
Hi, other people have also said that they solved this by upgrading there kernel to 2.6.39 rc4 I am not an expert on upgrading kernels but here is a link if you want to try.
[http://ubuntuguide.net/how-to-install-linux-kernel-3-0-rc2-in-ubuntu-11-04-natty-narwhal](http://ubuntuguide.net/how-to-install-linux-kernel-3-0-rc2-in-ubuntu-11-04-natty-narwhal)

Scroll down the page and you will find the kernel I just mentioned.
Thank you

---

### Post by Zanazabar on 2011-09-09
It is a good suggestion.  I also tried this and the problem remained.  I got the 2.6.39 kernel from the Ubuntu main-line area and followed the instructions there to install it (the PPA route using Synaptic Package Manager didn't seem to have the kernel).

Along the same lines I tried building the latest bleeding edge compat-wireless package and using it with that kernel.  Still no luck.

I am somewhat anxious to see Ubuntu 11.10 which I understand will be using the new 3.x linux kernel and hoping that may be the answer (but I don't want to wait a month).

---

### Post by wildmanne39 on 2011-09-09
Hi, in that link I gave you there is the 3.0 kernel and directions for installing it also.
Thank you

---

### Post by Zanazabar on 2011-09-10
Well, I installed the 3.0 kernel from the .deb packages.  When I booted up into the new kernel I did not see the Wireless Connection established message when I logged into Ubuntu.  When I clicked on the network icon in the system tray I didn't even see a Wireless Networking section.  At first I figured it was moving in the right direction.

Then I unplugged the ethernet cable and the within seconds the whole system froze up again.

Ubuntu and this laptop do not seem to be compatible at this time.

---

### Post by nm_geo on 2011-09-11
Let's check the kernel booting info:

```
dmesg | egrep 'ath|firmware|FW'
```

---

### Post by Zanazabar on 2011-09-11
Okay.  When I boot in the 3.0 kernel there isn't anything relevant from that command (just the device-mapper multi-path lines).  Here is the output from the 2.6.38 generic kernel:
```

steven@zanazabar:~$ dmesg | egrep 'ath|firmware|FW'
[    2.067479] device-mapper: multipath: version 1.2.0 loaded
[    2.067509] device-mapper: multipath round-robin: version 1.0.0 loaded
[   17.982388] ath9k 0000:07:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[   17.982414] ath9k 0000:07:00.0: setting latency timer to 64
[   18.059138] ath: EEPROM regdomain: 0x65
[   18.059148] ath: EEPROM indicates we should expect a direct regpair map
[   18.059159] ath: Country alpha2 being used: 00
[   18.059163] ath: Regpair used: 0x65
[   18.135916] ieee80211 phy0: Selected rate control algorithm 'ath9k_rate_control'
[   18.137536] Registered led device: ath9k-phy0::radio
[   18.137594] Registered led device: ath9k-phy0::assoc
[   18.137655] Registered led device: ath9k-phy0::tx
[   18.137712] Registered led device: ath9k-phy0::rx
```
To further explore I booted up into a Fedora 15 live CD.  Everything seems smooth.  It uses the 2.6.38 kernel as well with this ath9k driver pack.  I ran into a problem though when I booted up into the live CD with the ethernet cable plugged in, and then unplugged it while in the session.  System froze!

When I ran this dmesg command from the Fedora 15 live CD session there was some more information.  There was an error suggesting a bug in the firmware of one of the Atheros devices, but I couldn't tell from the command if it was referring to the wired or wireless device.  It referenced atl1c so I think that means the AR8152 firmware had the problem.

Could I have been blaming the wrong component all along?  Perhaps there is no issue at all with the AR9285 wireless, and the AR8152 **wired** component is to blame for all these issues.  It would make sense since the problem seems to occur when the cable is not plugged in or at the time the cable is unplugged.  Does AR8152 have rotten firmware?  If so, if I can't find new firmware to flash to it, will I have a way to disable the component entirely in Linux and just run wireless?  Since it is a laptop, that would not be a big deal at all.

---

### Post by Zanazabar on 2011-09-11
FWIW, if I boot the Fedora liveCD, the output of the dmesg command is identical to what I posted above with the addition of the 'firmware bug' line I mentioned.  Since this is such a low level issue I don't think it has anything to do with a specific linux distro.  Not sure if the 'bug' mentioned is because of the LiveCD setting, I'll have to try booting an Ubuntu LiveCD and seeing what the output is there.  Here is the exact line I get from dmesg if anyone can help decrypt it:

```
[   42.187024] atl1c 0000:06:00.0: vpd r/w failed.  This is likely a firmware bug on this device.  Contact the card vendor for a firmware update.
```

I *think* atl1c means it is the ethernet card and not the wireless card.  I don't know what 'vpd r/w' is.  Do I really have any hope of contacting Qualcom and getting a firmware update?

---

### Post by wildmanne39 on 2011-09-11
Hi, yes that bug is for the ethernet connection and qualcom just recently took over the company and they have not made new drivers available.

Here is a link to get the 8151 working and it probably covers the 8152.
[http://ubuntuforums.org/showthread.php?t=1806056&page=2](http://ubuntuforums.org/showthread.php?t=1806056&page=2)

Start with post 17 and see if the firmware is newer then the one you are using, other then that I am out of idea's those freezing issues are very difficult.
Thank you

---

### Post by Zanazabar on 2011-09-11
Okay, sounds like a good direction.  My previous attempt (in my initial post) with compat-wireless had focused on the ath9k driver instead of the atl1c driver.

From the thread you linked, it says to go to  [http://wireless.kernel.org]("http://wireless.kernel.org/en/users/Download#Directly_downloading_the_tarball"), but that host seems to be down at the moment.  I see what I think are the same packages available from [http://linuxwireless.org/](http://linuxwireless.org/), so I hope that is equivalent.  Gonna give it a shot.

---

### Post by wildmanne39 on 2011-09-11
Hi, I am doing some research, that link was good a few days ago.

Thank you

---

### Post by Zanazabar on 2011-09-12
Okay.  Well, I think the kernel.org web server is just down right now for whatever reason.  I used what I got from linuxwireless.

Still, same problem so no go.

I tried to follow the directions which seem standard (use the script to select the driver, in my case atlc1.  then do the make, make install, make unload, and reboot).

Where I am confused are there are so many version of compat-wireless to download.  I booted up into 2.6.38 standard kernel for Ubuntu, so I downloaded the compat-wireless that said it was for the 2.6.38 kernel.  I was thinking since it said to make sure the linux-headers is installed, that you had to match to the right version.  Or am I making this dependency up and I can just get whatever the latest bleeding edge compat-wireless is regardless of kernel?

At the least since I installed the 3.0 kernel, I can try again with that compat-wireless version.

If I can't get this to work now... what are my choices?  I am confused as to how I can buy a laptop that has a broken component.  Is it something I can remove and replace with a working ethernet card?  Also, if the firmware is messed up, how is it possible for Windows 7 to have no problem with these Atheros chipsets?

All your help is appreciated.  I really want to run Linux on this machine!

---

### Post by wildmanne39 on 2011-09-12
Hi, yes the kernel headers and build essentials have to be for the kernel you want to compile the driver for.

There is nothing wrong with the firmware for windows just linux because microsoft pays a lot of money to make sure the driver and firmware work for there operating system while making it has hard as possible for other operating systems to make working firmware and drivers. 

I also had tried to download the driver with out success, so maybe it will be back up soon.
Thank you

---

### Post by Zanazabar on 2011-09-12
Okay, [www.kernel.org](www.kernel.org) says it is down for maintenance now, but I've just been pulling the tarballs from linuxwireless.org.

Situation: boot up Ubuntu 11.04 into the 3.0 kernel.  I downloaded the compat-wireless tarball for the 3.0 kernel.  I targeted atl1c as the driver and went through the *make* process and installed the driver.  I unloaded all mods and rebooted.  Unfortunately, I locked up in the same way.

Still trying to run experiments, so I found out this piece.  I boot up again into the 3.0 kernel with the ethernet cable plugged in so everything is fine.  In the terminal I run the following command:

```
sudo modprobe -r atl1c
```

This disables the "Wired Connection".  Now, if I unplug the ethernet cable, the system stays up!  I can now use the laptop just without any network connectivity.  This is somewhat better than being tethered to the cable...

Now, in the 3.0 kernel remember I said the wireless ability doesn't show up at all?  Well I think that was just due to lack of drivers.  I guess ath9k isn't in the current pull down if you grab the kernel.  I used the same compat-wireless tarball and targeted ath9k and installed it.  When I loaded it with modprobe, the wireless ability appeared.

(Issue here, although the wireless functionality appeared, and it remembered my network name and password, it is unable to actually establish a wireless connection.  Note that this is true even if I have atl1c running and the ethernet cable plugged in.  Seems to be a new issue with the 3.0 kernel vs the 2.6.38 kernel.)

So what I'm wondering now is if it is possible to load wireless with the ath9k driver and not load wired with the atl1c driver.  Does ath9k depend on atl1c?  If this is possible, is there a way to suppress atl1c during bootup so that it won't mess up my system?  I think I have shown that it is atl1c that is causing the system to freeze.

---

### Post by nm_geo on 2011-09-12
So what I'm wondering now is if it is possible to load wireless with the  ath9k driver and not load wired with the atl1c driver. **Yes**

 Does ath9k  depend on atl1c? **No** 

run this 

```
modinfo ath9k
```read through it.

 If this is possible, is there a way to suppress atl1c  during bootup so that it won't mess up my system? **Sure**

 I think I have shown  that it is atl1c that is causing the system to freeze.

**Even if it does not solve the issue the fix is reversible.**

one line at a time.. just copy and paste

```
sudo su 
echo "blacklist atl1c" >> /etc/modprobe.d/blacklist.conf 
exit
```

---

### Post by Zanazabar on 2011-09-13
Very close now.

Here's what I did and what I saw:

First I realized with all my kernel and driver switching that I'd broken my wireless ability (ignoring the ethernet cable issue, unable to establish any type of wireless connection) which had been working out of the box.  So first, I did a clean install of Ubuntu 11.04 64-bit, and then ran Synaptic to apply all updates.  Now wireless functionality was restored and I was back in the original situation.

Then I ran the commands you indicated, nm_geo, to blacklist the problematic atl1c.  I still was having the issue however.  So I opened up Network Connections and then hit Edit on the Wired tab for "Auto eth0". I deselected "Connect automatically" and "Connect for all users", then I applied and received a message about a failed loopback command.  I ignored this and then deleted the entry for "Auto eth0" entirely from the Wired tab in Network Connections.  Then I rebooted.

The same issue still occurred, however, the laptop was now favoring the wireless connection by default.  The weird part is if I click on the network icon there is still an entry for "Auto eth0" in the pulldown (but it is not connected to it), however, if I open Network Connections there are no entries at all on the Wired tab.

In this situation, I ran:

```
lsmod
```

and there 'atl1c' was in the list!  I don't know how it is there.  So then I ran the command

```
sudo modprobe -r atl1c
```

and I was where I wanted to be!  If I click on the network icon there is nothing whatsoever about any "Wired connection" listed in the pulldown, not even an area for wired connections.  And if I unplug the ethernet cable the system stays stable, and I have network connectivity via the wireless card.  Just how I want it!

Problem is if I reboot, then I have to have the cable in so it doesn't freeze while I pull up a terminal and run "sudo modprobe -r atl1c". So...

Even after being blacklisted, how is atl1c resurrecting itself?

More importantly, how can I block it?  Can I manage through configurations, or will I need to try and uninstall the atl1c driver entirely to prevent it from running?

---

### Post by Zanazabar on 2011-09-13
To summarize, if I look at /etc/modprobe.d/blacklist.conf there is an entry there for atl1c.  But it is being loaded anyway and appears when I run lsmod.  Any suggestions for how to stop this?

Also, the wireless situation may not be ideal.  While it connects if the laptop is sitting directly next to the router, it seems to lose connection if I wander more than ~10 feet away.  I read threads about this issue to and have already gone through the things suggested trying to fix my other problem, unfortunately.

---

### Post by nm_geo on 2011-09-14
> **Zanazabar said:**
> To summarize, if I look at /etc/modprobe.d/blacklist.conf there is an entry there for atl1c.  But it is being loaded anyway and appears when I run lsmod.  Any suggestions for how to stop this?

Also, the wireless situation may not be ideal.  While it connects if the laptop is sitting directly next to the router, it seems to lose connection if I wander more than ~10 feet away.  I read threads about this issue to and have already gone through the things suggested trying to fix my other problem, unfortunately.

We could double up on that driver.
Let open a editor as root and add a statement that might stop the athl1c..
```
gksudo gedit /etc/rc.local
```Copy and paste or write carefully above the exit 0.
```
modprobe -r athl1c
```Save and Close

Maybe that will stop it.. ;-)

---

### Post by Zanazabar on 2011-09-18
Okay, got to a milestone at least.  When I add that line to /etc/rc.local (looks like a typo there, the driver is *atl1c*) I can boot up straight into Ubuntu with no ethernet cable plugged in and no system freeze.

An interesting thing to note.  Found this before I made the above change to /etc/rc.local.  If I did an initial boot in to Windows 7, then selected to restart from Windows 7, if I then went into Ubuntu, I would be fine.  atl1c would still show loaded in lsmod, and the disconnected Wired adapter would show in the context menu of the Network icon in the upper right, but no system freeze.  I don't know if anyone can explain that, but there seems to be some really weird behavior with the AR8152, and Windows has some secret to 'correct' the problem.

Regarding the AR9285 wireless, I can use it now with major limitations.  I can not get more than about 10 feet from the router without dropping the connection.  I also have limited bandwidth, if I try to for instance torrent a Linux ISO, the traffic will overload my connection and I lose all throughput.  I still show Connected, but I can't send or receive data.  If I manually Disconnect and then Connect again, I will be able to resume.  If I throttled the download speed to 250kB/s I could maintain (that was about the max).

Is it reasonable to think these chipset issues will be fixed or worked-around in future updates?

---

### Post by wildmanne39 on 2011-09-18
Hi, there are a few things you can try to make you connection more stable.
1.Set your router to g,b,n speed and not just n speed.

2. Set your router to wpa2 not mixed or wep.

3.Run these commands one at a time.
```
sudo ifconfig wlan0 down
sudo rmmod -f ath9k
sudo modprobe ath9k nohwcrypt=1
sudo ifconfig wlan0 up
```
if this helps we will make the 3rd suggestion permanent.

Please do not restart your computer after running those commands it is for test purposes and will be gone when you restart.

Also make sure your wired connection is unplugged before you run the commands.

As for the issues being fixed in the next release they could be but in my experience a lot of times somethings do not get fixed and we still have to use the work arounds.
Thank you

---

### Post by hofik on 2011-09-20
Hi guys, I have the same issue with Notebook Acer 5250; Wifi AR5B95 brand new, brand new Ubuntu 11.04 installed. It works on cable LAN, freezes when I remove the cable (turning on Wifi).

---

### Post by wildmanne39 on 2011-09-20
Hi, please go back and read post 2 and do what the link says and see if that fixes your problem if not then we will go from there.
Thank you

---

### Post by hofik on 2011-09-21
Thanks a lot!!!! It seams to be working!!! I used a few more tips from that doc. Extremely helpful!... One thing I havent managed to solve is waking-up from sleep mode, despite successfully installing Jupiter. I guess Ill need to spend a little bit more time on that.

---

### Post by wildmanne39 on 2011-09-21
Hi, yes that can be a problem is it your wireless card that does not wake up or your computer, also if I have been helpful would you consider showing your support for me becoming an ubuntu member by clicking on the red link in my signature?
Thank you

---

### Post by Zanazabar on 2011-09-21
Okay, I followed the steps to try out the nohwcrypt option with ath9k.  I did not see any change to my wireless connection, unfortunately.


Some other random data points: I installed Ubuntu 10.04 LTS.  I found it doesn't freeze up, seemingly because it doesn't offer any support for the AR8152 (no atl1c in the mod listing, and no ability to connect to a Wired connection).  Still has the same issues with wireless using the ath9k driver (works well next to router, but no distance).

FWIW, my router only does 802.11b,g so I don't have to disable 802.11n.  I have it set to WPA2 only.  I have also tried disabling encryption entirely, and the issue remained the same.

---

### Post by wildmanne39 on 2011-09-21
Hi, have you checked to see if you wireless power is turned up all the way in your router?

This usually
> Bit Rate=54 Mb/s   Tx-Power=9 dBm  reads
20 at least.

Try this please:
```
sudo iwconfig wlan0 power off

```
```
sudo iwconfig wlan0 rate auto
```
```
sudo service network-manager restart
```
Thank you

---

### Post by hofik on 2011-09-22
> **wildmanne39 said:**
> Hi, yes that can be a problem is it your wireless card that does not wake up or your computer, also if I have been helpful would you consider showing your support for me becoming an ubuntu member by clicking on the red link in my signature?
Thank you

Sure, ... I'm not familiar with the process. Is just clicking sufficient, or something more to be done?
Back to Wireless issue - I guess there must be another issue with the adapter. If I'm very close to the router, it seams to be working fine. If I go to another room, it randomly disconnects or the network is extremely slow. At the same time, the signal strength is good, e.g. >85% and all other devices are working there fine.... very strange.

---

### Post by wildmanne39 on 2011-09-22
Hi hofik, try what I posted in post 30, I recently learned that your card has issue like that so I am not sure we can do anything about it but if post30 does not help, I will do some more research.

When you click on the red link in my signature you just need to say you support my membership, you will see the things every one else has said as well.
Thank you

---

### Post by hofik on 2011-09-26
Folks, I believe I finally resolved almost all the major issues with Acer Aspire 5250.

I should have paid a little bit more info to every little details of the info posted in this thread. Major things I fixed recently on my Acer:
1. Wireless causes system freeze: The suggestion here of putting "boot from network" instead of booting from HDD helps... but once I upgraded  bios from v1.01 to v1.05 it started to work irrespectively of booting options
2. Wireless performance was terrible. It worked reliably only when the PC was next to the wifi router. After upgrading bios to v1.05 it seams to be working ok
3. I initially overlooked a suggestion of moving to the community video driver instead of using fglrx. Once I moved back to the community driver, sleep function started to work fine.
4. I found other suggestions very helpful, e.g. num lock indicator, Jupiter power schemes, etc.
5. The only issue that still bothers me a little is HDD clicking noise appearing every 7 seconds or so, when operating on battery. I found some articles on this suggesting that the noise is coming from HDD heads being parked... but didn't have time to focus properly on that. I'll need to spend more time on that - but it's not that huge priority compared to fixing wifi performance or sleep mode.

I'd like to say big THANKS esp. to [wildmanne39]("http://ubuntuforums.org/member.php?u=508533") for spending time on this with me. (I hope I supported your membership in the correct way. Pls. shout if I could help more.) Thanks!

---

### Post by wildmanne39 on 2011-09-26
Hi hofik, your welcome! I am glad you have had such success getting your wireless working properly.

---

### Post by hofik on 2011-09-27
I'm sorry, a step back again. Wifi making it freezing again, I had to change booting sequence again. Also working with that a little bit more, wifi performance isn't ideal, I've got it disconnected yesterday multiple times again...  it's certainly better than before, but far from being good.

---

### Post by wildmanne39 on 2011-09-27
Hi hofik, please post the results of these commands, run them after you have been disconnected before you reconnect.
```
cat /etc/lsb-release; uname -a
```
```
nm-tool
```
```
lspci -nnk | grep -iA2 net
```
```
iwconfig
```
```
rfkill list all
```
```
sudo iwlist scan
```
```
lsmod | grep ath
```
```
dmesg | egrep 'ath|firm|wlan0'
```
by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

