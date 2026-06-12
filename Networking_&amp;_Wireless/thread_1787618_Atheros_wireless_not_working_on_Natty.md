---
title: "Atheros wireless not working on Natty"
date: 2011-06-21
forum: Networking &amp; Wireless
---

### Post by jamadagni on 2011-06-21
Hello. I recently bought a new laptop and installed Kubuntu Natty on it. I am unable to connect to WiFi.

```

$ sudo lshw -C network
  *-network DISABLED      
       description: Wireless interface
       product: AR9285 Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 01
       serial: 68:a3:c4:4e:2f:a0
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=2.6.38-8-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:d0500000-d050ffff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 05
       serial: f0:de:f1:4b:d5:a8
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:40 ioport:2000(size=256) memory:d0404000-d0404fff memory:d0400000-d0403fff

```

```

iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
ppp0      no wireless extensions.

```

Network Manager applet says "wireless disabled by hardware" but in fact the WiFi + Bluetooth switch is on and I am able to use Bluetooth on Natty. On Windows 7 I am able to use WiFi as well.

My laptop is a Lenovo Ideapad Z570. I'm able to use wireless with no troubles on my older Compaq Presario C771UT.

Also noted this: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/780040](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/780040)

---

### Post by chili555 on 2011-06-21
> Also noted this: [https://bugs.launchpad.net/ubuntu/+s...ux/+bug/780040](https://bugs.launchpad.net/ubuntu/+s...ux/+bug/780040)I think you are on the right track but haven't gone far enough. Please run and post:```
rfkill list all
```If your wireless is soft blocked by acer-wireless (Acer on a Lenovo???) then do:```
sudo rmmod -f acer-wmi
sudo rfkill unblock all
```If your wireless springs to life, we'll amend a file and make it persistent.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/775414](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/775414)

---

### Post by jamadagni on 2011-06-21
> **chili555 said:**
> I think you are on the right track but haven't gone far enough. Please run and post:```
rfkill list all
```If your wireless is soft blocked by acer-wireless (Acer on a Lenovo???) then do:```
sudo rmmod -f acer-wmi
sudo rfkill unblock all
```If your wireless springs to life, we'll amend a file and make it persistent.
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/775414](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/775414)

Hi thanks for this feedback -- I also observed you help the other guy fix his BroadCom thingy at [http://ubuntuforums.org/showthread.php?t=1754456](http://ubuntuforums.org/showthread.php?t=1754456). 

I already posted the rfkill result at [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/771758/comments/8](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/771758/comments/8) but perhaps you didn't see.

So I did those two commands to kill the acer module but my wireless didn't "spring to life" i.e. NM still shows the "Enable wireless" as disabled. I don't know how to restart NM except for restarting the system. But if I do that, once more this acer driver will be loaded. 

I am not sure how to go about the blacklisting. Should I add blacklist acer-wmi to /etc/modprobe.d/blacklist.conf or something? Should I then do mkinitramfs too?

Thanks for your patience!

---

### Post by chili555 on 2011-06-21
> I already posted the rfkill result at [https://bugs.launchpad.net/ubuntu/+s...758/comments/8](https://bugs.launchpad.net/ubuntu/+s...758/comments/8) but perhaps you didn't see.Your comment #8 refers to wl and brcm80211. The title of this thread refers to Atheros. :confused::confused::confused:

Let's try this:```
sudo gedit /etc/rc.local
```Add three lines above exit 0```
modprobe acer-wmi
rmmod -f acer-wmi
rfkill unblock all

```Proofread, save and close gedit. Reboot and give us your report.

---

### Post by jamadagni on 2011-06-21
Oh oh oh -- sorry sorry sorry. I was sleeping on my feet when I posted that -- the correct link is [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/780040/comments/4](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/780040/comments/4) which is still on the Atheros system. I will reboot and get back to you.

---

### Post by chili555 on 2011-06-21
No worries. I've done worse, in fact, I think I've done worse *today*! So how did it work?

---

### Post by jamadagni on 2011-06-21
Hey man thanks for understanding. 

So I booted up but NM still has the "Enable wireless" check box disabled.

```
$ rfkill list all
0: ideapad_wlan: Wireless LAN
        Soft blocked: no
        Hard blocked: no                                                                                                                               
1: ideapad_bluetooth: Bluetooth                                                                                                                        
        Soft blocked: no                                                                                                                               
        Hard blocked: no                                                                                                                               
4: phy0: Wireless LAN                                                                                                                                  
        Soft blocked: no                                                                                                                               
        Hard blocked: yes                                                                                                                              
5: hci0: Bluetooth                                                                                                                                     
        Soft blocked: no                                                                                                                               
        Hard blocked: no

```

At least the Acer thingy seems to have disappeared.

---

### Post by jamadagni on 2011-06-21
So when the wireless hardware switch is off this is what is shown:

```
$ rfkill list all
0: ideapad_wlan: Wireless LAN
        Soft blocked: no
        Hard blocked: yes
1: ideapad_bluetooth: Bluetooth
        Soft blocked: no
        Hard blocked: yes
4: phy0: Wireless LAN
        Soft blocked: no
        Hard blocked: yes

```

And when the hardware switch is on:

```
$ rfkill list all
0: ideapad_wlan: Wireless LAN
        Soft blocked: no
        Hard blocked: no
1: ideapad_bluetooth: Bluetooth
        Soft blocked: no
        Hard blocked: no
4: phy0: Wireless LAN
        Soft blocked: no
        Hard blocked: yes
6: hci0: Bluetooth
        Soft blocked: no
        Hard blocked: no

```
So what is this phy0 that is hard-blocking the wireless?

Thanks!

---

### Post by chili555 on 2011-06-21
[http://en.wikipedia.org/wiki/PHY](http://en.wikipedia.org/wiki/PHY)

In this instance, phy0 simply refers to the wireless chipset as the operating system sees it. The fact that it's hardblocked no matter what the direction of the wireless switch and no matter if acer-wmi is present or not is troublesome, to say the least. Usually, by some method or another, we can get the wireless to come alive. So far, nothing works here.

My laptop, a Lenovo Thinkpad T60 has both a key combination Fn+F5 and a physical slider; both must be engaged to get the wireless working. Do you have just one switch?

We might play around with the lines in /etc/rc.local; for instance:```
modprobe acer-wmi
rfkill unblock all
rmmod -f acer-wmi

```Or maybe even:```
modprobe acer-wmi
rfkill unblock all
rmmod -f acer-wmi
rfkill unblock 4
```When you stumble on the fix, please be sure to report it to the developers by posting on your bug report. I'll put it in my book of tricks, too.

---

### Post by jamadagni on 2011-06-22
:( I went to Windows and found that by hitting Fn + F5 the OSD came up and showed the Wireless as OFF! I thought maybe this fiddled with the firmware somehow (just as my battery won't charge beyond 50% after I chose "long life" in the Energy Management utility on Windows even if I am running Linux, and as if I hibernate on windows and it turns my ethernet off then booting into Linux can't recognize the ethernet) ... but if so, turning it on on Windows should enable it in Linux as well ... but this didn't happen.

I don't know enough kernel/module-level twiddling to "stumble" on the fix, but given that the Launchpad reports said to *blacklist* the module, is rmmod which you have prescribed enough?

---

### Post by jamadagni on 2011-06-22
So I try toggling the Fn + F5 on Linux, and this is what happens:

```

$ rfkill list all
0: ideapad_wlan: Wireless LAN
        Soft blocked: no
        Hard blocked: no
1: ideapad_bluetooth: Bluetooth
        Soft blocked: no
        Hard blocked: no
2: hci0: Bluetooth
        Soft blocked: no
        Hard blocked: no
3: phy0: Wireless LAN
        Soft blocked: no
        Hard blocked: yes
$ rfkill list all
0: ideapad_wlan: Wireless LAN
        Soft blocked: yes
        Hard blocked: no
1: ideapad_bluetooth: Bluetooth
        Soft blocked: no
        Hard blocked: no
2: hci0: Bluetooth
        Soft blocked: no
        Hard blocked: no
3: phy0: Wireless LAN
        Soft blocked: yes
        Hard blocked: yes

```

The phy0 hard blocked status remains at yes. :(

This guy: [https://answers.launchpad.net/ubuntu/+source/gnome-nettool/+question/137718](https://answers.launchpad.net/ubuntu/+source/gnome-nettool/+question/137718) who had the same problem seems to have found some "light on his F12 key" but of course there is no such thing on my system.

This other guy: [https://answers.launchpad.net/ubuntu/+source/gnome-nettool/+question/159799](https://answers.launchpad.net/ubuntu/+source/gnome-nettool/+question/159799) has had no replies. sudo rfkill unblock all doesn't correct the phy0 hard block.

This one too without any productive answers: [http://forums.lenovo.com/t5/Linux-Discussion/Linux-wireless-driver/td-p/458913](http://forums.lenovo.com/t5/Linux-Discussion/Linux-wireless-driver/td-p/458913) 

Sheesh.

I am considering going back to Maverick.

---

### Post by chili555 on 2011-06-22
> is rmmod which you have prescribed enough?They are equivalent. Blacklist means don't load it. rmmod means, if it is loaded, remove it. I was going on the hunch that acer-wmi was needed, even momentarily, to enable the wireless but then it was safe to remove it to get rfkill to work. This guesswork comes from reading a lot of bug reports, for instance: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/668234](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/668234)

If the two variations I suggested above don't work, my next trial is a variant of the method in post #5 in the link I gave you.

It's bad; I am a Lenovo fan; I'm typing from a T60 now. My sister visited a few days ago and brought her perfectly operating Lenovo laptop running PCLinuxOS (hey, every family has a black sheep!) I dream about my next Thinkpad, but this is a negative in my deliberations.

---

### Post by chili555 on 2011-06-22
> I am considering going back to Maverick.If you run the live CD and the wireless and especially, the wireless button work as expected, that's exactly what I'd do. Maverick works just fine on another harddrive I have.

---

### Post by MeeMaw on 2011-06-22
> **chili555 said:**
> My sister visited a few days ago and brought her perfectly operating Lenovo laptop running PCLinuxOS (hey, every family has a black sheep!)

But it's **Linux**... 
 
Mine is a Lenovo G550, and yes, it works perfectly.

Thanks, chili555!
(from the black sheep...)

---

### Post by jamadagni on 2011-06-23
Hi -- thanks for your offer of trying further workarounds but I'm tired of trying kernel fixes -- I have to go back to my thesis work. So I guess Maverick it is. :( 

Thanks again for all your support! You guys are great! :)

---

### Post by jamadagni on 2011-06-24
Hello it's me again. So I installed Maverick (had space, could install) on my new Sandy Bridge laptop (Lenovo Ideapad Z570, same as on which I reported above problem) and I could connect to wireless!

rfkill list all lists 0: acer-wireless and 1: phy0. Crazy thing is that while phy0 lists both soft and hard block as NO, acer-wireless lists hardblock as NO but soft block as YES but the wireless still works. (I pinged another computer on the network -- I hope that's evidence enough that it works. I haven't tried NFS yet.) 

BTW on this Maverick the Fn + F5 doesn't cause any change in the output of rfkill unlike in Natty.

But since Maverick doesn't support Sandy Bridge, graphics are like real slow and I had to disable desktop effects to get a reasonably working system. Ah well, you win some you lose some.

Strange thing is, on my old Celeron 800 MHz Compaq Presario, I couldn't run productively on Maverick with desktop effects on, but that system now runs Natty with desktop effects (albeit not too many) and wireless works on that system.

Ah well.

---

### Post by jamadagni on 2011-06-24
OK guys so here's some good news. I tried installing an older kernel for Natty which I had downloaded from [here](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.37.6-natty/) while looking up [this bug](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/754777) (which I thankfully turned out NOT to have on my Sandy Bridge laptop).

So NOW the status is that the wireless is **no longer disabled** by hardware. But it *is* disabled by software. Here's the latest output of rkfill:

```

$ rfkill list all
0: ideapad_wlan: Wireless LAN
        Soft blocked: no
        Hard blocked: no
2: ideapad_bluetooth: Bluetooth
        Soft blocked: no
        Hard blocked: no
3: ideapad_killsw: Wireless LAN
        Soft blocked: yes
        Hard blocked: no
4: phy0: Wireless LAN
        Soft blocked: no
        Hard blocked: no
6: hci0: Bluetooth
        Soft blocked: no
        Hard blocked: no

```

Curiously, this time Fn + F5 doesn't change anything (as it did not do anything on Maverick as noted above).

Hovering over the NM icon in tray now says "Wireless disabled by software" where it previously said "Wireless disabled by hardware". The "Enable wireless" check box is no longer actually disabled, but if I click on it to check it, it automatically unchecks itself.

Then thinking I could try unloading the module as was done for Acer, I tried the following (and you can observe the results):

```

$ sudo modprobe ideapad_killsw
FATAL: Module ideapad_killsw not found.
$ lsmod | grep idea
ideapad_laptop          3976  0 

```

Any suggestions? I'm excited as I think I am very close to the solution (as I would definitely prefer Natty with Sandy Bridge graphics to Maverick without them). Please help. Chili?

---

### Post by chili555 on 2011-06-24
> Then thinking I could try unloading the module as was done for Acer, I tried the following (and you can observe the results):
```
$ sudo modprobe ideapad_killsw
FATAL: Module ideapad_killsw not found.
$ lsmod | grep idea
ideapad_laptop          3976  0

```
Any suggestions? I'm excited as I think I am very close to the solution (as I would definitely prefer Natty with Sandy Bridge graphics to Maverick without them). Please help. Chili?You might try removing *ideapad-laptop*:```
sudo rmmod -f ideapad-laptop
sudo rfkill unblock all
rfkill list all
```Also, may we see:```
modinfo ideapad-laptop
```Thanks.

---

### Post by jamadagni on 2011-06-25
Hey man, this is great! I've got wireless working now and I didn't even have to reboot or relogin! Just look at the following:

```

[samjnaa:~] sudo rmmod -f ideapad-laptop
[sudo] password for samjnaa: 

[samjnaa:~] sudo rfkill unblock all

[samjnaa:~] rfkill list all
4: phy1: Wireless LAN
        Soft blocked: no
        Hard blocked: no
5: hci0: Bluetooth
        Soft blocked: no
        Hard blocked: no

[samjnaa:~] modinfo ideapad-laptop
filename:       /lib/modules/2.6.37-02063706-generic/kernel/drivers/platform/x86/ideapad-laptop.ko
license:        GPL
description:    IdeaPad ACPI Extras
author:         David Woodhouse <dwmw2@infradead.org>
srcversion:     D327541D6995877E7CDD1EB
alias:          acpi*:VPC2004:*
depends:        
vermagic:       2.6.37-02063706-generic SMP mod_unload modversions 686 
parm:           no_bt_rfkill:No rfkill for bluetooth. (bool)

[samjnaa:~] ifconfig
eth0      Link encap:Ethernet  HWaddr f0:de:f1:4b:d5:a8  
          inet6 addr: fe80::f2de:f1ff:fe4b:d5a8/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:725 errors:0 dropped:0 overruns:0 frame:0
          TX packets:668 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:298609 (298.6 KB)  TX bytes:75980 (75.9 KB)
          Interrupt:41 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1150 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1150 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:89484 (89.4 KB)  TX bytes:89484 (89.4 KB)

wlan0     Link encap:Ethernet  HWaddr 68:a3:c4:4e:2f:a0  
          inet addr:192.168.1.6  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::6aa3:c4ff:fe4e:2fa0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:441 errors:0 dropped:0 overruns:0 frame:0
          TX packets:682 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:62124 (62.1 KB)  TX bytes:118094 (118.0 KB)

[samjnaa:~] ping 192.168.1.4
PING 192.168.1.4 (192.168.1.4) 56(84) bytes of data.
64 bytes from 192.168.1.4: icmp_req=1 ttl=64 time=6.97 ms
64 bytes from 192.168.1.4: icmp_req=2 ttl=64 time=2.04 ms
64 bytes from 192.168.1.4: icmp_req=3 ttl=64 time=1.99 ms
^C
--- 192.168.1.4 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2002ms
rtt min/avg/max/mdev = 1.996/3.672/6.975/2.335 ms

[samjnaa:~] sudo mount -t nfs 192.168.1.4:/home/samjnaa /mnt/temp

[samjnaa:~] touch /mnt/temp/foo

[samjnaa:~] :)
bash: syntax error near unexpected token `)'

```

