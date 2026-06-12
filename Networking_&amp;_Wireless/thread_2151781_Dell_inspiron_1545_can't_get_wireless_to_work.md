---
title: "Dell inspiron 1545 can't get wireless to work"
date: 2013-06-05
forum: Networking &amp; Wireless
---

### Post by Bryant777 on 2013-06-05
I just installed Ubuntu Studio 13.04 on this laptop but can't get wireless to show up.   I did a sudo lshw -C network and show  Broadcom BCM4312 802.11 b/g LP-PHY.  I need help with next steps.
thanks!

---

### Post by ahallubuntu on 2013-06-05
~

---

### Post by Hadaka on 2013-06-05
Hi Bryant777 and welcome
please open a terminal - ctrl/alt/t
then Copy and paste the following commands.
```
lspci -n | grep 0280
rfkill list
lsmod
```
post the results.
thanks.

---

### Post by Bryant777 on 2013-06-05
house@house-Inspiron-1545:~/Desktop$ lspci -n | grep 0280
0c:00.0 0280: 14e4:4315 (rev 01)
house@house-Inspiron-1545:~/Desktop$ rfkill list
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
house@house-Inspiron-1545:~/Desktop$ lsmod
Module                  Size  Used by
parport_pc             27504  0 
ppdev                  12817  0 
rfcomm                 37420  0 
bnep                   17669  2 
bluetooth             202046  10 bnep,rfcomm
binfmt_misc            17260  1 
snd_hda_codec_idt      63896  1 
arc4                   12543  2 
snd_hda_intel          38307  3 
joydev                 17097  0 
snd_hda_codec         117580  2 snd_hda_codec_idt,snd_hda_intel
b43                   351918  0 
snd_hwdep              13272  1 snd_hda_codec
snd_pcm                80890  2 snd_hda_codec,snd_hda_intel
snd_page_alloc         14230  2 snd_pcm,snd_hda_intel
bcma                   39645  1 b43
snd_seq_midi           13132  0 
i915                  531502  2 
mac80211              534711  1 b43
snd_seq_midi_event     14475  1 snd_seq_midi
snd_rawmidi            25114  1 snd_seq_midi
snd_seq                51280  2 snd_seq_midi_event,snd_seq_midi
cfg80211              444369  2 b43,mac80211
snd_seq_device         14137  3 snd_seq,snd_rawmidi,snd_seq_midi
drm_kms_helper         47545  1 i915
coretemp               13131  0 
drm                   232846  3 i915,drm_kms_helper
snd_timer              24411  2 snd_pcm,snd_seq
snd                    56485  15 snd_hwdep,snd_timer,snd_hda_codec_idt,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device
psmouse                81038  0 
soundcore              12600  1 snd
dell_laptop            17161  0 
gpio_ich               13236  0 
dcdbas                 14021  1 dell_laptop
i2c_algo_bit           13197  1 i915
dell_wmi               12601  0 
microcode              18286  0 
serio_raw              13031  0 
sparse_keymap          13658  1 dell_wmi
lpc_ich                16925  0 
mac_hid                13037  0 
wmi                    18590  1 dell_wmi
video                  18894  1 i915
lp                     13299  0 
parport                40753  3 lp,ppdev,parport_pc
ums_realtek            17669  0 is
usb_storage            47684  1 ums_realtek
ahci                   25507  2 
libahci                26108  1 ahci
sky2                   52846  0 
ssb                    50834  1 b43

 I could not find the pipe symbol.  I took a chance on shift key \ which is a double vertical line.  I dont' think that is  it.
I see the hard switch is off.  The only wireless switch I see is FN + F2 (antenna symbol).  That did not work. 

 I can tell that I also need to turn off tap to click option. cursor jumping all over the place.

---

### Post by Bryant777 on 2013-06-05
> **ahallubuntu said:**
> Do some searching - there are lots of threads on how to get wireless working in Ubuntu with Broadcom wireless cards.  It's probably just a few terminal commands.  Being plugged in (wired) temporarily to the internet will make things much easier.

