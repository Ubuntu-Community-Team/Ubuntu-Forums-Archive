---
title: "Wireless Became Hard Blocked"
date: 2011-12-15
forum: Networking &amp; Wireless
---

### Post by SteveBenz on 2011-12-15
Hey guys I have a Lenovo Idea Pad and I tried seeing how Debian was and then I thought naah, when I went back to Ubuntu my wireless has been Hard Blocked for no reason, the Wireless Switch is in On and I have tried pressing Fn + F5 (Wireless) this is the rfkill list all result:
```
ubuntu@ubuntu-Lenovo:~$ rfkill list all
0: ideapad_wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: ideapad_bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
2: phy0: Wireless LAN
    Soft blocked: no
    [COLOR=Red]Hard blocked: yes[/COLOR]
ubuntu@ubuntu-Lenovo:~$ 

```I tried rfkill unblock all but nothing is fixing it, I tried rebooting

this is my lspci -nn result:
```
00:00.0 Host bridge [0600]: Intel Corporation N10 Family DMI Bridge [8086:a010]
00:02.0 VGA compatible controller [0300]: Intel Corporation N10 Family Integrated Graphics Controller [8086:a011]
00:02.1 Display controller [0380]: Intel Corporation N10 Family Integrated Graphics Controller [8086:a012]
00:1b.0 Audio device [0403]: Intel Corporation N10/ICH 7 Family High Definition Audio Controller [8086:27d8] (rev 02)
00:1c.0 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 1 [8086:27d0] (rev 02)
00:1c.2 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 3 [8086:27d4] (rev 02)
00:1d.0 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 [8086:27c8] (rev 02)
00:1d.1 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 [8086:27c9] (rev 02)
00:1d.2 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 [8086:27ca] (rev 02)
00:1d.3 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 [8086:27cb] (rev 02)
00:1d.7 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller [8086:27cc] (rev 02)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev e2)
00:1f.0 ISA bridge [0601]: Intel Corporation NM10 Family LPC Controller [8086:27bc] (rev 02)
00:1f.2 SATA controller [0106]: Intel Corporation N10/ICH7 Family SATA AHCI Controller [8086:27c1] (rev 02)
00:1f.3 SMBus [0c05]: Intel Corporation N10/ICH 7 Family SMBus Controller [8086:27da] (rev 02)
05:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 02)
09:00.0 Network controller [0280]: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) [168c:002b] (rev 01)

```I would love for someone to help me because I am flipping out, thanks guys I hope you help

---

### Post by pastalavista on 2011-12-15
Hello and welcome to the forums. You have a common problem as I have had the same with my Asus laptop which has the same wireless adapter (Atheros Communications Inc. AR9285 Wireless Network Adapter) To fix it, first post the output from terminal (Ctrl+Alt+T) of this input```
lsmod
``` to see what driver module you have installed.

---

### Post by SteveBenz on 2011-12-15
lsmod results:
```

Module                  Size  Used by
parport_pc             32114  0 
ppdev                  12849  0 
joydev                 17393  0 
rfcomm                 38408  0 
bnep                   17923  2 
bluetooth             148839  10 rfcomm,bnep
snd_hda_codec_realtek   254125  1 
arc4                   12473  2 
ath9k                 112711  0 
mac80211              393459  1 ath9k
snd_hda_intel          24262  2 
snd_hda_codec          91754  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
uvcvideo               67271  0 
snd_pcm                80435  2 snd_hda_intel,snd_hda_codec
videodev               85626  1 uvcvideo
snd_seq_midi           13132  0 
snd_rawmidi            25241  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
ath9k_common           13599  1 ath9k
ath9k_hw              293933  2 ath9k,ath9k_common
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
psmouse                73673  0 
ath                    19387  2 ath9k,ath9k_hw
serio_raw              12990  0 
cfg80211              172392  3 ath9k,mac80211,ath
snd                    55902  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
ideapad_laptop         13575  0 
soundcore              12600  1 snd
sparse_keymap          13658  1 ideapad_laptop
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
binfmt_misc            17292  1 
i915                  505159  3 
drm_kms_helper         32889  1 i915
drm                   192194  4 i915,drm_kms_helper
i2c_algo_bit           13199  1 i915
wmi                    18744  0 
video                  18908  1 i915
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
ums_realtek            13096  0 
usb_storage            44173  1 ums_realtek
uas                    17699  0 
ahci                   21634  2 
libahci                25727  1 ahci
r8169                  43104  0 
```

---

### Post by praseodym on 2011-12-15
Hi,

try this:

```
sudo modprobe -rfv ath9k
sudo rfkill unblock all
sudo modprobe -v ath9k
```
Check it again. Other methods are: Pressing the keys/buttons permanently or repeatedly during boot-up, check the BIOS settings if it can be activated there, or reset the BIOS.

