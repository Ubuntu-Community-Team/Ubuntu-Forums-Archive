---
title: "Realplayer in Hardy"
date: 2008-04-24
forum: Multimedia Software
---

### Post by dede468 on 2008-04-24
Just upgraded from 7.10 to 8.04

Realplayer works fine for BBC radio progs in 7.10 but the upgrade killed the radio. I downloaded the 8.04RC package a couple of weeks ago and added Realplayer to it. Again it didn't work for BBC radio. 

Is this a bug as all was OK until I upgraded. I've tried turning off the firewall and using Epiphany browser in case it was the upgrade to Firefox  3 but same results.

Any suggestions appreciated as I'm a BBC radio addict.

---

### Post by andrebrait on 2008-04-24
I bet it's another Pulseaudio problem.

Try installing the package libsdl1.2debian-all

It will uninstall the libsdl1.2debian-alsa, but it comes with every plugin

If it don't work, try this...

```
export SDL_AUDIODRIVER=pulse
```

OR

```
export SDL_AUDIODRIVER=alsa
```

It solved some audio problems for me...

---

### Post by dede468 on 2008-04-24
Well thanks for the ideas but sadly none of them worked for me. I think 8.04 will have to go on the back-burner until such time as this bug is sorted as living in Turkey, I use BBC streaming radio to keep me up to date on UK news etc every morning 8.04 without Realplayer is no contest for 7.10 with Realplayer I'm afraid! :(

---

### Post by andrebrait on 2008-04-24
can't you use another player?

---

### Post by andrebrait on 2008-04-24
or better...
are the sound devices configured correctly in System > Preferences > Sound?

---

### Post by madbouy on 2008-04-24
I have the same problem too. It as working perfectly in 7.10 now I upgraded it sound garbled. Maybe it is Firefox but what ever it is. It sucks

---

### Post by harambe on 2008-04-25
I installed 8.04 yesterday and when I play a BBC radio program it starts up Totem which does not work properly - never playes the whole program and does not allow me to move through a clip - this is what Totem has always done for .ram files which is why I used RealPlayer 

For some reason though I just can't get FireFox to use realplayer - the settings in Applications tell it to, but it just won't.

---

### Post by lecter255 on 2008-04-26
ok i am in a worse situation

i downloaded realplayer in rpm and used alien to turn it into deb then installed it. now i try to run realplayer by clicking on the icon and selecting run and nothing happens. in 7.10, the player would show up. I really need realPlayer because I am a college student and I need to stream lectures with realPlayer

please help!

---

### Post by charles on 2008-04-29
Had the same problems - gave Firefox 3Beta5 the flick and installed the latest available of Firefox 2x - problems disappeared  ..

---

### Post by MangasColoradas on 2008-04-29
Realplayer is working for me in 8.04, I am using FF2 and I removed the totem FF plugin, I have to use the 'stand alone realplayer' option but thats no hardship.
I used to use Mplayer but that didnt allow me to fast forward/rewind the audio stream when using 'listen again'.

---

### Post by nickzeff on 2008-05-17
Can I make a humble suggestion to all of you?

Uninstall Realplayer and install the mozilla mplayer plugins instead - BBC radio player works perfectly with Hardy Heron/Firefox 3b5, and no dirty restricted software on your machine.

If you installed Realplayer using the downloaded bin file from real's site, you need to find their hidden uninstall script. Uninstall instructions on this thread at post #5:

[http://ubuntuforums.org/showthread.php?t=681778](http://ubuntuforums.org/showthread.php?t=681778)

My script wasn't exactly where the poster said it was, but I found it buried in my nominated Real install directory.

When you've done that, uninstall the Totem plugins. Just search for **totem-mozilla** in Synaptic and remove.

Now install the mplayer plugins by installing the package **mozilla-mplayer**.

You might need to do a restart of Firefox.

Now my BBC radio works, and it's all healthy, clean software!

---

### Post by Vic Morgan on 2008-05-23
Thanks nickzeff. In absence of RealPlayer, removing totem-mozilla and installing mozilla-mplayer worked perfectly for me!

---

### Post by gandaran on 2008-05-23
the best solution for bbc streaming is the totem plugin with the xine engine, just un-install totem gstreamer and install totem xine, with the xine engine you have the option on bbc to either stream real video or wmv, works a whole lot better than mplayer!

---

### Post by nickzeff on 2008-05-25
> **Vic Morgan said:**
> Thanks nickzeff. In absence of RealPlayer, removing totem-mozilla and installing mozilla-mplayer worked perfectly for me!
Glad to help. I might try gandaran's option now, just as an experiment!...

---

### Post by Elderlygent on 2008-05-27
> **nickzeff said:**
> Can I make a humble suggestion to all of you?

Uninstall Realplayer and install the mozilla mplayer plugins instead - BBC radio player works perfectly with Hardy Heron/Firefox 3b5, and no dirty restricted software on your machine.

If you installed Realplayer using the downloaded bin file from real's site, you need to find their hidden uninstall script. Uninstall instructions on this thread at post #5:

[http://ubuntuforums.org/showthread.php?t=681778](http://ubuntuforums.org/showthread.php?t=681778)

My script wasn't exactly where the poster said it was, but I found it buried in my nominated Real install directory.

When you've done that, uninstall the Totem plugins. Just search for **totem-mozilla** in Synaptic and remove.

Now install the mplayer plugins by installing the package **mozilla-mplayer**.

You might need to do a restart of Firefox.

Now my BBC radio works, and it's all healthy, clean software!

The problem with being a purist is that it restricts choice. In fact, mplayer does NOT work as well as Real Player with BBC sites because they are designed for RealPlayer. Mplayer is slower and the feed frequently breaks up. My motto is "Accept no substitutes!" or, the operative word in Open Source is "Open". That said I love Ubuntu. Cheers

---

### Post by oneup on 2008-05-27
> **charles said:**
> Had the same problems - gave Firefox 3Beta5 the flick and installed the latest available of Firefox 2x - problems disappeared  ..
Hi  ,I have had the same probs with 8.04 and realplayer 11,does this mean its a Firefox problem?

---

### Post by datakid on 2008-06-13
nickzeff's solution worked for me.

---

### Post by ssam on 2008-06-16
the totem gstreamer pluggin can play bbc radio, you dont need realplayer.
the is a bug in the current hardy version that gives garbled sound [https://bugs.launchpad.net/ubuntu/+source/totem/+bug/217301](https://bugs.launchpad.net/ubuntu/+source/totem/+bug/217301) but the fix on its way to updates.

you can grab it early from:
[http://launchpadlibrarian.net/15055137/gstreamer0.10-plugins-ugly_0.10.7-3ubuntu1_i386.deb](http://launchpadlibrarian.net/15055137/gstreamer0.10-plugins-ugly_0.10.7-3ubuntu1_i386.deb)
or for 64 bit
[http://launchpadlibrarian.net/15055175/gstreamer0.10-plugins-ugly_0.10.7-3ubuntu1_amd64.deb](http://launchpadlibrarian.net/15055175/gstreamer0.10-plugins-ugly_0.10.7-3ubuntu1_amd64.deb)

if you try it please report on the bug report.

---

### Post by anthortic on 2008-06-23
i found mozilla-mplayer plugin did not work for me

i actually removed it using synaptic and in its place installed 

mozilla-helix-player for using bbc radio

and 
mozilla-plugin-vlc 

to handle all other media in firefox. worked great for me but i share the pain of every other bbc radio addict that has trouble with this issue, it clearly needs to be addressed

---

