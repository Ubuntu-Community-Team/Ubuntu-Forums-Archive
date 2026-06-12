---
title: "Lost sound after 12th July package upgrade"
date: 2006-07-14
forum: Multimedia &amp; Video
---

### Post by Nimefurahi on 2006-07-14
Good day all,

I feel compelled to post this, although there's little scientific substance or brilliance of troubleshooting logic to report. It's just an observation that may or may not help someone who, like me, lost their sound after recent package manager updates. I lost my sound 12th July.

From the terminal, aplay -l listed positive card identification and alsamixer revealed all channels to be properly adjusted.

The "fix" (please don't laugh) was for me to simply access:

System -> Preferences -> Sound

(or gnome-sound-properties from the terminal)

A quick look at the options and all appeared to be normal. I clicked the "Select check box" test button under "System Sounds" and... the sound was restored!

In short, I did absolutely nothing except to bring up the Sound (gnome-sound-properties) utility and the sound was restored.

What can I say except that you never look a gift horse in the mouth!

Cheers

---

### Post by LeTon on 2006-07-14
Indeed....
Not totally though. I can play almost everything as I could, BUT
there's no more sound for realplayer, youtube and google videos!
Any clues?

---

### Post by Nimefurahi on 2006-07-14
Le Ton,

Just curious... is your current sound issue a result of recent (this week's) package upgrades?

---

### Post by Nimefurahi on 2006-07-14
Le Ton,

Hmmm...  I just checked to see if youtube would work for me and it didn't.
So I visited [this thread]("http://www.ubuntuforums.org/showthread.php?t=203723&highlight=lost+sound") and found bullon's reply #6.

After exacting bullon's instructions, a restart of FireFox didn't restore audio to youtube, so I logged out, logged back in again, launched FireFox and visited [fish slapping dance]("http://www.youtube.com/watch?v=ZMKCLyhBBwI") and all seems to work in regard to youtube. Perhaps there is a commonality in this fix with your realplayer and google videos as well.

What have you to lose by trying?

---

### Post by rniella on 2006-07-16
It happened to me too.  I use dapper 6.06 and after the last upgrade (july 12th) I lost all sound, even the drums at the beginning.. any ideas ??  thanks !

RN

---

### Post by Nimefurahi on 2006-07-16
Any ideas?

None other than the aforementioned.

The crazy thing is, that upgrade was supposed to involve only the following:

login 1:4.0.13-7ubuntu3.1 1:4.0.13-7ubuntu3.2
passwd 1:4.0.13-7ubuntu3.1 1:4.0.13-7ubuntu3.2
libxine-main1 1.1.1+ubuntu2-7.1 1.1.1+ubuntu2-7.2
linux-headers-2.6.15-26 2.6.15-26.44
linux-headers-2.6.15-26-686 2.6.15-26.44
linux-headers-686 2.6.15.23
linux-headers-686 2.6.15.24
linux-restricted-modules-common 2.6.15.11-2
linux-restricted-modules-common 2.6.15.11-3
openoffice.org-l10n-en-us 2.0.2-2ubuntu12 2.0.2-2ubuntu12.1
ttf-opensymbol 2.0.2-2ubuntu12 2.0.2-2ubuntu12.1
openoffice.org-core 2.0.2-2ubuntu12 2.0.2-2ubuntu12.1
python-uno 2.0.2-2ubuntu12 2.0.2-2ubuntu12.1
openoffice.org-writer 2.0.2-2ubuntu12 2.0.2-2ubuntu12.1
openoffice.org-calc 2.0.2-2ubuntu12 2.0.2-2ubuntu12.1
openoffice.org-draw 2.0.2-2ubuntu12 2.0.2-2ubuntu12.1
openoffice.org-impress 2.0.2-2ubuntu12 2.0.2-2ubuntu12.1
openoffice.org-math 2.0.2-2ubuntu12 2.0.2-2ubuntu12.1
openoffice.org-java-common 2.0.2-2ubuntu12 2.0.2-2ubuntu12.1
openoffice.org-base 2.0.2-2ubuntu12 2.0.2-2ubuntu12.1
openoffice.org 2.0.2-2ubuntu12 2.0.2-2ubuntu12.1
python2.4-samba 3.0.22-1ubuntu3 3.0.22-1ubuntu3.1
smbfs 3.0.22-1ubuntu3 3.0.22-1ubuntu3.1
smbclient 3.0.22-1ubuntu3 3.0.22-1ubuntu3.1
samba 3.0.22-1ubuntu3 3.0.22-1ubuntu3.1
samba-common 3.0.22-1ubuntu3 3.0.22-1ubuntu3.1
libsmbclient 3.0.22-1ubuntu3 3.0.22-1ubuntu3.1

I've yet to see where these would have an impact on sound. A sheer mystery to me. But just for the heck of it, from a terminal run gnome-sound-properties and let me know what happens, if anything.

---

### Post by catlett on 2006-07-16
It appears the sound issue was inflicted on purpose. This is an excerpt from the bug report, [https://launchpad.net/distros/ubuntu/+source/flashplugin-nonfree/+bug/29760](https://launchpad.net/distros/ubuntu/+source/flashplugin-nonfree/+bug/29760) which states that during the next update the way flash plays sound will change and it will cause isues.
> It is therefore my opinion that the instabilities these arrangements
introduce into the operating system's core web browser are
(a) unacceptable and (b) not straightforward to remedy while
maintaining the current approach.

I will therefore be changing the default configuration of dapper's
firefox so that it does not use the LD_PRELOAD hack. This will make
the web browser more stable but cause trouble with sound for users
using Flash. I consider this the appropriate tradeoff.

---

### Post by ericesque on 2006-07-17
If you lost all sound, check to make sure that your external amp is not checked in the volume manager.

here's a link on fixing the issue (probably works for non AC97 audio)

[http://www.ubuntuforums.org/showthread.php?t=189276](http://www.ubuntuforums.org/showthread.php?t=189276)

---

### Post by catlett on 2006-07-17
Hi everyone. I had sound and then I got the update. I still had sound in all aplications (xmms, xine media player etc) But I had no sound in firefox with flash.
I was very discouraged when I found the bug report which stated they knew this would happen because they changed the way firefox would deal with sound in Ubuntu. [https://launchpad.net/distros/ubuntu...ree/+bug/29760](https://launchpad.net/distros/ubuntu...ree/+bug/29760) 
But this is the Ubuntu forums. I kept searching and trying stuff until I fixed my problem.
I solved my firefox sound issue with a mix of these 2 threads and of course this one. [http://www.ubuntuforums.org/showthread.php?t=203723&highlight=lost+sound](http://www.ubuntuforums.org/showthread.php?t=203723&highlight=lost+sound)
 [http://www.ubuntuforums.org/showthread.php?t=186594&highlight=alsa](http://www.ubuntuforums.org/showthread.php?t=186594&highlight=alsa)
I don't know what worked when but this is what I did.
```
sudo apt-get install alsa-oss
```
```
sudo gedit /etc/firefox/firefoxrc
```
Then I changed it to say 
```
FIREFOX_DSP="aoss"
```
Then I edited ~/.asoundrc 
```
sudo gedit ~/.asoundrc
```
 I edited it by adding 
```
pcm.!default {
 type plug
  slave.pcm "dmix"
}
```
Then I edited /etc/environment
```
sudo gedit /etc/environment
```
by adding to it
```
FIREFOX_DSP=aoss
```

The last thing I did was make sure I had the correct sound card chosen. On the volume control at the top panel I opened up the volume control. From there I went to File<Change Devices
It had the wrong card selected. I had sound everywhere but firefox so I don't know how much this affected it. I was having issues with the wrong sound card chosen when I started up. I was going to System<Preferences<Sound to change cards. I just wanted to add it just in case.
I saved all the files and rebooted. Right now a fine young man is playing Scherzo in B minor by Chopin on You Tube. Chopin never sounded so good. No sound for a few weeks will do that to the classics.:-D 
I hope it helps someone else. If it doesn't, browse the links. Some people edited with "none", others edited with "auto".
The bug report sited one person who went to the Gentoo wiki and solved it.  [http://gentoo-wiki.com/HOWTO_ALSA_sound_mixer_aka_dmix#The_dmix_device](http://gentoo-wiki.com/HOWTO_ALSA_sound_mixer_aka_dmix#The_dmix_device)
Good luck.

---

### Post by odyniec on 2006-07-18
I had a similar problem after a recent system update -- no sound at all, aplay complaining about invalid arguments. It turned out reloading the soundcard driver module did the trick:
```
sudo rmmod snd-hda-intel
sudo modprobe snd-hda-intel
```

---

