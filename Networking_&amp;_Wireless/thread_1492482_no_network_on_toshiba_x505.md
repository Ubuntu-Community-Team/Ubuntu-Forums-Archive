---
title: "no network on toshiba x505"
date: 2010-05-24
forum: Networking &amp; Wireless
---

### Post by meskel on 2010-05-24
HI all.

I have such networking issues using ubuntu 10.04 on my toshiba qosmio x505.

I noticed the problem is both with wifi and ethernet cable: I simply don't have connection. It say I'm connected in both cases but connections s. e. internet are simply not working.

On same laptop I have win7 - dual bott- and no problems with win 7 so I dont think is an hw issue

---

### Post by chili555 on 2010-05-24
> **meskel said:**
> HI all.

I have such networking issues using ubuntu 10.04 on my toshiba qosmio x505.

I noticed the problem is both with wifi and ethernet cable: I simply don't have connection. It say I'm connected in both cases but connections s. e. internet are simply not working.

On same laptop I have win7 - dual bott- and no problems with win 7 so I dont think is an hw issuePlease post a new thread and give us more information:```
iwconfig
sudo lshw -C network
lsusb
lsmod
```Thanks.

---

### Post by Iowan on 2010-05-24
> **chili555 said:**
> Please post a new thread ... Thanks.Done...

---

### Post by doogieanese on 2010-05-26
My wired worked out of the box. I was doing some trouble shooting of what i perceived to be a speed issue (turns out it was a non issue), and downloaded compiled and installed the manufacturers driver from their web site. My box has two different nics: Atheros AR8131 for the wired and a Realtec rtl8192se (thanks to chili55 for the typo catch) for the wireless. This honestly blew my mind as it seems the exact opposite of what I would expect (atheros wired realtec wireless). still don't have wireless working was going to go to ndis wrapper for that but have had the time or need to sort out wireless yet.

hope that helps some.

\/-===-===-]edit[-===-===-\/

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/401126?comments=all](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/401126?comments=all)
has good info on the wireless card: realtec rtl8191se. I installed the dkms package from the later posts and will restart some day soon.

ymmv good luck

---

### Post by chili555 on 2010-05-26
So you gave us a link to 819[COLOR="Red"]2[/COLOR]se_pci but you referred to rtl819[COLOR="Red"]1[/COLOR]se. You state it isn't working for you. How does this help the original poster? Does he have the same wireless, do you think?

Do you have a question we can help solve in there somewhere?

---

### Post by doogieanese on 2010-05-27
To clarify: prior to my previous posting i had not done any  research into the issue of wireless networking. So i figured it was time and it provided an opportunity to help the community. I set about to Google  and forum research. thus the part marked edit after i had done some research and started a procedure. Also in my previous post i had a typo in the  chip-set type i have gone back and edited the post to clear it up.

I have not completed the procedure tested the fix, therefore i cannot conclusively say it doesn't work. it would seem that people have had success with this method, including another x505 user [maluka]("http://ubuntuforums.org/member.php?u=78886") [http://ubuntuforums.org/showthread.php?t=1233776](http://ubuntuforums.org/showthread.php?t=1233776)
had some luck with it.

Still not tested on my machine...  still don't know if it works. Can say for sure that i never said the procedure i linked to didn't work for me.

thats all i have to add im out. talk amongst yourselves.

