---
title: "Wifi not working for, BCM4312 10.10 Maverick Vostro 1520"
date: 2010-10-12
forum: Networking &amp; Wireless
---

### Post by Ucarty on 2010-10-12
Ok so lets do this by the book. (aka **HOWTO post a Wireless issue (ticket) '**[http://ubuntuforums.org/showthread.php?p=6183681](http://ubuntuforums.org/showthread.php?p=6183681)')
[I][B]
Below all the info is what clues I've found so far for anyone willing to help.[/B][/I]
(I'm adding the commands so you know what im doing.)
So here you have my digits; 

/////////////////////////////////////////////////////////////////////////

**1 ) Machine Brand and Model (PC/Laptop)**:[INDENT]Dell Vostro 1520 (Laptop)
[/INDENT][B]2 ) Wireless Brand, Model and Wireless Chipset:
[/B]
```
alexander@alexander-V1520:~$ lspci -nn | grep 'Broadcom'
0e:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)

```**3 ) Check interface:**

```
alexander@alexander-V1520:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:24:e8:c3:d5:2e  
          inet addr:192.168.1.3  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::224:e8ff:fec3:d52e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5430 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5215 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5428641 (5.4 MB)  TX bytes:903052 (903.0 KB)
          Interrupt:47 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:20 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1200 (1.2 KB)  TX bytes:1200 (1.2 KB)

alexander@alexander-V1520:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11  Access Point: Not-Associated   
          Link Quality:5  Signal level:0  Noise level:0
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0

```[B]4 ) Check for modules:
[/B]
[I]I thought the one to look at was 'wl' but I could be wrong so I posted the entire list.
[/I]```
alexander@alexander-V1520:~$ lsmod
Module                  Size  Used by
cryptd                  8140  0 
aes_x86_64              7936  239 
aes_generic            27631  1 aes_x86_64
parport_pc             30086  0 
dm_crypt               13381  0 
ppdev                   6804  0 
binfmt_misc             7984  1 
nvidia              10221046  41 
joydev                 11363  0 
lib80211_crypt_tkip     8732  0 
wl                   1965231  0 
snd_hda_codec_idt      64667  1 
snd_hda_intel          26019  2 
snd_hda_codec         100919  2 snd_hda_codec_idt,snd_hda_intel
lib80211                6175  2 lib80211_crypt_tkip,wl
snd_hwdep               6660  1 snd_hda_codec
snd_pcm                89104  2 snd_hda_intel,snd_hda_codec
snd_seq_midi            5932  0 
snd_rawmidi            22207  1 snd_seq_midi
snd_seq_midi_event      7291  1 snd_seq_midi
snd_seq                57512  2 snd_seq_midi,snd_seq_midi_event
snd_timer              23850  2 snd_pcm,snd_seq
snd_seq_device          6912  3 snd_seq_midi,snd_rawmidi,snd_seq
uvcvideo               62379  0 
videodev               49359  1 uvcvideo
v4l1_compat            15519  2 uvcvideo,videodev
v4l2_compat_ioctl32    12646  1 videodev
dell_laptop             6722  0 
dcdbas                  6910  1 dell_laptop
snd                    64117  13 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                62080  0 
serio_raw               4910  0 
soundcore               1240  1 snd
snd_page_alloc          8588  2 snd_hda_intel,snd_pcm
lp                     10201  0 
parport                37032  3 parport_pc,ppdev,lp
firewire_ohci          24679  0 
ahci                   21857  0 
r8169                  42222  0 
video                  22176  0 
output                  2527  1 video
libahci                26167  4 ahci
sdhci_pci               7765  0 
sdhci                  18400  1 sdhci_pci
led_class               3393  1 sdhci
firewire_core          54327  1 firewire_ohci
crc_itu_t               1739  1 firewire_core
mii                     5261  1 r8169
intel_agp              32080  0 

```[B]5 ) Kernel boot messages

[/B]*'dsmeg'* *kinda gives a long output so until you guys need more I'll keep it at the following, presuming 'wl' is the only thing you need information about.*

```
alexander@alexander-V1520:~$ dmesg | grep 'wl'
[   10.982837] wl: module license 'MIXED/Proprietary' taints kernel.
[   10.986866] wl 0000:0e:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   10.986879] wl 0000:0e:00.0: setting latency timer to 64

```[B]6 ) Network configuration

