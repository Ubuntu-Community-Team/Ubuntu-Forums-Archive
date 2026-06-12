---
title: "Totem permanent Slow-Mo"
date: 2008-06-08
forum: Multimedia Software
---

### Post by teaguepatrick on 2008-06-08
Um... I can't figure this out and I'm sure it's something super simple - but for some reason Totem is playing AVI files in slo-mo. I can't seem to find anything in the preferences section to turn this off nor can I believe it is the file itself as multpile AVI files from multiple sources are just in super slow motion, all the time...

Any ideas?

---

### Post by kripkenstein on 2008-06-21
Did you figure this out? I seem to have the same problem.

Videos are in slo-mo, no sound. It is fixed when I reboot, and then I can watch videos for a while, but then eventually the problem returns, and videos are in slo-mo until another reboot. Very strange. It's in both Totem and MPlayer.

---

### Post by minhamra on 2008-06-23
I get the same thing. I don't have to reboot only restart X with Ctrl-Alt-Backspace. Still its a pain.

---

### Post by jbencic on 2008-06-26
I have this slow motion problem when i have Virtualbox running

as soon as i start a virtualbox guest, my main machines totem goes in slow motion

ohh an i installed vlc player and the picture works fine only no sound

---

### Post by wolfen69 on 2008-06-26
i have installed ubuntu on many computers. either i am the luckiest person in the world, or my method works. i always completely remove totem, amd totem-mozilla. i then add mplayer, mozilla-mplayer and vlc. of course i get the [medibuntu repos first]("https://help.ubuntu.com/community/Medibuntu"). i have yet to have a problem with any media on any pc. if your sound is getting screwy, check out this thread. [http://ubuntuforums.org/showthread.php?t=776739&highlight=perfect+pulseaudio](http://ubuntuforums.org/showthread.php?t=776739&highlight=perfect+pulseaudio)

also, this worked for me as far as a good soundfix: from [HERE]("https://wiki.ubuntu.com/PulseAudio")

Be Default, libflashplugin (Flash 9 support in Firefox) doesn't work properly with PulseAudio. 

Update: libflashsupport is available in Hardy as a package via the synaptic package manager. 

Go to logicalnetworking.net to download the libflashsupport .deb and install it: 
```
wget [http://logicalnetworking.net/other/libflashsupport_1.0~2219-1_i386.deb](http://logicalnetworking.net/other/libflashsupport_1.0~2219-1_i386.deb)
```
```
sudo dpkg -i libflashsupport_1.0~2219-1_i386.deb
```

Restart Firefox to enable simultaneous audio output from flash and other sources

---

### Post by kgdowley on 2008-08-12
I found a very simple fix:

1. Close Firefox
2. Watch Movie

Not sure why, but it seems firefox is the problem.  I have firefox 3.0.1, ubuntu 8.04, and totem 2.22.1.

This might not work for you, but it worked for me 2x.

---

### Post by kuh74 on 2008-10-12
>I have this slow motion problem when i have Virtualbox running
>as soon as i start a virtualbox guest, my main machines totem goes in slow motion
>ohh an i installed vlc player and the picture works fine only no sound

When I set Host Audio Driver of VirtualBox VM to PulseAudio, problem disappeared.

For your reference.

---

### Post by piva on 2008-10-30
> **kgdowley said:**
> I found a very simple fix:

1. Close Firefox
2. Watch Movie

Not sure why, but it seems firefox is the problem.  I have firefox 3.0.1, ubuntu 8.04, and totem 2.22.1.

This might not work for you, but it worked for me 2x.
Same here, and closing firefox always seem to work. Pretty annoying fix though.

---

### Post by hanzomon4 on 2008-10-31
I'm having the same problem...

Videos slow down in totem, No sound in VLC, Flash videos on are choppy.. It has to be an audio configuration problem. Everything worked fine before I updated(was already running intrepid beta/alphas)

---

### Post by hanzomon4 on 2008-10-31
Running VLC in terminal I see the video keeps spitting out this error

```
alsa audio output error: cannot write: Broken pipe
```

---

### Post by hanzomon4 on 2008-10-31
I fixed by downgrading from the pulseaudio 0.9.12 ppa to the default Ubuntu PulseAudio. I deleted my .asoundrc and .pulse-cookie because I started having problems getting Pulse Audio to start. Now everything works.

---

### Post by Lambchopper on 2008-11-13
> **wolfen69 said:**
> i have installed ubuntu on many computers. either i am the luckiest person in the world, or my method works. i always completely remove totem, amd totem-mozilla. i then add mplayer, mozilla-mplayer and vlc. of course i get the [medibuntu repos first]("https://help.ubuntu.com/community/Medibuntu"). i have yet to have a problem with any media on any pc. if your sound is getting screwy, check out this thread. [http://ubuntuforums.org/showthread.php?t=776739&highlight=perfect+pulseaudio](http://ubuntuforums.org/showthread.php?t=776739&highlight=perfect+pulseaudio)

also, this worked for me as far as a good soundfix: from [HERE]("https://wiki.ubuntu.com/PulseAudio")

Be Default, libflashplugin (Flash 9 support in Firefox) doesn't work properly with PulseAudio. 

Update: libflashsupport is available in Hardy as a package via the synaptic package manager. 

Go to logicalnetworking.net to download the libflashsupport .deb and install it: 
```
wget [http://logicalnetworking.net/other/libflashsupport_1.0~2219-1_i386.deb](http://logicalnetworking.net/other/libflashsupport_1.0~2219-1_i386.deb)
```
```
sudo dpkg -i libflashsupport_1.0~2219-1_i386.deb
```

Restart Firefox to enable simultaneous audio output from flash and other sources



I was having the same problem.  Totem would work good, until you played a flash video in Firefox, then totem would play all video's slow and restarting X was the only way to get them to play normally again.  Thanks to wolfen69's suggestions about installing the PulseAudio and the libflashsupport the problem was fixed.  I didn't have to remove totem, totem-mozilla or add VLC.  Instead all I did was follow the directions [here]("https://wiki.ubuntu.com/PulseAudio") to resolve the problem.

Thanks wolfen69, this was just what I needed!

ROCKIN!!!!  :guitar:

---

### Post by pablolie on 2009-11-29
I came across this post after re-installing 8.04. Totem was slowing down etc, vlc was however working.

It seems that indeed adding "libflashsupport" via Synaptic solves the issue. The description says something about "adds a few crutches" which does not sound too encouraging, but for now Totem works again...

---