\/-===-===-]EDIT{-===-===-\/

procedure complete: rebooted.
works for me now.

---

### Post by meskel on 2010-06-04
Hi all,
first sorry for answer delay but I was out for a short holiday.
And sorry for english at it is not my mother language.

Well. I figured that the problem starts as follow: as soon as I get connected I can surf with firefox, then stops working. I suppose it is related to package manager, as that as soon as I launch it and authenticate, internet stops working: firefox doesn't find servers anymore and package manager can't download any updates. And for example wireless start strange behavor: in wireless icon, signal intensity moves up and down.
I confirm that I tested same connection using another OS and another pc with ubuntu. So the problem is on my qosmio and the ubuntu installation.


Now anyway I will follow links from your posts and go to my ubuntu box to gather and copy the more information requested by chili555.
Thank you very much to you all.
If it still does not working I will try to reinstall.

I let you know. Thank you, the community is very nice.

---

### Post by chili555 on 2010-06-04
> go to my ubuntu box to gather and copy the more information requested by chili555.I will be very glad to help. Don't worry, your English is fine enough.

---

### Post by meskel on 2010-06-04
> **chili555 said:**
> I will be very glad to help. Don't worry, your English is fine enough.

Ok great! Thanks.
So. First the results to your suggested inquiry:

**iwconfig:**
lo        no wireless extensions.

wlan0     802.11bg  ESSID:"Alice-53310137"  Nickname:"rtl8191SEVA2"
          Mode:Managed  Frequency=2.412 GHz  Access Point: 00:25:53:08:03:FC   
          Bit Rate=54 Mb/s   
          Retry:on   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=85/100  Signal level=-71 dBm  Noise level=-112 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.


**sudo lshw -C network:**
  *-network               
       description: Wireless interface
       product: Realtek Semiconductor Co., Ltd.
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:0a:00.0
       logical name: wlan0
       version: 10
       serial: 70:1a:04:f4:0d:62
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl819xSE driverversion=0014.0115.2010 firmware=62 ip=192.168.1.247 latency=0 link=yes multicast=yes wireless=802.11bg
       resources: irq:16 ioport:4000(size=256) memory:f0600000-f0603fff
  *-network
       description: Ethernet interface
       product: AR8131 Gigabit Ethernet
       vendor: Atheros Communications
       physical id: 0
       bus info: pci@0000:0b:00.0
       logical name: eth0
       version: c0
       serial: 00:26:9e:f3:db:c2
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.0.1-NAPI firmware=N/A latency=0 link=no multicast=yes port=twisted pair
       resources: irq:35 memory:f0400000-f043ffff ioport:5000(size=128)


**lsusb:**
Bus 002 Device 003: ID 04f2:b130 Chicony Electronics Co., Ltd 
Bus 002 Device 002: ID 8087:0020  
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 04d9:0462 Holtek Semiconductor, Inc. 
Bus 001 Device 002: ID 8087:0020  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


**lsmod:**
Module                  Size  Used by
nls_utf8                1421  1 
udf                    85529  1 
crc_itu_t               1715  1 udf
michael_mic             2164  8 
arc4                    1473  4 
binfmt_misc             7960  1 
joydev                 11072  0 
ppdev                   6375  0 
nvidia              10799466  40 
snd_hda_intel          25517  2 
uvcvideo               62403  0 
snd_hda_codec          85727  1 snd_hda_intel
snd_pcm_oss            41394  0 
snd_hwdep               6924  1 snd_hda_codec
videodev               40486  1 uvcvideo
v4l1_compat            15495  2 uvcvideo,videodev
v4l2_compat_ioctl32    12020  1 videodev
snd_mixer_oss          16299  1 snd_pcm_oss
snd_pcm                87850  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1782  0 
snd_seq_oss            31219  0 
snd_seq_midi            5829  0 
snd_rawmidi            23388  1 snd_seq_midi
snd_seq_midi_event      7267  2 snd_seq_oss,snd_seq_midi
snd_seq                57417  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              23553  2 snd_pcm,snd_seq
snd_seq_device          6824  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
fbcon                  39270  71 
tileblit                2487  1 fbcon
font                    8053  1 fbcon
bitblit                 5811  1 fbcon
softcursor              1565  1 bitblit
snd                    70978  15 snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_hwdep,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
vga16fb                12757  1 
soundcore               8052  1 snd
psmouse                64320  0 
serio_raw               4918  0 
vgastate                9857  1 vga16fb
r8192se_pci           486739  0 
snd_page_alloc          8660  2 snd_hda_intel,snd_pcm
atl1c                  33135  0 
sdhci_pci               6700  0 
sdhci                  17928  1 sdhci_pci
led_class               3732  1 sdhci
video                  20623  0 
output                  2503  1 video
lp                      9336  0 
parport                37160  2 ppdev,lp
usbhid                 40988  0 
hid                    83376  1 usbhid
ohci1394               30548  0 
ahci                   37550  4 
ieee1394               94798  1 ohci1394

---

### Post by chili555 on 2010-06-04
> *-network
description: Wireless interface
product: Realtek Semiconductor Co., Ltd.
vendor: Realtek Semiconductor Co., Ltd.
physical id: 0
bus info: pci@0000:0a:00.0
logical name: [COLOR="Red"]wlan0[/COLOR]
version: 10
serial: 70:1a:04:f4:0d:62
width: 32 bits
clock: 33MHz
capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
configuration: broadcast=yes driver=rtl819xSE driverversion=0014.0115.2010 firmware=62 [COLOR="Red"]ip=192.168.1.247[/COLOR] Everything looks just great. Let's look a at few other things:```
ping -c3 www.google.com
ping -c3 74.125.159.103
cat /etc/resolv.conf
route -n
```Thanks!

---

### Post by meskel on 2010-06-07
Hi all.

I think I am fine with the connection after working on it this weekend.

1- I downloaded again the 10.04 64bit iso, burned and reinstalled the system
2- Still network problems, but only with the wifi. Using a cable I did all the updates and **added pre-release updates** in the settings (as suggested by an italian blog fund around in internet for a similar issue)
3- I restarted and wifi is working as well

I had only a problem yesterday: using internet suddenly I got the message "disconnected" from my wifi network. And I needed a restart as it didn' connect again even I attempted to reconnect to the wifi. Anyway now I am using my ubuntu and I am not facing issues up now. Great!

Only now I am trying to use flash player in the browser... as it is not working...(say to download the plugin but then the system says cannot find it) Strange since ubuntu 6 is first time I am having all these problems.

Thank you to all! That was my solution.

Also I did anyway the commands asked by chili:
**ping -c3 www.google.com:**
PING www.l.google.com (72.14.234.104) 56(84) bytes of data.
64 bytes from mil01s07-in-f104.1e100.net (72.14.234.104): icmp_seq=1 ttl=52 time=55.2 ms
64 bytes from mil01s07-in-f104.1e100.net (72.14.234.104): icmp_seq=2 ttl=52 time=54.3 ms
64 bytes from mil01s07-in-f104.1e100.net (72.14.234.104): icmp_seq=3 ttl=52 time=55.0 ms

--- www.l.google.com ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2002ms
rtt min/avg/max/mdev = 54.305/54.867/55.203/0.399 ms


**ping -c3 74.125.159.103:**
PING 74.125.159.103 (74.125.159.103) 56(84) bytes of data.
64 bytes from 74.125.159.103: icmp_seq=1 ttl=47 time=168 ms
64 bytes from 74.125.159.103: icmp_seq=2 ttl=47 time=167 ms
64 bytes from 74.125.159.103: icmp_seq=3 ttl=47 time=167 ms

--- 74.125.159.103 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2003ms
rtt min/avg/max/mdev = 167.291/167.994/168.789/0.775 ms


**cat /etc/resolv.conf:**
# Generated by NetworkManager

---

### Post by Iowan on 2010-06-07
Moved post to this thread. If it was supposed to be [here]("http://ubuntuforums.org/showthread.php?t=1498672"), let me know - I can move it back.

---

### Post by chili555 on 2010-06-08
It's hard to understand how it resolves Google with no working nameserver in /etc/resolv.conf, but it evidently does:> ping -c3 [www.google.com:](www.google.com:)
PING [COLOR="Red"]www.l.google.com (72.14.234.104) [/COLOR]56(84) bytes of data.
64 bytes from mil01s07-in-f104.1e100.net (72.14.234.104): icmp_seq=1 ttl=52 time=55.2 msIf you are fine, we are happy.

---

