---
title: "change gdm theme"
date: 2010-09-01
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by stevetxt on 2010-09-01
I have been looking for a way to change the theme that applies to the gdm login window.  Searching the forums the range of advice is chaotic.  I recall doing this in Karmic, but I do not remember how.  Is there a simple way to do this in Maverick or a recent thread that describes this?

---

### Post by MacUntu on 2010-09-01
Well, what's simple?

1.) Log out, so you are at the GDM screen.
2.) Press Ctrl-Alt-F1 to change to a virtual terminal.
3.) Log in and run:
```
DISPLAY=:0.0 sudo -u gdm gnome-appearance-properties
```
4.) Go back to the GDM screen: Ctrl-Alt-F7 (or was it F8, not sure).
5.) You should see the Appearance Preferences window where you can change everything to your liking.
6.) When you're done, close it and that's it.

The good old days with tons of GDM themes that were easy to create, to modify, and to install are over. Hooray, evolution!

---

### Post by woodbj on 2010-09-01
GDM2Setup is easy to use.

[https://launchpad.net/gdm2setup]("https://launchpad.net/gdm2setup")

---

### Post by ranch hand on 2010-09-01
> **woodbj said:**
> GDM2Setup is easy to use.

[https://launchpad.net/gdm2setup](https://launchpad.net/gdm2setup)
Default does not bother me enough to fool with the current fix solution.

I am going to try this though.  Just installed the 10.10beta RC ISO last night and am setting it up right now.  Might as well add this too and have a look when I get over there in testing land in about an hour (I love chroot).

Thanks a bunch for the link.

---

### Post by ranch hand on 2010-09-01
Well bummer.  Don't appear to have anything for 64bit yet.

---

### Post by Mills00013 on 2010-09-01
Just installed on my 64bit maverick install. Had to change the dist to lucid because they dont have a maverick dist. Maybe thats why you are 404ing?

---

### Post by stevetxt on 2010-09-01
Thanks very much.  I used the first method, from MacUntu:

1.) Log out, so you are at the GDM screen.
2.) Press Ctrl-Alt-F1 to change to a virtual terminal.
3.) Log in and run:
Code:

DISPLAY=:0.0 sudo -u gdm gnome-appearance-properties

4.) Go back to the GDM screen: Ctrl-Alt-F8.
5.) You should see the Appearance Preferences window where you can change everything to your liking.
6.) When you're done, close it and that's it.

(It was F8 in step 4.)

---

### Post by ranch hand on 2010-09-01
> **Mills00013 said:**
> Just installed on my 64bit maverick install. Had to change the dist to lucid because they dont have a maverick dist. Maybe thats why you are 404ing?
I will look into that.  Just not a high priority item for me.  Already played with that install this morning.

Will see about it today and check it this evening on my way back to the land of stable releases.

Thanks for the tip, it probably is just that.

EDIT
Yes it was indeed a picnik problem.  The guy in the chair REALLY needs to learn to read.

---

### Post by ktp on 2010-09-01
> **ranch hand said:**
> EDIT
Yes it was indeed a picnik problem.  The guy in the chair REALLY needs to learn to read.

Did you forget to put on the glasses again?? I sure did. =)  
Thanks for the info Mills00013.

---

### Post by ranch hand on 2010-09-01
Nope, just too dumb to have the maverick part of the file title in sources.d register.  Seems to work fine if you go in and change the repo to lucid like a person that could read in the first place would have done.

---

### Post by wojox on 2010-09-01
> **ranch hand said:**
> Nope, just too dumb to have the maverick part of the file title in sources.d register.  Seems to work fine if you go in and change the repo to lucid like a person that could read in the first place would have done.

Last time I tried it for Lucid it downloaded and installed, but wouldn't run properly. I think they devs abandoned it after Karmic.

---

### Post by ktp on 2010-09-01
> **wojox said:**
> Last time I tried it for Lucid it downloaded and installed, but wouldn't run properly. I think they devs abandoned it after Karmic.

thanks for the info...i am still going to try it out since I want to do clean install after it.

---

