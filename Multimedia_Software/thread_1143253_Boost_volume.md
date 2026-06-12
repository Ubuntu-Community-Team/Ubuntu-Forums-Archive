---
title: "Boost volume"
date: 2009-04-29
forum: Multimedia Software
---

### Post by SneakyBooBoo on 2009-04-29
I'm sure this has probably been asked before, but i can't find any threads on how to boost volume on my Ubuntu. I've got an Acer 5620z laptop and sometimes i need to turn the volume on full in ubuntu just to hear a little. Is there a tweak or a patch or workaround i can use to boost my volume in ubuntu?

Its not the card or the media because the sound in xp is perfect.

Sorry if i'm repeating a post.

Thanks in advance.

---

### Post by mcbagpipe89 on 2009-04-29
I'm having the exact same problem.  One thing I have done that helps, is to install VLC (available via synaptic, or the add/remove menu under applications).  It is able to boost volume to levels exceeding that of other programs.  While it is not a fix, it can make listening to music and watching movies a bit nicer.

---

### Post by lovinglinux on 2009-04-29
First check in the "Volume Control" if the "Master", "PCM" and "Front" volumes are all the way up.

If you use mplayer, totem, gnome-mplayer, smplayer or other frontend for mplayer, then you can add this line to ~/.mplayer/config

```
[default]

af=volume=10:0
```

This will boost the audio of the player by 10 Db.

---

### Post by mcbagpipe89 on 2009-04-29
Is there a way to boost the volume across the whole system?  I.E. make the system volume maximum higher? Oh, and thank you for the tip!

---

### Post by mail.prabal on 2009-07-22
I am having a same problem problem on my desktop...all my volume bars are high,but not my system volume....

the corresponding speaker volume in xp just blasts all out....bt not in ubuntu...

plzz help

---

### Post by Francewhoa on 2009-09-17
Open Applications> Accessories> Terminal
Then type the following:
```
sudo gedit /etc/modprobe.d/alsa-base
```Then type your password if it asks for it
Once gedit opens up with this document scroll down to the end of the page
the last three line will look like this:

```
options snd-usb-caiaq index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
```Add one new line. So final result should be like the following.
```

options snd-usb-caiaq index=-2
options snd-hda-intel model=3stack
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388

```Save and restart the computer it should work.

Thanks to mssg131187

---

### Post by csatlas on 2009-10-12
I had the same problem (couldn't hear loud enough from desktop - speakers)
solved it by changing preferences in

System>Preferences>Sound>Devices>Sound Events

I selected OSS - Open Sound System


now, sound is even louder than my win xp
I hope it works!

---

### Post by lovinglinux on 2009-10-12
Pulseaudio in Karmic Beta has a volume booster. I thought you would like to know. The final release of Karmic will be in just a few days.

---

### Post by Fingaluna on 2010-12-28
Hi All,

I know I am replying to an ancient thread, but it is relevant to me...

As I am fairly new to Linux, I am not sure where to find the ~/.mplayer/config file to edit. Can someone please direct me where to find this file? I have spent about 1/2 an hour searching my system, but I don't really know where to look.

I should mention that I am using the Jolicloud version of ubuntu. Version 1.0 to be precise.

Thanks!


> **lovinglinux said:**
> First check in the "Volume Control" if the "Master", "PCM" and "Front" volumes are all the way up.

If you use mplayer, totem, gnome-mplayer, smplayer or other frontend for mplayer, then you can add this line to ~/.mplayer/config

```
[default]

af=volume=10:0
```

This will boost the audio of the player by 10 Db.

---

### Post by davec64 on 2010-12-28
HI it's in a hidden folder in your home folder. The full stop at the beginning of .mplayer denotes this.
In the file browser (Nautilus), go to **View** and select **Show Hidden files and folders**.

You should be able to see it now!  :)

---

