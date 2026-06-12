---
title: "Wireless is disabled by hardware switch"
date: 2011-06-10
forum: Networking &amp; Wireless
---

### Post by xecure on 2011-06-10
Hi guys, Just installed ubuntu 11.04. It told me a driver was missing and installed the Broadcom STA driver. I believe it went on line after that, but I restarted and its not going back online.

Also according to 'rfkill list all' my wifi seems to be hard blocked. Not sure what that means but I hope it helps.

EDIT: also iwconfig outputs this:
```

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
```

---

### Post by bkratz on 2011-06-10
Try 


sudo rfkill unblock all
rfkill list

and see what it says then

---

### Post by xecure on 2011-06-10
> **bkratz said:**
> Try 


sudo rfkill unblock all
rfkill list

and see what it says then

outputs: ```
$ rfkill list
0: dell-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

```

---

### Post by bkratz on 2011-06-11
Well it looks like you are no longer hard or soft blocked, does the wifi work now?  by the way hard blocked usually means the wifi switch is "off".

If not,

what do 

lspci | grep Network
lsmod
sudo iwlist scan

say? By the way those "l's" above are lowercase "L's"

---

### Post by Drone4four on 2011-06-12
I am experiencing a similar problem here.  I Googled wireless is disabled by hardware switch ubuntu and this thread was the first link.  In my case, the problem is not with Broadcom wireless.  I am trying to connect using an AR9285 Atheros Communications Wireless Network Adapter (PCI-Express) -- or at least that is what lspci | grep Network shows. This is a brand new Acer Aspire One 533 net-book.  I was connected and surfing the internet for a few hours and then I think I accidentally but foolishly clicked a pop up I didn't read very carefully and now I can't re-connect.  After entering $ sudo rfkill unblock all, $ rfkill list prints this:

```
$ rfkill list
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: yes
```

Of the following three devices (lo, eth0 and wlan0), $ sudo iwlist scan says: Interface doesn't support scanning.  And wlan0 also says Network is down.

$ sudo /etc/init.d/networking restart says that command is deprecated b/c it may not enable again some interfaces. And then it says Reconfiguring network interfaces...which ends up doing nothing.

I'm running 64 bit Xubuntu natty with the 2.6.38-8-generic kernel.

How do I reconnect?

---

### Post by Drone4four on 2011-06-12
rationalOgre in #ubuntu on FreeNode suggested that I try chording the function key and the key with a blue symbol that looks like an i with radio frequency waves emanating from it.  I recall I was playing with this function key combination when my connection to the internet was severed.  I just didn't make the connection by myself.  Thanks rationalOgre!

---

### Post by thatstrangeguy on 2011-06-12
[SIZE=4]I am havin the same problem as well been working on it to no avile any help would be welcomed here is what we are getting


[/SIZE]```
tanoah@tanoah-Inspiron-1545:~$ sudo rfkill list
[sudo] password for tanoah: 
0: dell-wifi: Wireless LAN
    Soft blocked: yes
    Hard blocked: yes
1: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
tanoah@tanoah-Inspiron-1545:~$ sudo rfkill unblock all
tanoah@tanoah-Inspiron-1545:~$ sudo rfkill list
0: dell-wifi: Wireless LAN
    Soft blocked: yes
    Hard blocked: yes
1: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
tanoah@tanoah-Inspiron-1545:~$ lspci | grep Network
0c:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g LP-PHY (rev 01)
tanoah@tanoah-Inspiron-1545:~$ lsmod
Module                  Size  Used by
nls_utf8               12557  1 
isofs                  40283  1 
binfmt_misc            17565  1 
sha256_generic         21031  2 
cryptd                 20510  0 
aes_x86_64             17208  375 
aes_generic            38279  1 aes_x86_64
parport_pc             36959  0 
ppdev                  17113  0 
dm_crypt               22993  1 
snd_hda_codec_idt      71137  1 
snd_hda_intel          33211  2 
snd_hda_codec         103804  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13604  1 snd_hda_codec
snd_pcm                96625  2 snd_hda_intel,snd_hda_codec
lib80211_crypt_tkip    17387  0 
snd_seq_midi           13324  0 
snd_rawmidi            30486  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
wl                   2568244  0 
snd_seq                61621  2 snd_seq_midi,snd_seq_midi_event
joydev                 17606  0 
snd_timer              29602  2 snd_pcm,snd_seq
uvcvideo               72195  0 
videodev               82052  1 uvcvideo
v4l2_compat_ioctl32    17078  1 videodev
snd_seq_device         14462  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    67382  13 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
lib80211               14991  2 lib80211_crypt_tkip,wl
psmouse                73535  0 
serio_raw              13166  0 
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
dell_laptop            13827  0 
dell_wmi               12681  0 
lp                     17825  0 
dcdbas                 14438  1 dell_laptop
sparse_keymap          13898  1 dell_wmi
parport                46458  3 parport_pc,ppdev,lp
i915                  514985  3 
drm_kms_helper         42136  1 i915
usb_storage            53538  0 
uas                    17996  0 
ahci                   25951  3 
drm                   227495  4 i915,drm_kms_helper
sky2                   58509  0 
i2c_algo_bit           13400  1 i915
libahci                26642  1 ahci
video                  19438  1 i915
tanoah@tanoah-Inspiron-1545:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Failed to read scan data : Invalid argument

tanoah@tanoah-Inspiron-1545:~$ sudo rfkill list
0: dell-wifi: Wireless LAN
    Soft blocked: yes
    Hard blocked: yes
1: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
tanoah@tanoah-Inspiron-1545:~$ 

```[SIZE=4] 

 [/SIZE]