Not sure what to do about that last syntax error there, though! :D

BTW as I previously reported for this kernel, Fn + F5 has no effect. Perhaps this kernel just doesn't recognize that sequence. Whatever.

Anyway thanks for all the handholding, Chili, you're truly great! :) Just tell me -- how to make this stick -- how do I edit my /etc/rc.local? Do I add an rmmod ideapad_laptop after the existing rmmod acer_wmi line? (Yeah I still have it.)

I'll try to check the intervening versions of kernel for Natty between abovementioned 2.6.37 version and default 2.6.38 version to find out where the break happened, but I won't be able to do that this week. 

BTW FWIW I tried out the 2.6.39-RC4 kernel (last one available in mainline for Natty) and apart from wireless still being disabled (as in the Natty default 2.6.38-8) it also caused my system to have freezes so I just avoided it. Anyway, the output of rfkill for that kernel was:

```

$ rfkill list all
1: ideapad_wlan: Wireless LAN
        Soft blocked: no
        Hard blocked: no
2: ideapad_bluetooth: Bluetooth
        Soft blocked: no
        Hard blocked: no
3: phy1: Wireless LAN
        Soft blocked: no
        Hard blocked: yes

```

One last thing. A weird behaviour now is that unless I switch off the hardware switch I am unable to disconnect from the wireless network by clicking on the red X near the connect in the KDE NM applet. If I disconnect it automatically immediately reconnects. Is that supposed to happen?

