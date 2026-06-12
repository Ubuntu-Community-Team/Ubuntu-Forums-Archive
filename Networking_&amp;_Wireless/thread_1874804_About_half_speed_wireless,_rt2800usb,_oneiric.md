---
title: "About half speed wireless, rt2800usb, oneiric"
date: 2011-11-03
forum: Networking &amp; Wireless
---

### Post by oedipuss on 2011-11-03
I'm using ubuntu 11.10, 64bit, with a wireless usb dongle from belkin.  It uses the rt2800usb driver, and gives about half the speed of what it used to under ubuntu 11.04. Testing with speedtest.net, gives about 4mbps when it should be closer to 8~10.
Other pcs connected to the same router work as expected.

I'm not sure what driver was used with 11.04, but I think it was 
rt2870sta. I'm not sure though.

lsusb info :
```
Bus 003 Device 005: ID 050d:825b Belkin Components F5D8055 N+ Wireless Adapter v2000 [Ralink RT3070]

```
ifconfig :
```
wlan0     Link encap:Ethernet  HWaddr 00:22:75:3f:51:b4  
          inet addr:192.168.1.78  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::222:75ff:fe3f:51b4/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:76464 errors:0 dropped:0 overruns:0 frame:0
          TX packets:65261 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:35458673 (35.4 MB)  TX bytes:10233593 (10.2 MB)
```

iwconfig:
```
wlan0     IEEE 802.11bgn  ESSID:"assurbanipal"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:1E:2A:FE:0C:74   
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=59/70  Signal level=-51 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:177  Invalid misc:99   Missed beacon:0

```
I've already tried loading the rt2800usb module with nohwcrypt=1 , as suggested in another thread, but it doesn't change anything.

Is it possible or desirable to try with the rt2870sta driver? How would this be done? Or maybe there's some other problem? Any help would be appreciated :)

---

### Post by nerderello on 2011-11-04
Hi oedipuss,
not sure if what I experienced is the same as what you have, but when I upgraded from 10.10 to 11.10 I too got rubbish network throughput.

I use an Asus N13 dongle (so this may have nothing to do with your problem) and had to force load the rt2780 driver (nice chap by the name of chilli555 showed me how) with 10.10 . However, with 11.10 the dongle is recognized "out of the box" and so there is no need for the force loading. But, not realising this, I had left the two files intact from the 10.10 us. This meant that two drivers were "fighting over" the dongle. 

In the end I had to remove the force loading files (actually just commented those lines out) **and** remove (count to 3) and replace the dongle (as there was something still loaded in it even after a re-boot or power down).

If (please note that word) this is what has happened with your set-up, then that's what you need to do.

fyi, when I now type **lsmod | grep rt** into a terminal I get:
> [FONT="Courier New"]rt2800usb              22300  0 
rt2800lib              48717  1 rt2800usb
crc_ccitt              12595  1 rt2800lib
rt2x00usb              20092  1 rt2800usb
rt2x00lib              48114  3 rt2800usb,rt2800lib,rt2x00usb
mac80211              272785  3 rt2800lib,rt2x00usb,rt2x00lib
cfg80211              172392  2 rt2x00lib,mac80211[/FONT]



And the two lines I had to comment out were:
> [FONT="Courier New"]ACTION=="add", SUBSYSTEM=="usb", ATTR{idVendor}=="0b05", ATTR{idProduct}=="1784", RUN+="/sbin/modprobe -qba rt2870sta[/FONT]in /etc/udev/rules.d/network_driver.rules
and
> [FONT="Courier New"]install rt2870sta /sbin/modprobe --ignore-install rt2870sta $CMDLINE_OPTS; /bin/echo "0b05 1784" > /sys/bus/usb/drivers/rt2870/new_id[/FONT] in /etc/modeprobe.d/network_drivers.conf

regards
Nerderello

---

### Post by oedipuss on 2011-11-04
This was a new install, there couldn't be any leftover drivers.
In any case, I can't find any trace of the rt2870sta module, only the builtin rt2800usb.
About the same shows up with lsmod | grep rt28 .

How did you find out the two modules were fighting for the device? Maybe something similar is happening. 

In any case, thanks for your answer :)


