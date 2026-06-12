---
title: "No Sound"
date: 2018-07-20
forum: Multimedia Software
---

### Post by skyesharica on 2018-07-20
Hi Linux Friends,
I have a desktop with Ubuntu 16.04 LTS.  I am unable to get any sound - either through music software, or online with UTube etc.  I'd like to listen to some music.  
Thanks  :popcorn:

---

### Post by yancek on 2018-07-20
Post info on your sound card with the command:  inxi -A
Additionally, has it ever worked?  What happens when you try to play a music file?

---

### Post by mIk3_08 on 2018-07-20
> **yancek said:**
> Post info on your sound card with the command:  inxi -A
Additionally, has it ever worked?  What happens when you try to play a music file?

yes, or you may have to install inxi

```
sudo apt-get install inxi
```

---

### Post by skyesharica on 2018-07-20
> **yancek said:**
> Post info on your sound card with the command:  inxi -A

Audio:     Card-1 Intel 8 Series/C220 Series High Definition Audio Controller
           driver: snd_hda_intel
           Card-2 NVIDIA High Definition Audio Controller
           driver: snd_hda_intel
           Sound: Advanced Linux Sound Architecture v: k4.4.0-131-generic

Yes, it has worked in the past.  If I try to play a music file simply nothing happens, there's no sound regardless of whether I have gmusicbrowser, or Parole Media Player or VLC Media Player open.

> **mIk3_08 said:**
> yes, or you may have to install inxi

```
sudo apt-get install inxi
```

I just tried and got this.  It appears I'm already up to date.:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
inxi is already the newest version (2.2.35-0ubuntu1).
The following package was automatically installed and is no longer required:
  libllvm5.0
Use 'sudo apt autoremove' to remove it.
0 to upgrade, 0 to newly install, 0 to remove and 1 not to upgrade.

:guitar:

---

### Post by mIk3_08 on 2018-07-20
> **skyesharica said:**
> Audio:     Card-1 Intel 8 Series/C220 Series High Definition Audio Controller
           driver: snd_hda_intel
           Card-2 NVIDIA High Definition Audio Controller
           driver: snd_hda_intel
           Sound: Advanced Linux Sound Architecture v: k4.4.0-131-generic

Yes, it has worked in the past.  If I try to play a music file simply nothing happens, there's no sound regardless of whether I have gmusicbrowser, or Parole Media Player or VLC Media Player open.


Do you mean do you have 2 audio card?

---

### Post by shantiq on 2018-07-20
Hi [**[COLOR=#000000]skyesharica[/COLOR]**]("https://ubuntuforums.org/member.php?u=1835597")
install **pavucontrol **and check all settings whilst you are playing a piece of music even even if you cannot hear it at first
play with settings on Configuration and Output Devices
see if it kicks in on one of the settings

---

### Post by skyesharica on 2018-07-20
Don't know how many audio cards I have.  There doesn't appear to be a software that shows you your machine's specifications, with Ubuntu.

> **shantiq said:**
> Hi [**[COLOR=#000000]skyesharica[/COLOR]**]("https://ubuntuforums.org/member.php?u=1835597")
install **pavucontrol **and check all settings whilst you are playing a piece of music even even if you cannot hear it at first
play with settings on Configuration and Output Devices
see if it kicks in on one of the settings

Thanks so much for replying to my PM shantiq.  PulseAudio Volume Control (pavucontrol) is already installed.  I've played around with the settings - there's a great deal of them so I didn't click on all of them - but nothing happens.

---

### Post by ardouronerous on 2018-07-20
Like shantiq said, install pavucontrol via Terminal:

```
 sudo apt-get install pavucontrol
```

In the Applications Menu, look for PulseAudio Volume Control.

In PulseAudio, go to Output Devices and check if anything is either set to mute or set to 0%.

> **skyesharica said:**
> I've played around with the settings - there's a great deal of them so I didn't click on all of them - but nothing happens.

In the Configuration tab, in Built-in Audio, check the profile, mine is set to Analog Stereo Duplex.

---

### Post by skyesharica on 2018-07-20
> **ardouronerous said:**
> Like shantiq said, install pavucontrol via Terminal:

```
 sudo apt-get install pavucontrol
```

In the Applications Menu, look for PulseAudio Volume Control.

In PulseAudio, go to Output Devices and check if anything is either set to mute or set to 0%.

Done that.  Terminal says:  "pavucontrol is already the newest version (3.0-3build1)."  Went to Output Devices in PulseAudio and nothing is set to mute or 0%.

> **ardouronerous said:**
> In the Configuration tab, in Built-in Audio, check the profile, mine is set to Analog Stereo Duplex.

Yes, mine is set to Analog Stereo Duplex too, thanks.

---

### Post by ardouronerous on 2018-07-20
Are you on a Desktop or Laptop?
If on a Desktop, check if the speakers are turned on. If they are on, check if the audio jack is lose or disconnected.

Just checking all possibilities lol :)

---

### Post by skyesharica on 2018-07-20
> **ardouronerous said:**
> Are you on a Desktop or Laptop?
If on a Desktop, check if the speakers are turned on. If they are on, check if the audio jack is lose or disconnected.

Thanks.  I'm on a desktop and I don't have speakers attached.

---

### Post by ardouronerous on 2018-07-20
Does your desktop have built-in speakers?
Normally, a standard desktop needs external speakers in order to get sound.

---

### Post by skyesharica on 2018-07-21
> **ardouronerous said:**
> Does your desktop have built-in speakers?
Normally, a standard desktop needs external speakers in order to get sound.

Well thankyou.  Great.  I don't know why but I tried attaching some small speakers and it worked!  I must have changed one setting or other because it didn't work before.  I'm playing "Star Man" by the late )-: David Bowie.  The sound is quite bad - I probably downloaded the song online.  Whoops.  :guitar:
Thankyou all my Linux friends and shantiq.

---

### Post by ardouronerous on 2018-07-21
No problem, glad your issue is fixed.
Maybe you can look around for better speakers?

---

### Post by skyesharica on 2018-07-21
> **ardouronerous said:**
> No problem, glad your issue is fixed.
Maybe you can look around for better speakers?

Thanks for that.  Yes, the sound is still shocking - all crackly and a bit warped - I guess it is the speakers - they were given to me.  :guitar:

---

### Post by skyesharica on 2018-07-21
> **mIk3_08 said:**
> Cool stuff you solve it. Good luck.

Thanks.  My speakers are terrible - I'll have to save up for some.  Thanks again.

---

### Post by sangamswadik on 2018-07-21
Can anyone help me with this?

[https://ubuntuforums.org/showthread.php?t=2396689](https://ubuntuforums.org/showthread.php?t=2396689)

---