---

### Post by bkratz on 2011-06-12
> **thatstrangeguy said:**
> [SIZE=4]I am havin the same problem as well been working on it to no avile any help would be welcomed here is what we are getting


[/SIZE]```
tanoah@tanoah-Inspiron-1545:~$ sudo rfkill list
[sudo] password for tanoah: 
0: dell-wifi: Wireless LAN
    Soft blocked: yes
    Hard blocked: yes
1: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
tanoah@tanoah-Inspiron-1545:~$ sudo rfkill unblock all
tanoah@tanoah-Inspiron-1545:~$ sudo rfkill list
0: dell-wifi: Wireless LAN
    Soft blocked: yes
    Hard blocked: yes
1: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
tanoah@tanoah-Inspiron-1545:~$ lspci | grep Network
0c:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g LP-PHY (rev 01)
tanoah@tanoah-Inspiron-1545:~$ lsmod
Module                  Size  Used by
nls_utf8               12557  1 
isofs                  40283  1 
binfmt_misc            17565  1 
sha256_generic         21031  2 
cryptd                 20510  0 
aes_x86_64             17208  375 
aes_generic            38279  1 aes_x86_64
parport_pc             36959  0 
ppdev                  17113  0 
dm_crypt               22993  1 
snd_hda_codec_idt      71137  1 
snd_hda_intel          33211  2 
snd_hda_codec         103804  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13604  1 snd_hda_codec
snd_pcm                96625  2 snd_hda_intel,snd_hda_codec
lib80211_crypt_tkip    17387  0 
snd_seq_midi           13324  0 
snd_rawmidi            30486  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
wl                   2568244  0 
snd_seq                61621  2 snd_seq_midi,snd_seq_midi_event
joydev                 17606  0 
snd_timer              29602  2 snd_pcm,snd_seq
uvcvideo               72195  0 
videodev               82052  1 uvcvideo
v4l2_compat_ioctl32    17078  1 videodev
snd_seq_device         14462  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    67382  13 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
lib80211               14991  2 lib80211_crypt_tkip,wl
psmouse                73535  0 
serio_raw              13166  0 
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
[COLOR="Red"]dell_laptop [/COLOR]           13827  0 
dell_wmi               12681  0 
lp                     17825  0 
dcdbas                 14438  1 dell_laptop
sparse_keymap          13898  1 dell_wmi
parport                46458  3 parport_pc,ppdev,lp
i915                  514985  3 
drm_kms_helper         42136  1 i915
usb_storage            53538  0 
uas                    17996  0 
ahci                   25951  3 
drm                   227495  4 i915,drm_kms_helper
sky2                   58509  0 
i2c_algo_bit           13400  1 i915
libahci                26642  1 ahci
video                  19438  1 i915
tanoah@tanoah-Inspiron-1545:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Failed to read scan data : Invalid argument

tanoah@tanoah-Inspiron-1545:~$ sudo rfkill list
0: dell-wifi: Wireless LAN
    Soft blocked: yes
    Hard blocked: yes
1: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
tanoah@tanoah-Inspiron-1545:~$ 

```[SIZE=4] 

 [/SIZE]



Yours could be as simple as



```
sudo rmmod -f dell-laptop
```

Then look at rfkill list again.  If this does help we can make it permanent (it will return when rebooted)  by blacklisting the module.

---

### Post by thatstrangeguy on 2011-06-12
[SIZE=4]I did what you hear it is[/SIZE]


```
tanoah@tanoah-Inspiron-1545:~$ sudo rmmod -f dell-laptop
[sudo] password for tanoah: 
tanoah@tanoah-Inspiron-1545:~$ rfkill list
1: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
tanoah@tanoah-Inspiron-1545:~$ sudo rfkill unblock all
tanoah@tanoah-Inspiron-1545:~$ rfkill list
1: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
tanoah@tanoah-Inspiron-1545:~$

```
[SIZE=4]I still have the hard block on the brcmwl and there is no switch or button on my internal card [/SIZE]

---

