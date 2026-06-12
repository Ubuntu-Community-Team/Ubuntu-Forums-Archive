---
title: "Ubuntu Minimal:  No Sound"
date: 2009-03-03
forum: Multimedia Software
---

### Post by ArtF10 on 2009-03-03
When I installed Ubuntu 8.10(standard gnome edition), I got sound detected automatically.  It was very clear.  I'm using onboard(ASUS motherboard) sound and have never had any problems with pervious versions of Ubuntu.i.e. they have ALL automatically produced sound upon installation.

Now, I recently installed Ubuntu 8.10 minimal + gnome.  I have turned ALL the volume controls to maximum.  However, I don't get sound.  Do I need to install a specific package?

---

### Post by markbuntu on 2009-03-03
More than one

[http://ubuntuforums.org/showthread.php?t=997506](http://ubuntuforums.org/showthread.php?t=997506)

---

### Post by ArtF10 on 2009-03-03
Thanks, I'll give it a go and see what happens.

One question though:  Is there any way to do it WITHOUT the package "ubuntu-restricted-extras"?

---

### Post by markbuntu on 2009-03-04
If you don't need the all codecs or flash or java you can just get what you want piecemeal.

---

### Post by ArtF10 on 2009-03-14
Mark, just wanted to say thank you.

I finally gave it a try(was away from the Ubuntu machine) and it worked like a charm.  I never had to install gstreamer or restricted extras.  The "piecemeal" thing you talked about worked.

EDIT:  For others considering this installation, the only problem I had was that Applications>Pulse Audio Device Chooser, which was suposed to give me an icon on the panel to choose the appropriate device, never opened up.  I rebooted but that made no difference.....it still never produced an icon on the panel.  Did not make a difference to me......sound still showed up.

---

### Post by ArtF10 on 2009-03-14
One thing I noticed....I'm only getting sound out of one of my two speakers.  Both are supposed to be working.

Any idea what could be causing this?

---

### Post by markbuntu on 2009-03-14
You can check the volume controls and volume meters to see if it is a software problem. You can check your speaker connections to see if it is a hardware problem.

---

### Post by buldozerceto on 2009-03-14
you can also use alsamixer from the terminal.

---

### Post by ArtF10 on 2009-03-15
**ERROR MESSAGE**

Ok I seem to have both speakers with sound.  HOWEVER, I have noticed that after around 6 minutes, the system loses sound.i.e. sounds do not play.

I went to System>Preferences>Sound and clicked on test to test the various options and here is the error message I get:

audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink profile=chat: Failed to connect stream: Invalid argument

Any ideas as to what could be causing this sound loss?

Could it be because I did not install gstreamer or ubuntu-restricted-extras, as was said in the instructions posted above?

---

