---
title: "MythTV Frontend - No TV"
date: 2007-05-09
forum: Multimedia &amp; Video
---

### Post by jacrider on 2007-05-09
All:  I am still struggling with a MythTV installation.

Hardware: Desktop with 3.0 Celeron, 2GB RAM, 2 x 250 GB HD's, PVR 150 Card, NVidia 5500

So far, I have had to drop the mySQL database and re-install the database.

I have done the backend configuration and I think it is right.  I can see the PVR 150 in dmesg and I can record TV from the command line "cat /dev/video0>test.mpg" and watch it in mplayer.

I can start the frontend, but when I go to watch TV it is a black screen.

My message output is here:

2007-05-09 23:04:37.802 MainServer::HandleAnnounce Monitor
2007-05-09 23:04:37.807 adding: andrew-UbuntuBox as a client (events: 0)
2007-05-09 23:04:37.809 MainServer::HandleAnnounce Monitor
2007-05-09 23:04:37.810 adding: andrew-UbuntuBox as a client (events: 1)
2007-05-09 23:04:49.310 MainServer::HandleAnnounce Playback
2007-05-09 23:04:49.317 adding: andrew-UbuntuBox as a client (events: 0)
2007-05-09 23:04:49.321 TVRec(1): Changing from None to WatchingLiveTV
2007-05-09 23:04:49.329 TVRec(1): HW Tuner: 1->1
2007-05-09 23:04:49.849 NVR: Won't work with the streaming interface, falling back
VIDIOCGMBUF:: Invalid argument


I have no idea what that error is at the end ... anyone else with an idea?

Thanks.

---

### Post by newlinux on 2007-05-10
Did you set your capture card up as an mpeg-2 encoder? I've seen this error when a PVR-150 is setup as a V4L card.

---

### Post by jacrider on 2007-05-10
I thought I was supposed to use the V4L.

I will try tonight to set it up as a mpeg2.

Thanks for your response!

---

### Post by AusIV4 on 2007-05-10
Mythbackend (which does the recording), runs as the mythtv user. Make sure the mythtv user is in the video and audio groups.

---

### Post by newlinux on 2007-05-10
> **jacrider said:**
> I thought I was supposed to use the V4L.

I will try tonight to set it up as a mpeg2.

Thanks for your response!

The PVR-150, 250, 350, and 500 are all hardware encoding tuners and need to be setup as hardware mpeg-2 encoder cards. Hopefully that will fix your problem.

---

### Post by jacrider on 2007-05-11
Ok, problem solved.  Card setup as a mpeg-2 and I now get TV through MythTV.

Next problem is that I am only getting a few channels ... up to maybe 13.  (I am in Canada using a cable service and zap2it, with lots of available channels.)

Any ideas on where I would have gone wrong?

Again, thanks for all the help.  This place is a fantastic resource.

---

### Post by newlinux on 2007-05-11
Are those all the channels you get when you scan? What scan settings are you using? Can you confirm that you get more than that many analog stations with another tuner (like an analog TV)?

---

### Post by barney_1 on 2007-05-11
You need to make sure that you have your tuner set up as cable-us, not default or antennae.  Find this setting under Video Source Setup --> Channel Frequency Table

---

### Post by Georgie-o on 2007-05-12
I have a Hapauge 150 and new install of Fiesty.  I downloaded Mythtv and think it is pretty worthless for the average user.  The amount screens (4 steps?!?!) with about a million blanks to fill in?  Maybe they think I know how to run a TV studio?  I don't have a clue what I supposed to accomplish in all of those screens.  The only thing I recognized is a one point it listed my card as the Hapauge,,,,nothing else.  I hate to say it but I am sorely disappointed.

---

### Post by superm1 on 2007-05-12
> **Georgie-o said:**
> I have a Hapauge 150 and new install of Fiesty.  I downloaded Mythtv and think it is pretty worthless for the average user.  The amount screens (4 steps?!?!) with about a million blanks to fill in?  Maybe they think I know how to run a TV studio?  I don't have a clue what I supposed to accomplish in all of those screens.  The only thing I recognized is a one point it listed my card as the Hapauge,,,,nothing else.  I hate to say it but I am sorely disappointed.
This is why there are guides explaining what everything does and what needs to be filled in where :)
[http://help.ubuntu.com/community/MythTV](http://help.ubuntu.com/community/MythTV)

---

### Post by jacrider on 2007-05-12
Once again, you guys are right.   Changing the tuner setup to cable-us worked!

Last question, the top and bottom bars of Ubuntu are still there when the TV is up and running.  How do I get them to go away?

Next I will try and get the remote to work.

Thanks.

---

### Post by Erlander on 2007-05-13
[QUOTE=jacrider;2641979
Last question, the top and bottom bars of Ubuntu are still there when the TV is up and running.  How do I get them to go away?
Thanks.[/QUOTE]
In your frontend setup:  Utilities?setup/Setup/Appearance on the second screen uncheck "Run Myth Frontend In a Window'

Rob

---

### Post by jacrider on 2007-05-13
Thanks for the reply.  I had already done that, but the bars remain.  I get the top panel and bottom panel as well, not the TV in a window.

Any ideas?

---

### Post by newlinux on 2007-05-13
Perhaps you have you panels set to be "Always on top?" I don't use gnome, but check your panel properties.

---

### Post by superm1 on 2007-05-13
> **jacrider said:**
> Thanks for the reply.  I had already done that, but the bars remain.  I get the top panel and bottom panel as well, not the TV in a window.

Any ideas?
This is a side effect of running beryl/compiz afaik.  Only workaround i've seen is to disable before running myth.

---

