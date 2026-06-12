---
title: "A Wifi Communications Question"
date: 2012-04-19
forum: Networking &amp; Wireless
---

### Post by held7over on 2012-04-19
Different versions of Ubuntu on different computers. Home Network Router= Linksys WRT54-TM with dd-WRT, wifi transmitting on Channel 1 using g mode. And wifi Analyzer shows no other networks on channel 1 or channel 2, and only a very very weak neighboring network on channel 3. 

How can I have anywhere between 60% to 90% signal strength being reported when I hover my pointer over the the signal icon on my different computers, and at the same time, experience a transmission speed slow down or even loose my connection to my router?  

I mean, I've seen signal strength in the past drop down very low and then loose a connection, but I've never seen data flow slow down and loose the connection while the computer is reporting high signal strength!!!

Thanks!

---

### Post by nothingspecial on 2012-04-20
*Thread moved to **Networking & Wireless**.*

---

### Post by fixitdude on 2012-04-20
Microwave ovens don't show up on your wifi readings.

2.4 Ghz telephones don't either.

People walking around reflect signals, cars passing by.

And there are 3 frequencies on wifi, so really 3 channels. 1, 6 and 11.

Don't get that confused with "channels". They really cheated us on using our own PUBLIC RADIO WAVES for things we need to use it for.

Oh, and if you live near an airport, better run a wire.

---

### Post by held7over on 2012-04-20
Correction: I said I had company on frequency 3, but I meant to say, it was on frequency 6. No one appears to be transmitting on anything below that, except me on 1. 

I have used dd-WRT to boost my signal on my router to about 80. I think I can go up to 100 before I need to attach a fan. But I read somewhere quite a while back, i think, that at much over 80 or so and my signal will start having more distortion...which I assume means my communication speeds will slow down. And somewhere over 100 I can shorten the life of my router...

A couple of blocks from me, Viaero has just built a tower which they say is going to give their cell phone customers better coverage in this area. It is about the same time as their antennas were installed that I began to experience these problems....but I figured it was probably coincidence...

However, the problem seems to go away late at night...which wouldn't seem consistent with a communications tower. 

I guess it is going to be either wire, as you suggest, or tinfoiling my house (and maybe making a hat out of tinfoil for myself)!  

It would be nice if there were a device that let's one's house electrical wiring become one big wifi antenna! You'd be surrounded by your own wifi antenna that way! I have been looking for such a beast, but the closest I have found to that, are devices that have to be installed at the router and one for each each computer in the house, but evidently you can put a second wifi router on those devices also...which I assume probably operates on another frequency number than your primary router.

---

### Post by wildmanne39 on 2012-04-20
Hi, please open a terminal ctrl+alt+t copy and paste the following commands into it one line at a time, then paste the results here:

```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
lsusb
iwconfig
rfkill list all
lsmod
```
by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by held7over on 2012-04-20
```
lucky@lucky:~$ cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.10
DISTRIB_CODENAME=maverick
DISTRIB_DESCRIPTION="Ubuntu 10.10"
Linux lucky 2.6.35-32-generic #68-Ubuntu SMP Tue Mar 27 17:01:54 UTC 2012 i686 GNU/Linux
lucky@lucky:~$ lspci -nnk | grep -iA2 net
00:09.0 Ethernet controller [0200]: Atheros Communications Inc. Atheros AR5001X+ Wireless Network Adapter [168c:0013] (rev 01)
	Subsystem: D-Link System Inc Device [1186:3a1b]
	Kernel driver in use: ath5k
--
00:12.0 Ethernet controller [0200]: VIA Technologies, Inc. VT6102 [Rhine-II] [1106:3065] (rev 78)
	Subsystem: ASUSTeK Computer Inc. Device [1043:80ff]
	Kernel driver in use: via-rhine
lucky@lucky:~$ lsusb
Bus 005 Device 002: ID 058f:9360 Alcor Micro Corp. 8-in-1 Media Card Reader
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 045e:00db Microsoft Corp. Natural Ergonomic Keyboard 4000 V1.0
Bus 002 Device 002: ID 045e:0040 Microsoft Corp. Wheel Mouse Optical
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
lucky@lucky:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"FortApache"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:1A:70:FD:AB:03   
          Bit Rate=11 Mb/s   Tx-Power=27 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=31/70  Signal level=-79 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

lucky@lucky:~$ rfkill list all
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
lucky@lucky:~$ lsmod
Module                  Size  Used by
aes_i586                7280  0 
aes_generic            26875  1 aes_i586
binfmt_misc             6599  1 
iptable_nat             3752  0 
nf_nat                 16289  1 iptable_nat
nf_conntrack_ipv4      10783  3 iptable_nat,nf_nat
nf_conntrack           63258  3 iptable_nat,nf_nat,nf_conntrack_ipv4
nf_defrag_ipv4          1117  1 nf_conntrack_ipv4
iptable_mangle          1371  0 
iptable_filter          1302  0 
ip_tables              10492  3 iptable_nat,iptable_mangle,iptable_filter
x_tables               15921  4 iptable_nat,iptable_mangle,iptable_filter,ip_tables
snd_via82xx            20140  2 
snd_via82xx_modem       8498  0 
gameport                9327  1 snd_via82xx
snd_ac97_codec         99227  2 snd_via82xx,snd_via82xx_modem
arc4                    1165  2 
ac97_bus                1014  1 snd_ac97_codec
snd_pcm                71475  3 snd_via82xx,snd_via82xx_modem,snd_ac97_codec
snd_mpu401_uart         5661  1 snd_via82xx
ath5k                 130083  0 
snd_seq_midi            4588  0 
snd_rawmidi            17783  2 snd_mpu401_uart,snd_seq_midi
snd_seq_midi_event      6047  1 snd_seq_midi
snd_seq                47174  2 snd_seq_midi,snd_seq_midi_event
snd_timer              19067  2 snd_pcm,snd_seq
mac80211              231959  1 ath5k
nouveau               517434  2 
snd_seq_device          5744  3 snd_seq_midi,snd_rawmidi,snd_seq
ath                     8153  1 ath5k
ttm                    56633  1 nouveau
drm_kms_helper         30200  1 nouveau
ppdev                   5556  0 
cfg80211              144758  3 ath5k,mac80211,ath
snd                    49102  13 snd_via82xx,snd_via82xx_modem,snd_ac97_codec,snd_pcm,snd_mpu401_uart,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
drm                   168124  4 nouveau,ttm,drm_kms_helper
lp                      7342  0 
parport_pc             26058  1 
snd_page_alloc          7120  3 snd_via82xx,snd_via82xx_modem,snd_pcm
parport                31492  3 ppdev,lp,parport_pc
via_agp                 5322  1 
shpchp                 29886  0 
soundcore                880  1 snd
joydev                  8767  0 
i2c_viapro              5777  0 
psmouse                59027  0 
i2c_algo_bit            5168  1 nouveau
agpgart                32011  3 ttm,drm,via_agp
led_class               2633  1 ath5k
serio_raw               4022  0 
usb_storage            40492  0 
firewire_ohci          21330  0 
hid_microsoft           2691  0 
usbhid                 36882  0 
hid                    67934  2 hid_microsoft,usbhid
via_rhine              19038  0 
pata_via                7332  0 
firewire_core          46675  1 firewire_ohci
sata_via                7344  3 
mii                     4425  1 via_rhine
crc_itu_t               1383  1 firewire_core
lucky@lucky:~$ 
```

