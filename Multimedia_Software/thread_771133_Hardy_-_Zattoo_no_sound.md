---
title: "Hardy - Zattoo no sound"
date: 2008-04-27
forum: Multimedia Software
---

### Post by litmos95 on 2008-04-27
Since upgrading to Hardy there is no sound in Zattoo. I found a similar thread here but then just closed without any solution. Any suggestions? 

Thanks in advance

---

### Post by Gunman1982 on 2008-04-28
Check what your logfile says.

~/.Zattoo/Data/logs/zattoo.debuglog

---

### Post by Route490 on 2008-04-28
Hey,
I was having the same problem, Here is my entries in the logs (the ones I think are relevant anyway)

```

debuglog:
19:24:08 28/04/08 [MSG]	new zattood status = 1007, old status = 1006
ERROR: Could not initialize the sound hardware: Device or resource busy

errlog:
ALSA lib pcm_dmix.c:874:(snd_pcm_dmix_open) unable to open slave


```

I leave Exaile on pause while not using it. So after pressing stop I was able to get sound on Zattoo.

Never had to do this previously with Gusty and Zattoo but I guess I can live with that if there is no easy work around?

Cheers

---

### Post by litmos95 on 2008-04-29
Here is the suspicious snapshot:

```

08:39:07 29/04/08 [MSG] new zattood status = 1006, old status = 1002
08:39:07 29/04/08 [MSG] new zattood status = 1007, old status = 1006
ERROR: Could not configure the sound system periods
08:39:08 29/04/08 [DEBUG]       Found new key from zattood_get_key!

08:39:08 29/04/08 [DEBUG]       Found new key from zattood_get_key!


```

But it does not help a lot. :(

---

### Post by Doc Holyday on 2008-04-29
Hello!

I had the same problem - after closing my media-player everything worked right. It seems, that Zattoo tries to get somewhat an exclusive handle on the sound hardware ;-)

---

### Post by Gunman1982 on 2008-04-29
Um sadly that 
"ERROR: Could not configure the sound system periods"
doesn't mean the same as
"ERROR: Could not initialize the sound hardware: Device or resource busy"
cause this one means that your soundcard is not capable of hardwaremixing so just one program at a time can access it. Gnome uses the esd sound daemon to avoid that problem.

The sound system periods problem leaves me puzzled, zattoo technical support suggests trying some stuff mentioned here: [http://ubuntuforums.org/showthread.php?t=590989](http://ubuntuforums.org/showthread.php?t=590989)
but if you have no problems with sound in firefox flash applications I don't think it will help.

I tried the solution with moving/deleting .asoundrc (which handles the software mixing in my case but anyhow). As expected it didn't work and I got a different error: Could not find sound device. yay ... 

Zattoo just does some strange stuff -.-

---

### Post by borobudur on 2008-06-29
Have you tried a reinstallation of Zattoo?

---

### Post by asdir on 2009-01-20
Reinstallation worked for me on Intrepid. Be careful though: Zattoo is not in the repositories of Ubuntu and can only be downloaded from an IP in area where Zattoo is legal. So if you changed your IP area since your last installation, better try do download the file before removing your installed version.

---