If you ever feel like upgrading your wireless card in your 1545 to an Intel card: I put an Intel WiFi link 5100 card in my Inspiron 1545 (running 9.10, then 10.04, now 12.04).  The wireless has always worked automatically (and well) in every version of Ubuntu I've used.  (I don't care for Broadcom wireless cards in Linux.)  You need a "half height" 5100 card (not "full height"), but don't get the version for HP/Lenovo/IBM.  You can get a used 5100 half-height card off eBay for about $5 USD used.  It's easy to install: pop off the oblong panel on the bottom, pop off the two antenna wiress, one screw to remove the card, and replace.  I did upgrade my 1545's BIOS to A14 (latest) first, though - through Windows.

This is a laptop.  Thanks.  I think I do need better wifi card.

---

### Post by ahallubuntu on 2013-06-05
~

---

### Post by ahallubuntu on 2013-06-05
~

---

### Post by Bryant777 on 2013-06-05
> **ahallubuntu said:**
> Yes, "Pipe"  (|) is the shift of the \ key (above Enter).

Fn + F2 toggles wireless on and off on the 1545.  If it were off, "rfkill list all" would show a hard block.  Try the command again, hit Fn + F2 and then (up arrow in terminal) to try again to see the difference.  Just make sure it's not hard blocked before you proceed.

Try these instructions to get the driver installed correctly.  As I said above, it will be easier if you are wired temporarily to the internet until you get wireless working:

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

(Try the instructions under "11.10 (Oneiric Ocelot) - 12.10 (Quantal Quetzal)")

house@house-Inspiron-1545:~/Desktop$ rfkill list all
0: phy0: Wireless LAN, 
    Soft blocked: no
    Hard blocked: yes

As you see, it is hard blocked.  I can't change it.  Mamy tries but no success.
I used Software Center to get the b43 drivers but with no success.  Do you know how I turn off tap to click???

---

### Post by Bryant777 on 2013-06-05
> **ahallubuntu said:**
>   As I said above, it will be easier if you are wired temporarily to the internet until you get wireless working:


I have ethernet connection.  Thanks

---

### Post by Hadaka on 2013-06-05
Hi, your card driver is determined by this number [14e4:4315]
so you can do from a wired connection..
```
sudo apt get install firmware-b43-lpphy-installer
sudo modprobe b43
```
or probably..(and i prefer)
```
sudo apt-get install linux-firmware-nonfree
sudo modprobe b43
```
but first you need to ublock the hard block
try this..
```
sudo rfkill unblock all
rfkill list
```
if it isnt cleared then
press Fn/F2  one time time and check with
```
rfkill list all
```
if it still isnt cleared go into BIOS and reset the wireless and the pci enable
keep us posted.
thanks.

---

### Post by ahallubuntu on 2013-06-05
~

---

### Post by Bryant777 on 2013-06-05
> **Hadaka said:**
> Hi, your card driver is determined by this number [14e4:4315]
so you can do from a wired connection..
```
sudo apt get install firmware-b43-lpphy-installer
sudo modprobe b43
```
or probably..(and i prefer)
```
sudo apt-get install linux-firmware-nonfree
sudo modprobe b43
```
but first you need to ublock the hard block
try this..
```
sudo rfkill unblock all
rfkill list
```
if it isnt cleared then
press Fn/F2  one time time and check with
```
rfkill list all
```
if it still isnt cleared go into BIOS and reset the wireless and the pci enable
keep us posted.
thanks.

Yeah!  Trip to BIOS fixed the hard switch off.  I was then able to get the drivers and I am on wifi.
Thanks very much!!!

If I can just get the touch pad driver and get that option for tap to click turned off, I will be totally happy with this laptop.

---

### Post by ahallubuntu on 2013-06-05
~

---

### Post by Bryant777 on 2013-06-05
It was jumping like crazy.  That was because the tap to click option was enabled.  I went to software center and found using search term "touchpad" a little program to provide controls which allowed me to turn off option.

I am now very happy.  I love ubuntu studio 13.04.  It is the best distro I have used/tested.  I have been through about 15 distros in last month.

---

### Post by Hadaka on 2013-06-05
Great !..glad the wireless is working.
on your touch pad..
click the cog wheel...launcher..left side
then
click ..mouse/touchpad
im attaching a screen shot of mine...i also have a dell.
and lastly, since your post was for wireless and its fixed..
please mark this thread solved..
How to -> [https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)
[ATTACH=CONFIG]243547[/ATTACH]
if its still not fixed post a new thread....thanks.

---

### Post by Bryant777 on 2013-06-05
Thanks, all is good!

---

