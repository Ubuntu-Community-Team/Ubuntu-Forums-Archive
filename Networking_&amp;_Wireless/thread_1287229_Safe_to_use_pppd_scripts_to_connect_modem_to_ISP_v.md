---
title: "Safe to use pppd scripts to connect modem to ISP via dialup?"
date: 2009-10-09
forum: Networking &amp; Wireless
---

### Post by OrangeVixen on 2009-10-09
I have some old pppd scripts that I use to connect my PCI modem via dialup to my ISP on my old Linux.

Is it safe to just copy those to my new Ubuntu 9.04 box and run them? (not using gnome-network-admin and gnome-ppp, etc?)

Or is that not the correct way to do that with Ubuntu?

---

### Post by rippin on 2009-10-09
> **OrangeVixen said:**
> I have some old pppd scripts that I use to connect my PCI modem via dialup to my ISP on my old Linux.

Is it safe to just copy those to my new Ubuntu 9.04 box and run them? (not using gnome-network-admin and gnome-ppp, etc?)

Or is that not the correct way to do that with Ubuntu?

Please work on talking to us. :confused:

Which scripts are you mentioning? Are they yours or from some unknown to us OS?

---

### Post by OrangeVixen on 2009-10-10
These are scripts that I (me, orangevixen) wrote myself, I use them to get pppd to tell my modem to connect to my ISP using dialup, they are currently on my old Linux, meaning my old computer.

I just got Ubuntu 9.04 Jaunty (that is the version and codename you asked for about which version of Ubuntu I had) with a totally new computer, so this is my new computer with a fresh install of said Ubuntu.

My old computer is NOT Ubuntu Linux, and so I was not sure if I should just install my scripts (put them in /etc/ppp) and run them like I did with my old computer or not. Since lots of other users complained about Ubuntu 9.04 not having dialup support and reading all the help docs recommend various workarounds (e.g. d/l gnome-network-admin on to a separate CD from a computer w/ internet, and dpkg install the gnome-network-admin to the Ubuntu computer).

I basically want to know if using my old scripts is safe/proper.

PS: I have a 3Com PCI modem on serial port 1 /dev/ttyS0 according to lspci on my new computer.

---

### Post by rippin on 2009-10-11
> **OrangeVixen said:**
> These are scripts that I (me, orangevixen) wrote myself, I use them to get pppd to tell my modem to connect to my ISP using dialup, they are currently on my old Linux, meaning my old computer.

I just got Ubuntu 9.04 Jaunty (that is the version and codename you asked for about which version of Ubuntu I had) with a totally new computer, so this is my new computer with a fresh install of said Ubuntu.

My old computer is NOT Ubuntu Linux, and so I was not sure if I should just install my scripts (put them in /etc/ppp) and run them like I did with my old computer or not. Since lots of other users complained about Ubuntu 9.04 not having dialup support and reading all the help docs recommend various workarounds (e.g. d/l gnome-network-admin on to a separate CD from a computer w/ internet, and dpkg install the gnome-network-admin to the Ubuntu computer).

I basically want to know if using my old scripts is safe/proper.

PS: I have a 3Com PCI modem on serial port 1 /dev/ttyS0 according to lspci on my new computer.
[B]
[COLOR=Red]We're not in your room looking over your shoulder. You have to be our ears & eyes[/COLOR][/B].

You failed to say which kernel is in use. I know by experience 2.6.26 worked wonderfully with my Winmoden but 2.6.28 didn't. Plus, I had Linux kernel modules for the device. You have omitted important pieces of information.

Check if your user is setup with the proper groups - dialup, ppp, etc.

Let's answer a fundamental question: have you test the modem in 9.04? If so, what are the results? 

I looked at the scripts. They seem OK. _[COLOR=black]***BUT***[/COLOR] _...

***_[COLOR=Red]... looks like you posted some private information. IF so, please contact your ISP and alter it ![/COLOR]_***

From pppd-connect.sh

#    Ultimate Internet Access (UIA) - uia.net
#
#    Account # 1224128257
#
#    Voice/Technical Support: 1-800-982-6898
#
ACCESS_SITE_PHONE_NUMBER="6060183"
#ACCESS_SITE_PHONE_NUMBER="6064199"
#ACCESS_SITE_PHONE_NUMBER="19093483766"
#ACCESS_SITE_PHONE_NUMBER="19093484199"
#ACCESS_SITE_PHONE_NUMBER="19093483187"
ISP_NAME="uia"
LOGIN_NAME="sandrac"

---

### Post by OrangeVixen on 2009-10-11
Well, I was trying to be thoouuuurrrrrough. 9.9 :) There are no passwords in there and its not my login any more. All those phone numbers are the ISP's numbers.

I only wanted to know if this is the *right* way to connect via dial-up in Ubuntu 9.04. Is it????? **I really want to make sure**.

FYI, I am posting this using my new comp that's now connected via dial-up, so it proves the scripts work. But the problem now is, is this the right way? do I still need to install gnome-network-admin(sp?) and all the other various methods described in the help docs?

Is there any way I can have this script run at **start-up**?

Just because you asked 3 times in red, here is my Linux kernel version on the new comp (old one was 2.2.15):

user@zareason-limbo:~$ uname --all
Linux zareason-limbo 2.6.28-15-generic #52-Ubuntu SMP Wed Sep 9 10:48:52 UTC 2009 x86_64 GNU/Linux

