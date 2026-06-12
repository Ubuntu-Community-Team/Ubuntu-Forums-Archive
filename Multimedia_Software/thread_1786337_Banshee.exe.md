---
title: "Banshee.exe????"
date: 2011-06-19
forum: Multimedia Software
---

### Post by silex89 on 2011-06-19
My Banshee Media Player just crashed, the window to force quit didn't appear, so I opened a terminal and typed "ps aux | grep banshee" to close it using the kill command. I got this output

```
daniel@Silex:~$ ps aux | grep banshee

daniel    3076  0.0  0.0   6164  1440 ?        S    12:29   0:00 bash /usr/bin/banshee --redirect-log --device-activate-play=/home/daniel/.gvfs/CDDA montado en sr0
daniel    3082  0.8  2.6 412784 73996 ?        Sl   12:29   0:48 banshee /usr/lib/banshee/Banshee.exe --redirect-log --device-activate-play=/home/daniel/.gvfs/CDDA montado en sr0
daniel    4062  0.0  0.0   5320   848 pts/2    S+   14:02   0:00 grep --color=auto banshee
```

As you can see in the 3082 line, the path says /usr/lib/banshee/Banshee.exe... I didn't knew I was backporting Wine to run banshee :S

Am I having a problem or it's meant to be (or appear) that way?

---

### Post by ajgreeny on 2011-06-19
Interesting one!

I just started banshee to check what I would get in terminal and it is almost the same, except that I do not see the ```
--device-activate-play=/home/daniel/.gvfs/CDDA montado en sr0
```at the end of the first two lines, mine just has ```
--play-enqueued
```I do get the "/usr/lib/banshee/banshee.exe" just like your output, and my banshee was playing perfectly as I ran the command.  I presume from this that it is nothing to worry about and that the banshee.exe is a standard file of the app.  Weird, I must admit.

I think, however, that it may be related to the apps that use mono, as the command ```
locate .exe
```gave me this output
```
/usr/lib/banshee-1/Banshee.exe
/usr/lib/banshee-1/Banshee.exe.config
/usr/lib/banshee-1/Beroe.exe
/usr/lib/banshee-1/Halie.exe
/usr/lib/banshee-1/Muinshee.exe
/usr/lib/banshee-1/Nereid.exe
/usr/lib/banshee-1/gconf-schema-extractor.exe
/usr/lib/f-spot/f-spot.exe
/usr/lib/f-spot/f-spot.exe.config
/usr/lib/gbrainy/gbrainy.exe
/usr/lib/gbrainy/gbrainy.exe.config
/usr/lib/mono/2.0/gacutil.exe
/usr/lib/mono/gac/mono-service/2.0.0.0__0738eb9f132ed756/mono-service.exe
/usr/lib/podsleuth/PodSleuth.Hal.exe
/usr/lib/tomboy/Tomboy.exe
/usr/lib/tomboy/Tomboy.exe.config
/usr/share/mono/MonoGetAssemblyName.exe
``` ie. all applications that rely on mono as dependencies.

---

### Post by silex89 on 2011-06-19
I see... thank gosh is not a big deal! :D

BTW you didn't see that output because I was trying to play a CD, that the mounting path that my drive has. :)


Thanks a lot for answering :)

---

### Post by directhex on 2011-06-20
Banshee is as native as any app written in, say, Python. It's got a .exe in the filename because Mono follows the recommendations in the ECMA335 specification it follows.

---

