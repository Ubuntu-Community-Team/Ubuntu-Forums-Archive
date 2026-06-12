---
title: "Bought an RT2870 Wireless Network Adapter but cannot figure out how to install it."
date: 2010-07-03
forum: Networking &amp; Wireless
---

### Post by kirbyparufo on 2010-07-03
I'm pretty new at this stuff, so keep solutions simple if possible. As the topic title says, I got a RT2870 Wireless Network Adapter  (compatible with Linux) but I have NO clue about how to install the  thing. Inside the Linux portion of the install CD was a file, which I  extracted to the desktop. Inside of that is a readme with instructions  far too complex for me to understand. I can post the readme if  necessary. For now, I'm trying to figure out a way to install this  thing.

---

### Post by roosh on 2010-07-03
It is possible that Ubuntu already has the driver installed, in which case you can just plug-in the adapter. If that doesn't work, then there are a few options of what to do.

---

### Post by kirbyparufo on 2010-07-03
Plugging it in has no effect. It powers on (at least, a tiny green light  on the thing flashes a few times), but I can't connect to a nearby  wireless network.

---

### Post by roosh on 2010-07-03
I'm assuming this connects via USB.
Make sure the device is plugged in. Then, in a terminal, please run ```
lsusb
``` and ```
lsmod
``` and post the output here

---

