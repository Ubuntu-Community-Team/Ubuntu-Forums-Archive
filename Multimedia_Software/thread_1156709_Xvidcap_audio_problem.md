---
title: "Xvidcap audio problem"
date: 2009-05-12
forum: Multimedia Software
---

### Post by Braedon on 2009-05-12
This may sound like an utterly stupid question but...
How do you record Audio in Xvidcap? I have all of my microphone settings turned on maximum volume, and the UBuntu Sound recorder works like a charm. I have the latest ALSA drivers and I am running a duel boot with OSX on a unibody macbook. 

If no one can answer that question then, how can I make GTK Recordmydesktop not slur my audio? By saying "slur" I mean doing this: And so I wouketosajonaismy name. Translation: And so I would like to say Jonas is my name. It finishes waaay earlier that the video clip ends... It's like it fast fowards on some parts.
Please help!

---

### Post by Braedon on 2009-05-12
bump

---

### Post by johnnygoodman on 2009-05-23
> This may sound like an utterly stupid question but...
How do you record Audio in Xvidcap? I have all of my microphone settings turned on maximum volume, and the UBuntu Sound recorder works like a charm. I have the latest ALSA drivers and I am

I have this same issue. Unable to trick Google into telling me the answer. :)

Johnny

---

### Post by johnnygoodman on 2009-05-23
Figured it out! The newest version doesn't include the audio tab in preferences and doesn't support audio due to a bug. Uninstall it through synaptic and install xvidcap_1.1.7intrepid_i386.deb. 

I followed these directions and it worked with no config:

[https://bugs.launchpad.net/ubuntu/+source/xvidcap/+bug/375711/+activity](https://bugs.launchpad.net/ubuntu/+source/xvidcap/+bug/375711/+activity)

Johnny

---

### Post by MetroPietro on 2009-08-20
Hi, still cannot record sound from a flash presentation playing in Firefox.
Uninstalled Jaunty version, installed intrepid version; got Audio Settings on MultiFrame tab. 
Started xvidcap from terminal as:
$ padsp xvidcap
...to ensure that pulseaudio is being used. However, could not record streaming sound except to capture it via the microphone (built-in or jacked in). How do I:
1. Mute the microphone so that xvidcap is not picking up microphone sounds from the room (such as me clicking the mouse)?
2. Get xvidcap to record the streaming audio from a flash animation in Firefox?

If this should "just work", are you aware of bugs in pulseaudio which prevent this from "just working"?

---

### Post by geodanny on 2009-11-18
This solution worked for me as well. I uninstalled the version installed through the software center. I then downloaded xvidcap_1.1.7jaunty_i386 (the most recent version shown on Sourceforge) from the SourceForge project page for xvidcap [http://sourceforge.net/projects/xvidcap/](http://sourceforge.net/projects/xvidcap/)  Audio now works for captures. I am running 9.10.

---

### Post by GoodPanos on 2010-01-26
Me too :D

Thank you for the solution.  Too bad the version in the repository does not work right.

---

### Post by Lektorvis on 2010-03-11
> This solution worked for me as well. I uninstalled the version installed through the software center. I then downloaded xvidcap_1.1.7jaunty_i386 (the most recent version shown on Sourceforge) from the SourceForge project page for xvidcap [http://sourceforge.net/projects/xvidcap/](http://sourceforge.net/projects/xvidcap/) Audio now works for captures. I am running 9.10.

Worked for me too, but isn't the real problem the GUI? Here is how XvidCap looks on my desktop: [http://img57.imageshack.us/img57/5559/xvidcapmu.png]("http://img57.imageshack.us/img57/5559/xvidcapmu.png") compared to other screen-dumps of the program-gui I miss some menu buttons.
I figured out the hot-keys for preference: ctrl+p

Any-body who found the missing buttons?

---

### Post by Potters Son on 2010-05-12
> **Lektorvis said:**
> Worked for me too, but isn't the real problem the GUI? Here is how XvidCap looks on my desktop: [http://img57.imageshack.us/img57/5559/xvidcapmu.png]("http://img57.imageshack.us/img57/5559/xvidcapmu.png") compared to other screen-dumps of the program-gui I miss some menu buttons.
I figured out the hot-keys for preference: ctrl+p

Any-body who found the missing buttons?

@Lektorvis: Right click on the button on the left. It's a menu. Bad GUI design, I know.

I'm having problems with "padsp xvidcap"; it's still silent and crackly; nothing gets through.

---

### Post by rjwse on 2011-01-22
I am unable to record audio with padsp xvidcap in 10.10 even though Audacity and Desktop Recorder record audio okay.  I have experimented with the settings in Sound Preferences and Pulse-Audio Volume Control but have been unable to record sound with xvidcap.  I have been using a VLC video as audio source.  There are literally hundreds of combinations to try.  I found padsp on Google.  Apparently it is a patch to refer to an older sound system in Linux which supposedly enables dev/dsp in Pulse audio and ALSA.  I want to use xvidcap instead of Desktop Recorder because the video seems much clearer.  I am making How To tutorials about Ubuntu for Youtube.  The ones I have made so far have subtitles instead of sound except for a couple of blurry ones made with Desktop Recorder.  If anyone can help I would appreciate it very much.

---