---

### Post by pastalavista on 2011-12-15
What praseodym advised should work but to keep from having to do that every time you restart, you may need to blacklist the wmi module from loading on boot-up
```
sudo su
echo "blacklist wmi" >> /etc/modprobe.d/blacklist.conf
```

then reboot

---

### Post by SteveBenz on 2011-12-15
none of them worked, wireless is still hard blocked

---

### Post by pastalavista on 2011-12-15
Forgot to have you do this:

```
gksu gedit /etc/rc.local
```
Add one line above Exit 0 

```
rfkill unblock all
```
Proofread, save and close gedit. Then reboot

---

### Post by SteveBenz on 2011-12-15
> **pastalavista said:**
> Forgot to have you do this:

```
gksu gedit /etc/rc.local
```Add one line above Exit 0 

```
rfkill unblock all
```Proofread, save and close gedit. Then reboot
do you mean add ```
rfkill unblock all
``` one line above exit 0?

---

### Post by pastalavista on 2011-12-15
yes

---

### Post by SteveBenz on 2011-12-15
Still says it is disabled by hardware switch (Hard Blocked)

---

### Post by pastalavista on 2011-12-15
Don't understand then. Did you reboot? Did you try the hardware switch again?? These steps have fixed mine and several others. Hope you can find a solution because I don't know any way else.

---

### Post by SteveBenz on 2011-12-15
> **pastalavista said:**
> Don't understand then. Did you reboot? Did you try the hardware switch again?? These steps have fixed mine and several others. Hope you can find a solution because I don't know any way else.
Yes I reboot, yes I tried the hardware switch and the software switch, thanks anyay

---

### Post by praseodym on 2011-12-15
Try in the /etc/rc.local before "exit 0"

```
modprobe -rf ath9k
rfkill unblock all
modprobe ath9k
```

---

### Post by SteveBenz on 2011-12-15
> **praseodym said:**
> Try in the /etc/rc.local before "exit 0"

```
modprobe -rf ath9k
rfkill unblock all
modprobe ath9k
```
still hard blocked

---

### Post by praseodym on 2011-12-15
Did you check/reset the BIOS?

---

### Post by SteveBenz on 2011-12-15
> **praseodym said:**
> Did you check/reset the BIOS?
yea I checked the BIOS and wireless is enabled, how do you reset it?

---

### Post by SteveBenz on 2011-12-15
I have to go recharge the laptop, so I wont be able to reply for awhile. Please keep on putting suggestions I need this fixed, thanks guys

---

### Post by praseodym on 2011-12-15
There should be an option like F9 or whatever in your BIOS

---

### Post by SteveBenz on 2011-12-15
Wireless is still hard blocked even after resetting BIOS
after I reset BIOS I did rfkill list all and the phy0 turned into phy1, can that help?

EDIT: did a normal restart, now the phy1 is back to phy0, but wireless is still Hard Blocked

---

### Post by SteveBenz on 2011-12-15
help anyone?

---

### Post by praseodym on 2011-12-16
Is/was that a dualboot system with windows? Maybe Debian did shut off the card?

---

### Post by SteveBenz on 2011-12-16
> **praseodym said:**
> Is/was that a dualboot system with windows? Maybe Debian did shut off the card?
I never had a dualboot, I only did a LIVE test with debian, could that turn it off? is it possible for me to go back on debian and turn it on, debian is on my USB thats how I did a live test

---

### Post by praseodym on 2011-12-16
Please check in Debian

```
rfkill list
```

---

### Post by SteveBenz on 2011-12-16
I cant rfkill list in debian, says command not found

---

### Post by praseodym on 2011-12-16
Anything with:

```
dmesg | egrep 'radio|kill|switch'
```
there?

---

### Post by SteveBenz on 2011-12-16
> **praseodym said:**
> Anything with:

```
dmesg | egrep 'radio|kill|switch'
```
there?
I used this in debian:

```
[   21.710694] Console: switching to colour frame buffer device 128x37
[   21.748255] Registered led device: ath9k-phy0::radio
```

---

### Post by praseodym on 2011-12-16
Try this module (makes no harm if its not working):

```
sudo modprobe -v fsam7400 radio=1
sudo rfkill unblock all
```

---

### Post by SteveBenz on 2011-12-16
> **praseodym said:**
> Try this module (makes no harm if its not working):

```
sudo modprobe -v fsam7400 radio=1
sudo rfkill unblock all
```

Am I meant to reboot?

---

### Post by praseodym on 2011-12-16
No, check "rfkill list"

---

### Post by SteveBenz on 2011-12-16
Nothing changed

---