[/B]```
alexander@alexander-V1520:~$ sudo lshw -C network
[sudo] password for alexander: 
  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth0
       version: 03
       serial: 00:24:e8:c3:d5:2e
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.1.3 latency=0 link=yes multicast=yes port=MII speed=100MB/s
       resources: irq:47 ioport:4000(size=256) memory:fe004000-fe004fff memory:fe000000-fe003fff memory:fe020000-fe03ffff
  *-network DISABLED
       description: Wireless interface
       product: BCM4312 802.11b/g LP-PHY
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0e:00.0
       logical name: eth1
       version: 01
       serial: 00:26:5e:1c:2f:3d
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.60.48.36 latency=0 multicast=yes wireless=IEEE 802.11bg
       resources: irq:18 memory:f6000000-f6003fff

```[B]7 ) Scan for networks:

[/B]```
alexander@alexander-V1520:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Interface doesn't support scanning.

```[B]8 ) Ubuntu Version:

[/B]```
alexander@alexander-V1520:~$ lsb_release -d
Description:    Ubuntu 10.10

``` [I]No, I was not lying, but by the book is by the book.

[/I][B]9 ) Kernel/architecture (including 32 vs. 64 bit):

[/B]```
alexander@alexander-V1520:~$ uname -mr
2.6.35-22-generic x86_64

```[B]10 ) Restarting the network:

[/B]```
alexander@alexander-V1520:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                   [ OK ] 

```///////////////////////////////////////////////////////////////////////////

[B]What I found
[/B]In *System-->Administration-->*Additional Drivers I've enabled the 'Broadcom STA wireless driver' and its noted as 'This driver is activated and currently in use.'

**Changes I made**
- I've activated the Nvidia driver.
- I've installed Boxee (media center)
- I'm using CPU frequency scalers for both my cores.
- I've updated my system and am using maverick-security, -updates and -proposed.
- I've installed b43-fwcutter
- I've installed firmware-b43-lpphy-installer
Other than those adjustments the system is completely fresh.

[B]Hint
[/B]When I suspend or hibernate and activate my laptop again it only shows a backlight-lit black screen and does not continue restoring. Other than the occasional flash my cpu 'business' indicator led does nothing. **BUT** The wireless led is now on.

I've tried the Broadcom B43 driver as you could've guessed from the changes I made, no result. I had to use the 'lpphy' installer(for BCM4312 (with Low-Power aka LP-PHY)), the 'legacy' and normal version both gave an error upon executing the post installation script.


Unfortunately this is all I can give you, if you decide to help me and possibly others with this problem,

***THANKS!***

---

### Post by johnnytm on 2010-10-12
I have the same wireless card in my Inspiron 1545 and it works flawlessy. I did not install B43 fw-cutter or any firmware. All I did was enable the STA driver and that was it. your *NETWORK output shows the right driver installed. Do you have a wireless toggle on your keyboard somewhere? Maybe the B43 stuff is conflicting with the STA driver. Just thoughts but it may be something simple like that.

---

### Post by Ucarty on 2010-10-12
> **johnnytm said:**
> I have the same wireless card in my Inspiron 1545 and it works flawlessy. I did not install B43 fw-cutter or any firmware. All I did was enable the STA driver and that was it. your *NETWORK output shows the right driver installed. Do you have a wireless toggle on your keyboard somewhere? Maybe the B43 stuff is conflicting with the STA driver. Just thoughts but it may be something simple like that.
Hmm, I dont have a wifi toggle on my keyboard but I have a switch. It is currently set to on. Funny thing is, I just had a successful restore from a suspended session and now the wifi led is burning bright and blue.(switching it on and off with the switch works too) Any ideas as to what could help me now. I didnt check all the commands again, but I did check the  Module list 'lsmod' and the driver is still not being used.

---

### Post by johnnytm on 2010-10-12
That sounds like the problem I had with 10.04. I had to reboot my computer immediately after the startup, then the connection was found. Are you using network manager? If so make sure wireless connections are being enabled by your wireless switch, Check sudo lshw -C network again and see if wireless is still disabled.

---