---

### Post by jamadagni on 2011-06-25
A correction to the above post is that I don't actually have to throw the hardware switch to stop the wireless from reconnecting -- it is enough if I uncheck the "Enable wireless" in the NM tray applet.

And about the Fn + F5 not having effect in the older kernel, I had actually reported it for Maverick, but it seems the effect continues till the 2.6.37~38 transition (but of course I have not checked the 2.6.38.x kernels other than Natty default).

Now the interesting thing is, I didn't have to do anything to make the thing stick. After once I enabled the wireless and connected to it, the next time I rebooted there are no blocks, soft or hard, and even in subsequent repeated reboots.

See:
```

[samjnaa:~] rfkill list all
1: ideapad_wlan: Wireless LAN
        Soft blocked: no
        Hard blocked: no
2: ideapad_bluetooth: Bluetooth
        Soft blocked: no
        Hard blocked: no
3: ideapad_killsw: Wireless LAN
        Soft blocked: no
        Hard blocked: no
4: hci0: Bluetooth
        Soft blocked: no
        Hard blocked: no
5: phy1: Wireless LAN
        Soft blocked: no
        Hard blocked: no

```

BTW I also tested whether I needed those lines in the rc.local to remove the Acer module with the older kernel as well, and it seems the answer is yes, because if this module is not removed, then it soft-blocks the wireless:

