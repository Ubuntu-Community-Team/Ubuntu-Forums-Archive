---
title: "Webcam Surveillance w/ GUI"
date: 2009-07-31
forum: Multimedia Software
---

### Post by pteri498 on 2009-07-31
I'm looking for a very simple option to do video surveillance with my webcam for while I am out. There was a Windows program that did this nicely in the past, taking snapshots in case of motion, and then saving the image or e-mailing it to me (which is a great feature, I think).

Are there any such options for Linux?

Thank you.

---

### Post by SteveDee on 2009-08-02
> **pteri498 said:**
> I'm looking for a very simple option to do video surveillance with my webcam for while I am out. There was a Windows program that did this nicely in the past, taking snapshots in case of motion, and then saving the image or e-mailing it to me (which is a great feature, I think).

Are there any such options for Linux?

Thank you.

The application "motion" works well. Although it does not have a user interface it is very configurable via a config file, and the output can be viewed live with a web browser.

Read about it here: [http://www.lavrsen.dk/twiki/bin/view/Motion/WebHome](http://www.lavrsen.dk/twiki/bin/view/Motion/WebHome)

---

### Post by MarkX on 2009-10-11
LOL! The OP asked for a *simple* option to do video surveillance.
"Simple" means it installs in a couple of clicks, detects your connected USB cams and is ready for viewing over the net after setting up the hot zones on a GUI and a password.

Instead of clicking on the file, this is what you have to learn JUST to install "Motion":
[http://www.lavrsen.dk/foswiki/bin/view/Motion/MotionGuideInstallation](http://www.lavrsen.dk/foswiki/bin/view/Motion/MotionGuideInstallation)

FORGET IT! Life's too short.

Zoneminder is even worse.

---

### Post by brian mcgee on 2009-10-12
> **MarkX said:**
> LOL! The OP asked for a *simple* option to do video surveillance.
"Simple" means it installs in a couple of clicks, detects your connected USB cams and is ready for viewing over the net after setting up the hot zones on a GUI and a password.

Instead of clicking on the file, this is what you have to learn JUST to install "Motion":
[http://www.lavrsen.dk/foswiki/bin/view/Motion/MotionGuideInstallation](http://www.lavrsen.dk/foswiki/bin/view/Motion/MotionGuideInstallation)


I don't think that's true. While I've never used Motion, you can install it from the Ubuntu repository by doing:
```
sudo apt-get install motion
```Your webcam should automatically be detected by Ubuntu when you plug it in. Here is a step-by-step walkthrough which makes Motion look pretty simple.

[http://www.junauza.com/2009/07/turn-ordinary-webcam-into-security-spy.html](http://www.junauza.com/2009/07/turn-ordinary-webcam-into-security-spy.html)

---

### Post by brian mcgee on 2009-10-12
> **MarkX said:**
> Zoneminder is even worse.

ZoneMinder is also available in the repos. I'm not sure what you tried, but here's a walkthrough: [http://ubuntuforums.org/showthread.php?t=1050638](http://ubuntuforums.org/showthread.php?t=1050638)

---

### Post by SteveDee on 2009-10-12
Yeah I admit that the documentation on Motion looks daunting, but in fact it installs and runs quite easy.

However, you have to be prepared to spend hours (maybe days) experimenting on something like this. I used it a few months ago with an analogue camera and video capture card to see what was visiting my garden pond each night. 

You need to try different sensitivity settings and maybe only trigger on certain parts of the picture, as trees swaying in the wind will trigger it. But apart from cats (lots of cats!) and foxes, I could get it to trigger on smaller animals such as birds.

I had absolutely no joy with ZoneMinder.

---

