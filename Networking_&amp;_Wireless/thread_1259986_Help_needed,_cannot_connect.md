---
title: "Help needed, cannot connect"
date: 2009-09-07
forum: Networking &amp; Wireless
---

### Post by ukozok on 2009-09-07
Today's my first day using Ubuntu. Installation went smoothly and I set up my wireless network and everything worked. Then I was prompted to download the most recent software update and after that I was unable to connect to my wireless networks. I can connect by Ethernet though. 
I went through the troubleshooting section and it was suggested that the modem is not on, which it is - I have three other computers that all connect fine (Windows and Macs).

Needless to say that networking and wireless are enabled. Whet I normally can see.n I click on the network manager it doesn't list any networks at all as in fact there are at least 10 that I normally can see. Anyone able to assist?

This is the result of the terminal query:

aike@aike-laptop:~$ sudo lshw -C network
[sudo] password for aike: 
  *-network               
       description: Wireless interface
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: eth1
       version: 01
       serial: 00:22:5f:f2:f3:52
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl1 driverversion=5.10.79.10 latency=0 module=wl multicast=yes wireless=IEEE 802.11bg
  *-network
       description: Ethernet interface
       product: 88E8040 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 13
       serial: 00:25:64:56:4c:b3
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.22 duplex=full firmware=N/A ip=192.168.200.95 latency=0 link=yes module=sky2 multicast=yes port=twisted pair speed=100MB/s
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: fa:64:1a:34:c5:9c
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
aike@aike-laptop:~$ 
aike@aike-laptop:~$

---

### Post by hal10000 on 2009-09-07
A silly question: Did you reboot after installing the latest software updates?

Post the outputs of the following commands:
1.) [COLOR="Red"]lsmod | grep bcm[/COLOR]
2.) [COLOR="Red"]iwconfig[/COLOR]
3.) [COLOR="Red"]ifconfig[/COLOR]
4.) [COLOR="Red"]cat /etc/network/interfaces[/COLOR]

---

### Post by ukozok on 2009-09-08
> **hal10000 said:**
> A silly question: Did you reboot after installing the latest software updates?

Post the outputs of the following commands:
1.) [COLOR="Red"]lsmod | grep bcm[/COLOR]
2.) [COLOR="Red"]iwconfig[/COLOR]
3.) [COLOR="Red"]ifconfig[/COLOR]
4.) [COLOR="Red"]cat /etc/network/interfaces[/COLOR]
Vielen Dank! 
Yes, rebooted many times. Terminal did not recognise the lsmod | grep bcm command, but all the other, which are here:

iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

eth1      IEEE 802.11  Nickname:""
          Access Point: Not-Associated   
          Link Quality:5  Signal level:0  Noise level:0
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0

aike@aike-laptop:~$ 
aike@aike-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:25:64:56:4c:b3  
          inet6 addr: fe80::225:64ff:fe56:4cb3/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:12097 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5961 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:7951946 (7.9 MB)  TX bytes:926471 (926.4 KB)
          Interrupt:18 

eth1      Link encap:Ethernet  HWaddr 00:22:5f:f2:f3:52  
          inet6 addr: fe80::222:5fff:fef2:f352/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:196 errors:0 dropped:0 overruns:0 frame:0
          TX packets:196 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:15228 (15.2 KB)  TX bytes:15228 (15.2 KB)

aike@aike-laptop:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

