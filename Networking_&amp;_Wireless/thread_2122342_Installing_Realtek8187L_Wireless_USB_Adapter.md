---
title: "Installing Realtek8187L Wireless USB Adapter"
date: 2013-03-04
forum: Networking &amp; Wireless
---

### Post by Donnie Love on 2013-03-04
I have a Realtek8187L Wireless USB Adapter, and I need to install the drivers in Ubuntu 11.10. It came with instructions, but they are beyond my understanding and I need help.

---

### Post by Donnie Love on 2013-03-05
Here is a view of what's on the driver disk. --> [http://www.donnielove.com/Driver%20disk.html]("http://www.donnielove.com/Driver%20disk.html")

I don't even know where to start. The User Guide is for Windows only. Where do i go from here?

---

### Post by varunendra on 2013-03-05
*Thread moved to **Networking & Wireless**.*
-----------------------------

Please post outputs of -
```
lsusb
lsmod
```

---

### Post by Donnie Love on 2013-03-05
```
donnie@donnie-amdnew:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 0bda:8172 Realtek Semiconductor Corp. RTL8191S WLAN Adapter
Bus 002 Device 002: ID 093a:2510 Pixart Imaging, Inc. Optical Mouse
Bus 001 Device 005: ID 12d1:1035 Huawei Technologies Co., Ltd.
```
```
donnie@donnie-amdnew:~$ lsmod
Module                  Size  Used by
nls_utf8               12493  1 
isofs                  39549  1 
bnep                   17923  2 
rfcomm                 38408  0 
bluetooth             148869  10 bnep,rfcomm
snd_hda_codec_realtek   254163  1 
binfmt_misc            17292  1 
r8712u                163310  0 
ppdev                  12849  0 
snd_hda_intel          28358  2 
snd_hda_codec          91888  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80435  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25241  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
parport_pc             32114  1 
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
nouveau               667359  3 
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    55902  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
ttm                    65224  1 nouveau
drm_kms_helper         32889  1 nouveau
drm                   196290  5 nouveau,ttm,drm_kms_helper
i2c_algo_bit           13199  1 nouveau
mxm_wmi                12859  1 nouveau
wmi                    18744  1 mxm_wmi
video                  19069  1 nouveau
soundcore              12600  1 snd
snd_page_alloc         14108  2 snd_hda_intel,snd_pcm
k10temp                12990  0 
i2c_nforce2            12906  0 
lp                     17455  0 
parport                40930  3 ppdev,parport_pc,lp
usbhid                 41905  0 
usb_storage            44172  0 
hid                    77367  1 usbhid
uas                    17829  0 
sata_nv                23379  3 
forcedeth              58103  0
```

---

### Post by eyeneedhelp on 2013-03-05
ill be watching,,same sw,thanks

---

### Post by varunendra on 2013-03-05
> **Donnie Love said:**
> ```
donnie@donnie-amdnew:~$ lsusb
..
Bus 001 Device 003: ID **[COLOR="#FF0000"]0bda:8172[/COLOR]** **Realtek Semiconductor Corp. RTL8191S WLAN Adapter**

```
```
donnie@donnie-amdnew:~$ lsmod
Module                  Size  Used by
..
**[COLOR="#FF0000"]r8712u  [/COLOR]**              163310  0 

```
As highlighted above, you already have the correct driver loaded for the adapter. Are you unable to detect or connect to any networks ?

What are the outputs of-
```
iwconfig
iwlist scan
rfkill list all
```

**PS:**
Please wrap the output codes in 'Code' tags while posting. It preserves its formatting and makes it more readable.
Follow the 'Code tags example' link in my signature to see how to use it.

---

### Post by Donnie Love on 2013-03-05
```

donnie@donnie-amdnew:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     unassociated  Nickname:"rtl_wifi"
          Mode:Managed  Access Point: Not-Associated   Sensitivity:0/0  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


```
```

donnie@donnie-amdnew:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: <removed mac>
                    ESSID:"ATT504"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:wpa_ie=dd1c0050f20101000050f20202000050f2040050f20201000050f2020c00
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Extra:rsn_ie=30180100000fac020200000fac04000fac020100000fac020c00
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Signal level=62/100  

```
```

donnie@donnie-amdnew:~$ rfkill list all
donnie@donnie-amdnew:~$ rfkill list all
donnie@donnie-amdnew:~$ 

```