```

[samjnaa:~] rfkill list all
0: acer-wireless: Wireless LAN
        Soft blocked: yes
        Hard blocked: no
1: ideapad_wlan: Wireless LAN
        Soft blocked: no
        Hard blocked: no
2: ideapad_bluetooth: Bluetooth
        Soft blocked: no
        Hard blocked: no
3: ideapad_killsw: Wireless LAN
        Soft blocked: no
        Hard blocked: no
4: hci0: Bluetooth
        Soft blocked: no
        Hard blocked: no
5: phy0: Wireless LAN
        Soft blocked: no
        Hard blocked: no

```

But I still wonder whether the automatic re-connection to wireless as noted previously is correct behaviour. I mean, I am telling it to disconnect from wireless for a reason, right, I mean, because I want to disconnect. So why on earth is it automatically reconnecting?

---

### Post by chili555 on 2011-06-25
> But I still wonder whether the automatic re-connection to wireless as noted previously is correct behaviour. Not at all. I tried it on my two computers that run NM and if I command it to disconnect, it stays disconnected. I think it is a slight flaw in NM and I'd think there is a bug report somewhere you could add to. [https://bugs.launchpad.net/ubuntu/](https://bugs.launchpad.net/ubuntu/)> BTW as I previously reported for this kernel, Fn + F5 has no effect. That's what ideapad_laptop is supposed to do. That's what acer_wmi was supposed to do and they evidently conflict. I know there are several bug reports on that subject. It seems logical that the wmi that is supposed to translate the Fn key presses into useful information, "Turn on the wireless, Mr. Kernel," isn't working right and we remove it, the keys aren't going to do anything at all.

