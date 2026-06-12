---
title: "Logitech c210 built in micriphone not working."
date: 2010-09-22
forum: Multimedia Software
---

### Post by solar_anus on 2010-09-22
Help please. =(

---

### Post by lidex on 2010-09-25
OK, I give up, what is  a Logitech C210?

---

### Post by frogotronic on 2010-10-22
> **solar_anus said:**
> Help please. =(

Did you get this WebCam to work?  Under Skype?

---

### Post by cajunlibra on 2011-01-15
I just bought one and I'm having the same issue. THe video works fine.

---

### Post by frogotronic on 2011-01-16
> **cajunlibra said:**
> I just bought one and I'm having the same issue. THe video works fine.

Hello,

  System>Preferences>Sound

  Choose the Input tab and select Analog input, not the internal.

  Restart your application (Skype, Gmail Video Chat, etc)

  Microphone should now work.

- CH

---

### Post by piccobello on 2011-06-09
I guess this is from some time ago, however I had a similar problem recently, 
and I found a turnaround in [this thread]("http://ubuntuforums.org/showthread.php?t=1477942").

My system: Kubuntu Linux 11.04 (Natty)
My skype: 2.2.0.25
My webcam: Logitech c210
Issue: Mic did not work in skype, but did work in audacity
What I did:
-sudo apt-get remove pulseaudio*
-sudo killall pulseaudio
-skype settings -> sound devices -> Microphone -> USB device 0x46d:0x819, Usb audio (hw:1,0)

Now everything works. Video worked out of the box btw.

---

