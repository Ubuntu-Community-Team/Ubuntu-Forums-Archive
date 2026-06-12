---
title: "pulseaudio -- a godsend or a disaster?"
date: 2011-03-02
forum: Multimedia Software
---

### Post by pwabrahams on 2011-03-02
My microphone has stopped working, and one of the threads here advises removing pulseaudio.  That worked for some people but it doesn't work for me.  I did have the microphone working a week or so ago and pulseaudio was installed then.

From what I read around here, the Ubuntu experts believe that pulseaudio is the way to go.  Are they wrong?

---

### Post by inkrypted on 2011-03-02
I can hear my mic but cannot use it with Skype or any other program. I had to remove Pulse audio just to get that far. I don't remember having any such troubles with ALSA. So I am not a big Pulse audio fan. I was really bummed to see it coming to Kubuntu.

---

### Post by pwabrahams on 2011-03-02
I tried removing pulseaudio and pavucontrol as an experiment, but it didn't work.  I still see the message "no input devices" from various programs like kmixer.

---

### Post by inobe on 2011-03-02
i removed pulse a wile back and all my devices are still working fine, skype works great as well.

pulse seems to be great for gnome, not so great for kde.

pulse will hide muted slider controls... in which these controls can't be modified with pulse installed.

after removing pulse and restarted, kde asked if i wanted it to handle my device, of course i clicked yes.

for folks that are having problems, it seems this only happens on kde!

if you have a gnome desktop, stay clear, it just may mean, your device isn't detected and you should find other way to troubleshoot them.

---

### Post by Yellow Pasque on 2011-03-02
recurring discussion..

---

### Post by pwabrahams on 2011-03-03
For me, the trick turned out to be muting Smart 5.1 in alsamixer.  Now my mike works with pulseaudio removed.  I don't know if it would work with pulseaudio installed.

---

### Post by inkrypted on 2011-03-03
I have installed pavucontrol and also removed pulse audio and had the message asking if i wanted to remove devices all that good stuff. My biggest problem is if i go in and unmute my mic I hear it plain as day but Skype or other programs will not use it no matter what I do so I just gave up. My sound works ok and voice chat is not that essential to my life.

---

### Post by pwabrahams on 2011-03-03
> **inkrypted said:**
> I have installed pavucontrol and also removed pulse audio and had the message asking if i wanted to remove devices all that good stuff. My biggest problem is if i go in and unmute my mic I hear it plain as day but Skype or other programs will not use it no matter what I do so I just gave up. My sound works ok and voice chat is not that essential to my life.

You might just need to be patient.  Skype won't pick up the removal until you've quit it and come back -- or maybe even logged out and logged in again.  Then go to the Skype Options and look at Sound Devices.  If you look at Sound Devices *before* you've restarted Skype, chances are that you'll see it's still trying to use PulseAudio.

---

### Post by inkrypted on 2011-03-04
Very true and I have rebooted and restarted Skype multiple times during the time I was trying to figure that out. I have some hope for Natty that pulse will be implemented better with KDE 4.6 or whatever version is out when it officially launches. Thanks for the advice though.

---

