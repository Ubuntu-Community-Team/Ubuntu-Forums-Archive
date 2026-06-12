---
title: "Problem with Broadcom BCM4306"
date: 2011-10-08
forum: Networking &amp; Wireless
---

### Post by David Morris on 2011-10-08
Before I start, I should point out that any internet searches mentioned in this post were done on separate systems (my Win7 netbook and my Windows Phone).

I've just installed Ubuntu 11.04 using Wubi on a system that already had Windows Vista. Both OSs are 64-bit.

When I started Ubuntu, I noticed the wireless didn't work.

I needed to refresh my memory of the driver details for the WiFi card and discovered that I had a Broadcom BCM4306 card that needs a b43 driver.

Doing commands such as 'lshw -C network' and iwconfig told me than wlan0 was disabled for some reason.

After doing lsmod, I noticed that b43 was in the list, but there was a 0 next to it and I presumed this meant that it wasn't in use.

Doing 'modprobe b43' didn't solve the problem.

After doing another Google search, I noticed one source suggesting that I needed to do 'sudo apt-get install b43-fwcutter'. Unsurprisingly, this didn't work.

Another website had this link - [http://security.ubuntu.com/ubuntu/pool/main/b/b43-fwcutter]("http://security.ubuntu.com/ubuntu/pool/main/b/b43-fwcutter")

This showed a long list of drivers. I went for the latest amd64.deb file (the machine with the Ubuntu installation has an AMD dual core processor) and put it on a pen drive, so I could transfer them to the Ubuntu installation. I successfully installed the driver via the Software Centre.

I installed it, but the wireless network is still disabled. I went through all the commands again and nothing worked. I also checked System>Administration>Additional Drivers and nothing was listed.

Does anyone have any ideas? My long term goal is to have Ubuntu as the primary OS and, obviously a successful wireless connection is vital.

Incidentally, the wireless card works fine with Windows Vista.

---

### Post by nm_geo on 2011-10-08
> **David Morris said:**
> Before I start, I should point out that any internet searches mentioned in this post were done on separate systems (my Win7 netbook and my Windows Phone).

I've just installed Ubuntu 11.04 using Wubi on a system that already had Windows Vista. Both OSs are 64-bit.

When I started Ubuntu, I noticed the wireless didn't work.

I needed to refresh my memory of the driver details for the WiFi card and discovered that I had a Broadcom BCM4306 card that needs a b43 driver.

Doing commands such as 'lshw -C network' and iwconfig told me than wlan0 was disabled for some reason.

After doing lsmod, I noticed that b43 was in the list, but there was a 0 next to it and I presumed this meant that it wasn't in use.

Doing 'modprobe b43' didn't solve the problem.

After doing another Google search, I noticed one source suggesting that I needed to do 'sudo apt-get install b43-fwcutter'. Unsurprisingly, this didn't work.

Another website had this link - [http://security.ubuntu.com/ubuntu/pool/main/b/b43-fwcutter](http://security.ubuntu.com/ubuntu/pool/main/b/b43-fwcutter)

This showed a long list of drivers. I went for the latest amd64.deb file (the machine with the Ubuntu installation has an AMD dual core processor) and put it on a pen drive, so I could transfer them to the Ubuntu installation. I successfully installed the driver via the Software Centre.

I installed it, but the wireless network is still disabled. I went through all the commands again and nothing worked. I also checked System>Administration>Additional Drivers and nothing was listed.

Does anyone have any ideas? My long term goal is to have Ubuntu as the primary OS and, obviously a successful wireless connection is vital.

Incidentally, the wireless card works fine with Windows Vista.

Hi .. and welcome to the forum ..
You do need the b43 driver but firmware is also needed.

there are two different types for the Bcm4306 chipset.

```
lspci -nn | grep 0280
```

run that in terminal and paste results please.

---

### Post by David Morris on 2011-10-09
The following is the output for 'lspci -nn | grep 0280':

```
david@ubuntu:~$ lspci -nn | grep 0280
01:06.0 Network controller [0280]: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller [14e4:4320] (rev 03)
```

If it helps, here's a relevant section of the 'lsmod' output:

```
nouveau               682322  2 
snd_pcm                96625  3 snd_hda_intel,snd_hda_codec,snd_usb_audio
snd_hwdep              13604  2 snd_hda_codec,snd_usb_audio
snd_usbmidi_lib        25139  1 snd_usb_audio
snd_seq_midi           13324  0 
b43                   318638  0 
snd_seq_midi_event     14899  1 snd_seq_midi
```

Note the presence of b43, but there is a 0 next to it.

Here's what I get after typing 'iwconfig':

```
david@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
```

So, it detects my wireless card, but it can't detect the Netgear DGND3300v2 router - presumably because of the driver issues.

The following is what I get when I type 'lshw -C network':

```
david@ubuntu:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: MCP65 Ethernet
       vendor: nVidia Corporation
       physical id: 6
       bus info: pci@0000:00:06.0
       logical name: eth0
       version: a3
       serial: 00:1f:d0:6c:76:07
       capacity: 1Gbit/s
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.64 latency=0 maxlatency=20 mingnt=1 multicast=yes port=MII
       resources: irq:42 memory:f5106000-f5106fff ioport:c800(size=8)
  *-network
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 6
       bus info: pci@0000:01:06.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=32
       resources: irq:16 memory:f5004000-f5005fff
  *-network DISABLED
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:11:50:1c:36:ca
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=b43 driverversion=2.6.38-8-generic firmware=N/A multicast=yes wireless=IEEE 802.11bg
WARNING: output may be incomplete or inaccurate, you should run this program as super-user.
```

I hope this helps you figure out how to solve my problem. If you need anything else, let me know.

---

### Post by nm_geo on 2011-10-09
[QUOTE]Wireless LAN Controller **[COLOR=Red][14e4:4320] (rev 03)[[/COLOR]**/QUOTE]```
-network DISABLED
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:11:50:1c:36:ca
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=b43 driverversion=2.6.38-8-generic**[COLOR=Red] firmware=N/A [/COLOR]**multicast=yes wireless=IEEE 802.11bg

```

Your driver need the normal firmware.
Ok we are on the right track.
You need the firmware-b43-installer and the b43-fwcutter.
You can install both in Synaptic package manager or in command line in terminal.

```
sudo apt-get install b43-fwcutter
```
```
sudo apt get install firmware-b43-installer
```

---

### Post by David Morris on 2011-10-10
I already have b43-fwcutter installed.

I managed to find firmware-b43-installer_4.150.10.5-4_all.deb on the web (obviously, couldn't download using Synaptic or Ubuntu Software Centre due to lack of wireless connection in Linux). This is what I got when I tried installing it via the Software Centre:

```
(Reading database ... 
(Reading database ... 5%
(Reading database ... 10%
(Reading database ... 15%
(Reading database ... 20%
(Reading database ... 25%
(Reading database ... 30%
(Reading database ... 35%
(Reading database ... 40%
(Reading database ... 45%
(Reading database ... 50%
(Reading database ... 55%
(Reading database ... 60%
(Reading database ... 65%
(Reading database ... 70%
(Reading database ... 75%
(Reading database ... 80%
(Reading database ... 85%
(Reading database ... 90%
(Reading database ... 95%
(Reading database ... 100%
(Reading database ... 128886 files and directories currently installed.)
Preparing to replace firmware-b43-installer 4.150.10.5-4 (using .../firmware-b43-installer_4.150.10.5-4_all.deb) ...
Unpacking replacement firmware-b43-installer ...
Setting up firmware-b43-installer (4.150.10.5-4) ...
--2011-10-10 23:35:40--  http://mirror2.openwrt.org/sources/broadcom-wl-4.150.10.5.tar.bz2
Resolving mirror2.openwrt.org... failed: Name or service not known.
wget: unable to resolve host address `mirror2.openwrt.org'
dpkg: error processing firmware-b43-installer (--install):
 subprocess installed post-installation script returned error exit status 4
Errors were encountered while processing:
 firmware-b43-installer
```

So, part of the installer needs an internet connection to complete the job.

I can't do an wired connection to the router as my router is downstairs (where the only phone socket is) and my PC is upstairs.

When in Windows, I went to the URL specified in the install details ([http://mirror2.openwrt.org/sources]("http://mirror2.openwrt.org/sources")) to get the file it was trying to download (broadcom-wl-4.150.10.5.tar.bz2).

The problem is, I can't find a way to install this. I can't use the Software Centre or Synaptic. I've found one or two things relating to the 'make install' command (which I remember from my days using Slackware) on Google, but nothing gives me clear instructions for my particular problem.

Can anyone help?

---

### Post by wildmanne39 on 2011-10-10
Hi, here is a link with directions to install the firmware without internet connection also, you will need to scroll down the page some.
[http://ubuntuforums.org/showpost.php?p=10796508&postcount=44](http://ubuntuforums.org/showpost.php?p=10796508&postcount=44)

Is you computer a desktop the reason you do not want to take it to your router, that would be much easier on you.
Thank you

---

### Post by David Morris on 2011-10-12
Thanks for all the help. My wireless connection is working fine now.

---

### Post by wildmanne39 on 2011-10-12
Hi, I am glad it is working.
Enjoy

---

