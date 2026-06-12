---
title: "trouble connecting to secured Wireless Network"
date: 2012-03-23
forum: Networking &amp; Wireless
---

### Post by jackey101 on 2012-03-23
[FONT=Arial Black][SIZE=2][FONT=Arial][SIZE=3]My ubuntu 10.04 is not connecting to secured Wireless Network Connection of college wifi.... can anyone help?[/SIZE][/FONT]
[/SIZE][/FONT]

---

### Post by Damascushead on 2012-03-23
First make sure your wireless card is turned on. Some machines actually have a physical button for this. If that doesn't work;
 
use 
```
ifconfig
```
to see what the name of your wireless card is (usually wlan0).
 
Then run this command to turn your card on.
 
```
sudo ifconfig wlan0 up
```
 
If your card is already on, I guess just make sure that the password is correct.
 
Hopefully this helps
 
:p

---

### Post by Bucky Ball on 2012-03-23
Do you have all the appropriate details configured on your computer?

Right click the network icon and 'Edit Connections'. Go to the Wireless tab and make sure you have the correct ESSID (network name) and security setup, etc. You will need to get these details from your uni IT department.

Are you sure your card is working and configured with the correct drivers/firmware? If not, plug an ethernet cable in, get online, get updates then check 'Additional Drivers'.

---

### Post by jackey101 on 2012-03-23
yes i have turned on my wifi, i can see the networks and entered correct SSID name and authentication details like username and password. yes i am pretty sure that my card is working properly but unsure that it is configured with the correct drivers/firmware. Can you name the drivers necessary.

---

### Post by Bucky Ball on 2012-03-23
Can you plug in an ethernet cable and get updates as I suggested in my last post? That may set things up for you.

No idea what you need as don't know what wireless card you have. Could you input this in a terminal and post the output back here, please. That will tell us the make and model of the card:

```
sudo lshw -C network
```

(Applications>Accesories>Terminal)

---

### Post by jackey101 on 2012-03-23
outpu of lshw -C network command

 *-network               
       
    description: Ethernet interface
       
    product: NetLink BCM5784M Gigabit Ethernet PCIe
       
    vendor: Broadcom Corporation
       
    physical id: 0
       
    bus info: pci@0000:02:00.0
       
    logical name: eth0
       
    version: 10
       
    serial: 00:1f:16:c9:30:bf
       
    capacity: 1Gbit/s
       
    width: 64 bits
       
    clock: 33MHz
       
    capabilities: pm vpd msi pciexpress bus_master cap_list ethernet 

physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
      

    configuration: autonegotiation=on broadcast=yes driver=tg3 

driverversion=3.116 firmware=sb v2.19 latency=0 link=no multicast=yes 

port=twisted pair
       
    resources: irq:45 
    memory:f4500000-f450ffff
  

*-network
       
    description: Wireless interface
       
    product: WiFi Link 5100
       
    vendor: Intel Corporation
       
    physical id: 0
       
    bus info: pci@0000:04:00.0
       
    logical name: wlan0
       
    version: 00
       
    serial: 00:1e:65:a4:2c:c4
       
    width: 64 bits
       
    clock: 33MHz
       
    capabilities: pm msi pciexpress bus_master cap_list ethernet physical 

wireless
  
    configuration: broadcast=yes driver=iwlagn driverversion=2.6.38-8

-generic firmware=8.83.5.1 build 33692 latency=0 link=no multicast=yes 

wireless=IEEE 802.11abgn
       resources: irq:47 memory:f4600000-f4601fff

---

### Post by Bucky Ball on 2012-03-23
You have this card:

Intel WiFi Link 5100

Sometimes switching off N capabilities helps. There are a couple of fixes here:

