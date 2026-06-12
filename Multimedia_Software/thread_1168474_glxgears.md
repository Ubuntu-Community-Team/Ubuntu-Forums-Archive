---
title: "glxgears"
date: 2009-05-24
forum: Multimedia Software
---

### Post by gnu-stu on 2009-05-24
Hi all,
Can someone tell me what the purpose of glxgears is?
When I run glxgears I get a small blank black screen. The terminal I launch from reports back some frames per second even though I see nothing.
Has anyone seen this behaviour before?
My current setup is:
Dual pIII
1.2GB Ram
xubuntu 8.10 (intrepid)

Cheers
Stu

---

### Post by bela42 on 2009-05-24
Its for OpenGL test and benchmark purposes.

You should see three rotating gears...

---

### Post by gnu-stu on 2009-05-24
Thanks bela42,
The thing is I've actually had it working previously (yesterday actually).
When I booted up today it didn't work!!
If it's not working do you know where I would start looking to found out why?

I forgot to mention that I'm using an ATI Radeon 9800 Pro and am running the latest proprietary driver.

Cheers

---

### Post by mcduck on 2009-05-24
> **bela42 said:**
> Its for OpenGL test and benchmark purposes.

You should see three rotating gears...

Testing, yes, but definitely not benchmark.. :D

Actually you used to need to run it as "glxgears --iacknowledgethatthistoolisnotabenchmark" to see the fps readings.. For some reason that was changed at some point, but you still shouldn't use it as a benchmark.

---

### Post by gnu-stu on 2009-05-24
> Testing, yes, but definitely not benchmark.. :grin:
@Mcduck, it's the testing part that I'm interested in ... and failing in also.
If glxgears isn't working what is that telling me and, more importantly, how do I go about fixing it?.
When I boot up everything appears  to be working normally except (I'm assuming) 3D acceleration.
Are there any diagnostic tools available that would help me out in this situation?

Cheers

---

### Post by mcduck on 2009-05-25
It's simply telling you that you don't have correct driver for your graphics card installed.

As far as I know Radeon 9800 Pro isn't supported by Ati's proprietary drivers. They decided to drop support for all older cards (which seems to include even some cards that are only year or two old..).

You should try with open-source drivers instead.

---

### Post by Arup on 2009-05-25
glxgears is not any sort of benchmark, please use gtkperf which is in repos.

---

### Post by Yellow Pasque on 2009-05-25
> As far as I know Radeon 9800 Pro isn't supported by Ati's proprietary drivers.
It is with Catalyst 9.3 or earlier. Since the OP is running Ubuntu 8.10, the card will be supported.

---

### Post by gnu-stu on 2009-05-25
Hi Temüjin,
Thanks for that, I thought my card was supported from all that I'd read at ATI.
And yes I'm using 9.3, the last available driver for me it seems until I upgrade my hardware.

Having said all that I'm still finding my 3D acceleration somewhat shakey.
Twice today I've had 3D fail on reboot, that is, glxgears was giving me a blank screen.
Also, twice today I've had 3D work OK on reboot ... it's actually working right now. But it may not work on next reboot.

@Arup,
Could you possibly elaborate a bit more on gtkperf.
Is this the package name?
I'm browsing through the synaptic interface looking for the closest match.

Cheers

---

### Post by kzipz on 2009-05-25
I have just installed UbuntuStudio x64 Jaunty on a system I built myself. I have a gigabyte motherboard, Phenom 940 CPU, 4GB ram and a sapphire 4950 1Gb graphics card.

After about a week of tweaking my settings and installing 2.6.28-11-server kernel I'm getting some great results. 

kserv@fire-serv:~$ glxgears
Running synchronized to the vertical refresh.  The framerate should be
approximately 1/387921 the monitor refresh rate.
61917 frames in 5.0 seconds = 12383.396 FPS
66289 frames in 5.0 seconds = 13257.679 FPS
65820 frames in 5.0 seconds = 13163.824 FPS
66307 frames in 5.0 seconds = 13261.268 FPS

This is a drastic improvement over the results on the generic kernel which where topping at about 5000-7000 FPS

Any feedback from the community on these results would be great to hear. 

I've been on the steep side of the learning curve for 3 months but it seems like it's coming together.

:DKz

---

