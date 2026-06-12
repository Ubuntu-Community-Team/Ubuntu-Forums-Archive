---
title: "I dont get virtual terminals with nvidia driver"
date: 2006-09-18
forum: Multimedia &amp; Video
---

### Post by walovaton on 2006-09-18
Hi,

I have a Dell XPS 1210 laptop and it have been working great with Ubuntu Dapper but after I installed the nVidia driver to get 3D acceleration I got no virtual terminal.  Any time I try to switch with Alt + F[1-6] I just get a blank screen.  It used to work before installing the nVidia driver.

The other sympthom I noticed is that when booting up the splash (or graphical boot) gets messy after a while.  It starts fine but after loading some services the letters gets blury and corrupted.  The system starts fine though.

When I shutdown I dont get the usual graphical mode, I just get a blank screen and the only indicator of the shutdown process is the hard drive led.

I have XGL/Compiz installed and in general everything is working great, even the webcam with Ekiga... the only annoying thing is this virtual terminal issue since I am a command-line type of guy.

Thank God I didn't got affected by the faulty Xorg update some weeks ago.

Cheers,

-William

---

### Post by nalinde on 2006-09-19
Hi William..

Think that I've got the same problem actually. :-/...
Must be something with the nividia drivers i think? Somebody confirm?

Recognize the problems you have with not being able to use the virtual terminal properly. In my case it seems like X crashes. This problem also appears when i try to log out from my session. Witch is really annoying, arrgh.

Even though i am a noob I've tried to figure out this problem fore quite some time now :-/. But My X.log don't give me any output concerning this problem :'-(. Did a test when i cleaned out my x.conf to default and everything worked properly. But as i changed "nv" to "nvidia" in the conf-file i had the same problem :-!

Will post a video later on that shows how the shutdown process is blurred out. The only thing that i don't recognize in your description is that I don't have this problem at start up.. but when the nvidia drivers is loaded... then the problems appears

[Here is the vidoe of my ubuntu when i shut down.. recognize?]("http://www.nalinde.se/raw/ubuntu.avi")

---

### Post by walovaton on 2006-09-20
I think yours looks better than mine.  The main difference between you and me is that I got a blank screen on shutdown and when booting the graphical boot gets corrupted after a while.  What video card do you have? I have an nVidia GeForce Go 7400 256MB.  I hope nVidia release a new driver soon.

---

### Post by tseliot on 2006-09-20
Read point 13 of the Problems Section of my guide:
[http://doc.gwos.org/index.php/Latest_Nvidia_Dapper#PROBLEMS_SECTION](http://doc.gwos.org/index.php/Latest_Nvidia_Dapper#PROBLEMS_SECTION)

if you don't want to remove "splash" just don't remove splash and add "vga=791" beside it.

If that doesn't work you will have to remove it (as I suggest in my guide).

---

### Post by ethan@xmlstandards.org on 2006-09-20
OK.

So I have tried to option to turn off the splash flag from defoptions and then rebooted.

All is working fine now.

And after following the tutorial for decreasing the screen resolution for the boot up screen, I now have a nice set of VTs to use at a nice resolution.

Many thanks for this tip people.

Can anyone recommend a good resource for learning more about virtual terminals and their day to day usage.

Now I have them working I would like to make the most use of them.

Thanks again, Ethan

---

