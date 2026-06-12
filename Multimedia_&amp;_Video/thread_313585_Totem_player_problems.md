---
title: "Totem player problems"
date: 2006-12-06
forum: Multimedia &amp; Video
---

### Post by coine on 2006-12-06
Hi there.

I'm an absolute newb at Ubuntu and Linux in general as I've been using Macs all my life. However, I got an old IBM ThinkPad a few weeks ago, and I've finally managed to install Ubuntu on it (I needed the alternate install disc as it couldn't handle a Live CD startup).

I haven't done much with it so far, and it isn't connected to the internet yet, but I did try opening some of the example files. It then starts the Totem movie player, and I see the window for a split second before it quits again and pops up an error message:

```
Totem could not startup.

Could not open resource for writing.
```

The laptop is an 8 year old ThinkPad 600E with 128MB of RAM and a Pentium II at (I think) 266Mhz.

I have no idea what the problem is, as I'm running an account that has all privileges opened. Any help would be appreciated.

Cheers,
Mirko

---

### Post by spqr1 on 2006-12-22
I have the same problem with the Totem Player.  

The Totem movie player starts and I see the window for a split second before it quits and pops up the error message:  Totem could not startup. Could not open resource for writing.

I am running a Dell Optiplex GX1  with 384MB of RAM and a Pentium III at 450Mhz.

Any help would be appreciated.

Thanks.

---

### Post by Canis familiaris on 2006-12-22
Try updating or reinstalling Totem from Synaptic. I would recommend that you use gxine, or mplayer (install them using Synaptic Package Manager) : these are much more stable than totem.

---

### Post by spqr1 on 2006-12-22
I ran totem through the terminal and got the following error:

ALSA lib confmisc.c:670:(snd_func_card_driver) cannot find card '0'
ALSA lib conf.c:3479:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib confmisc.c:391:(snd_func_concat) error evaluating strings
ALSA lib conf.c:3479:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib confmisc.c:1070:(snd_func_refer) error evaluating name
ALSA lib conf.c:3479:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib conf.c:3947:(snd_config_expand) Evaluate error: No such device
ALSA lib pcm.c:2146:(snd_pcm_open_noupdate) Unknown PCM default


Help

---

### Post by spqr1 on 2006-12-22
Totem now works! :) 

My sound card was not configured.

See link below for the detailed process.
[http://www.ubuntuforums.org/showthread.php?t=205449](http://www.ubuntuforums.org/showthread.php?t=205449)

---

### Post by kanna1620 on 2007-01-13
> **Anurag_panda said:**
> Try updating or reinstalling Totem from Synaptic. I would recommend that you use gxine, or mplayer (install them using Synaptic Package Manager) : these are much more stable than totem.

I installed the gxine and xine movie players but they are not working properly.
gxine is playing the movie files with a very bad picture quality and the xine is stop playing the movie file abruptly without any error message or what so ever.
Any help would greatly appreciated.
Thanks

---

### Post by joriad on 2007-01-22
I also had the same problem with totem closing after a second or two. This started happening right after a totem update. I just did a reboot and everything was fine after that.

---

### Post by Canis familiaris on 2007-01-23
> **kanna1620 said:**
> I installed the gxine and xine movie players but they are not working properly.
gxine is playing the movie files with a very bad picture quality and the xine is stop playing the movie file abruptly without any error message or what so ever.
Any help would greatly appreciated.
Thanks
Install all media players using Automatix.
Automatix wil also be able to run all MP3, MPEG, and DVDs very well.
For info on installing Automatix, follow the link below:
[http://ubuntuforums.org/showpost.php...58&postcount=2](http://ubuntuforums.org/showpost.php...58&postcount=2)

After installing Automatix, open Automatix and install your codecs in a straightforward manner

:roll: If it isn't a codec problem it may be a video card problem.

Try reconfiguring the Xserver using the command:
```
sudo dpkg-reconfigure xserver-xorg
```

---

