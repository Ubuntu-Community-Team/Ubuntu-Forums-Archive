---
title: "broken sound from backports"
date: 2008-04-25
forum: Multimedia Software
---

### Post by bayonetblaha on 2008-04-25
while trying to get the microphone to work on my Inspiron 1520 I installed linux-backports-modules-2.6.2 from synaptic (since linux-backports-modules-generic was the common fix for gutsy).  Before I at least had sound from my speakers, but now it's a total mess!  The sound preferences shows no devices at all, and any attempt at a test yields:

 audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink profile=chat: Failed to connect stream: Invalid argument

or similar error.  How can I just go back to regular ALSA like I had a half hour ago? I'd like to just wait until someone figures out a proper microphone solution.

---

### Post by bayonetblaha on 2008-04-25
also, the solution I was using to get usb internet from phone now reports

/lib/modules/2.6.24-16-386/build: No such file or directory.  Stop.

when I try to build it.  Did I change my kernel? This is awful.

---

### Post by bayonetblaha on 2008-04-25
also I have a hyperactive system beep- any holding down of the backspace key for example in an empty field yields a loud beep.  Seems like I just need to "install" my undetected sound card.  How?

asoundconf list yields nothing

---

### Post by bayonetblaha on 2008-04-25
uninstalled pulse audio to see what happens and a reboot went to the terminal login. startx worked but I'm back where I started with no sound.  I did get a popup telling me to run asoundconf set-default-card, though.  No success there

---

### Post by entwoska on 2008-04-25
I got the same problem switching from Alsa to PulseAudio.
Alsa worked great but no more sound in Hardy with PulseAudio.



I'll work on this today and let you no if anything (good) happens! :)

---

### Post by bayonetblaha on 2008-04-25
I'd like to note that before I installed (and subsequently removed) linux-backports-modules-hardy pulseaudio worked great for me!

---

### Post by crimsontime on 2008-04-30
The same thing happened to me on gutsy.   It was horrible and I could not solve it after hours on the forums.  Since I'm a new user I cut my losses, blew out everything and installed Hardy.  Now the only thing not working is still the microphone but I won't install the backports again.  Good luck solving this.

In Hardy Heron, I solved it this way:
 Re: HOWTO: XPS M1530 internal microphone (resolved)
On the Ubuntu Hardy release candidate, the microphone works out-of-the-box (ALSA 1.0.16 is already included). You do have to configure it, however:

   1. Double-click the volume control icon in the top right of the screen.
   2. Select Edit / Preferences.
   3. Add "Digital" and "Digital Input Source" to the list of visible tracks.
   4. On the Options tab, select "Digital Mic 1" for "Digital Input Source".
   5. On the Recording tab, set the volume for the microphone.

---

