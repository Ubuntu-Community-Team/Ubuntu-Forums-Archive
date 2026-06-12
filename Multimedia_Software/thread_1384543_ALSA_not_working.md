---
title: "ALSA not working"
date: 2010-01-18
forum: Multimedia Software
---

### Post by yasmeene on 2010-01-18
Hi all,
I found myself in troubles.
I was trying to get dts passthrough works in many many ways with no success. Finally I (desperately) decided to try OSS rather than ALSA following this guide: [http://https://help.ubuntu.com/community/OpenSound]("http://https://help.ubuntu.com/community/OpenSound")
And there the things went wrong. I ended up with no sound at all so I tried to reinstall alsa again but with no luck.

basicaly what I did after following the guide was:
sudo apt-get install alsa-base alsa-utils

sudo dpkg-reconfigure linux-sound-base //and choose alsa

but still, for example:
$ alsamixer
puts:
alsamixer: function snd_ctl_open failed for default: No such file or directory

$ /etc/init.d/alsa-utils start
* Setting up ALSA...       [ OK ]

but no alsa process at all.

$ aplay -l
aplay: device_list:223: no soundcards found...

It seems to me like sound card drivers are gone..

Any sugestions anybody please?

---

### Post by tarvtarv on 2010-01-18
Hey this is very common dont stress i have installed and re-installed ubuntu heaps of times and nearly always i run into this problem i have an internal mic on my Fujitsu lifebook to add to the confusing list of properties,

To be honest i document most fixes that i use (when they are proven to work), for future reference gotta love tomboy for this!

Sorry to drag on, but this is one of the only problems ive come across, and followed many different guides on and ive never found a definitive method to fix it

dont worry tho i always get it i just open skype or sound recorder and process of elimination change around all the settings till it works,

Hope you can make it work! Mark your thread solved if you do


<edit> I havent ever found re-insalling a package to be of any use.

---

### Post by Yellow Pasque on 2010-01-18
[http://ubuntuforums.org/showthread.php?t=1046137](http://ubuntuforums.org/showthread.php?t=1046137)

---

### Post by yasmeene on 2010-01-20
thanx for an afford, I finally reinstall whole ubuntu and try to reach my sound problem in more sofisticated way than installing packages :o) 

Finnaly I found out that my original audio problems (lost sound in rhytmbox after playing few tracks, cycling sound - like: he-he-he-he-hellou) are caused by SB Live drivers.

if it has any use to anybody who has music drop-outs throught digital output (spdif, iec958):

I found out this lines repeating in /var/log/syslog durring audio lost:

```

alsa-util.c: snd_pcm_avail() returned a value that is exceptionally large:
4294962300 bytes (22369595 ms).
Jan 20 18:41:46 desktop pulseaudio[1479]: alsa-util.c: 
Most likely this is a bug in the ALSA driver 'snd_emu10k1'. 
Please report this issue to the ALSA developers.

```

And when I start investigation I found out this is problem in my soundcard kernel drivers and since Creative isn't very supportive to linux user I switch to another soundcard and my problems hase gone.

As for statement for this bug from main developer of Pulse audio:
> 
Lennart Poettering 2008-12-08 13:30:36 EST 
The Creative drivers are broken. The inform us about "readability" on the audio
device, but when we query with snd_pcm_update_avail() there is actually nothing
to read.

Don't buy Creative. They are uncooperative. They don't like Linux, they don't
like you. So don't give them your money.


Thanx everybody for support

---

### Post by Yellow Pasque on 2010-01-20
> Don't buy Creative. They are uncooperative. They don't like Linux, they don't
like you. So don't give them your money. 
Heh, that's one thing I agree with Lennart on.

---