### Post by praseodym on 2011-12-17
Try a hardware reset:


[LIST]
[*]Shutdown and shut off

[*]Current cable out _and_ battery out

[*]Press the "On"-button for at least 30 seconds

[*]Battery and current cable in and start the computer
[/LIST]

---

### Post by SteveBenz on 2011-12-17
> **praseodym said:**
> Try a hardware reset:


[LIST]
[*]Shutdown and shut off

[*]Current cable out _and_ battery out

[*]Press the "On"-button for at least 30 seconds

[*]Battery and current cable in and start the computer
[/LIST]
so your saying, 
1. turn off the computer
2. take out the battery and charger
3. Hold the Power button for at least 30 seconds then let go
4. place the battery and charger back in and start the computer
is that what you are trying to say?

---

### Post by praseodym on 2011-12-17
Yes

---

### Post by SteveBenz on 2011-12-17
Still Hard Blocked

---

### Post by SteveBenz on 2011-12-18
can Anyone help me?

---

### Post by praseodym on 2011-12-18
Do you have a Windows CD to install it? Maybe this turns off the hard block...

---

### Post by SteveBenz on 2011-12-18
> **praseodym said:**
> Do you have a Windows CD to install it? Maybe this turns off the hard block...

I have it but I don't want to wait for the install and then to install linux again, is there such thing as a LIVE Windows?

---

### Post by praseodym on 2011-12-18
You can make a Windows Live-CD from an installed system, or you need to buy one. If you install Windows _after_ Ubuntu you need to repair the bootloader, otherwise Ubuntu will not start anymore, because Win overwrites GRUB2. Its always easier to install Ubuntu after Windows

---

### Post by SteveBenz on 2011-12-18
> **praseodym said:**
> You can make a Windows Live-CD from an installed system, or you need to buy one. If you install Windows _after_ Ubuntu you need to repair the bootloader, otherwise Ubuntu will not start anymore, because Win overwrites GRUB2. Its always easier to install Ubuntu after Windows

Ok thanks, should I install Windows XP or 7? can I make a windows live from windows 7? can you give me steps on how to install Ubuntu after windows without losing windows?

---

### Post by praseodym on 2011-12-18
I recommend, saving your data and install Win7 completely with losing Ubuntu. After that install Ubuntu, it recognizes Windows on your hard disc without problems, so you can use both side-by-side.

See here and the links therein:

[https://wiki.ubuntu.com/AsusUL/Installation](https://wiki.ubuntu.com/AsusUL/Installation)

---

### Post by SteveBenz on 2011-12-18
> **praseodym said:**
> I recommend, saving your data and install Win7 completely with losing Ubuntu. After that install Ubuntu, it recognizes Windows on your hard disc without problems, so you can use both side-by-side.

See here and the links therein:

[https://wiki.ubuntu.com/AsusUL/Installation](https://wiki.ubuntu.com/AsusUL/Installation)

thanks man, ill see how it goes and report back

---

### Post by SteveBenz on 2011-12-18
My wireless still doesnt work even after install windows 7, and I installed latest drivers

---

### Post by praseodym on 2011-12-19
This means there is a "real" hardware switch somewhere (hidden), which can not be adressed by a driver! Have a good look anywhere.

---

### Post by SteveBenz on 2011-12-19
> **praseodym said:**
> This means there is a "real" hardware switch somewhere (hidden), which can not be adressed by a driver! Have a good look anywhere.

but it worked perfectly fine before,what I did before it stopped was, install Ubuntu 11.10 then install GNOME 3.2 then did a live test on Debian and then the wireless stopped and then I re-installed ubuntu 11.10 and now I installed windows 7

---

### Post by SteveBenz on 2011-12-19
Wireless LED Turns On before the Windows loads up, can that help?

---

### Post by bastus013 on 2012-05-12
Try
sudo add-apt-repository ppa:webupd8team/jupiter && sudo apt-get update
sudo apt-get install jupiter

Than in jupiter applet
Devices -> enable/disable wifi

---

### Post by tarahmarie on 2012-10-14
I can confirm this bug, and that it replicates on a Lenovo Ideapad Z570. I've submitted it to Launchpad; you guys can see the bug here: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/782137](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/782137)

---

### Post by tarahmarie on 2012-10-18
Hah! Solution is here:

[http://thecowgirlcoder.com/2012/10/18/lenovo-z570-phy0-hard-blocked-solution/](http://thecowgirlcoder.com/2012/10/18/lenovo-z570-phy0-hard-blocked-solution/)

---

### Post by tarahmarie on 2012-10-18
> **mscatopats said:**
> What do you have that you would reuse, hard drives, monitors etc
<snip>

Your post doesn't seem relevant to the topic. Can you clarify?

---

