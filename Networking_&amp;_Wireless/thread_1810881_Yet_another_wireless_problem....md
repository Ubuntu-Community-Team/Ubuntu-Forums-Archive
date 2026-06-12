---
title: "Yet another wireless problem..."
date: 2011-07-23
forum: Networking &amp; Wireless
---

### Post by skipjack2001 on 2011-07-23
Hi all... 

I thought I'd give Ubuntu 11.04 (Natty Narwhal??) a try on an old Dell Latitude D600 I had lying around.  Install went great.  Everything seems to run nice and slick.. except one thing.. the wireless is giving me the old "Device not ready (firmware missing)"  So I can only use my lappy on a leash.

It's a pretty common Broadcom NIC... and I've tried running the System / Administration / Additional Drivers and nothing comes up.

It seems to me I need a driver someplace... but being a Ubuntu noob.. I don't know where or how to get it installed. 

Your help would be appreciated as I would rather be typing this out on the patio with a gin & tonic in my hand than in my cluttered office.

---

### Post by nm_geo on 2011-07-23
> **skipjack2001 said:**
> Hi all... 

I thought I'd give Ubuntu 11.04 (Natty Narwhal??) a try on an old Dell Latitude D600 I had lying around.  Install went great.  Everything seems to run nice and slick.. except one thing.. the wireless is giving me the old "Device not ready (firmware missing)"  So I can only use my lappy on a leash.

It's a pretty common Broadcom NIC... and I've tried running the System / Administration / Additional Drivers and nothing comes up.

It seems to me I need a driver someplace... but being a Ubuntu noob.. I don't know where or how to get it installed. 

Your help would be appreciated as I would rather be typing this out on the patio with a gin & tonic in my hand than in my cluttered office.

Assuming you have not tried to install any other drivers.
```

lspci -nn | grep 0280
```

Give us that 

```
lsmod
```

---

### Post by wildmanne39 on 2011-07-23
Hi, run these commands in a terminal please
```
lspci -nn | grep 0280
```
```
iwconfig
```
```
lsmod
```
```
rfkill list All
```
and post the results here by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by skipjack2001 on 2011-07-24
Thanks! Here you go, guys:

```
02:03.0 Network controller [0280]: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller [14e4:4320] (rev 02)
```

```
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

```

```
Module                  Size  Used by
binfmt_misc            13213  1 
snd_intel8x0           33213  2 
snd_ac97_codec        105614  1 snd_intel8x0
radeon                900494  3 
ac97_bus               12642  1 snd_ac97_codec
arc4                   12473  2 
snd_pcm                80042  2 snd_intel8x0,snd_ac97_codec
b43legacy             127415  0 
snd_seq_midi           13132  0 
snd_rawmidi            25269  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
pcmcia                 39671  0 
ttm                    65184  1 radeon
drm_kms_helper         40745  1 radeon
joydev                 17322  0 
drm                   180037  5 radeon,ttm,drm_kms_helper
ppdev                  12849  0 
snd_timer              28659  2 snd_pcm,snd_seq
yenta_socket           27230  0 
pcmcia_rsrc            18292  1 yenta_socket
mac80211              257001  1 b43legacy
cfg80211              156212  2 b43legacy,mac80211
video                  18951  0 
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
i2c_algo_bit           13184  1 radeon
pcmcia_core            21505  3 pcmcia,yenta_socket,pcmcia_rsrc
parport_pc             32111  1 
shpchp                 32345  0 
dcdbas                 14054  0 
snd                    55295  11 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                73312  0 
lp                     13349  0 
serio_raw              12990  0 
soundcore              12600  1 snd
parport                36746  3 ppdev,parport_pc,lp
snd_page_alloc         14073  2 snd_intel8x0,snd_pcm
tg3                   131476  0 
ssb                    45942  1 b43legacy
```

```
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

```

It looks like it sees that it's a Broadcom... so, I'm not sure how to troubleshoot beyond this point.

---

### Post by wildmanne39 on 2011-07-24
Hi , you click on the internet icon in the top right corner yet? if not do so and make sure wireless is enabled the click on edit connections and enter your SSID, I do not see one in the information you gave us.
Then we will go from there.

---