aike@aike-laptop:~$ lsmod
Module                  Size  Used by
nls_iso8859_1          13440  1 
nls_cp437              15104  1 
vfat                   21120  1 
fat                    65592  1 vfat
i915                   75272  2 
drm                   123232  3 i915
binfmt_misc            18572  1 
ppdev                  16904  0 
bridge                 63904  0 
stp                    11140  1 bridge
bnep                   22912  2 
input_polldev          12688  0 
joydev                 20864  0 
lp                     19588  0 
parport                49584  2 ppdev,lp
snd_hda_intel         557364  3 
snd_pcm_oss            52352  0 
snd_mixer_oss          24960  1 snd_pcm_oss
snd_pcm                99336  2 snd_hda_intel,snd_pcm_oss
snd_seq_dummy          11524  0 
snd_seq_oss            41984  0 
snd_seq_midi           15744  0 
snd_rawmidi            33920  1 snd_seq_midi
snd_seq_midi_event     16512  2 snd_seq_oss,snd_seq_midi
snd_seq                66272  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              34064  2 snd_pcm,snd_seq
snd_seq_device         16276  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
uvcvideo               69512  0 
snd                    78792  15 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
ieee80211_crypt_tkip    17920  0 
soundcore              16800  1 snd
compat_ioctl32         18304  1 uvcvideo
psmouse                64028  0 
wl                   1496016  0 
videodev               45184  2 uvcvideo,compat_ioctl32
dcdbas                 16944  0 
serio_raw              14468  0 
pcspkr                 11136  0 
snd_page_alloc         18704  2 snd_hda_intel,snd_pcm
ieee80211_crypt        14596  2 ieee80211_crypt_tkip,wl
intel_agp              39408  1 
v4l1_compat            23940  2 uvcvideo,videodev
video                  29204  0 
iTCO_wdt               21712  0 
iTCO_vendor_support    12420  1 iTCO_wdt
output                 11648  1 video
usb_storage            94912  1 
sky2                   63236  0 
fbcon                  49792  0 
tileblit               11264  1 fbcon
font                   17024  1 fbcon
bitblit                14464  1 fbcon
softcursor             10368  1 bitblit
aike@aike-laptop:~$ lsmod | grep bcm
aike@aike-laptop:~$

---

### Post by hal10000 on 2009-09-08
I just figured out that the bcm43xx driver module is an older one.
The problem is that we have to find out which is the right module to load.
A newer driver for your card may be the b43.ko kernel module.
So try [COLOR="Red"]lsmod | grep b43[/COLOR] to see if it's loaded. If you get an empty string, then it's not loaded. You can try to manually load it with [COLOR="Red"]sudo modprobe b43[/COLOR] (without the .ko suffix). If you get no error message, then you were successful. Verify this with [COLOR="Red"]lsmod | grep b43[/COLOR]
If you had success in loading the module, then you can go on a rn your network-manager to config your network

If you have no success in loading the module, then you should install the package [COLOR="Red"]linux-backports-modules-jaunty-generic[/COLOR] (i assume you are using jaunty, if not, then replace the -jaunty- part with your ubuntu-version) and do the upper steps with lsmod and modprobe again.

After you manually loaded the module and configured your network, do a reboot to verify wether the module is loaded at boot time. If you get no network after  the reboot, then post it here, so we can go further.

---

### Post by ukozok on 2009-09-09
Partly succeeded:
aike@aike-laptop:~$ lsmod | grep b43
b43                   145192  0 
ssb                    46724  1 b43
mac80211              251144  1 b43
led_class              13064  1 b43
input_polldev          12688  1 b43
aike@aike-laptop:~$ 

but the network manager still shows no wireless networks.

Tried this, but no success:

aike@aike-laptop:~$ apt-get install linux-backports-modules-jaunty-generic
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
aike@aike-laptop:~$ 

Any suggestion?

Thanks!!

---

### Post by t0mppa on 2009-09-09
Actually the wl module showed by lshw is the module for the Broadcom STA, which is the latest native driver for this card and thus the preferred choice. It often has issues, if it's not activated with a working Internet connection, so the easiest fix would be just plucking in wired and then going to System / Administration / Hardware Drivers and deactivating and then reactivating the STA, so it can download all the things it needs to install itself properly.

If you can't get the STA working, then you can always fall back on b43, but that is not as simple as just running **modprobe b43**, as you also need to install *b43-fwcutter* and then use it to install firmware on your card, that the driver requires to work properly. Also have to blacklist the wl, so that it doesn't get loaded in vain and cause any conflicts.