[http://ubuntuforums.org/showthread.php?t=1490830](http://ubuntuforums.org/showthread.php?t=1490830)

... and you might like to dig through this:

[http://au.yhs4.search.yahoo.com/search;_ylt=A7exU8J.LG1PViIAGxA36At.?p=WiFi%20Link%205100%20intel%20ubuntu%2010.04&fr2=sb-top&fr=altavista&rd=r1]("http://au.yhs4.search.yahoo.com/search;_ylt=A7exU8J.LG1PViIAGxA36At.?p=WiFi%20Link%205100%20intel%20ubuntu%2010.04&fr2=sb-top&fr=altavista&rd=r1")

I'll have a bit more of a dig myself later ...

You might also like to check you're using the same security type (WEP, WPA, etc) on your local machine as the uni network is using ...

Generally Intel cards are pretty problem free but this one seems to need some gentle persuasion. And yes, the driver seems to be installed ok.

---

### Post by jackey101 on 2012-03-24
> **Bucky Ball said:**
> You have this card:

Intel WiFi Link 5100

Sometimes switching off N capabilities helps. There are a couple of fixes here:

[http://ubuntuforums.org/showthread.php?t=1490830](http://ubuntuforums.org/showthread.php?t=1490830)

... and you might like to dig through this:

[http://au.yhs4.search.yahoo.com/search;_ylt=A7exU8J.LG1PViIAGxA36At.?p=WiFi%20Link%205100%20intel%20ubuntu%2010.04&fr2=sb-top&fr=altavista&rd=r1](http://au.yhs4.search.yahoo.com/search;_ylt=A7exU8J.LG1PViIAGxA36At.?p=WiFi%20Link%205100%20intel%20ubuntu%2010.04&fr2=sb-top&fr=altavista&rd=r1)

I'll have a bit more of a dig myself later ...

You might also like to check you're using the same security type (WEP, WPA, etc) on your local machine as the uni network is using ...

Generally Intel cards are pretty problem free but this one seems to need some gentle persuasion. And yes, the driver seems to be installed ok.


Security Type is  WPA-personal and Encryption type is TKIP. I didnt find anything working in those links...

---

### Post by jackey101 on 2012-03-27
Bump

---

### Post by jackey101 on 2012-03-29
bump bump bump............

---

### Post by Bucky Ball on 2012-03-29
Left click on network icon and 'Connect to Hidden Networks'? Stab in the dark ...

---

### Post by jackey101 on 2012-03-30
> **Bucky Ball said:**
> Left click on network icon and 'Connect to Hidden Networks'? Stab in the dark ...

We dont have any hidden network around here. Still i tried but it was of no use.
In windows, i never had any problem connecting to wireless network, why ubuntu gives me so much trouble. :(

---

### Post by westie457 on 2012-03-30
> **jackey101 said:**
> We dont have any hidden network around here. Still i tried but it was of no use.
In windows, i never had any problem connecting to wireless network, why ubuntu gives me so much trouble. :(

Hi could post the complete output of 'lsmod' please.

---

### Post by jackey101 on 2012-03-31
this is the output of lsmod command

```

Module                  Size  Used by
parport_pc             32111  0 
ppdev                  12849  0 
arc4                   12473  2 
snd_hda_codec_hdmi     27479  1 
snd_hda_codec_realtek   255820  1 
binfmt_misc            13213  1 
i915                  450944  3 
iwlagn                284569  0 
joydev                 17322  0 
snd_hda_intel          24140  4 
acer_wmi               23123  0 
iwlcore               148965  1 iwlagn
sparse_keymap          13666  1 acer_wmi
snd_hda_codec          90901  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13274  1 snd_hda_codec
snd_pcm                80244  4 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25269  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
mac80211              257001  2 iwlagn,iwlcore
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
uvcvideo               66851  0 
snd_timer              28659  2 snd_pcm,snd_seq
drm_kms_helper         40745  1 i915
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
drm                   180037  4 i915,drm_kms_helper
i2c_algo_bit           13184  1 i915
cfg80211              156212  3 iwlagn,iwlcore,mac80211
videodev               75143  1 uvcvideo
psmouse                73312  0 
snd                    55295  17 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
serio_raw              12990  0 
soundcore              12600  1 snd
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
video                  18951  1 i915
lp                     13349  0 
parport                36746  3 parport_pc,ppdev,lp
usbhid                 41704  0 
usb_storage            43946  0 
hid                    77084  1 usbhid
uas                    17676  0 
tg3                   131476  0 
ahci                   21591  6 
libahci                25548  1 ahci


```

---

### Post by westie457 on 2012-04-01
Hi, take a look at this thread [http://ubuntuforums.org/showthread.php?t=1790646&highlight=acer-wmi](http://ubuntuforums.org/showthread.php?t=1790646&highlight=acer-wmi)

Run the commands that have 'acerwmi' in them, Do not run any others because they will do nothing for your problem.

Hope this helps.

---

### Post by michaeldam on 2012-06-20
hi

I have the same truble connecting to wireless, whit the security off in the router there is no problem!
What is or maybe the trouble.
It is after the last update.

michael

---

### Post by Bucky Ball on 2012-06-20
> **michaeldam said:**
> hi

I have the same truble connecting to wireless, whit the security off in the router there is no problem!
What is or maybe the trouble.
It is after the last update.

michael

Welcome.

Please start a new thread with a title describing your problem and as much info as you can give. 

This thread is over two months old and you probably won't get much help here. ;)

---

