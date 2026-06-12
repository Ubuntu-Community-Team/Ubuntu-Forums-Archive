---
title: "RTL8188CE wireless card on Ideapad S100"
date: 2011-08-17
forum: Networking &amp; Wireless
---

### Post by UnixlyChallenged on 2011-08-17
I have installed Ubuntu 11.04 on a Lenovo Ideapad S100, with a Realtek RTL8188CE wireless network card.  I have installed the driver from Realtek, but the machine is not connecting to the wireless network.  The output of iwlist scan correctly identifies the wireless switches available to me.  lsmod does show rtl8192ce.  Any suggestions?  Thanks.

---

### Post by UnixlyChallenged on 2011-08-18
bump.

I have  since tried ndiswrapper too.  Anyone?

---

### Post by ray field on 2011-09-06
I wish I could offer help -- I wonder if you've solved this problem, and also I am very curious about your experience running Ubuntu on the S100 as I am thinking about buying it.

---

### Post by JohnFretwell on 2012-01-04
Hi

I have not used ubuntu yet but i have the same issue with RedHat that you have. I did use Fedora but that picked up the wireless card on my Lenovo s100 with no problems.

This does not help you of course but if i can fix the issue on RedHat then it may fix the issue you have also. I will post here if i fix it.


Regards
John

---

### Post by gatesdrovme2it on 2012-03-21
Any news on this?  I am having the dreaded "bad password" issue on my S100 with Ubuntu 11.10.  I have looked at a lot of threads regarding this issue but an too new to Linux to follow most of the workarounds.

---

### Post by ray field on 2012-03-22
> **gatesdrovme2it said:**
> Any news on this?  I am having the dreaded "bad password" issue on my S100 with Ubuntu 11.10.  I have looked at a lot of threads regarding this issue but an too new to Linux to follow most of the workarounds.

I have the S100 and it runs Lucid just fine (except for an occasional problem with the video driver on bootup, which a reboot always fixes).

unfortunately, I don't know how the wifi works, because I transferred the entire setup from an Asus netbook via Remastersys. I was very apprehensive about the wireless working, since I'm sure the Asus uses a different chip, but much to my astonishment (& pleasure) it worked as soon as I rebooted. 

I am not very technical but if someone tells me how to find out what driver is working I'm happy to report it here.

---

### Post by gatesdrovme2it on 2012-03-22
thanks for the response Ray.  do you know if you are using WICD or network manager?  i was having a lot of problems with network manager and i switched to WICD and it worked great for a while, but now i am having this bad password issue with my WPA2 router.

---

### Post by ray field on 2012-03-22
I use WICD, which has generally worked fine.

now I'm not completely sure this S100 has the RTL8188CE. running lshw -C network gives

```
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: 05
       serial: 50:af:73:12:69:b7
       size: 10MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10MB/s
       resources: irq:27 ioport:e000(size=256) memory:e0004000-e0004fff(prefetchable) memory:e0000000-e0003fff(prefetchable)
  *-network
       description: Wireless interface
       product: AR9285 Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 01
       serial: 90:a4:de:78:84:c6
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+netathw driverversion=1.55+,08/11/2009,7.7.0.377 ip=192.168.1.134 latency=0 link=yes multicast=yes wireless=IEEE 802.11g
       resources: irq:17 memory:fe900000-fe90ffff
```

---

### Post by gatesdrovme2it on 2012-03-22
mine says this:

  *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: 05
       serial: 50:af:73:14:b0:06
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl_nic/rtl8105e-1.fw ip=192.168.0.101 latency=0 multicast=yes port=MII speed=100Mbit/s
       resources: irq:42 ioport:e000(size=256) memory:e0004000-e0004fff memory:e0000000-e0003fff
  *-network
       description: Wireless interface
       product: RTL8188CE 802.11b/g/n WiFi Adapter
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 01
       serial: 00:1c:7b:9e:a2:f7
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl8192ce driverversion=3.0.0-16-generic firmware=N/A latency=0 multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 ioport:d000(size=256) memory:fe900000-fe903fff
WARNING: output may be incomplete or inaccurate, you should run this program as super-user.

---

### Post by ray field on 2012-03-22
well it looks like we've got different chipsets, so I can't help you. 

when you say

> I have looked at a lot of threads regarding this issue but an too new to Linux to follow most of the workarounds.

I can completely relate, since I've been a noob myself and still basically think of myself as pretty clueless. but believe me, it's always worth the effort!

---

### Post by UltimateCat on 2012-03-22
I had the same problem with the RTL8168 and until I blacklisted the 8169 I couldn't get online.

---

### Post by gatesdrovme2it on 2012-03-22
what does that mean UltimateCat?  is that what i need to do?  let's blacklist the whole #$%^ village if we have to, just make my wifi work!!!!  LOL

