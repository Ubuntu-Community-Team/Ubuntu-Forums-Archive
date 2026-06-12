---
title: "Need step-by-step, D-link DWA-160 dongle on a HP a6334f PC"
date: 2011-12-25
forum: Networking &amp; Wireless
---

### Post by okanagansage on 2011-12-25
Hello, I'm hoping I can get some instruction on how to set up my wireless connection. According to one webpage in the community documentation my dongle works "out of the box". According to a page on a different linux support site (I found the link in a lifehacker article), firmware is required. 
That link is [http://linux-wless.passys.nl/query_part.php?brandname=D-Link](http://linux-wless.passys.nl/query_part.php?brandname=D-Link)
On that page there is a note about my usb dongle that says 
"driver in kernel for ath5k/ath9k; see [http://wireless.kernel.org/en/users/Drivers/ar9170](http://wireless.kernel.org/en/users/Drivers/ar9170) ; firmware required". In that quote, the link goes to a firmware download.

Fresh install of 10.04. In Network Tools the wireless interface state is listed as active. When I enter the command nm-tool in the terminal, the state is listed as disconnected. 

I haven't entered any information from my router's configuration. I'm not sure what info I'll need and where to enter it in Ubuntu. I'm guessing I'll have to deal with any driver/firmware issues first. Supposedly the driver is included in the kernel, but there's also a linux driver on D-link's website (if it's needed). 

A sticky thread says to include the following information. The only thing not listed is the output from dmesg (5). It was really long and I don't know how to put info into a dropdown box.

1. HP Pavilion a6334f PC

2. lsusb: Bus 002 Device 004: ID 07d1:3c10 D-Link System DWA 160A 802.11n
(according to... [http://linux-wless.passys.nl/query_part.php?brandname=D-Link](http://linux-wless.passys.nl/query_part.php?brandname=D-Link) ...the chipset is Atheros)

3. iwconfig
wlan0     IEEE 802.11abg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=27 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

4. lsmod
Module                  Size  Used by
binfmt_misc             6587  1 
ppdev                   5259  0 
arc4                    1153  2 
snd_hda_codec_realtek   203168  1 
fbcon                  35102  71 
tileblit                2031  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
vga16fb                11385  0 
vgastate                8961  1 vga16fb
snd_hda_intel          21877  2 
snd_hda_codec          74201  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
i915                  282354  4 
drm_kms_helper         29297  1 i915
snd_pcm                70662  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
drm                   162471  5 i915,drm_kms_helper
snd_seq_dummy           1338  0 
i2c_algo_bit            5028  1 i915
snd_seq_oss            26726  0 
video                  17375  1 i915
lp                      7028  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
ar9170usb              51200  0 
parport                32635  2 ppdev,lp
snd_timer              19098  2 snd_pcm,snd_seq
output                  1871  1 video
mac80211              204922  1 ar9170usb
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
intel_agp              24177  2 i915
led_class               2864  1 ar9170usb
agpgart                31724  2 drm,intel_agp
ath                     7611  1 ar9170usb
snd                    54148  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               6620  1 snd
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
cfg80211              126485  3 ar9170usb,mac80211,ath
psmouse                63245  0 
serio_raw               3978  0 
usb_storage            39425  0 
ohci1394               26950  0 
ieee1394               81181  1 ohci1394
r8169                  33884  0 
mii                     4381  1 r8169
ahci                   32008  3 

6. sudo lshw -C network
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:22:b0:5b:e4:f0
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11abg

7. iwlist scan
wlan0     No scan results

8. lsb_release -d
Description:    Ubuntu 10.04 LTS

9. uname -mr
2.6.32-21-generic i686          (32 bit computer)

10. sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                          
Ignoring unknown interface eth0=eth0.
[ OK ]

I would appreciate some instruction if you've got the patience. 
Thanks.

Edit: Colon and o's are showing up (above) as emoticons.

---

### Post by okanagansage on 2011-12-26
Okay, so I opened up Network Connections (under System and Preferences). Under the wireless tab I clicked add, which opened up a new window (Editing Wireless Connection 1) with four of its own tabs.

EDITING WIRELESS CONNECTION 1
Wireless (tab). Entered SSID. Mode is set to infrastructure. As far as I understand, BSSID and MAC Address are the same thing so I only filled in the MAC address.

Wireless Security (tab). Chose wpa and wpa2 personal. Entered wireless security password.

IPv4 Settings (tab). The drop-down list for Method was at Automatic (DHCP). I left that unchanged.
...........................................

DRIVER AND FIRMWARE
I believe the driver is included in the terminal. The firmware link on this website is 'bad' (404 not found). Link on this page: [http://wireless.kernel.org/en/users/Drivers/ar9170](http://wireless.kernel.org/en/users/Drivers/ar9170)
 ...............................................

I just searched the name of the firmware (ar9170.fw) and found a page listing a search result for ubuntu packages. It shows the path and filename /lib/firmware/ar9170.fw
_I checked my system for that file and I already have it._ A different page (firmware download page) said to put it in this folder so I'm guessing I don't have to move it or do anything with it.

It looks like I have all drivers and firmware. I just have to set things up properly. Before this new install of lucid 10.04 the wireless used to try to connect over and over. A window would keep reappearing with my password (as dots) and I could press connect everytime it came up but I couldn't load pages in my browser. Now in this new installation, if I disconnect my ethernet it doesn't try to connect to wireless (the radio waves on the wireless icon are not flashing). There's just a red exclamation mark on the icon. 

I'm looking through the settings for "Editing wireless connection 1". Maybe I've got something wrong. Like I said, I've got the bssid blank. It's the same as mac address, isn't it? I've put in the mac address. In my router, under status, the mac address is the same for lan and wlan. That's the one I used. 

Any suggestions?

---

### Post by okanagansage on 2011-12-26
I clicked the wireless icon and a list of available wireless networks popped up. Mine was listed and my neighbor's and others. I chose mine. The 'authentication is required' window appears. I put in my password and it tries to connect for a while. Then the authentication window reappears. This is what it was doing before I reinstalled the OS (10.04). It's seeing the networks that are available but won't connect.

---

### Post by okanagansage on 2011-12-26
I GOT IT! The mac address/bssid was not the problem. The problem was that I was entering the password I use to enter my router's settings page and not the "pre-shared key".

What worked for me (in more detail) is this. I clicked on the network manager applet in my panel. The available wireless networks are listed. When I click on mine, a window opens up with the name of the network and the space to enter the password. Before I was entering the password that I use to access my router's settings (the one that is used when you enter 192.168.0.1, or what ever, into your browser's address bar to check on or make changes to your router, then it asks for the password). The word password was throwing me off I guess. 

What worked instead was the 'pre-shared key'. This can be found by going into your router settings. For my d-link 615  router I entered 192.168.0.1 into the browser address bar and entered my router's password. Then I went to: 

SETUP (top menu), 
then WIRELESS SETTINGS (left menu), 
then click on the ADD WIRELESS DEVICE button in the center, 
choose MANUAL and press next. 
Four settings are listed: ssid, security code, cipher type, and the pre-shared key. The key is LONG (about 30 or 40 letters and numbers). I pasted this into a text file using notepad on my Windows machine and saved it onto a usb drive. I opened up that text file on my ubuntu machine and pasted it into the password field (the one that appears when you choose your wireless network in the panel applet menu). And that's it. 

I'm sure this is pretty basic. I've only set up a few wireless connections before on Windows machines using the instruction manual. I'm sure there's some people out there who've made the same mistake as me in Ubuntu. If they find this thread, I hope it helps. :)

Just wanted to add: Now when I enter sudo iwconfig into the terminal, the access point shows its MAC address. Before connecting, it said "access point: not-associated". Bit rate is listed there as well now.

---

### Post by okanagansage on 2011-12-26
I had this thread marked as solved and have now taken that solved label off. The wireless connection crashed on me. The authentication window keeps popping up again. I'll have to take a look at this another day.

---

### Post by ctsdownloads on 2011-12-26
Following this thread and it occurs to me -- you're using a rather dated release of Ubuntu (yes, it's LTS...but it's not going to have newer bug fixes). Wouldn't using 11.04 make a lot more sense? Back then, folks still had to do the following, due to a bug.

[http://myubuntunotes.wordpress.com/2011/03/03/hello-world/](http://myubuntunotes.wordpress.com/2011/03/03/hello-world/)

Same driver is used here, so if you're needing to use an old release of Ubuntu, that will help you.

I want to know if ar9170usb works in recent releases of Ubuntu, such as 11.04-11.10.

---

### Post by okanagansage on 2011-12-27
Thanks ctcdownloads for the reply. I thought I'd try the method from the link you posted but it didn't work for me for some reason. I'm not sure if I did something wrong or what. I appreciate the tip anyways. One bonus would have been to feel like I've learned something. Although I did learn some, it would have been better had I got it fixed.

Like you suggested, it seems like a good time to try a younger OS. Before trying the newest Ubuntu I may try out CrunchBang or ArchBang. I thought I'd heard that Debian has excellent documentation. I may look into that as well. I definitely would like to try the latest Ubuntu and see how I like Unity. 

In your post you said you like to know if ar9170usb works on the newest releases of Ubuntu. Below I've pasted in a section of: [http://wireless.kernel.org/](http://wireless.kernel.org/)
It states that ar9170 has been removed and replaced with carl9170.
............................................................

From wireless.kernel.org:
**** 
  
**July 22, 2011**

 With a little delay, Linus released [3.0]("http://kernelnewbies.org/Linux_3.0"). Besides numbering change, this version contains some interesting wireless changes [IMG]http://wireless.kernel.org/moin/linuxwireless/img/smile.png[/IMG] 

[LIST]
[*]ar9170usb: remove driver (replaced by carl9170) 
[*]ath6kl: add support for AR6003 v2.1.1 
[*]ath9k_htc: add AP and P2P modes 
[*]ath9k_hw: support for AR9340 
[*]b43: fix DMA problems on some LP-PHY cards 
[*]iwlagn: fix performance regression since 2.6.35 (use cts-to-self protection) 
[*]iwlagn: support for new 105 series devices 
[*]rt2860sta: remove driver (replaced by mainline rt2800pci) 
[*]rt2870sta: remove driver (replaced by mainline rt2800usb) 
[*]rt2x00: Initial support for RT5370 USB devices 
[*]rt2x00: Enable support for RT53xx PCI devices by default 
[*]rt2x00: RT33xx device support is no longer experimental 
[*]rtlwifi: support for RTL8192SE chips added
[/LIST]

---

### Post by ctsdownloads on 2011-12-27
> **okanagansage said:**
> Thanks ctcdownloads for the reply. I thought I'd try the method from the link you posted but it didn't work for me for some reason. I'm not sure if I did something wrong or what. I appreciate the tip anyways. One bonus would have been to feel like I've learned something. Although I did learn some, it would have been better had I got it fixed.

Like you suggested, it seems like a good time to try a younger OS. Before trying the newest Ubuntu I may try out CrunchBang or ArchBang. I thought I'd heard that Debian has excellent documentation. I may look into that as well. I definitely would like to try the latest Ubuntu and see how I like Unity. 

In your post you said you like to know if ar9170usb works on the newest releases of Ubuntu. Below I've pasted in a section of: [http://wireless.kernel.org/](http://wireless.kernel.org/)
It states that ar9170 has been removed and replaced with carl9170.
............................................................

From wireless.kernel.org:
**** 
  
**July 22, 2011**

 With a little delay, Linus released [3.0]("http://kernelnewbies.org/Linux_3.0"). Besides numbering change, this version contains some interesting wireless changes [IMG]http://wireless.kernel.org/moin/linuxwireless/img/smile.png[/IMG] 

[LIST]
[*]ar9170usb: remove driver (replaced by carl9170) 
[*]ath6kl: add support for AR6003 v2.1.1 
[*]ath9k_htc: add AP and P2P modes 
[*]ath9k_hw: support for AR9340 
[*]b43: fix DMA problems on some LP-PHY cards 
[*]iwlagn: fix performance regression since 2.6.35 (use cts-to-self protection) 
[*]iwlagn: support for new 105 series devices 
[*]rt2860sta: remove driver (replaced by mainline rt2800pci) 
[*]rt2870sta: remove driver (replaced by mainline rt2800usb) 
[*]rt2x00: Initial support for RT5370 USB devices 
[*]rt2x00: Enable support for RT53xx PCI devices by default 
[*]rt2x00: RT33xx device support is no longer experimental 
[*]rtlwifi: support for RTL8192SE chips added
[/LIST]

Ah, yes, carl9170. Cool. With any luck carl9170 will help with some of the problems. Another thought for problematic wifi dongles is to test PCLinuxOS. I've seen their wireless support remains strong, especially with dongles that gave me grief in other distros. It's worth checking out. :)

---

