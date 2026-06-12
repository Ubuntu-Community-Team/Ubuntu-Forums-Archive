---
title: "Startup Sounds"
date: 2011-04-24
forum: Multimedia Software
---

### Post by Derek Karpinski on 2011-04-24
I have 2 problems:

1. I want to use my internal sound card with the headphone and mic jacks on the front of the PC for skype, and chatting. And I want to use my SB audigy for all the rest.

2. The login sounds are now messed up.

To solve item 1, I was under the impression that Pulseaudio is how I handle that situation.  So I installed:

```
sudo apt-get install padevchooser paman paprefs pavucontrol pavumeter
```

And installed those packages.

Before installing them, the login screen played the 'bongos' fine, and played the 'safari type' login sound after I logged into the Desktop.

Now, while booting after GRUB, I hear a slight pop, then the 'bongos', then after I log in, I hear a static pop, and another static pop, and no safari music in the DE.

All sounds after logging into the desktop seem to work.  I can play songs in rythymbox and hear sound.  It's not really a big deal, but if I leave the volume up loud, the static sounds like crap, and it generally is not impressive.  So, I'd like to fix item 2 before moving on to item 1.

Any help is appreciated!! :D

---

### Post by KegHead on 2011-04-24
Hi!

system...preferences...sound.

KegHead

---

### Post by Derek Karpinski on 2011-04-24
KegHead..........

and do what inside that menu?

Thanks

---

### Post by KegHead on 2011-04-25
Hi!

Make your selections.

KegHead

---

### Post by lidex on 2011-04-28
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---

### Post by Derek Karpinski on 2011-04-28
Thanks lidex,

I have removed the SB card for ease of troubleshooting.  What has changed?

-I hear 'bongos' and 'safari' music on gdm screen and then login. :)
-No more 'scratchy' sound when adjusting volume graphically in some apps.

What has stayed the same?

-That really annoying digital sounding screech right before the gdm screen.

With all that said and done I still can't mute the speakers when I plug the headphones in the front jack.

Here is the info you requested:

[http://www.alsa-project.org/db/?f=600971c6b0a4bd3e5da9b6a219d55883b1c7df7c](http://www.alsa-project.org/db/?f=600971c6b0a4bd3e5da9b6a219d55883b1c7df7c)

:KS

---

### Post by lidex on 2011-04-28
OK. Remove this entry from alsa-base.conf:
```
options snd-hda-intel model=3stack-dig
```
Now run the info script again.

---

### Post by Derek Karpinski on 2011-04-30
lidex,

I installed 11.04, so the alsa-base.conf has been reset. I don't have the popping, or screech noise anymore.  Sound works perfect.  But, I still have no speaker mute when I plug the headphones in the front jack.

I ran your script.

[http://www.alsa-project.org/db/?f=94aff650a44ac29824589cec889b95f7a01cae43](http://www.alsa-project.org/db/?f=94aff650a44ac29824589cec889b95f7a01cae43)

---

### Post by lidex on 2011-04-30
> **Derek Karpinski said:**
> lidex,

I installed 11.04, so the alsa-base.conf has been reset. I don't have the popping, or screech noise anymore.  Sound works perfect.  But, I still have no speaker mute when I plug the headphones in the front jack.

I ran your script.

[http://www.alsa-project.org/db/?f=94aff650a44ac29824589cec889b95f7a01cae43](http://www.alsa-project.org/db/?f=94aff650a44ac29824589cec889b95f7a01cae43)

Let's try adding this to alsa-base.conf:
```
options snd slots=snd-hda-intel
alias snd-card-0 snd-hda-intel
options snd-hda-intel probe_mask=1
```
To edit:
```
gksu gedit /etc/modprobe.d/alsa-base.conf

```
Save. Close. Reboot.

---

### Post by Derek Karpinski on 2011-05-01
lidex,

Sound still works great.........but no speaker mute with headphones.  Although, I could swear I did hear the speakers mute for a tiny bit when I first plugged them in, but couldn't duplicate it.  (It is really late and my ears are playing tricks!)

Again, the info from your script:

[http://www.alsa-project.org/db/?f=ee60b67ca5942aaa7ec95ee158966fb939342d92](http://www.alsa-project.org/db/?f=ee60b67ca5942aaa7ec95ee158966fb939342d92)

Thanks,
Derek

---

### Post by lidex on 2011-05-01
There's some kind of regression with natty alsa for the alc1200. Need to get the devs involved.
Try running this command in a terminal:
```
ubuntu-bug audio
```
Reference the Ubuntu-Bug Audio link in my sig.

---

### Post by Derek Karpinski on 2011-05-02
Thank you lidex. :P

A bug has been filed.

---

### Post by lidex on 2011-05-04
Good deal, can you post the bug link please?

---