thanks for the moral support Ray!!!!  yeah, im completely new to Linux so this is twice as frustrating.  :)

---

### Post by chili555 on 2012-03-22
> **UltimateCat said:**
> I had the same problem with the RTL8168 and until I blacklisted the 8169 I couldn't get online.That's a wired ethernet driver; this thread is about wireless.> is that what i need to do? let's blacklist the whole #$%^ village if we have to, just make my wifi work!!!! LOLThat won't help.

Does your wireless scan?```
sudo iwlist wlan0 scan
```

---

### Post by gatesdrovme2it on 2012-03-23
Yeah, no problems scanning.  It always finds my network, but when I attempt to connect I get the "bad password" error.  There is info here on it:

[http://ubuntuforums.org/showthread.php?t=1675398](http://ubuntuforums.org/showthread.php?t=1675398)

there is more here:

[http://ubuntuforums.org/showthread.php?t=1595106&page=2](http://ubuntuforums.org/showthread.php?t=1595106&page=2)

Reading these threads doesn't help me because I am too new to Linux.  I believe I am running WICD 1.7; network manager was a nightmare for me so I switched to WICD.

Chili if you have any suggestions at all I would really appreciate it.  I have a feeling that like others I have run into this issue after an update.  For several weeks it was working fine with wireless after I switched to WICD.  But now my "bad password" error comes up 100% of the time so I am tethered to my ethernet cable which is really frustrating for a modern pc and modern operating system.

---

### Post by gatesdrovme2it on 2012-03-23
Anyone with an answer please feel free to jump in here.  I am not sure if I should switch back to network manager from WICD.  Anyone?

---

### Post by chili555 on 2012-03-23
Is your network set up as mixed WPA and WPA2? I believe either the driver or wpa_supplicant has difficulty with that. Can you change your router to WPA2 only?

---

### Post by gatesdrovme2it on 2012-03-23
I am leery of changing my router when other computers work fine with it.  Also since many other people mention this problem with WICD 1.7 and they seem to be using a different workaround I think I would rather not mess with the router.  I agree that it is the wpa_supplicant- others mention that.  It has to do, apparently, with the way WICD 1.7 stores the password.  

It's kind of rotten that the WICD people shut down their forum because of "advertising bots" instead of admitting that they don't know what is wrong with their software.  On the other hand, network manager created its own set of problems for me and I don't want those back either.

I am wondering if Ubuntu is really ready for the "mainstream"?  Like other people mentioned, there are not a lot of features in a modern operating system that are as important as wireless.  And in the couple of months that I have had Ubuntu on this machine I have posted many, many times asking for help and it is definitely not easy to find solutions.  

I appreciate those that have tried to help, but I think it is pretty plain that Ubuntu has major problems with wireless.

---

### Post by gatesdrovme2it on 2012-03-23
I would like to try the method here:

[http://www.pc-freak.net/blog/how-to-fix-wicd-1-7-0ds1-5-connection-failed-bad-password-on-ubuntu-10-10-maverick-merkaaat/](http://www.pc-freak.net/blog/how-to-fix-wicd-1-7-0ds1-5-connection-failed-bad-password-on-ubuntu-10-10-maverick-merkaaat/)

But I get errors if I try to execute those commands:

E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

---

### Post by chili555 on 2012-03-23
Only change the router if you actually want it to work, or at least see if it works.

I'm not at all sure it's the way Wicd stores the password. I think it is more likely an interaction between wpa_supplicant and the driver your wireless chipset uses. The driver, incidentally, is written by the chipset manufacturer, not Ubuntu. 

There are bug reporting mechanisms that seem to fix most issues and point fingers at the other guy for other issues. 

Ubuntu has a few issues; so does Windows (security, for a glaring example) and so does Mac. I can refer you to any number of whiner forums for any operating system extant.

You might see if this helps:```
sudo modprobe -r rtl8192ce
sudo modprobe rtl8192ce swenc=1
```Any improvement? If so, we can wite a quick .conf file and make it persistent.

Wireless is a tough one. If you need it and it works out of the box, as it does on both of my laptops, life is beautiful. If not...well, you know.

---

### Post by chili555 on 2012-03-23
> **gatesdrovme2it said:**
> I would like to try the method here:

[http://www.pc-freak.net/blog/how-to-fix-wicd-1-7-0ds1-5-connection-failed-bad-password-on-ubuntu-10-10-maverick-merkaaat/](http://www.pc-freak.net/blog/how-to-fix-wicd-1-7-0ds1-5-connection-failed-bad-password-on-ubuntu-10-10-maverick-merkaaat/)

But I get errors if I try to execute those commands:

E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?Did you preceed the commands with sudo?

---

### Post by gatesdrovme2it on 2012-03-23
Wow, it worked.  I'm on wireless now for the first time in several days.  Viva la Chili555!!!  I'm not worthy!!!  :)

What do those two little bits of code do, and I am your willing servant if you want to make a .conf file.  Just keep in mind I'm totally new to Linux.  And the last time I used DOS was many moons ago!  Pointing and clicking in Windows made me soft.

Thanks, man.  Your help is very much appreciated.

---

### Post by chili555 on 2012-03-23
> What do those two little bits of code do,They ask the driver to use software, in this case, wpa_supplicant, to handle encryption. Otherwise it would be handled in hardware; all those tiny transistors on the physical chip. In many cases, one works better than the other and so many wireless drivers give us the option to choose. Check:```
modinfo rtl8192ce
```> filename:       /lib/modules/3.0.0-16-generic/updates/cw-3.2/rtl8192ce.ko
firmware:       rtlwifi/rtl8192cfwU_B.bin
firmware:       rtlwifi/rtl8192cfwU.bin
firmware:       rtlwifi/rtl8192cfw.bin
description:    Realtek 8192C/8188C 802.11n PCI wireless
license:        GPL
author:         Larry Finger	<Larry.Finger@lwfinger.net>
author:         Realtek WlanFAE	<wlanfae@realtek.com>
author:         lizhaoming	<chaoming_li@realsil.com.cn>
srcversion:     B0FFAF1582CCC278600E21F
<snip>
vermagic:       3.0.0-16-generic SMP mod_unload modversions 686 
[COLOR="Red"]parm:           swenc:Set to 1 for software crypto (default 0)
 (bool)[/COLOR]
parm:           ips:Set to 0 to not use link power save (default 1)
 (bool)
parm:           swlps:Set to 1 to use SW control power save (default 0)
 (bool)
parm:           fwlps:Set to 1 to use FW control power save (default 1)
 (bool)
parm:           debug:Set debug level (0-5) (default 0) (int)It's always worth a shot to try software encryption if it's defaulted to hardware and vice-versa. 

Let's get the driver to use the parameter always:```
sudo gedit /etc/modprobe.d/rtl8192ce.conf
```A new empty file will open. Type in one line:```
options rtl8192ce swenc=1
```Proofread, save and close gedit.

If you don't have the text editor gedit, use nano or any other text editor. Now the parameter load with rtl8192ce automagically.

I'm glad it's fixed! Have fun.

---

### Post by gatesdrovme2it on 2012-03-24
I made the file as you directed.  That was very easy to follow- thank you!!!!!

I will do some testing and see if everything is running smoothly now.  Thanks again so much for helping!  I was going crazy with that issue!!!

---

### Post by chili555 on 2012-03-24
I was very happy to help. I enjoy solving the mystery and I enjoy reading follow-up posts, sometimes years later, reporting that the fix worked for others, too.

I'm glad it's working. Post back if we can help you further.

---

### Post by white_hat on 2012-03-26
Had the same problem on HP 4330s and 12.04 and only your advice solved it!!!! THANK YOU!! :roll:\\:D/

---

### Post by gatesdrovme2it on 2012-04-05
Chili!  It came back!  I have no wireless at all now.  Even if I restart, I get the bad password error.

---

### Post by chili555 on 2012-04-05
Let's look at a few diagnostics:```
cat /etc/modprobe.d/rtl8192ce.conf
dmesg | grep 8192
sudo cat /var/log/syslog | grep -e etwork -e wlan | tail -n20
```Thanks.

---

### Post by gatesdrovme2it on 2012-04-05
Wow that was quick!  :)

options rtl8192ce swenc=1

and...

[   30.292035] rtl8192c: Loading firmware file rtlwifi/rtl8192cfw.bin
[   32.591073] rtl8192c: Loading firmware file rtlwifi/rtl8192cfw.bin
[   33.888946] rtl8192c: Loading firmware file rtlwifi/rtl8192cfw.bin
[   36.501253] rtl8192c: Loading firmware file rtlwifi/rtl8192cfw.bin
[ 1913.045730] rtl8192c: Loading firmware file rtlwifi/rtl8192cfw.bin
[ 1917.126064] rtl8192c: Loading firmware file rtlwifi/rtl8192cfw.bin
[ 2019.896613] rtl8192c: Loading firmware file rtlwifi/rtl8192cfw.bin
[ 2023.076989] rtl8192c: Loading firmware file rtlwifi/rtl8192cfw.bin
[ 3282.703059] rtl8192c: Loading firmware file rtlwifi/rtl8192cfw.bin
[ 3339.535446] rtl8192c: Loading firmware file rtlwifi/rtl8192cfw.bin
[ 3379.723990] rtl8192c: Loading firmware file rtlwifi/rtl8192cfw.bin
[ 3393.139263] rtl8192c: Loading firmware file rtlwifi/rtl8192cfw.bin
[21049.922593] rtl8192c: Loading firmware file rtlwifi/rtl8192cfw.bin
[21142.906616] rtl8192c: Loading firmware file rtlwifi/rtl8192cfw.bin
[87982.011721] rtl8192c: Loading firmware file rtlwifi/rtl8192cfw.bin
[88002.433394] rtl8192c: Loading firmware file rtlwifi/rtl8192cfw.bin
[88003.982840] rtl8192c: Loading firmware file rtlwifi/rtl8192cfw.bin
[88009.095458] rtl8192c: Loading firmware file rtlwifi/rtl8192cfw.bin
[88012.523525] rtl8192c: Loading firmware file rtlwifi/rtl8192cfw.bin
[88018.715630] rtl8192c: Loading firmware file rtlwifi/rtl8192cfw.bin
[88024.907995] rtl8192c: Loading firmware file rtlwifi/rtl8192cfw.bin
[88031.104068] rtl8192c: Loading firmware file rtlwifi/rtl8192cfw.bin
[88037.292336] rtl8192c: Loading firmware file rtlwifi/rtl8192cfw.bin
[88043.480140] rtl8192c: Loading firmware file rtlwifi/rtl8192cfw.bin
[88049.668109] rtl8192c: Loading firmware file rtlwifi/rtl8192cfw.bin
[88050.485445] rtl8192c: Loading firmware file rtlwifi/rtl8192cfw.bin
[88050.924025] rtl8192c: Loading firmware file rtlwifi/rtl8192cfw.bin
[88066.117673] rtl8192c: Loading firmware file rtlwifi/rtl8192cfw.bin
[88068.325568] rtl8192c: Loading firmware file rtlwifi/rtl8192cfw.bin
[88069.916156] rtl8192c: Loading firmware file rtlwifi/rtl8192cfw.bin
[88072.487887] rtl8192c: Loading firmware file rtlwifi/rtl8192cfw.bin
[88075.891766] rtl8192c: Loading firmware file rtlwifi/rtl8192cfw.bin
[88082.083649] rtl8192c: Loading firmware file rtlwifi/rtl8192cfw.bin
[88088.272002] rtl8192c: Loading firmware file rtlwifi/rtl8192cfw.bin
[88094.467793] rtl8192c: Loading firmware file rtlwifi/rtl8192cfw.bin
[88100.667989] rtl8192c: Loading firmware file rtlwifi/rtl8192cfw.bin
[88106.860199] rtl8192c: Loading firmware file rtlwifi/rtl8192cfw.bin
[88113.056020] rtl8192c: Loading firmware file rtlwifi/rtl8192cfw.bin
[88116.092026] rtl8192c: Loading firmware file rtlwifi/rtl8192cfw.bin
[88118.351453] rtl8192c: Loading firmware file rtlwifi/rtl8192cfw.bin
[88119.837475] rtl8192c: Loading firmware file rtlwifi/rtl8192cfw.bin
[88120.811330] rtl8192c: Loading firmware file rtlwifi/rtl8192cfw.bin
[88122.404511] rtl8192c: Loading firmware file rtlwifi/rtl8192cfw.bin
[88132.908206] rtl8192c: Loading firmware file rtlwifi/rtl8192cfw.bin
[88139.099780] rtl8192c: Loading firmware file rtlwifi/rtl8192cfw.bin
[88145.295955] rtl8192c: Loading firmware file rtlwifi/rtl8192cfw.bin
[88151.492041] rtl8192c: Loading firmware file rtlwifi/rtl8192cfw.bin
[88157.684112] rtl8192c: Loading firmware file rtlwifi/rtl8192cfw.bin
[88162.108027] rtl8192c: Loading firmware file rtlwifi/rtl8192cfw.bin
[88164.434062] rtl8192c: Loading firmware file rtlwifi/rtl8192cfw.bin
[88164.879144] rtl8192c: Loading firmware file rtlwifi/rtl8192cfw.bin
[88166.131725] rtl8192c: Loading firmware file rtlwifi/rtl8192cfw.bin
[88167.179655] rtl8192c: Loading firmware file rtlwifi/rtl8192cfw.bin
[88168.728025] rtl8192c: Loading firmware file rtlwifi/rtl8192cfw.bin
[88179.224019] rtl8192c: Loading firmware file rtlwifi/rtl8192cfw.bin
[88185.427580] rtl8192c: Loading firmware file rtlwifi/rtl8192cfw.bin
[88191.615857] rtl8192c: Loading firmware file rtlwifi/rtl8192cfw.bin
[88197.811730] rtl8192c: Loading firmware file rtlwifi/rtl8192cfw.bin
[88204.005213] rtl8192c: Loading firmware file rtlwifi/rtl8192cfw.bin
[88210.084023] rtl8192c: Loading firmware file rtlwifi/rtl8192cfw.bin
[88212.205333] rtl8192c: Loading firmware file rtlwifi/rtl8192cfw.bin
[88213.476942] rtl8192c: Loading firmware file rtlwifi/rtl8192cfw.bin
[88214.611590] rtl8192c: Loading firmware file rtlwifi/rtl8192cfw.bin
[88216.056024] rtl8192c: Loading firmware file rtlwifi/rtl8192cfw.bin
[88226.559797] rtl8192c: Loading firmware file rtlwifi/rtl8192cfw.bin
[88232.751841] rtl8192c: Loading firmware file rtlwifi/rtl8192cfw.bin
[88238.951908] rtl8192c: Loading firmware file rtlwifi/rtl8192cfw.bin
[88245.144412] rtl8192c: Loading firmware file rtlwifi/rtl8192cfw.bin
[88251.336180] rtl8192c: Loading firmware file rtlwifi/rtl8192cfw.bin
[88256.541021] rtl8192c: Loading firmware file rtlwifi/rtl8192cfw.bin
[88411.093222] rtl8192c: Loading firmware file rtlwifi/rtl8192cfw.bin
[88413.252761] rtl8192c: Loading firmware file rtlwifi/rtl8192cfw.bin
[88414.665467] rtl8192c: Loading firmware file rtlwifi/rtl8192cfw.bin
[88417.188030] rtl8192c: Loading firmware file rtlwifi/rtl8192cfw.bin
[88420.576299] rtl8192c: Loading firmware file rtlwifi/rtl8192cfw.bin
[88426.768695] rtl8192c: Loading firmware file rtlwifi/rtl8192cfw.bin
[88432.960834] rtl8192c: Loading firmware file rtlwifi/rtl8192cfw.bin
[88439.160718] rtl8192c: Loading firmware file rtlwifi/rtl8192cfw.bin
[88445.356452] rtl8192c: Loading firmware file rtlwifi/rtl8192cfw.bin
[88451.548426] rtl8192c: Loading firmware file rtlwifi/rtl8192cfw.bin
[88457.740186] rtl8192c: Loading firmware file rtlwifi/rtl8192cfw.bin
[88461.505801] rtl8192c: Loading firmware file rtlwifi/rtl8192cfw.bin
[88461.956061] rtl8192c: Loading firmware file rtlwifi/rtl8192cfw.bin
[88605.993269] rtl8192c: Loading firmware file rtlwifi/rtl8192cfw.bin
[88622.752495] rtl8192c: Loading firmware file rtlwifi/rtl8192cfw.bin
[138185.022080] rtl8192c: Loading firmware file rtlwifi/rtl8192cfw.bin
[169532.167200] rtl8192c: Loading firmware file rtlwifi/rtl8192cfw.bin
[174389.285100] rtl8192c: Loading firmware file rtlwifi/rtl8192cfw.bin
[174390.680841] rtl8192c: Loading firmware file rtlwifi/rtl8192cfw.bin
[174393.688022] rtl8192c: Loading firmware file rtlwifi/rtl8192cfw.bin
[174397.112359] rtl8192c: Loading firmware file rtlwifi/rtl8192cfw.bin
[174403.315824] rtl8192c: Loading firmware file rtlwifi/rtl8192cfw.bin
[174409.511964] rtl8192c: Loading firmware file rtlwifi/rtl8192cfw.bin
[174415.703948] rtl8192c: Loading firmware file rtlwifi/rtl8192cfw.bin
[174421.897782] rtl8192c: Loading firmware file rtlwifi/rtl8192cfw.bin
[174428.089027] rtl8192c: Loading firmware file rtlwifi/rtl8192cfw.bin
[174434.280029] rtl8192c: Loading firmware file rtlwifi/rtl8192cfw.bin
[174435.205386] rtl8192c: Loading firmware file rtlwifi/rtl8192cfw.bin
[174624.711898] rtl8192c: Loading firmware file rtlwifi/rtl8192cfw.bin
[174625.156587] rtl8192c: Loading firmware file rtlwifi/rtl8192cfw.bin
[174626.681407] rtl8192c: Loading firmware file rtlwifi/rtl8192cfw.bin
[174629.260024] rtl8192c: Loading firmware file rtlwifi/rtl8192cfw.bin
[174632.655590] rtl8192c: Loading firmware file rtlwifi/rtl8192cfw.bin
[174638.852550] rtl8192c: Loading firmware file rtlwifi/rtl8192cfw.bin
[174645.048648] rtl8192c: Loading firmware file rtlwifi/rtl8192cfw.bin
[174651.240585] rtl8192c: Loading firmware file rtlwifi/rtl8192cfw.bin
[174657.440712] rtl8192c: Loading firmware file rtlwifi/rtl8192cfw.bin
[174663.632700] rtl8192c: Loading firmware file rtlwifi/rtl8192cfw.bin
[174669.824204] rtl8192c: Loading firmware file rtlwifi/rtl8192cfw.bin
[174670.599195] rtl8192c: Loading firmware file rtlwifi/rtl8192cfw.bin
[174671.044042] rtl8192c: Loading firmware file rtlwifi/rtl8192cfw.bin
[174834.090290] rtl8192c: Loading firmware file rtlwifi/rtl8192cfw.bin
[174836.251250] rtl8192c: Loading firmware file rtlwifi/rtl8192cfw.bin
[174837.680676] rtl8192c: Loading firmware file rtlwifi/rtl8192cfw.bin
[174840.235767] rtl8192c: Loading firmware file rtlwifi/rtl8192cfw.bin
[174843.634661] rtl8192c: Loading firmware file rtlwifi/rtl8192cfw.bin
[174849.836019] rtl8192c: Loading firmware file rtlwifi/rtl8192cfw.bin
[174856.028274] rtl8192c: Loading firmware file rtlwifi/rtl8192cfw.bin
[174862.220275] rtl8192c: Loading firmware file rtlwifi/rtl8192cfw.bin
[174868.412407] rtl8192c: Loading firmware file rtlwifi/rtl8192cfw.bin
[174874.604579] rtl8192c: Loading firmware file rtlwifi/rtl8192cfw.bin
[174880.800272] rtl8192c: Loading firmware file rtlwifi/rtl8192cfw.bin
[174884.103537] rtl8192c: Loading firmware file rtlwifi/rtl8192cfw.bin
[174886.255383] rtl8192c: Loading firmware file rtlwifi/rtl8192cfw.bin
[174887.652815] rtl8192c: Loading firmware file rtlwifi/rtl8192cfw.bin
[174888.879260] rtl8192c: Loading firmware file rtlwifi/rtl8192cfw.bin
[174890.256018] rtl8192c: Loading firmware file rtlwifi/rtl8192cfw.bin
[175105.778975] rtl8192c: Loading firmware file rtlwifi/rtl8192cfw.bin
[175106.505873] rtl8192c: Loading firmware file rtlwifi/rtl8192cfw.bin
[175106.887158] rtl8192c: Loading firmware file rtlwifi/rtl8192cfw.bin
[175110.019111] rtl8192c: Loading firmware file rtlwifi/rtl8192cfw.bin
[175132.177307] rtl8192c: Loading firmware file rtlwifi/rtl8192cfw.bin
[177506.894788] rtl8192c: Loading firmware file rtlwifi/rtl8192cfw.bin
[177519.482330] rtl8192c: Loading firmware file rtlwifi/rtl8192cfw.bin
[177521.034631] rtl8192c: Loading firmware file rtlwifi/rtl8192cfw.bin
[177524.347670] rtl8192ce 0000:02:00.0: PCI INT A disabled
[177525.560556] rtl8192ce 0000:02:00.0: restoring config space at offset 0xf (was 0x1ff, writing 0x10a)
[177525.560585] rtl8192ce 0000:02:00.0: restoring config space at offset 0x6 (was 0x4, writing 0xfe900004)
[177525.560597] rtl8192ce 0000:02:00.0: restoring config space at offset 0x4 (was 0x1, writing 0xd001)
[177525.560608] rtl8192ce 0000:02:00.0: restoring config space at offset 0x3 (was 0x0, writing 0x10)
[177525.560621] rtl8192ce 0000:02:00.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100007)
[177525.562281] rtl8192ce 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[177527.788127] rtl8192c: Loading firmware file rtlwifi/rtl8192cfw.bin
[177536.969321] rtl8192c: Loading firmware file rtlwifi/rtl8192cfw.bin
[178044.309718] rtl8192c: Loading firmware file rtlwifi/rtl8192cfw.bin
[178045.814664] rtl8192c: Loading firmware file rtlwifi/rtl8192cfw.bin
[178048.927315] rtl8192ce 0000:02:00.0: PCI INT A disabled
[178050.304561] rtl8192ce 0000:02:00.0: restoring config space at offset 0xf (was 0x1ff, writing 0x10a)
[178050.304589] rtl8192ce 0000:02:00.0: restoring config space at offset 0x6 (was 0x4, writing 0xfe900004)
[178050.304602] rtl8192ce 0000:02:00.0: restoring config space at offset 0x4 (was 0x1, writing 0xd001)
[178050.304612] rtl8192ce 0000:02:00.0: restoring config space at offset 0x3 (was 0x0, writing 0x10)
[178050.304625] rtl8192ce 0000:02:00.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100007)
[178050.306307] rtl8192ce 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[178052.585282] rtl8192c: Loading firmware file rtlwifi/rtl8192cfw.bin
[178059.416926] rtl8192c: Loading firmware file rtlwifi/rtl8192cfw.bin
[178242.372609] rtl8192c: Loading firmware file rtlwifi/rtl8192cfw.bin
[178246.442628] rtl8192c: Loading firmware file rtlwifi/rtl8192cfw.bin


and...

[FONT=monospace]The last line of code (sudo cat /var/log/syslog | grep -e etwork -e wlan | tail -n20) returns nothing.  Is that normal?[/FONT]

---

### Post by chili555 on 2012-04-05
> The last line of code (sudo cat /var/log/syslog | grep -e etwork -e wlan | tail -n20) returns nothing. Is that normal?Periodically, the file gets archived and a new file started. If you query right after, you get nothing. Let's look at the previous:```
sudo cat /var/log/syslog[COLOR="Red"].1[/COLOR] | grep -e etwork -e wlan | tail -n20
```> [ 3339.535446] rtl8192c: Loading firmware file rtlwifi/rtl8192cfw.bin
[ 3379.723990] rtl8192c: Loading firmware file rtlwifi/rtl8192cfw.bin
[ 3393.139263] rtl8192c: Loading firmware file rtlwifi/rtl8192cfw.binVery wierd! It almost sounds like the driver is dropping out and reloading continuously. Let's look at the firmware:```
md5sum /lib/firmware/rtlwifi/rtl8192cfw.bin
```We hope we see:```
$ md5sum /lib/firmware/rtlwifi/rtl8192cfw.bin
[COLOR="Red"]748944fbffd3b08b5b1929bb6c7fc537[/COLOR]  /lib/firmware/rtlwifi/rtl8192cfw.bin
```If not, perhaps the firmware file is somehow corrupt; we'll replace it. Let's also see:```
modinfo rtl8192ce | grep firmware
```

---

### Post by gatesdrovme2it on 2012-04-05
OK, that gives me something:

Apr  4 15:17:17 david-Ideapad-S100 dhclient: send_packet: Network is unreachable
Apr  4 15:17:17 david-Ideapad-S100 dhclient: Listening on LPF/wlan0/00:1c:7b:9e:a2:f7
Apr  4 15:17:17 david-Ideapad-S100 dhclient: Sending on   LPF/wlan0/00:1c:7b:9e:a2:f7
Apr  4 15:17:18 david-Ideapad-S100 dhclient: DHCPRELEASE on wlan0 to 192.168.0.1 port 67
Apr  4 15:17:18 david-Ideapad-S100 dhclient: send_packet: Network is unreachable
Apr  4 15:17:18 david-Ideapad-S100 kernel: [178046.154267] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Apr  4 15:17:18 david-Ideapad-S100 dhclient: send_packet: Network is unreachable
Apr  4 17:44:04 david-Ideapad-S100 dhclient: Listening on LPF/wlan0/00:1c:7b:9e:a2:f7
Apr  4 17:44:04 david-Ideapad-S100 dhclient: Sending on   LPF/wlan0/00:1c:7b:9e:a2:f7
Apr  4 17:44:05 david-Ideapad-S100 dhclient: DHCPRELEASE on wlan0 to 192.168.0.1 port 67
Apr  4 17:44:05 david-Ideapad-S100 dhclient: send_packet: Network is unreachable
Apr  4 17:44:06 david-Ideapad-S100 kernel: [178059.756454] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Apr  4 17:44:06 david-Ideapad-S100 dhclient: send_packet: Network is unreachable
Apr  4 17:47:12 david-Ideapad-S100 dhclient: Listening on LPF/wlan0/00:1c:7b:9e:a2:f7
Apr  4 17:47:12 david-Ideapad-S100 dhclient: Sending on   LPF/wlan0/00:1c:7b:9e:a2:f7
Apr  4 17:47:12 david-Ideapad-S100 dhclient: DHCPRELEASE on wlan0 to 192.168.0.1 port 67
Apr  4 17:47:12 david-Ideapad-S100 dhclient: send_packet: Network is unreachable
Apr  4 17:47:13 david-Ideapad-S100 kernel: [178246.782081] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Apr  4 17:47:13 david-Ideapad-S100 dhclient: send_packet: Network is unreachable
Apr  4 17:47:14 david-Ideapad-S100 dhclient: send_packet: Network is unreachable


and


748944fbffd3b08b5b1929bb6c7fc537  /lib/firmware/rtlwifi/rtl8192cfw.bin

[COLOR=Red]748944fbffd3b08b5b1929bb6c7fc537[/COLOR]
yes, that looks like a match!  

and...

firmware:       rtlwifi/rtl8192cfw.bin


It's funny about my wifi dropping out continuously because with Transmission I would always see it go to zero, then download normally, then zero again over and over again.  I just changed to qbittorent and now it seems to be acting normally, but I wonder if it is just masking the problem.  

Thanks for being so smart and helpful Chili!  :)

---

### Post by chili555 on 2012-04-05
> Apr 4 17:44:05 david-Ideapad-S100 dhclient: send_packet: Network is unreachable
Apr 4 17:44:06 david-Ideapad-S100 kernel: [178059.756454] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Apr 4 17:44:06 david-Ideapad-S100 dhclient: send_packet: Network is unreachableHmmm. May we check again?```
rfkill list all
```Strange...

---

### Post by gatesdrovme2it on 2012-04-06
0: ideapad_wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: ideapad_bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
3: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
5: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

Tricky, huh?

---

### Post by chili555 on 2012-04-06
Very tricky.> I believe I am running WICD 1.7; network manager was a nightmare for me so I switched to WICD.Did you completely remove Network Manager? Would you please let me check your kernel messages? Please reboot and do:```
dmesg > me2it.txt
lsmod >> me2it.txt
zip me2it.zip me2it.txt
```Find the file me2it.zip in your user directory and attach it to your reply using the paperclip tool at the top of the reply box. I am fascinated to hopefully discover what's going wrong.

---

### Post by gatesdrovme2it on 2012-04-06
Yeah I find all of this fascinating too.  Hahhahahhaa NOT.  :)

Thanks a bunch for your help Chili I would be lost without you. :KS

---

### Post by chili555 on 2012-04-06
I have reviewed your dmesg extensively. I see a few warnings that seem unrelated to wireless or rtl8192ce but nothing at all alarming that points to a fix we might try. There is a newer driver here:```
sudo apt-get install linux-backports-modules-cw-3.1-oneiric-generic
```You might try it and reboot and let us have a report.

I am low on ideas...

---

### Post by gatesdrovme2it on 2012-04-07
Thanks for the code to install the new driver- I got that done, and rebooted, but still "bad password".  Also often when I reboot my pointer freezes and I have to log out, then log back in to get it un-frozen.  I don't know if this is related to the password problem but I doubt it.  Another problem I have had continuously is with update manager- it always gives me an error when I try to update.  Communication problems.  This is true whether I am on wireless or wired.  

When I use synaptic package manager and hit "reload" I get a communication error as well.  That is also whether I am wired or wireless.  It says this:

Failed to fetch [http://ppa.launchpad.net/bisigi/ppa/ubuntu/dists/oneiric/main/source/Sources](http://ppa.launchpad.net/bisigi/ppa/ubuntu/dists/oneiric/main/source/Sources)  404  Not Found
Failed to fetch [http://ppa.launchpad.net/bisigi/ppa/ubuntu/dists/oneiric/main/binary-i386/Packages](http://ppa.launchpad.net/bisigi/ppa/ubuntu/dists/oneiric/main/binary-i386/Packages)  404  Not Found
Some index files failed to download. They have been ignored, or old ones used instead.

Do you think I should ditch Wicd and go back to network manager?

---

### Post by chili555 on 2012-04-07
> When I use synaptic package manager and hit "reload" I get a communication error as well. That is also whether I am wired or wireless. It says this:

Failed to fetch [http://ppa.launchpad.net/[COLOR="Red"]bisigi[/COLOR]/ppa/...source/Sources](http://ppa.launchpad.net/[COLOR="Red"]bisigi[/COLOR]/ppa/...source/Sources) 404 Not Found
Failed to fetch [http://ppa.launchpad.net/[COLOR="Red"]bisigi[/COLOR]/ppa/...-i386/Packages](http://ppa.launchpad.net/[COLOR="Red"]bisigi[/COLOR]/ppa/...-i386/Packages) 404 Not Found
Some index files failed to download. They have been ignored, or old ones used instead.That's simply because the bisigi ppa is defunct or moved or simply doesn't exist for Oneiric. Attached is what I get on my perfectly running system. I think you need to go into Software Sources and uncheck (disable) that ppa. If it is for a software package you need, search for it and find out where the ppa has moved to.> Do you think I should ditch Wicd and go back to network manager? Did you completely remove NM when you installed Wicd?```
ps aux | grep etwork
```

---

### Post by johnathansmith on 2012-06-10
If somebody using Ubuntu 10.04.4 try unistall Network Manager and then install again from Ubuntu software resources. Working quite good on 128bit WEP. No random disconection.

---