---

### Post by wildmanne39 on 2012-04-20
Hi, please do:
```
gksudo gedit /etc/modprobe.d/ath5k.conf
```
Add a single line:

```
options ath5k nohwcrypt=1
```

Proofread carefully, save and close gedit. Reboot.
Thanks

---

### Post by held7over on 2012-04-20
My connection signal strength today is ranging between 44 and 57 percent, and generally is at 48%.

I tried the modification to /etc/modprobe.d/ath5k.conf and rebooted. The result was the same connection signal strengths being reported for my connection to my router, BUT...I couldn't access anything on the Internet. Skype, Thunderbird, my web browser all couldn't find the servers they were looking for.

---

### Post by wildmanne39 on 2012-04-20
Hi, open the file and copy the contents here please.

This is what usually fixes slow connection speeds for your device, it does not change signal strength necessarily.
Thanks

---

### Post by held7over on 2012-04-20
Hi!  

Interesting!  --There was nothing written in that file when I opened it originally. I was using linux cut and paste to open the file and add the programming text. I didn't type either of them. But, I did try a second time, to make sure I had opened the right file and hadn't cut anything off. 

I had to remove the program text from that file and reboot again, in order to get back onto the internet.

So. The file remains empty.

---

### Post by wildmanne39 on 2012-04-20
Hi, that is strange that should have let you connect to the internet, the only time I have seen it not is when the person typed the wrong text instead of just copy and paste into the blank file.

You can also set your wireless settings to match the ones in the screenshots I am including, it helps improve speed but not signal strength and you are right if your signal is weak your speed will be slow but this driver causes it to be slow and sometimes disconnects without the parameters I posted for you to put in the file.
Thanks

---

### Post by held7over on 2012-04-20
Thanks wildmanne39! 

I think that actually did speed up my internet access some.

My modem is at 192.168.1.1 and my Linksys Router is at 192.168.2.1 and my DNS had been pointing at my router at 192.168.2.1

---

### Post by wildmanne39 on 2012-04-20
Hi, yes it usually does quite a bit, I wish we could get the driver parameter to work.

---

### Post by held7over on 2012-04-20
Hey! I have your fix working! Thanks!

I tried it a third time, the only thing I did differently, was, instead of doing a RESTART, I did a full shutdown, then booted up and I had a connection!

I rechecked the file to make sure the line of code was there, and it is.

I think I may have gained some tiny increase in transmission speed, but it is hard to tell, I will have to watch it over time. For some reason, my signal strength has dropped to 40%! It's 6:30pm here right now, which means the houses around me may have more people in them now, perhaps they are all using wireless phones and doing things which cause interference...got me!

I will wait for my signal strength to increase and then try to see if we have accomplished an improvement...

---

### Post by wildmanne39 on 2012-04-20
Hi, I am glad the parameter took effect it will help but you may still have to much interference during certain situations.
Thanks

---

### Post by fixitdude on 2012-05-22
I like your tin foil idea.

Not the whole house, but maybe try it to block where you think the signal is coming from.

---

### Post by held7over on 2012-05-22
The latest thing I have done, is, I took a 8" metal mixing bowl, and placed it so that it's edge is setting on the right angle connectors of my dual antennas of my wifi router, which leaves the antennas themselves inside the bowl, with the bowl aimed like a dish toward the area/path I want to increase the signal.

This has actually increased the signal strength and I have fewer connection and data transfer problems. I haven't gotten rid of all of them, but this does seem to significantly impact whatever interference that was going on.  

The bowl is deep and rounded internally, so it isn't really a parabolic dish, so it is probably very inefficient at what I want it to do. I have heard that a person can grab an old DirecTV Dish and replace one of the antennas with a connector to the dish and tell the router to only use the dish side for transmission reception. The parabolic dish should be a lot better than the bowl....and I my wife is trying to steal her mixing bowl back   ....so, I may scrounge up a DirecTV dish and see what happens...

---