It's bad. I love Lenovo laptops; I'm typing from one right now. But the acer-wmi vs. ideapad_laptop vs. Natty issue is a mess. End rant.> After once I enabled the wireless and connected to it, the next time I rebooted there are no blocks, soft or hard, and even in subsequent repeated reboots.That is awesome! I am glad that persistence and patience finally cracked this case.> [samjnaa:~] :)
bash: syntax error near unexpected token `)'And that little gem caused me a great laugh. I shal remember it and trick some of my pals with it for many years to come. It replaces my old favorite:```

man woman
```Glad it's working!

---

### Post by jamadagni on 2011-06-25
> **chili555 said:**
> Not at all. I tried it on my two computers that run NM and if I command it to disconnect, it stays disconnected. I think it is a slight flaw in NM and I'd think there is a bug report somewhere you could add to. [https://bugs.launchpad.net/ubuntu/](https://bugs.launchpad.net/ubuntu/)

Hey man, how much do you think they'd like to receive a bug with a non-standard kernel installed? Especially when it is the non-standard kernel that has enabled the wireless!? If you say go ahead anyway, I'll go and report the bug, but I'm not sure myself.

> That's what ideapad_laptop is supposed to do. ... is supposed to translate the Fn key presses into useful information, "Turn on the wireless, Mr. Kernel," isn't working right and we remove it, the keys aren't going to do anything at all.

Well there's a big difference between using these keys on Windows and on Linux. Linux has the minus that there is no visual feedback as to the effect of the keypress, but the plus that the tray is not cluttered with icons (OneKey Theater, Energy Management, Hard Disk Management...) which aren't really all that meaningful to exist.

> That is awesome! I am glad that persistence and patience finally cracked this case.

Yeah, but it does seem a little strange that I didn't have to add an rmmod ideapad-laptop line to rc.local. Any thoughts on that?

> And that little gem caused me a great laugh. I shal remember it and trick some of my pals with it for many years to come. It replaces my old favorite:```