[QUOTE=ukozok]aike@aike-laptop:~$ apt-get install linux-backports-modules-jaunty-generic
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
aike@aike-laptop:~$

Any suggestion?[/QUOTE]

You need to use sudo in front of the command, to run it as an administrator, since your normal user account does not have these priviledges (security issue). So, in order to use apt-get, just have to always remember to start with sudo, ie. **sudo apt-get install xxx**. It will then ask for a password, which is the password you have specified for your user account. However, none of the drivers really need the backports modules to be installed, if you're using Jaunty (Ubuntu 9.04), so I recommend not doing that.

---

### Post by ukozok on 2009-09-09
I did everything as suggested. It still does not show any wireless networks. There is no need to download the drivers from the Broadcom website? [http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)

If I cannot get it going with the native driver should I just throw out the card and replace it with a more reliable card? Which one would you recommend? 

Many thanks,

Uli

---

### Post by hal10000 on 2009-09-09
> aike@aike-laptop:~$ apt-get install linux-backports-modules-jaunty-generic
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

I think you don'tneed the linux-backports-modules, because you already have the correct driver installed.
And besides, you always have to run apt-get with the sudo command, because you'll need root-privileges to install packages.

As we already have the correct kernel module, we don't need to install another one. The problem is now to find out, why it is not loaded.

We now have to get to a well-defined status and because i don't know which kernel modules you have currently loaded, i suggest you reboot your computer now and then, after logging in again, shoot up the following commands and post their output here (even if the output is empty):

1.) **[COLOR="Red"]lsmod | grep b43[/COLOR]** This is to verify wether it's loaded after you rebooted the system

2.) **[COLOR="Red"]sudo lspci -vvv[/COLOR]** This will probably produce a very long output. You should only post the chapter which belongs to your wireless card.
In the last two or three lines of the chapter you can see which kernel module is loaded instead of b43.

3.) If it's _[U]not_[/U] the b43 module, then you should try to unload it: **[COLOR="Red"]sudo rmmod kernel_model_you_found[/COLOR]** If this command produces errors, then post these.

4.) **[COLOR="Red"]sudo modprobe b43[/COLOR]** This loads the b43 module. Only if you get **no** output then everything is ok.

5.) **[COLOR="Red"]sudo /etc/init.d/networking restart[/COLOR]** This reinitializes your network, although you will probably get no connection because it's not configured yet.

6.) Again run **[COLOR="Red"]sudo lspci -vvv[/COLOR]** and look in the wireless-cards chapter for the lines "Kernel driver in use:" and "Kernel modules:".
You should find there the b43 module.

If everything works so far, than you can call your network-manager and configure your settings.
If you geterrors here, then post them too.

Good luck


[EDIT] I just noticed @t0mppa's posting #6. Maybe it's abetter idea to follow his advices.

---

### Post by ukozok on 2009-09-09
1.) lsmod | grep b43 
--empty

2.) sudo lspci -vvv This will probably produce a very long output. You should only post the chapter which belongs to your wireless card.
In the last two or three lines of the chapter you can see which kernel module is loaded instead of b43.
Broadcom BCM3412 802.11b/g
--Kernel driver in use: wl
Kernel modules: wl

3.) If it's not the b43 module, then you should try to unload it: sudo rmmod kernel_model_you_found If this command produces errors, then post these.

i typed: sudo rmmod wl
--empty

4.) sudo modprobe b43 This loads the b43 module. Only if you get no output then everything is ok.
--empty

5.) sudo /etc/init.d/networking restart This reinitializes your network, although you will probably get no connection because it's not configured yet.
--ignoring unknown interface eth0=eth0

6.) Again run sudo lspci -vvv and look in the wireless-cards chapter for the lines "Kernel driver in use:" and "Kernel modules:".
You should find there the b43 module.
--there is nothing on wireless cards

