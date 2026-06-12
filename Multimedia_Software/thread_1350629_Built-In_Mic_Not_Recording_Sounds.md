---
title: "Built-In Mic Not Recording Sounds"
date: 2009-12-09
forum: Multimedia Software
---

### Post by ChappyHappy on 2009-12-09
I'm using Audacity in Windows7 and Ubuntu9.10 to record audio.
My Dell 1318 comes with a built-in mic. 
And also a 3.5mm analog jack, but that isnt the issue.

In Win7, it records the audio properly from the built-in mic.
In 9.10, it doesnt record it from the built-in and requires the analog jack.

I know the built-in mic works cause it worked in Win7. So how would I get it to work in Karmic too?

Thanks

---

### Post by gordintoronto on 2009-12-09
If you run Preferences/Sound and select the Input tab, does the built-in mic show up?

---

### Post by ChappyHappy on 2009-12-09
Only "Internal Analog Audio Stereo"
Which is the 3.5" mic.

---

### Post by markbuntu on 2009-12-11
You can get the gnome-alsamixer which should expose all the switches and controls for you sound chip. If it does not then you may need to add some options to the driver. These problems are very hardware specific as you will see if you go here:

[http://ubuntuforums.org/showthread.php?t=1043568](http://ubuntuforums.org/showthread.php?t=1043568)

I do not think the dell 1318 is listed but you can try some of the options that work for other dell and hp machines.

---

### Post by dolphinsonar on 2010-05-14
This thread is marked solved, but there isn't a solution listed.  I have checked out the database linked to in the previous post and the Dell inspiron 1318 is not listed.  The problem persists.  I tried a couple of the solutions listed for other Dell computers, but I would like to have a more targeted approach, rather than trial and error.  Anyone make progress on getting the built in mic working on this laptop?

---

### Post by dolphinsonar on 2010-05-16
Markbuntu,

I found someone who has fixed the Dell Inspiron 1318 internal microphone problem by editing the ALSA configuration file, as you suggested.  Here is a link to the explaination.  I will add it to your database thread also.

[http://www.tighturl.com/243n](http://www.tighturl.com/243n)

---