man woman
```

Oh -- it's indeed an honour to have my quip compared with **man woman**. I suppose typing **Bad command or file name** on the DOS prompt which returns the same text as result is old hat to you? LOL!

---

### Post by chili555 on 2011-06-25
> Hey man, how much do you think they'd like to receive a bug with a non-standard kernel installed? Especially when it is the non-standard kernel that has enabled the wireless!? If you say go ahead anyway, I'll go and report the bug, but I'm not sure myself.I'd post it; either they will investigate and fix a few things or they'll tell you to take your non-standard kernel and buzz off. No harm done.> it does seem a little strange that I didn't have to add an rmmod ideapad-laptop line to rc.local. Any thoughts on that?I have seen a few cases over the years that ought to work because everything is perfect and, inexplicably, it just doesn't work. I have also seen, as in your case, a few cases that shouldn't work by all that's Linux, but, inexplicably does. I don't fight momentum; I just smile and say, "Great! Glad it's working." Afterwards, I ask myself why, oh why is it working.

And, uhh...Great! Glad it's working.

---

### Post by hocke4me on 2011-06-25
This is what my info looks like.  I have a hp mini with an AR 9285 and can't get it to connect.  When  I change my router to no encryption it works just fine.   However, when i return it to WPA/ WPA2 personal it will not connect.  Been at it for hours.  I tried to get it to work.  Please help.  I am a newbie.  Maybe I am supposed to put in in a new post, but I hope I am really close to solving this.  I thought about ndiswrapper, but don't know how to get it installed.:(

Tet@et-HP-Mini-110-3000:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:21:cc:51:46:f8  
          inet addr:192.168.0.143  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::221:ccff:fe51:46f8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:217 errors:0 dropped:0 overruns:0 frame:0
          TX packets:50 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:19791 (19.7 KB)  TX bytes:10173 (10.1 KB)
          Interrupt:42 Base address:0x6000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:480 (480.0 B)  TX bytes:480 (480.0 B)

wlan0     Link encap:Ethernet  HWaddr 74:f0:6d:6b:90:7b  
          inet6 addr: fe80::76f0:6dff:fe6b:907b/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:34 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:8607 (8.6 KB)

et@et-HP-Mini-110-3000:~$ rfkill list all
0: hp-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
et@et-HP-Mini-110-3000:~$ his is what my info looks like.  Doesn't appear to be anything wrong.




> **jamadagni said:**
> A correction to the above post is that I don't actually have to throw the hardware switch to stop the wireless from reconnecting -- it is enough if I uncheck the "Enable wireless" in the NM tray applet.

And about the Fn + F5 not having effect in the older kernel, I had actually reported it for Maverick, but it seems the effect continues till the 2.6.37~38 transition (but of course I have not checked the 2.6.38.x kernels other than Natty default).

Now the interesting thing is, I didn't have to do anything to make the thing stick. After once I enabled the wireless and connected to it, the next time I rebooted there are no blocks, soft or hard, and even in subsequent repeated reboots.

See:
```

