---
title: "mythtv frontend crashed - blank screen after changing to opengl"
date: 2007-05-13
forum: Multimedia &amp; Video
---

### Post by SuperJETT on 2007-05-13
I was trying to speed up the menus on the frontend on my desktop/backend/frontend machine and after changing the engine from qt to opengl and broke the frontend.

When I start it, I get the scaling theme images messages, then the theme background for a second or two, then it goes black and stays that way.  If i hit escape, it comes back with the yes/no about exiting.

I've searched and searched and can't find where that setting is stored, either in the db or a config file.

My questions are, do I need to enable OpenGL (have a geforce4 MX card) or is there a way to reset the engine?  

I did remove mythtv-frontend and reinstalled it with no change.

Help!  this is my machine connected to our projector and it's kind of pointless now.

I'm tempted to just reinstall Edgy and start over as I could be done in an hour probably.

---

### Post by barney_1 on 2007-05-15
Don't reinstall edgy, first try running the frontend with the reset option:

```
mythfrontend --reset
```

Oh, and let me know if that works, I've not tried it before ;-)

---

### Post by SuperJETT on 2007-05-15
> **barney_1 said:**
> Don't reinstall edgy, first try running the frontend with the reset option:

```
mythfrontend --reset
```

Oh, and let me know if that works, I've not tried it before ;-)

Too late, I went ahead and wiped it and had it back up in less than 2 hours running Myth.

I have an lirc issue too, so I figured starting with a clean slate may make it easier to get that functional again.  (I had it working 2 installs ago, just gotta get back there)

Thanks for the tip on the reset command though, I haven't seen that mentioned anywhere or I would have tried it.

---

### Post by dannyboy79 on 2007-05-30
I would just like to provide feedback for any others that maybe screw up their frontend settings and make it unviewable etc etc. I tried to make it so that I could watch tv using the frontend in a little window and still be able to work. I chose a 800x600 resolution and all of a sudden my entire screen resolution went to that and I couldn't see far enough down to chose the mythtv frontend appearance setup again so I thought if I went to the normal screen res within System, Admin, then change the resolution there I would be alright, well all of sudden my computer was frozen. So I did a total restart of the machine using the reset button since ctrl-alt-f1 didn't bring me to a tty so that I could issue sudo shutdown -r now. Anyway, once my desktop was backup I hit mythfrontend again and it brought up a black screen and froze machine again. I though, oh man, what did I do now!!! So I found this thread using winbloz and did it and it brought everything withi mythfrontend back to default and I could use it again, I was sooooo happy!!!!!!!!!!!

So this command will return the mythfrontend back to default in every way and settings that you have done. I was so happy a problem was so easy to fix!!!!!!

---

### Post by drocra on 2007-06-02
> **barney_1 said:**
> Don't reinstall edgy, first try running the frontend with the reset option:

```
mythfrontend --reset
```

Oh, and let me know if that works, I've not tried it before ;-)

I just had the same problem - switched to OpenGL and got the black screen. I'm running with an older NVidia card with the beta drivers. I have OpenGL enabled but it can be iffy sometimes.

I used mythfrontend --reset and it worked perfectly. Thanks!

---

### Post by dannyboy79 on 2007-06-04
> **drocra said:**
> I just had the same problem - switched to OpenGL and got the black screen. I'm running with an older NVidia card with the beta drivers. I have OpenGL enabled but it can be iffy sometimes.

I used mythfrontend --reset and it worked perfectly. Thanks!

i have a XFX GeForce 6200 128mb AGP and mine works with opengl in mythfrontend. I am using the nvidia-glx-new driver from synaptic which I believe is the 9755 proprietary driver.

---

### Post by drocra on 2007-06-07
I'm running with an nvidia geforce4 MX (same as the original poster), with the 9639 driver.

---

### Post by nickgriffiths on 2007-12-06
> **barney_1 said:**
> Don't reinstall edgy, first try running the frontend with the reset option:

```
mythfrontend --reset
```

Oh, and let me know if that works, I've not tried it before ;-)

Many thanks for the tip, worked a treat!

I had the same problem as previously described. I set the Paint Engine option to OpenGL and then ran mythfrontend, got the "prescaling images" progress bar and then a black screen. I use an Nvidia Geforce 4 MX and Mythbuntu 7.10, with nvidia-glx driver version 1.0.9639:

```
$ lspci | grep VGA
01:00.0 VGA compatible controller: nVidia Corporation NV18 [GeForce4 MX - nForce GPU] (rev a3)
```

Not entirely sure how to check if OpenGL is working entirely correctly; I ran glxgears as a quick test and that runs fine. Also, I have a Feisty+Mythtv installation on a separate partition on the same PC (from before Mythbuntu existed) which doesn't have this problem. I believe it uses an earlier version of nvidia-glx, so perhaps this is nvidia-glx related?

I can't find any bug reports on Launchpad or Mythtv's Trac page that describe this problem, so I guess I better report it at some point :)

---