### Post by moonsal on 2011-07-24
Try this.... If ya can move sys to router... Also have your "driver".inf ready too... 

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

---

### Post by glouw on 2011-07-24
After struggling forever to get my wireless working, I've just resorted to the following workaround:

Connect to the network on my phones wireless, and tether the phone to the laptop.  Works a treat.

---

### Post by skipjack2001 on 2011-07-24
> **wildmanne39 said:**
> Hi , you click on the internet icon in the top right corner yet? if not do so and make sure wireless is enabled the click on edit connections and enter your SSID, I do not see one in the information you gave us.
Then we will go from there.

The wireless is enabled.. however... under Wireless Networks it says "device not ready (firmware missing)"

If I go into "Edit Connections" nothing is listed under the Wireless tab.   I've tried adding a connection manually by entering my WiFi SSID and my WEP key.. but nothing seems to happen WiFi-wise.

Moonsal, I glanced at the NDISWrapper stuff... I'll poke around with it, thanks. [EDIT:] Actually, I found the most recent .inf driver file from Dell's website and try to install it with ndisgtk and it comes up "invalid driver".

---

### Post by bkratz on 2011-07-24
See Joseph's excellent compilation, your's is about halfway down. (14e4:4320 )

[http://ubuntuforums.org/showpost.php?p=10796508&postcount=44](http://ubuntuforums.org/showpost.php?p=10796508&postcount=44)

---

### Post by wildmanne39 on 2011-07-24
Hi, if you still have trouble post back here and we will help you.

---

### Post by skipjack2001 on 2011-07-28
Ok... wow... I've really screwed things up now.  I took the initiative and tried to find some solutions on the web before BKRATZ posted his link (which I've also tried to no avail)...

So... anywhoo... now when I click on the network symbol I don't even see "wireless network" listed any longer as an option.  Yikes.   Here's my stuff again.  



```
02:03.0 Network controller [0280]: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller [14e4:4320] (rev 02)
```

```
lo        no wireless extensions.

eth0      no wireless extensions.

```

```
Module                  Size  Used by
snd_intel8x0           33213  2 
radeon                900494  3 
snd_ac97_codec        105614  1 snd_intel8x0
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                80042  2 snd_intel8x0,snd_ac97_codec
snd_seq_midi           13132  0 
snd_rawmidi            25269  1 snd_seq_midi
binfmt_misc            13213  1 
joydev                 17322  0 
snd_seq_midi_event     14475  1 snd_seq_midi
ttm                    65184  1 radeon
pcmcia                 39671  0 
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
drm_kms_helper         40745  1 radeon
ndiswrapper           192828  0 
snd_timer              28659  2 snd_pcm,snd_seq
ppdev                  12849  0 
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
drm                   180037  5 radeon,ttm,drm_kms_helper
yenta_socket           27230  0 
pcmcia_rsrc            18292  1 yenta_socket
pcmcia_core            21505  3 pcmcia,yenta_socket,pcmcia_rsrc
snd                    55295  11 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
dcdbas                 14054  0 
psmouse                73312  0 
soundcore              12600  1 snd
serio_raw              12990  0 
i2c_algo_bit           13184  1 radeon
parport_pc             32111  1 
shpchp                 32345  0 
video                  18951  0 
snd_page_alloc         14073  2 snd_intel8x0,snd_pcm
lp                     13349  0 
parport                36746  3 ppdev,parport_pc,lp
tg3                   131476  0 

```

And now when I type "rfkill list All" I get:

```
Bogus list argument 'All'.
```

That can't be good.

I'm thinking I might try a whole reinstall of UBUNTU and try Bkratz's link again unless you guys can see something I'm missing.  I really haven't had time to sit and fiddle with (learn) this stuff as much as I want to. So, sorry about my sporadic postings.

---

### Post by wildmanne39 on 2011-07-28
Hi, I did a typo the command should have been.
```
rfkill list all
```
Also lets get this fixed please run this command to remove ndiswrapper, then restart your system.
```
sudo apt-get autoremove ndiswrapper
```
Now run these two commands
```
sudo apt-get install firmware-b43legacy-installer && sudo apt-get install b43-fwcutter
```
Then unplug your wired internet connection and restart your system.
Thank you

---