[samjnaa:~] rfkill list all
1: ideapad_wlan: Wireless LAN
        Soft blocked: no
        Hard blocked: no
2: ideapad_bluetooth: Bluetooth
        Soft blocked: no
        Hard blocked: no
3: ideapad_killsw: Wireless LAN
        Soft blocked: no
        Hard blocked: no
4: hci0: Bluetooth
        Soft blocked: no
        Hard blocked: no
5: phy1: Wireless LAN
        Soft blocked: no
        Hard blocked: no

```BTW I also tested whether I needed those lines in the rc.local to remove the Acer module with the older kernel as well, and it seems the answer is yes, because if this module is not removed, then it soft-blocks the wireless:

```

[samjnaa:~] rfkill list all
0: acer-wireless: Wireless LAN
        Soft blocked: yes
        Hard blocked: no
1: ideapad_wlan: Wireless LAN
        Soft blocked: no
        Hard blocked: no
2: ideapad_bluetooth: Bluetooth
        Soft blocked: no
        Hard blocked: no
3: ideapad_killsw: Wireless LAN
        Soft blocked: no
        Hard blocked: no
4: hci0: Bluetooth
        Soft blocked: no
        Hard blocked: no
5: phy0: Wireless LAN
        Soft blocked: no
        Hard blocked: no

```But I still wonder whether the automatic re-connection to wireless as noted previously is correct behaviour. I mean, I am telling it to disconnect from wireless for a reason, right, I mean, because I want to disconnect. So why on earth is it automatically reconnecting?

---

### Post by chili555 on 2011-06-25
> However, when i return it to WPA/ WPA2 personal it will not connect. Rather than the mixed mode WPA and WPA2, could you set your router to WPA2 only? Please see attached. Whether it is the driver or Network Manager or wpa_supplicant or what I don't know; mixed mode is often troublesome. Also be sure the ethernet cable is detached as you try to connect with wireless.

---

### Post by hocke4me on 2011-06-25
trying it now.  Went to WPA only and I am connected.  I will try a reboot and test it again

---

### Post by hocke4me on 2011-06-25
Changed wireless set up to WPA only and success.  Don't understand it, but it works now.  Someone more knowledgable than me should post this for resolution in a better spot.  Genious idea.   Thanks  [chili555:):):):):)]("http://ubuntuforums.org/member.php?u=35909")

5 stars

---

### Post by arpad on 2011-07-16
Just thought I'd thank you for getting wireless working on my little Acer Aspire with this:

```
modprobe acer-wmi
rfkill unblock all
rmmod -f acer-wmi
rfkill unblock 4
```

---

### Post by jamadagni on 2011-07-19
Hello chili and others! Apparently I can now get the wireless working with the latest Ubuntu kernel for Natty viz 2.6.38-10 but only with the rmmod hack. Please see updates at [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/780040/comments/31](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/780040/comments/31)

Incidentally now that I have loaded 2.6.38 series kernel, I am able to use the Ideapad Fn softkeys:

```

[samjnaa:~] rfkill list all
1: ideapad_wlan: Wireless LAN
        Soft blocked: yes
        Hard blocked: no
2: ideapad_bluetooth: Bluetooth
        Soft blocked: no
        Hard blocked: no
4: phy0: Wireless LAN
        Soft blocked: yes
        Hard blocked: no
5: hci0: Bluetooth
        Soft blocked: no
        Hard blocked: no
[samjnaa:~] rfkill list all
1: ideapad_wlan: Wireless LAN
        Soft blocked: no
        Hard blocked: no
2: ideapad_bluetooth: Bluetooth
        Soft blocked: no
        Hard blocked: no
4: phy0: Wireless LAN
        Soft blocked: no
        Hard blocked: no
5: hci0: Bluetooth
        Soft blocked: no
        Hard blocked: no

```

Thanks once more to Chili for all the handholding. I wouldn't have held on till the kernel people woke up if it hadn't been for chili! :) Thanks man!

---

### Post by jamadagni on 2011-07-27
Some more weirdness -- I did a separate Natty install and it seems upgrading to 2.6.38-10 alone is not enough to solve the problem. I once have to install the 2.6.37-6 mainline and *then* if I boot into 2.6.38-10 the wireless still stays up. Note comment at [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/780040/comments/34](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/780040/comments/34)

Weird...

---