---

### Post by varunendra on 2013-03-05
So you are able to detect available wireless networks (ATT504). Does it appear in the Network Manager's drop-down list?

What happens if you click on the wireless network name in that list ? Does it attempt to connect, ask for password etc.?

---

### Post by Donnie Love on 2013-03-05
Yes, it attempts to connect and then asks for password.

---

### Post by praseodym on 2013-03-05
Hi,

the support for 11.10 ends in April. I recommend updating to 12.04. The drivers improved significantly there.

---

### Post by varunendra on 2013-03-05
Then..? Does it fail everytime ?

Check Network Manager settings. Make sure you are using correct encryption type. Also in router, make sure the encryption type is NOT set to WPA/WPA2 mixed mode (preferably, set it to WPA2-only).

Make sure you are entering correct passphrase (mind the small/caps case of letters).

If all these are correct, then please follow the 'Wireless Script' link in my signature, do what the linked post tells to do and post back the contents of "netinfo.txt" file it creates.

**PS:**
A **BIG +1** to what praseodym suggested.

---

### Post by Donnie Love on 2013-03-05
> the support for 11.10 ends in April. I recommend updating to 12.04. The drivers improved significantly there.

Well, that's a whole other discussion. I have found every "new" version to be a great disappointment. It seems they just subtract features, name it after some animal you've never heard of and call it "new". It took me a week to recover from what 11.10 did to my machine, I'm certainly not going to downgrade to any newer versions. I'd actually like to go back a few versions if that were possible.

---

### Post by Donnie Love on 2013-03-05
Yeah, it just keeps asking for a password. I'm on a wired network right now, but I'll be moving to a new office where the network is all wireless. I was hoping to get all the bugs worked out before I move. I don't even know who this ATT504 belongs to.

Also, I'm not clear on what you mean by "Network Manager". This version has "Network Connections," is that the same thing?

[IMG]http://www.donnielove.com/images/Network%20Connections.png[/IMG]

---

### Post by varunendra on 2013-03-05
> **Donnie Love said:**
> Well, that's a whole other discussion. I have found every "new" version to be a great disappointment. It seems they just subtract features, name it after some animal you've never heard of and call it "new". It took me a week to recover from what 11.10 did to my machine, I'm certainly not going to downgrade to any newer versions. I'd actually like to go back a few versions if that were possible.

Well.. I won't do any advocacy then :D

But the recommended way to install a newer version is to 'try' it from a live cd/usb first, then install it only if it seems to play well with your hardware and you are satisfied with its features/performance.

I'd say try the live cd of 12.04 if you haven't already, then decide *(oh, advocacy.... I'll shut up now ;))*

**PS:**
Pangolin is a really nice animal by the way :)

---

### Post by varunendra on 2013-03-05
> **Donnie Love said:**
> I don't even know who this ATT504 belongs to.
Then which one have you been trying to connect ?

> Also, I'm not clear on what you mean by "Network Manager". This version has "Network Connections," is that the same thing?
I hope so. It is the small icon on the right side of the top panel, between the bluetooth and speaker icon in my 12.04 (...mail, battery, BT, NM applet (the network manager), volume control, Date/time.... is the order to be precise).

But its location or label does not matter. As long as it is the default one that gives you the list of available networks, it is Network Manager (or the nm-applet program in other words).

---

### Post by Donnie Love on 2013-03-05
> 'try' it from a live cd/usb first,
That sounds like good advice, varunendra, I'm not sure how to do that, but I will try.

---

### Post by praseodym on 2013-03-05
You need to change the boot setup in your BIOS to CD as first boot device, then insert the CD and reboot

---

### Post by Donnie Love on 2013-03-05
> Then which one have you been trying to connect ?

I'm just trying to see if the device works on my machine before I disconnect here. Having gotten this far, can I assume it is working then, until I get to my new office?

---

### Post by Donnie Love on 2013-03-05
> You need to change the boot setup in your BIOS to CD as first boot device, then insert the CD and reboot

I don't know how to do that, but I'll start a new thread (or look for an old one) when I'm ready to tackle that. I'll probably use a USB device.

---

### Post by Donnie Love on 2013-03-05
Yes, it works.

---

### Post by varunendra on 2013-03-06
> **Donnie Love said:**
> Yes, it works.

So.. Happy to make the switch now? 12.04 ?

---

