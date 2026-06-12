---
title: "setting up TV tuner being webcam for Skype ?"
date: 2008-09-07
forum: Multimedia Software
---

### Post by arheon on 2008-09-07
Hello,guys.I'm another guy who has finally moved from windows to Ubuntu.
And I have a problem =) Since my webcam is based on "sn9c325bfg " chipset I had no success finding the drivers... Besides,webcam's fps is really poor.
So, being a Windows user I used to hook up my FUJI S8000 camera to "s-video in" of the TV tuner,the Avermedia Go 007 Plus(?),setup up the source => "s-video in" @ some stock tv program,defined the tuner as a capture device in Skype options and had great videocam for Skype.
Now I've moved to Ubuntu.Webcam has no drivers.Ok,I was aware of limited HW support.But.. Actually Skype sees the tuner :
[IMG]http://lh3.ggpht.com/arheon/SMQ9jy9_b5I/AAAAAAAABvs/6Fqq2YAhUtA/s288/Screenshot-Options.png[/IMG]
Okay... Tuner sees the camera (s-video in) via TVtime :
[IMG]http://lh5.ggpht.com/arheon/SMQ9j0BtyqI/AAAAAAAABvk/-d6DNt5k0fo/s288/Screenshot-1.jpeg[/IMG]

I've searched over whole Google & didn't find anything... I can be wrong with that statement =) The only idea is to make a "device" with pre-defined settings : smth like "webcam0" is "/dev/video0@s-video"..
But I have no idea how & where to do it..

My question is : is there any possible way to hook these three things? coz I really-really don't wanna buy another webcam.. :(

Any help appreciated..

---

### Post by RuarriS on 2008-09-07
Is Skype trying to look for video coming from the "cable plug" rather than the s-video?

I beleive for my pchdtv card, the inputs are listed as video0, video1, video2

---

### Post by arheon on 2008-09-08
no idea.it's just a dead black screen coming up when i press the "Test" button.
i was trying to give him some input signals connecting antenna and the camera too,but it stays totally blind.no changes at all.I've got one channel in Tvtime (nationally broadcasted,so the tuner is ok),with no sound.as i've seen through forum this issue is solvable,but i don't watch tv at all, coz i've got no cable O_o anyway... skype can't define the input port of the tuner as i can see... i'm sorry about my poor english. please tell me if i'm talking weired or so,coz i've got no "training" at all. =(
anyways... any ideas? coz reverting back to windows after setting up everything is... well... not making the world better.. open-source... and all these things...

---

### Post by arheon on 2008-09-08
> **RuarriS said:**
> Is Skype trying to look for video coming from the "cable plug" rather than the s-video?

i think so.but with no defined channel. looking down at my LCD monitor i see something like lines O_o but they're hardly visible... because of low contrast i presume... there is "something"... but where does it come from??

and there are no options to select @ skype. just the device.](*,)

---

### Post by RuarriS on 2008-09-08
First off, your English is fine! I didn't even know it wasn't your first language. 

Now:
See if the camera is recognized by Ekiga (Applications -> Internet -> Ekiga Softphone). If it is, then it may be a deficiency with Skype (which is lacking compared to the Windows release). You should try the Skype forums; They have a Linux specific one.

---

