---
title: "Wireless networking on Packard Bell easynote tn36 ubunto 11.04"
date: 2011-05-01
forum: Networking &amp; Wireless
---

### Post by SAJA4 on 2011-05-01
Hi everyone..

I have Packard Bell easynote tn36 and I used to use ubuntu 10.10 and  then when I upgrad it to ubuntu 11.04 the wireless doesn't work (disable)  and I can't press the  botton of Enable wireless. 

what can I do !!

---

### Post by deuz on 2011-05-02
Yess, I've exacly the same issue, with something like
$ iwconfig wlan0 up 

I got the light of the wireless card to work -- but not the wireless itself. I might have a look at another linux.. it sucks if you upgrade & your computer doesn't work anymore, I just don't have time to try 10 things at this moment

---

### Post by deuz on 2011-05-02
Ok, this works
$ sudo ifconfig wlan0 up
$ sudo iwlist wlan0 scan
$ sudo iwconfig wlan0 essid "campusnet"
$ sudo dhclient wlan0
which shows wireless networks and I was able to make a connection with the console

so now I can surf wireless but the wireless applet doesn't work at all.. and I have to do it always manually.. Anyone an idea how to fix the wireless applet & make it automatic?

---

### Post by SAJA4 on 2011-05-03
I try the code but it's doesn't work ..

this is the result
> saja@saja-EASYNOTE-TN36:~$ sudo ifconfig wlan0 up
[sudo] password for saja: 
SIOCSIFFLAGS: Operation not possible due to RF-kill
saja@saja-EASYNOTE-TN36:~$

---

### Post by josephmills on 2011-05-03
try 

```

rfkill unblock all 

```
if that dosent work try 
```

rfkill unblock wifi 

```
then let us see 
```

rfkill list all 

```
thanks

---

### Post by SAJA4 on 2011-05-03
I try the three code but there is no change at all ..

---

### Post by josephmills on 2011-05-03
> **SAJA4 said:**
> I try the three code but there is no change at all ..

could you please copy and paste what the terminal says thanks

---

### Post by SAJA4 on 2011-05-04
this is what the terminal says:

> saja@saja-EASYNOTE-TN36:~$ rfkill unblock all
saja@saja-EASYNOTE-TN36:~$ rfkill unblock wifi
saja@saja-EASYNOTE-TN36:~$ rfkill list all
0: acer-wireless: Wireless LAN
    Soft blocked: yes
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
saja@saja-EASYNOTE-TN36:~$ 

---

### Post by deuz on 2011-05-05
First do the unblocking josephmills suggests
 
$ rfkill unblock wifi

then try this again;

$ sudo ifconfig wlan0 up
$ sudo iwlist wlan0 scan

[I][B]do you see any wireless networks now?
[/B][/I]

$ sudo iwconfig wlan0 essid "campusnet" 
 *(^ replace "campusnet" with the essid from the network you want to connect to )* 

$ sudo dhclient wlan0

---

### Post by SAJA4 on 2011-06-02
> **deuz said:**
> First do the unblocking josephmills suggests
 
$ rfkill unblock wifi

then try this again;

$ sudo ifconfig wlan0 up
$ sudo iwlist wlan0 scan

[I][B]do you see any wireless networks now?
[/B][/I]

$ sudo iwconfig wlan0 essid "campusnet" 
 *(^ replace "campusnet" with the essid from the network you want to connect to )* 

$ sudo dhclient wlan0

I did this but still It's not working

---

### Post by josephmills on 2011-06-02
could we see a ```
lsmod
``` thanks

---

### Post by SAJA4 on 2011-06-02
> **josephmills said:**
> could we see a ```
lsmod
``` thanks


```
saja@saja-EASYNOTE-TN36:~$ lsmod
Module                  Size  Used by
arc4                   12473  2 
ath9k                 103633  0 
mac80211              257001  1 ath9k
ath9k_common           13611  1 ath9k
ath9k_hw              300328  2 ath9k,ath9k_common
ath                    19141  2 ath9k,ath9k_hw
cfg80211              156212  3 ath9k,mac80211,ath
binfmt_misc            13213  1 
vboxnetadp             13323  0 
vboxnetflt             27855  0 
vboxdrv               219250  2 vboxnetadp,vboxnetflt
parport_pc             32111  0 
dm_crypt               22463  0 
ppdev                  12849  0 
snd_hda_codec_realtek   255820  1 
snd_hda_intel          24140  4 
snd_hda_codec          90901  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13274  1 snd_hda_codec
snd_pcm                80244  3 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25269  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28659  2 snd_pcm,snd_seq
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    55295  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              12600  1 snd
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
joydev                 17322  0 
uvcvideo               66851  0 
videodev               75143  1 uvcvideo
psmouse                73312  0 
serio_raw              12990  0 
acer_wmi               23123  0 
ndiswrapper           192828  0 
sparse_keymap          13666  1 acer_wmi
lp                     13349  0 
parport                36746  3 parport_pc,ppdev,lp
usb_storage            43946  0 
usbhid                 41704  0 
hid                    77084  1 usbhid
uas                    17676  0 
i915                  450944  3 
drm_kms_helper         40745  1 i915
drm                   180037  4 i915,drm_kms_helper
ahci                   21591  2 
libahci                25548  1 ahci
r8169                  42534  0 
i2c_algo_bit           13184  1 i915
video                  18951  1 i915
saja@saja-EASYNOTE-TN36:~$
```

---

### Post by josephmills on 2011-06-02
acer_wmi   what is that doing there lets play with it and see if it does anything ```
sudo rmmod -f acer_wmi
``` then let us see a ```
rfkill list all
``` thanks

---

### Post by SAJA4 on 2011-06-03
> **josephmills said:**
> acer_wmi   what is that doing there lets play with it and see if it does anything ```
sudo rmmod -f acer_wmi
``` then let us see a ```
rfkill list all
``` thanks



**see this **

```
saja@saja-EASYNOTE-TN36:~$ sudo rmmod -f acer_wmi
[sudo] password for saja: 
saja@saja-EASYNOTE-TN36:~$ rfkill list all
1: phy0: Wireless LAN
    Soft blocked: yes
    Hard blocked: yes
saja@saja-EASYNOTE-TN36:~$ 
```

**Thanks for help**

---

### Post by SAJA4 on 2011-06-04
Where are you?
What should i do now?

---

### Post by SAJA4 on 2011-06-08
**No one knows how to fix it :(**

---

### Post by spaceinvader on 2011-06-12
hi not sure if this will help but on my packbell easy NOT lspci can see the card,  any card,  but it wont work..but by adding to the end of the boot line in grub,after quiet splash   ' acpi=force pnpbios=off  irqpoll'  it works !!

---

### Post by spaceinvader on 2011-06-12
sorry edit to above post ' acpi=force  pnpbios=off  irqpoll '
hit shift at boot to get grub menu and e to edit line.

if it works then to make it permanent edit grub..
with various boot switches i've got several elderly laptops working
regards Theo

---

### Post by SAJA4 on 2011-07-22
[spaceinvader]("http://ubuntuforums.org/member.php?u=759124")

[B]I try what you said but still doesn't work nothing change 
 
any idea?[/B]

---