### Post by kirbyparufo on 2010-07-03
lsusb gave me:
```
Bus 003 Device 003: ID 058f:9360 Alcor Micro Corp. 8-in-1 Media Card Reader
Bus 003 Device 002: ID 15d9:0a4c Dexon 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 005: ID 148f:3070 Ralink Technology, Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

lsmod gave me:
```
Module                  Size  Used by
rt2870sta             461811  0 
arc4                    1153  2 
rt2800usb              31531  0 
rt2x00usb               9703  1 rt2800usb
rt2x00lib              27509  2 rt2800usb,rt2x00usb
led_class               2864  1 rt2x00lib
mac80211              205146  2 rt2x00usb,rt2x00lib
cfg80211              126517  2 rt2x00lib,mac80211
crc_ccitt               1339  1 rt2800usb
binfmt_misc             6587  1 
fbcon                  35102  71 
tileblit                2031  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
vga16fb                11385  0 
vgastate                8961  1 vga16fb
snd_atiixp             12446  2 
snd_ac97_codec        100646  1 snd_atiixp
ac97_bus                1002  1 snd_ac97_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70662  3 snd_atiixp,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26726  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
radeon                674824  3 
snd_timer              19098  2 snd_pcm,snd_seq
cdc_ether               3541  0 
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
ttm                    49943  1 radeon
drm_kms_helper         29297  1 radeon
ppdev                   5259  0 
drm                   162377  5 radeon,ttm,drm_kms_helper
i2c_algo_bit            5028  1 radeon
usbnet                 14943  1 cdc_ether
snd                    54148  14 snd_atiixp,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
parport_pc             25962  1 
ati_agp                 5094  0 
soundcore               6620  1 snd
snd_page_alloc          7076  2 snd_atiixp,snd_pcm
k8temp                  3024  0 
i2c_piix4               8335  0 
agpgart                31724  3 ttm,drm,ati_agp
shpchp                 28820  0 
lp                      7028  0 
parport                32635  3 ppdev,parport_pc,lp
usb_storage            39425  0 
usbhid                 36110  0 
ohci1394               26950  0 
hid                    67032  1 usbhid
ieee1394               81181  1 ohci1394
8139too                18545  0 
8139cp                 16186  0 
mii                     4381  3 usbnet,8139too,8139cp
pata_atiixp             3148  2 
sata_sil                6959  0 
```

---

### Post by roosh on 2010-07-03
So it looks like Ubuntu is loading the driver, but I've googled around and it looks like out-of-the-box, Ubuntu doesn't do a good job with that specific card.

There is good news, however. I can see two options: compiling the driver from the CD you have. Or, you can use another option, ndiswrapper. I have had success with ndiswrapper, but not with the first option, so I would recommend it. But the choice is yours. So, which do you want to do?

---

### Post by kirbyparufo on 2010-07-03
Might as well go for the one you're better with, ndiswrapper. >_>

---

### Post by roosh on 2010-07-03
Whoa! Hang on a sec; there might be a really easy fix to this. Try this:
in a terminal type:

Have your wireless plugged in. In a terminal type:
```
sudo rmmod rt2800usb
```
it will prompt for your password, enter it.

See if the wireless works (wait ~1 min)

If it doesn't, detach the adapter then reattach it after a few seconds.
See if it works. 

It it does, make sure to post back so we can make the changes permanent. If it doesn't post back all the same.

---

### Post by DThurman on 2010-07-03
Holy smokes!

rmmod rt2800usb WORKS for me!

Why does it require this step!?!?
What's going on?

---

### Post by kirbyparufo on 2010-07-03
lol, I went through all of your other steps before seeing that you edited your post. >_>

Anyway, the (new) fix worked. How do I make this permanent?

---

### Post by roosh on 2010-07-03
I hate to admit it but I think this is Ubuntu's fault. Basically, there were two drivers that were using the adapter (look in the lsmod above, you'll see: rt2870sta and rt2800usb). This causes the card not to function properly. To fix this permanently simply open a terminal and type in:

```
sudo gedit /etc/modprobe.d/blacklist.conf
```

You'll be prompted for your password, enter it. Then a text editor will pop-up with some text. Scroll down to the bottom and add this:

```
blacklist rt2800usb
```

Save the file. Now reboot to make sure the change works. Sorry kirbyparufo I got a little anxious and didn't diagnose the problem correctly. If you guys want, you can learn more about the problem here: [http://ubuntuforums.org/showthread.php?t=1342593](http://ubuntuforums.org/showthread.php?t=1342593)

---

### Post by roosh on 2010-07-03
Also, kirbyparufo, how far did you get with the ndiswrapper? I would suggest uninstalling ndiswrapper:
go to system --> administration --> synaptic package manager
in the "quick search" type in: ndis

Then uncheck "ndisgtk" "ndiswrapper-utils-1.9" and "ndiswrapper-common"
The click apply.

Finally, if everything works, please edit to add [solved] to the header of this thread.

---

### Post by DThurman on 2010-07-03
Yes, those steps are when you do not have your AP base
station appearing on the nm-applet list (left-mouse-click),
or wish to have non-default settings (DHCP).

If your base station appears on the list, you want the
default settings (Auto-DHCP) then it is a matter of
clicking on your AP base station ssid, enter your
pass-phrase, and you are done.

I am glad that someone besides us noobs are looking
into this problematic issue and offering a solution!

Dan

---

### Post by DThurman on 2010-07-03
> **roosh said:**
> Also, kirbyparufo, how far did you get with the ndiswrapper? I would suggest uninstalling ndiswrapper:
go to system --> administration --> synaptic package manager
in the "quick search" type in: ndis

Then uncheck "ndisgtk" "ndiswrapper-utils-1.9" and "ndiswrapper-common"
The click apply.

Thanks roosh!

This helped me alot, more than you know.  I have
had this issue since way back when and still have
v9.04 installed so I can test it there was well.

I would like to request that the Ubuntu team fix this bug
and save us all future headaches :)

Dan

---

### Post by kirbyparufo on 2010-07-03
Thanks so much for the help. :D

---

### Post by roosh on 2010-07-03
> **DThurman said:**
> Thanks roosh!

This helped me alot, more than you know.  I have
had this issue since way back when and still have
v9.04 installed so I can test it there was well.

I would like to request that the Ubuntu team fix this bug
and save us all future headaches :)

Dan

Glad to help. I think the Ubuntu developers are working on it, albeit slowly. You guys might be able to help move it along by clicking on the "this bug affects me too" link at the bug page (and maybe giving some info) at [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/549801](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/549801)

---

### Post by DThurman on 2010-07-03
Ugh....

There seems to be a problem still...

Changing the default auto settings from DHCP
to Manual seems to break things...  I cannot
access my local networks....

The DHCP (default) seems to have missing router
and network DNS information that I need...

What is wierd here, is that when I use the nslookup
command, enter 'server', it contains all the
DNS information as I expected, however, I think
that this information is not used by the wireless
connection.

How I noticed this, is that I could not access my
local imap connections, hence my local dns servers
are not being used at all...

Any advice?

---

### Post by roosh on 2010-07-03
I can't offer any advice there, sorry. I would suggest looking to see if there is a similar problem, and if there isn't make a new thread. If all else fails, you could try ndiswrapper ([https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper))

---

### Post by DThurman on 2010-07-03
OK!  Now I got Manual working!!!

Thanks for everything!  I'm a happy camper now!

---

### Post by roosh on 2010-07-03
Glad to hear it:)

---