---

### Post by ukozok on 2009-09-09
In the network manager there is nothing on wireless connections any longer -they cannot even be enabled. The Hardware Drivers show that the Broadcom STA is activated but not in use..

---

### Post by ukozok on 2009-09-09
I would like to thank all of you for your advise. Unfortunately the issue was not resolved despite having tried everything. 
I noticed that I am not the only one having problems with the Broadcom BCM3412. Isn't it easier if I just throw the card out and purchase one that is better supported by Linux?
Would you have any suggestions?

Before doing this I would like to try following t0mppa's advise:

"If you can't get the STA working, then you can always fall back on b43, but that is not as simple as just running modprobe b43, as you also need to install b43-fwcutter and then use it to install firmware on your card, that the driver requires to work properly. Also have to blacklist the wl, so that it doesn't get loaded in vain and cause any conflicts."

Could you do me the favor and write down the steps/commands I have to follow?

Thank you,

uk

---

### Post by community nerd on 2009-09-09
Go to *System>Administration>Hardware Drivers *and click activate if it shows your driver.

---

### Post by ukozok on 2009-09-09
It is activated. That's the problem...

---

### Post by hal10000 on 2009-09-10
> eth1 IEEE 802.11 Nickname:""
Access Point: Not-Associated
Link Quality:5 Signal level:0 Noise level:0
Rx invalid nwid:0 invalid crypt:0 invalid misc:0

> It is activated. That's the problem...

I just noticed that your driver is loaded, but you get no Accesspoint. So it my be not a driver problem but a problem between your card and your accesspoint.
Can you see other Accesspoints(maybe from your neighbour) if you run network-manager?
What about the Network-Name (ESSID), the Mode(ad-hoc, managed, infrastructure), the wireless-key, the encryption  (WEP, WPA, WPA2). These things must all be configured your wireless-card and your AP.
Maybe these seetings were accidently damaged.

Can you post the content of **/etc/network/interfaces** ?
Which network-manager are you using (wicd, network-manager-gnome, knetworkmanager etc.)?

---

### Post by ukozok on 2009-09-10
After installing Ubuntu 9.04 I was able to access various networks (mine and that of my neighbours), but after upgrading to the most recent version of Ubuntu I lost my connection.

The Network manager Applet is version 0.7.0.100 

content of /etc/network/interfaces: 
auto lo
iface lo inet loopback

Does this give you any clue?

---

### Post by t0mppa on 2009-09-10
> **ukozok said:**
> I would like to thank all of you for your advise. Unfortunately the issue was not resolved despite having tried everything. 
I noticed that I am not the only one having problems with the Broadcom BCM3412. Isn't it easier if I just throw the card out and purchase one that is better supported by Linux?
Would you have any suggestions?

Before doing this I would like to try following t0mppa's advise:

"If you can't get the STA working, then you can always fall back on b43, but that is not as simple as just running modprobe b43, as you also need to install b43-fwcutter and then use it to install firmware on your card, that the driver requires to work properly. Also have to blacklist the wl, so that it doesn't get loaded in vain and cause any conflicts."

Could you do me the favor and write down the steps/commands I have to follow?

Thank you,

uk

Broadcom cards are pretty well supported, and if your wireless worked earlier, then there's nothing wrong with the drivers, it's just some other issue.

[Here]("http://linuxwireless.org/en/users/Drivers/b43") are instructions for getting b43 to work.

[QUOTE=ukozok]After installing Ubuntu 9.04 I was able to access various networks (mine and that of my neighbours), but after upgrading to the most recent version of Ubuntu I lost my connection.[/QUOTE]

This has been a somewhat common issue as of late with a number of different cards and no one seems to have found out any fix that would work for all users, but if you do a search on the forum about update breaking wireless, you'll find maybe a dozen or so threads where some of the people have documented how got their connection working again.

---