Regarding the rt2800usb module, are there any other options besides nohwcrypt I could experiment with ?

---

### Post by nerderello on 2011-11-06
Hi,
sounds like your's is a different issue from mine.

Have you tried the other "fix" that is doing the rounds ([http://ubuntuforums.org/showthread.php?t=1859558]("http://ubuntuforums.org/showthread.php?t=1859558")), that of disabling ip v6? I've put the word fix into quotes, because I can't see it having any effect, but then others have said it worked for them.

To answer your queries. I found out about the need to force the driver install with my dongle and pre-v3 versions of the kernel, thru this forum and a member called chilli555. And I'm afraid that I don't know of any other options for the module, apart from turning the on-board encryption (nohwcrypt) which some old dongles can't cope with.

Sorry I couldn't help, good luck
Nerderello

---

### Post by tvrtuscan on 2012-03-19
Hi,

Did you get anywhere with this.  I have the same problem.  Very slow internet connection with Belkin F5D8055.  Is anyone aware if we should be using the default oneiric rt2800usb driver or should we download the ralink driver.  It seems to be almost working and sometimes iwconfig is showing speeds above 54Mb/s so I think the n is working.

I've tried several solutions including turning the power saving off.  Does anyone know how I would disable the hw decyrpt on this device?

Any help much appreciated.

I get almost exactly the same output as oedipuss.

---

### Post by wildmanne39 on 2012-03-19
Hi tvrtuscan, if you are using rt2800usb you can try this if it helps we will need to make it permanent.
```
sudo ifconfig wlan0 down
sudo rmmod -f rt2800usb
sudo modprobe rt2800usb nohwcrypt=1
sudo ifconfig wlan0 up

```
do not reboot after running those commands.
Thanks

---

### Post by jawilljr on 2012-03-19
Turn off power mangement:

```
sudo iwconfig wlan0 power off
```

---

### Post by tvrtuscan on 2012-03-20
Thanks very much for the replies.  I have now tried both of these workarounds with no effect plus setting the ipv6 to ignore.

I'm also taking a long network cable home today so I can compare the speedtest both wired and unwired.  It looks as though Windows 7 is about twice the speed of Ubuntu though with the same configuration.

---

### Post by wildmanne39 on 2012-03-20
Hi, please open a terminal ctrl+alt+t copy and paste the following commands into it one line at a time, then paste the results here:

```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
iwconfig
rfkill list all
lsmod
lsusb
```
by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by tvrtuscan on 2012-03-20
Thanks wildmanne39, it's people like you that make Ubuntu!

I've just done a speedtest in Windows and it's around 9.7Mbps where as Ubuntu is registering 1.59Mbps.

Requested info is as follows:

cat /etc/lsb-release; uname -a
```

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.10
DISTRIB_CODENAME=oneiric
DISTRIB_DESCRIPTION="Ubuntu 11.10"
Linux trev 3.0.0-16-generic #29-Ubuntu SMP Tue Feb 14 12:48:51 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

```

lspci -nnk | grep -iA2 net
```

04:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 01)
	Subsystem: Giga-byte Technology GA-EP45-DS5 Motherboard [1458:e000]
	Kernel driver in use: r8169

```

iwconfig
```

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"TrevsHome"  
          Mode:Managed  Frequency:2.472 GHz  Access Point: 00:22:75:9E:80:C8   
          Bit Rate=52 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=55/70  Signal level=-55 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:445  Invalid misc:0   Missed beacon:0

```

rfkill list all
```

0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

```

lsmod
```

Module                  Size  Used by
vesafb                 13809  1 
snd_usb_audio         118122  1 
snd_usbmidi_lib        25371  1 snd_usb_audio
rfcomm                 47946  0 
bnep                   18436  2 
bluetooth             166112  10 bnep,rfcomm
arc4                   12529  2 
rt2800usb              22590  0 
rt2800lib              54538  1 rt2800usb
crc_ccitt              12667  1 rt2800lib
rt2x00usb              20830  1 rt2800usb
rt2x00lib              50365  3 rt2800usb,rt2800lib,rt2x00usb
mac80211              462046  3 rt2800lib,rt2x00usb,rt2x00lib
cfg80211              199630  2 rt2x00lib,mac80211
gspca_zc3xx            52562  0 
gspca_main             28314  1 gspca_zc3xx
videodev               92992  1 gspca_main
v4l2_compat_ioctl32    17083  1 videodev
ppdev                  17113  0 
snd_hda_codec_hdmi     32040  1 
binfmt_misc            17540  1 
snd_hda_codec_realtek   330815  1 
snd_hda_intel          33390  3 
snd_hda_codec         104931  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13668  2 snd_usb_audio,snd_hda_codec
snd_pcm                96714  4 snd_usb_audio,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30547  2 snd_usbmidi_lib,snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
fglrx                2928969  111 
psmouse                73882  0 
serio_raw              13166  0 
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
parport_pc             36962  1 
snd_timer              29991  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    68266  20 snd_usb_audio,snd_usbmidi_lib,snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
lp                     17799  0 
parport                46562  3 ppdev,parport_pc,lp
firewire_ohci          40722  0 
firewire_core          63626  1 firewire_ohci
floppy                 70365  0 
crc_itu_t              12707  1 firewire_core
ahci                   26002  2 
libahci                26861  1 ahci
pata_jmicron           12747  0 
r8169                  52788  0 
usbhid                 47198  0 
hid                    95463  1 usbhid

```

lsusb
```

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 050d:825b Belkin Components F5D8055 N+ Wireless Adapter v2000 [Ralink RT3070]
Bus 003 Device 002: ID 046d:08ad Logitech, Inc. QuickCam Communicate STX
Bus 008 Device 002: ID 413c:2105 Dell Computer Corp. Model L100 Keyboard

```

I'm now going to try the wired speedtest as I've got a longer network cable from work...

---

### Post by wildmanne39 on 2012-03-20
Hi, see if this helps if it does we will need to make it permanent.
```
sudo ifconfig wlan0 down
sudo rmmod -f rt2800usb
sudo modprobe rt2800usb nohwcrypt=1
sudo ifconfig wlan0 up
```
do not reboot.
Thanks

---

### Post by tvrtuscan on 2012-03-20
I disabled power management again (still a very low speed test at around 1.79Mbps).

I then turned off hardware decryption again and got a speed test of around 6Mbps.  However on the second speed test it went down to around 1.4Mbps so maybe it's a little intermittent but mostly it's down around 1.5Mbps.

As suspected I ran a wired speed test and it's 9.79Mbps.

---

### Post by tvrtuscan on 2012-03-20
Thanks wildmanne39, sorry, I was posting at the same time as you.

I followed your steps exactly and run three tests and got the following results 4.59 1.18 1.01.

I switched power management on and got the following results 3.01 1.55 0.97.

I then tried turning the nohwcrypt off (I think) using the following:
```

sudo ifconfig wlan0 down
sudo rmmod -f rt2800usb
sudo modprobe rt2800usb nohwcrypt=0
sudo ifconfig wlan0 up

```
and got the following three results 7.02 0.81 4.58

The speed seems variable between about 1 and 7Mbps but still not what I would expect.  The power management and nohwcrypt do not seem to have an effect on the speed tests.

---

### Post by wildmanne39 on 2012-03-20
Hi, it is usually better to have power management off.

Also set your wireless settings to match the screenshot and see if that helps.

I am not sure that you can get better speeds but this is what helps most people.

You can try ```
sudo modprobe rt2800usb nohwcrypt=1
```
instead of the =0 and see if that helps.
Thanks

---

### Post by tvrtuscan on 2012-03-26
Sorry for the delay in response.  I was just trying a few other ideas/suggestions.

Thanks for your suggestions but unfortunately none of the steps worked so at the moment I'm stuck with an average of around 1.5Mbps wireless connection.  Shame as in Windows it's up at 9.5Mbps so I know the hardware is capable of it.  

It sounds like a bug to me so maybe it'll be fixed in 12.04.

It looks like it's close to working out the box but I might try the ralink rt2870 driver to see it that improves the speed but last time I did this it was a pain whenever there was a Ubuntu update.

---

### Post by wildmanne39 on 2012-03-26
Hi, most like your only option is to compile the driver yourself.
Thanks

---

