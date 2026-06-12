---
title: "microphone problems - kubuntu 7.04"
date: 2007-05-21
forum: Multimedia &amp; Video
---

### Post by arimed on 2007-05-21
hello all!

I'm using  kubuntu 7.04, and just bought an external microphne for Skype.
the problem is that I can hear myself speaking in the microphone through the speakers/headphones. but niether in Skype or sound recorder I can't hear myself.
if I use the pc camera as microphone - in skype it works just fine.

I checked in kmix - the mic is not muted, it is marked for capture (red light under mic icon) and the volume is high.

any suggestions?

thanks...

---

### Post by leisuresuitgreg on 2007-06-26
I've got the exact same problem. Just updated to 1.4 beta and still nothing... Hope someone figures something out soon, as my girlfriend is moving to England (I live in NZ) and I can't afford the phone bills!!!

Greg

---

### Post by solanky on 2007-07-01
I am also having same problem. I am using laptop built-in mic, when I say something in mic my voice play via speaker but not in Skype or Sound Recorder.
I have searhed a lot but could not find a solution yet.

---

### Post by punkybouy on 2007-07-04
On the top panel right click on the speaker icon and select "Open volume control" Then in the window that pops up you should have two tabs: "Playback" and "Capture". Make sure your mic is not muted in these and in the "Capture" tab make sure it is not muted here and push the volume sliders to maximum. That should work.

---

### Post by alexsb on 2007-07-06
Hi, I have exactly the same problem since I updated to 7.04 on a  Samsung q35 notebook.

No channels are muted. Any Ideas?

---

### Post by alexsb on 2007-07-06
Ok, I got it working in skype now, by selecting the input device manually and not using the default input device. However, in the KDE audio recorder I can't see such an option and there I still don't have sound (which is not really important to me thought)

Alex

---

### Post by leisuresuitgreg on 2007-07-08
The more I search and try to figure out the problem, the more I seem to think it is to do with the Sigmatel driver used by WinXP. In windows when you plug in a microphone or line in, Windows gives a pop up to ask whether it is a microphone or line-in. So I'm pretty sure that Ubuntu is handling that too well and can't capture properly from any line in's.

Thoughts???

Greg

---

### Post by leisuresuitgreg on 2007-07-11
It's working but I have to run an external sound card (Creative SB Live 24 bit external) which required a couple of patches and rewrite of .asoundrc (see [http://ubuntuforums.org/showthread.php?t=204840&highlight=SoundBlaster+Live+External&page=2]("http://ubuntuforums.org/showthread.php?t=204840&highlight=SoundBlaster+Live+External&page=2") )
Bit of an expensive fix but at least I'm not back on windows just for skype

Greg

---

### Post by needhelpplease on 2008-03-04
I'm having the same problem.  Incoming sound is fine.  Incoming video is fine even.  Mic doesn't work.

Skype used to work *fine* on Linux.

How can this be so hard?  Linux has had sound capabilities for over ten years now.  ALSA itself is ten years old and has been a standard part of the kernel for five years.

Skype for Linux worked pretty well for the past couple of years.

And now I install it on my Vaio, running Kubuntu 7.04 and Skype 2.0.0.43, and the mic no longer works.  I don't know if the Vaio has a built-in mic, but in any case, the mic on my plain old headset doesn't produce any sound on Skype.

I know it's pointless of people to whine about free software, but this is beyond absurd.  Sound for Linux is old old stuff and it worked reliably before and now it is broken.

I looked at the Skype for Linux sound help pages and tried their suggestions, to no avail.  Any other ideas would be welcome.

---

### Post by roxyisgoofy on 2008-03-07
Maybe someone can help me I am very new to Ubuntu. I don't know how to set up my microphone. The sound works fine but if I try to use sound recorder it says Your audio capture settings are invalid. Please correct them in the Multimedia settings. I don't even know how to get to Multimedia settings. HELP!!!!!:guitar:Music is my first love

---