### Post by johnnytm on 2010-10-12
Found a couple of threads u might want to look at [http://ubuntuforums.org/showthread.php?t=1307077&page=2](http://ubuntuforums.org/showthread.php?t=1307077&page=2) and [http://ubuntuforums.org/showthread.php?t=1592544](http://ubuntuforums.org/showthread.php?t=1592544) they boyh have some other suggestions. I am still leaning towards removing the B43 stuff though and just using the broadcom sta driver. My first install of linux would not work with the B43 and fw-cutter. Hope this helps you.

---

### Post by Ucarty on 2010-10-12
> **johnnytm said:**
> Found a couple of threads u might want to look at [http://ubuntuforums.org/showthread.php?t=1307077&page=2](http://ubuntuforums.org/showthread.php?t=1307077&page=2) and [http://ubuntuforums.org/showthread.php?t=1592544](http://ubuntuforums.org/showthread.php?t=1592544) they boyh have some other suggestions. I am still leaning towards removing the B43 stuff though and just using the broadcom sta driver. My first install of linux would not work with the B43 and fw-cutter. Hope this helps you.
Those people are describing exactly what i'm dealing with, im going to try the bios update, that'll probably fix it. Weird I didnt find the thread the second link, links to, bad title though, that might explain it. I'll probably be marking this one fixed in a few hours. 
Thanks, you've been a big help.

---

### Post by Ucarty on 2010-10-14
**Solution: **Update bios drivers. The link provided johnnysm( [http://ubuntuforums.org/showthread.php?t=1592544](http://ubuntuforums.org/showthread.php?t=1592544) ) links to a thread with people with the same problem who also go into more detail about the bios updating.
Thanks again, johnnysm

---

### Post by johnnytm on 2010-10-14
[LEFT]Glad to help. Have fun with your wireless. 
[/LEFT]

---

### Post by Angelo Maldito on 2010-10-30
After several hours struggling to fix my wifi on my HP MINI 210, even  with broadcom sta driver enabled, wireless supposedly enabled (but with  the led light off and not able to see the available networks) I have  finally found the solution here:

[http://life.firelace.com/2010/10/tips-and-tricks-upgrading-to-ubuntu-10-10-wireless-fix/](http://life.firelace.com/2010/10/tips-and-tricks-upgrading-to-ubuntu-10-10-wireless-fix/)   (THANK YOU VERY MUCH DARKMOON !!!) 

The solution was simple, for whatever reason that I am not able to  understand, after you intall the drivers and everything else, THE BLOODY  THING COMES BLOCKED !!!

So in order to unblock, the goddamn thing just open a terminal, login as root ant type the following command:

rfkill unblock all


Thats is it, now its done, working perfectly !!!

I hope it save some hours for someone !

---

### Post by Kaorichan2009 on 2010-11-01
It keeps telling me that permission is denied.

---

### Post by solnyshok on 2010-11-01
use sudo

---

### Post by fkenjikamei on 2010-11-01
> **Angelo Maldito said:**
> After several hours struggling to fix my wifi on my HP MINI 210, even  with broadcom sta driver enabled, wireless supposedly enabled (but with  the led light off and not able to see the available networks) I have  finally found the solution here:

[http://life.firelace.com/2010/10/tips-and-tricks-upgrading-to-ubuntu-10-10-wireless-fix/](http://life.firelace.com/2010/10/tips-and-tricks-upgrading-to-ubuntu-10-10-wireless-fix/)   (THANK YOU VERY MUCH DARKMOON !!!) 

The solution was simple, for whatever reason that I am not able to  understand, after you intall the drivers and everything else, THE BLOODY  THING COMES BLOCKED !!!

So in order to unblock, the goddamn thing just open a terminal, login as root ant type the following command:

rfkill unblock all


Thats is it, now its done, working perfectly !!!

I hope it save some hours for someone !
Thank you very much!
Since the launch of Ubuntu 10.10 release, I'm looking for a solution!
Now, my wifi is working perfect!

Thank you DarkMoon and Angelo Maldito.

---

### Post by larseko on 2010-11-03
This also worked on Vostro 3300 with 10.04. The strange thing is that wireless worked initially, but after a week or so of use, it gets blocked(!). How come?? I have 25 similar PCs, all with the same disk image. They work for a while, but will eventually loose network connectivity.

I guess the solution is just to install a cron job on all of them, unblocking everything every hour or so... 

Thanks anyway, but I still don't understand how wireless became blocked all of a sudden.

---

### Post by larseko on 2010-11-19
This didn't solve the problem for all my PCs. However, I took a look at this bug, which still isn't solved for 10.04. Thats just ridiculous:

[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/524454](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/524454)

---

### Post by hilariusmind on 2011-02-12
> **Angelo Maldito said:**
> 
[http://life.firelace.com/2010/10/tips-and-tricks-upgrading-to-ubuntu-10-10-wireless-fix/](http://life.firelace.com/2010/10/tips-and-tricks-upgrading-to-ubuntu-10-10-wireless-fix/)   (THANK YOU VERY MUCH DARKMOON !!!) 

The solution was simple, for whatever reason that I am not able to  understand, after you intall the drivers and everything else, THE BLOODY  THING COMES BLOCKED !!!

So in order to unblock, the goddamn thing just open a terminal, login as root ant type the following command:

**rfkill unblock all**


Thank you! After 3 months I can use my wireless interface again (and i can also keep my hair).

HM

---