user@zareason-limbo:~$ lsmod
Module                  Size  Used by
ppp_deflate            13568  0 
zlib_deflate           30616  1 ppp_deflate
bsd_comp               14208  0 
ppp_async              18560  1 
crc_ccitt              10496  1 ppp_async
nls_iso8859_1          13440  0 
nls_cp437              15104  0 
vfat                   21120  0 
fat                    65592  1 vfat
binfmt_misc            18572  1 
ppdev                  16904  0 
bridge                 63776  0 
stp                    11140  1 bridge
bnep                   22912  2 
video                  29844  0 
output                 11648  1 video
input_polldev          12688  0 
lp                     19588  0 
parport                49584  2 ppdev,lp
joydev                 20864  0 
snd_hda_intel         559028  3 
snd_pcm_oss            52352  0 
snd_mixer_oss          24960  1 snd_pcm_oss
snd_pcm                99464  2 snd_hda_intel,snd_pcm_oss
snd_seq_dummy          11524  0 
snd_seq_oss            41984  0 
snd_seq_midi           15744  0 
snd_rawmidi            33920  1 snd_seq_midi
snd_seq_midi_event     16512  2 snd_seq_oss,snd_seq_midi
snd_seq                66272  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              34064  2 snd_pcm,snd_seq
snd_seq_device         16276  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    78920  15 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                64028  0 
soundcore              16800  1 snd
usb_storage           115520  0 
snd_page_alloc         18704  2 snd_hda_intel,snd_pcm
serio_raw              14468  0 
usbhid                 47040  0 
iTCO_wdt               21712  0 
iTCO_vendor_support    12420  1 iTCO_wdt
pcspkr                 11136  0 
nvidia               8123768  36 
ohci1394               42164  0 
r8169                  46596  0 
ieee1394              108288  1 ohci1394
mii                    14464  1 r8169
floppy                 75816  0 
fbcon                  49792  0 
tileblit               11264  1 fbcon
font                   17024  1 fbcon
bitblit                14464  1 fbcon
softcursor             10368  1 bitblit

---

### Post by rippin on 2009-10-12
> I only wanted to know if this is the *right* way to connect via dial-up in Ubuntu 9.04. Is it????? **I really want to make sure.**

I think they're OK.

> FYI, I am posting this using my new comp that's now connected via dial-up, so it proves the scripts work. But the problem now is, is this the right way? do I still need to install gnome-network-admin(sp?) and all the other various methods described in the help docs?

Is there any way I can have this script run at **start-up**?I prefer pon/poff method. Can be set with ~/.bashrc & ~/.bash_logout or autostart. Look at gpppon for GUI.

> Just because you asked 3 times in red, here is my Linux kernel version on the new comp (old one was 2.2.15):

user@zareason-limbo:~$ uname --all
Linux zareason-limbo 2.6.28-15-generic #52-Ubuntu SMP Wed Sep 9 10:48:52 UTC 2009 x86_64 GNU/Linux<snip>

Problem I had with that kernel, not *-15, was it would connect but lock file after poff. Hopefully that has been corrected.

So, **before I [COLOR=SandyBrown]*die*[/COLOR]**[COLOR=MediumTurquoise]*,*[/COLOR] are you gonna [COLOR=Plum]**TEST**[/COLOR] the modem and report results  :rolleyes:??

---

### Post by rippin on 2009-10-12
> **OrangeVixen said:**
> 
<snip>

user@zareason-limbo:~$ lsmod
Module                  Size  Used by
ppp_deflate            13568  0 
zlib_deflate           30616  1 ppp_deflate
bsd_comp               14208  0 
ppp_async              18560  1 
crc_ccitt              10496  1 ppp_async
nls_iso8859_1          13440  0 
nls_cp437              15104  0 
vfat                   21120  0 
fat                    65592  1 vfat
binfmt_misc            18572  1 
ppdev                  16904  0 
bridge                 63776  0 
stp                    11140  1 bridge
bnep                   22912  2 
video                  29844  0 
output                 11648  1 video
input_polldev          12688  0 
lp                     19588  0 
parport                49584  2 ppdev,lp
joydev                 20864  0 
snd_hda_intel         559028  3 
snd_pcm_oss            52352  0 
snd_mixer_oss          24960  1 snd_pcm_oss
snd_pcm                99464  2 snd_hda_intel,snd_pcm_oss
snd_seq_dummy          11524  0 
snd_seq_oss            41984  0 
snd_seq_midi           15744  0 
snd_rawmidi            33920  1 snd_seq_midi
snd_seq_midi_event     16512  2 snd_seq_oss,snd_seq_midi
snd_seq                66272  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              34064  2 snd_pcm,snd_seq
snd_seq_device         16276  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    78920  15 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                64028  0 
soundcore              16800  1 snd
usb_storage           115520  0 
snd_page_alloc         18704  2 snd_hda_intel,snd_pcm
serio_raw              14468  0 
usbhid                 47040  0 
iTCO_wdt               21712  0 
iTCO_vendor_support    12420  1 iTCO_wdt
pcspkr                 11136  0 
nvidia               8123768  36 
ohci1394               42164  0 
r8169                  46596  0 
ieee1394              108288  1 ohci1394
mii                    14464  1 r8169
floppy                 75816  0 
fbcon                  49792  0 
tileblit               11264  1 fbcon
font                   17024  1 fbcon
bitblit                14464  1 fbcon
softcursor             10368  1 bitblit

I don't recognize any of these as being for a modem. Maybe I missed it. I see modules for ppp. Is your modem module loaded?

---

