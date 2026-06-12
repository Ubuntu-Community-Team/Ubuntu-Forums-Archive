---
title: "3D Problem with 8.28.8 fglrx"
date: 2006-09-15
forum: Multimedia &amp; Video
---

### Post by orangek3nny on 2006-09-15
Hello all!

I have a problem with the 3D game PlanetPenguinRacer (TuxRacer). It only runs with 10fps on 1024 with all options turned on and there is even a display bug...see screenshot below for details.
Btw, the deferred start-flag is only present in screenshot.

This problem occured after updating my fglrx drivers to the newest official driver version ( 8.28.8 ) according to [this](http://www.ubuntuforums.org/showthread.php?t=204910&highlight=ati+libgl) guide.
I must say Tux looks more smooth now...but the fps isnt very good :roll: 

I don't have many 3D games installed here...only JFDuke3D and Nexuiz. JFDuke3D runs absolutely fine with 1024, 32bit and all the other things. Nexuiz has whole 2 frames... ](*,) 

[COLOR="Red"]EDIT:[/COLOR]
Just found out that ppr runs fine without antialiasing (you have to restart the game after chaging that option!!)

My notebook:
- Dapper
- AMD Sempron 3100+
- ATi 200M chipset with 128MB shared memory (set in BIOS to 128MB)
- 512MB Ram

---

### Post by mrunion on 2006-09-15
The 8.28.8 drivers do not seem to be compatible with the 200M cards.  You really need to revert to the 8.24.8 driver I believe.  I have to use those to get acceleration from my ATI X200 on my laptop.

---

### Post by orangek3nny on 2006-09-15
Thanks for your answer.
I will try to install them and report here!

---

### Post by Melcar on 2006-09-15
> **mrunion said:**
> The 8.28.8 drivers do not seem to be compatible with the 200M cards.  You really need to revert to the 8.24.8 driver I believe.  I have to use those to get acceleration from my ATI X200 on my laptop.


I'm using the 8.28 drivers with my 200M and it works just fine. 

 
> **orangek3nny said:**
> Hello all!

I have a problem with the 3D game PlanetPenguinRacer (TuxRacer). It only runs with 10fps on 1024 with all options turned on and there is even a display bug...see screenshot below for details.
Btw, the deferred start-flag is only present in screenshot.

This problem occured after updating my fglrx drivers to the newest official driver version ( 8.28.8 ) according to [this](http://www.ubuntuforums.org/showthread.php?t=204910&highlight=ati+libgl) guide.
I must say Tux looks more smooth now...but the fps isnt very good :roll: 

I don't have many 3D games installed here...only JFDuke3D and Nexuiz. JFDuke3D runs absolutely fine with 1024, 32bit and all the other things. Nexuiz has whole 2 frames... ](*,) 

My notebook:
- Dapper
- AMD Sempron 3100+
- ATi 200M chipset with 128MB shared memory (set in BIOS to 128MB)
- 512MB Ram

I ran into similar problems when I tried to update video drivers.  Since back then I was new to Ubuntu and still experimenting, my first solution was to reformat and do a fresh install with the new drivers.  That's obviously not the best solution, but you should try uninstalling the old drivers first (there are ways to do it but I just don't know how, sorry.)

---

### Post by orangek3nny on 2006-09-15
@Melcar:
Well, a really don't want to format because I will loose many customized things and settings...

Could you please post your glxgears, fgl_glxgears fps rates and tell me if tuxracer runs fine?

---

### Post by orangek3nny on 2006-09-15
I just noticed when i turn on "polygon-antialising" in armagetron, then the game gets nearly unresponsible and i get 100& cpu usage.
Maybe thats also the problem with tuxracer? :/

EDIT:

no driver version works normal...i tried 24,25,27,28 ...nothing!

I think its time to reinstall ubuntu :roll:

---

### Post by orangek3nny on 2006-09-16
Just found out that ppr runs fine without antialiasing. I had to restart the game to apply the changes.

Is there any way to fix that?

---