### Post by bkratz on 2011-06-12
In your other posting Dr Chilli asked you to check the switch on the laptop not on the card. Is it on?  Is it disabled in the bios?

---

### Post by thatstrangeguy on 2011-06-12
[SIZE=4]I checked that first my widows worked and my bios is in check[/SIZE]

---

### Post by thatstrangeguy on 2011-06-12
[SIZE=4]I have checked[/SIZE]  [SIZE=4]other post it is a bug up stream grrr not shure how to fix it[/SIZE]

---

### Post by thatstrangeguy on 2011-06-12
[SIZE=4]the bios is good and my windows is cheacked[/SIZE]

---

### Post by bkratz on 2011-06-12
Since this appears to be a dual boot system  "I checked that first my widows worked" did you perhaps turn it off while in Windows?  I have seen cases where Ubuntu is unable to turn it back on and it must be done in Windows, then left on.

---

### Post by thatstrangeguy on 2011-06-12
[SIZE=4]it works in windows[/SIZE]

---

### Post by bkratz on 2011-06-12
> **thatstrangeguy said:**
> [SIZE=4]it works in windows[/SIZE]

I realize that, I just wanted to make sure you did not turn it off when in Windows. I don't have any other good ideas--perhaps Dr. Chili will come up with something in your other posting.

---

### Post by thatstrangeguy on 2011-06-12
[SIZE=4]sorry i just mad it short I did not intend to be rude or any thing [/SIZE]

---

### Post by bkratz on 2011-06-12
Did not take it that way, just looking for other postings and possible answers.

---

### Post by xecure on 2011-06-12
> **bkratz said:**
> Well it looks like you are no longer hard or soft blocked, does the wifi work now?  by the way hard blocked usually means the wifi switch is "off".

If not,

what do 

lspci | grep Network
lsmod
sudo iwlist scan

say? By the way those "l's" above are lowercase "L's"

On my laptop hitting fn + f2 usually turns on and off wifi. When I hit fn + f2 now nothing happens. 
Wireless still doesn't work. Infact when i hit network manger on the top corner it doesn't even have a section for wireless.

This is my output:
```
**$ lspci | grep Network**
0b:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)

**~$ lsmod**
Module                  Size  Used by
parport_pc             32111  0 
ppdev                  12849  0 
snd_hda_codec_idt      60537  1 
b44                    35301  0 
ssb                    45942  1 b44
binfmt_misc            13213  1 
snd_hda_intel          24140  2 
snd_hda_codec          90901  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13274  1 snd_hda_codec
snd_pcm                80244  2 snd_hda_intel,snd_hda_codec
i915                  450944  3 
joydev                 17322  0 
dell_wmi               12601  0 
sparse_keymap          13666  1 dell_wmi
wl                   2642531  0 
snd_seq_midi           13132  0 
snd_rawmidi            25269  1 snd_seq_midi
drm_kms_helper         40745  1 i915
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
drm                   180037  4 i915,drm_kms_helper
dell_laptop            13515  0 
dcdbas                 14054  1 dell_laptop
snd_timer              28659  2 snd_pcm,snd_seq
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
r852                   17878  0 
psmouse                73312  0 
serio_raw              12990  0 
i2c_algo_bit           13184  1 i915
sm_common              16737  1 r852
nand                   49822  2 r852,sm_common
nand_ids                8547  1 nand
nand_ecc               13070  1 nand
mtd                    26720  2 sm_common,nand
snd                    55295  13 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
lib80211               14570  1 wl
video                  18951  1 i915
soundcore              12600  1 snd
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
lp                     13349  0 
parport                36746  3 parport_pc,ppdev,lp
firewire_ohci          31504  0 
firewire_core          56138  1 firewire_ohci
sdhci_pci              13623  0 
sdhci                  22720  1 sdhci_pci
crc_itu_t              12627  1 firewire_core

**~$ sudo iwlist scan**
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

```

---

### Post by xecure on 2011-06-12
ok so I got it up and running by following this:
[http://ubuntuforums.org/showpost.php?p=10758325&postcount=25](http://ubuntuforums.org/showpost.php?p=10758325&postcount=25)


But every time I restart I have to type in 'sudo modprobe b43' to get my wireless working again. How can I automate this so I don't have to do it everything I start up?

---

### Post by thatstrangeguy on 2011-06-12
[SIZE=4]That last message did it for me thank you guys so much for you help [/SIZE]

---

### Post by freedomtolearn on 2011-06-16
What worked for me: I run Windows through Virtual Box.  I have a wireless switch (which is really my F2 button on my Inspiron 1545).  Pushing that button in Ubuntu didn't do anything, but then I started up Windows, pushed the button and voilà!  Fixed.

---

### Post by librepensador on 2011-06-29
Hi,

I had the same problem and this solution worked for me. Thanks.

---

