---
title: "Ubuntu server no sound"
date: 2008-10-26
forum: Multimedia Software
---

### Post by holamyburrito on 2008-10-26
Hey guys, I'm pretty much an absolute noob at linux. I've had ubuntu installed on my laptop for all of two weeks now, but I really like it.

So here's my problem - sorry if this is been asked countless times, but I did search the forums for a while and went through the comprehensive sound guide to no avail.

I installed ubuntu server on my desktop with the idea of using it as a central music device that can be used by all the computers in my dorm. I found out about mpd and it's various clients on this forum, and when I installed it, everything went okay. When I run it, I get an error:

Avahi: Failed to create client: Daemon not running

Yet I can still connect to it from the clients, and my music library shows up and it can "play". That is, it looks like it's playing but no sound comes out of the server's speakers. 

Now, I also have mp3blaster installed and when I try to use that, it just says "Failed to access sound device" or something similar. 

Is there something this big noob is missing? Sorry again if this is one of those questions that is just so obvious that that's why I didn't find any threads about it. lol

---

### Post by cariboo on 2008-10-26
I run a headless emachine with no gui as an mp3 player, so all the intructions need to be done in a terminal.

step 1. Make sure your sound card is detected and the driver loaded:

```
sudo lshw -C multimedia
```

It should give you an output something like this:

```
sudo lshw -C multimedia
  *-multimedia            
       description: Multimedia audio controller
       product: 5880 AudioPCI
       vendor: Ensoniq
       physical id: 12
       bus info: pci@0000:00:12.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: driver=ENS1371 latency=64 maxlatency=128 mingnt=12 module=snd_ens1371
```

as you can see from the above listing my soundcard is detected and the driver is installed.

Step 2. Check to see if your card is listed by asound:

```
asoundconf list
```

the output should look something like this:

```
 asoundconf list
Names of available sound cards:
AudioPCI
```

Step 3. Tell asound what sound card to use:

```
asoundconf set-default-card PARAMETER
```

where PARAMETER is the card found by running asoundconf list

Step 4. Make sure alsa-base and alsa-utils are installed

You should now be ready to play tunes. Open alsamixer and set the volume levels and test your system.

I use a program called randomplay in combination with mpg321 to play mp3s.I have approximately 10,000 mp3 files and I have set randomplay to not repeat for 30 days.

I also use gnump3d to play mp3s to individual computers, as my server and mp3 player are located in my unattached garage.

Jim

---

### Post by holamyburrito on 2008-10-26
Thanks for the reply.

I tried all of that but it didn't work. I don't think the problem is getting to recognize the sound card. Not to say that I know what it is.. >_>

I tried turning up all the volumes on the alsamixer and that didn't work. There was one channel called "jack line sense" that seems to be turned off completely, perhaps that has something to do with it?

Thanks again.

---

### Post by forger on 2008-10-26
what's the output of 
```
sudo lshw -C multimedia
```

---

### Post by holamyburrito on 2008-10-26
> **forger said:**
> what's the output of 
```
sudo lshw -C multimedia
```

 ```
 *-multimedia            
       description: Multimedia audio controller
       product: 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller
       vendor: Intel Corporation
       physical id: 1f.5
       bus info: pci@0000:00:1f.5
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: driver=Intel ICH latency=0 module=snd_intel8x0
```

---

### Post by forger on 2008-10-26
Not sure, but maybe you could try with pulseaudio instead of alsa?
I don't know how to set pulseaudio on a server though :(

---

### Post by holamyburrito on 2008-10-26
Well, thanks anyway. I know I don't know much about linux in general, but could someone help me out as to the "line jack sense" thing? Even if it's not the problem, I'd just like to know what it is for future reference. :)

I'm planning on completely phasing windows out of my laptop eventually, but for now I'm still dual-booting XP so I have a safety net when I don't know what the heck is going on. lol

So, yeah, thanks to the people who replied already, and hopefully someone else can offer some insight? I'd really like to listen to music again. haha

---

### Post by holamyburrito on 2008-10-26
Sorry, but.. bump? Anyone out there know what's going on with my system?

---

### Post by cariboo on 2008-10-27
That is for the line in jack on your sound card. What application are you usingto try and play mp3s.

Jim

---

### Post by holamyburrito on 2008-10-27
Ok sorry for triple post, but it's no longer giving me errors. Now it just doesn't play any sound when it says a song is playing. I'm really in need of ideas here. Could it just be Hardy? Should I try an earlier version?

---

### Post by holamyburrito on 2008-10-27
I'm using mpd on the server and sonata on my laptop.

---

### Post by forger on 2008-10-27
You could try other media player daemons:
deejayd says it has a web user interface:
```
sudo apt-get install deejayd djc deejayd-client deejayd-gstreamer deejayd-webui deejayd-xine
```
(there's also deejayd-gstreamer instead of xine backend)


```
sudo apt-get install xmms2 xmms2-plugin-all xmms2-client-cli xmms2-client-avahi xmms2-client-medialib-updater
```

Never tried any of them, but do search for more info in google :)

---

### Post by forger on 2008-10-27
just tested both suggestions locally (not over a network).. deejayd seems very unstable.

xmms2 worked in a few steps ;)
Note: install the packages I mentioned above!

[http://www.debian-administration.org/articles/509](http://www.debian-administration.org/articles/509)

---

