---
title: "Skype webcam problem"
date: 2009-04-29
forum: Multimedia Software
---

### Post by WildeBeest on 2009-04-29
I'm running a fresh install of Jaunty.

I installed skype, installed the driver for my webcam (Lifecam vx-1000).

It works with cheese, but not with skype. All I get is colorful static.

It does work with my Hardy install.

Any help is appreciated.

---

### Post by prvteprts on 2009-04-29
Same here.

Using an A4tech PK-35N webcam on Ubuntu Jaunty 9.04. It seems to work only with Cheese. On Skype it outputs static.

It worked with Ekiga on Intrepid, but oddly Ekiga on Jaunty doesn't show the webcam option, so I can't test it.

---

### Post by dmizer on 2009-04-30
The current implementation of Skype was developed and released for Hardy, so I wouldn't count on great Skype support for Jaunty. Since Skype is closed source, the community can't develop an update for it.

I do suggest searching the Skype forums for possible solutions though, as they do have a Linux specific forum: [http://forum.skype.com/index.php?showforum=18](http://forum.skype.com/index.php?showforum=18)

---

### Post by Arup on 2009-04-30
Skype runs fine on Jaunty as long as you dont' use PULSE for audio out. Jaunty's gpspca is built into the kernel so webcams are recognized by default, only issue is that they tend to run dark, to fix that, install xatv and adjust the cam with the settings there, selecting auto gain works out good for the cam.

---

### Post by WildeBeest on 2009-04-30
Where do I find xatv?

---

### Post by Jose Catre-Vandis on 2009-04-30
think Arup means xawtv

And @ Arup how do I tell Skype not to use Pulse, I have no option for such a choice in Skype's sounde devices section, only lots of hardware device choices?

---

### Post by WildeBeest on 2009-04-30
xawtv didn't work.

---

### Post by hobo14 on 2009-05-09
Me too.

Cam works in Cheese (too dark, but it works), but just green static in Skype.  
9.04.

I tried xawtv to adjust my cam settings, but it didn't seem to make any difference.


[COLOR="Red"]**EDIT: I was using the latest .deb from skypes website.  I unistalled it, then reinstalled skype from the repositories through Synaptic, and now my webcam is fine! ;) **[/COLOR]

---

### Post by Jose Catre-Vandis on 2009-05-10
> **hobo14 said:**
> 
[COLOR="Red"]**EDIT: I was using the latest .deb from skypes website.  I unistalled it, then reinstalled skype from the repositories through Synaptic, and now my webcam is fine! ;) **[/COLOR]

OK. Skype is not in the standard Ubuntu repos, so do you have medibuntu in your repos?

**skype 2.0.0.72-0medibuntu4**  ??

---

### Post by hobo14 on 2009-05-10
> **Jose Catre-Vandis said:**
> OK. Skype is not in the standard Ubuntu repos, so do you have medibuntu in your repos?

**skype 2.0.0.72-0medibuntu4**  ??

Ah, yes I do, I put it in there for something else, forget what.

The package is just called "skype" (not skype 2.0.0.72-0medibuntu4) and the version is 2.0.0.72-1.

---

### Post by Jose Catre-Vandis on 2009-05-11
Hmmm, I am only getting 2.0.0.72-0 on my jaunty?

---

### Post by ryecomp on 2009-05-12
Prvteprts, 

VX1000 works with ekiga. 
I didn't test it under skype. 

See my post for fixing procedure.

kernel : 2.6.28-11-generic
latest stable gspca : v4l-dvb-fe524e0a6412

---

### Post by hobo14 on 2009-05-12
I don't know what's going on, to be honest.
Could it be because I installed their latest version, and then changed to the repos version?
[IMG]http://img222.imageshack.us/img222/1131/screenshotsxv.png[/IMG]

---

### Post by Jbike on 2009-05-12
For the record, I have never been able to get skype to work with a web cam on any other distro. 

Jbike

---

### Post by sorak on 2009-05-12
medibuntu fixed up my skype errors and the v4l bounciness. :) thanks! (running 9.04, here)

---

### Post by lelamal on 2009-05-14
Hi, I found a solution in [this thread]("http://ubuntuforums.org/showthread.php?t=997807&page=3"). I'm now using gregbzh's suggestion, and everything's working fine. Hope that helps! ;)

---

