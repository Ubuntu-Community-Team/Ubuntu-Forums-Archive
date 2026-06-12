---
title: "asoundconf-gtk doesn't work"
date: 2011-01-02
forum: Multimedia Software
---

### Post by Cotopaxi on 2011-01-02
Hi,

I downloaded and installed "asoundconf-gtk" from the repositories, hoping it would enable me to switch between the computer soundcard and the USB headset.

My operative system is 10.04
The laptop is a Lenovo

When I start asoundconf-gtk from terminal I get this error message:

> no@Laptop:~$ asoundconf-gtk
sh: /usr/bin/asoundconf: not found
You need to make sure asoundconf is active!
By default, asoundconf's configuration file is ~/.asoundrc.asoundconf
and must be included in ~/.asoundrc. Open this file to make sure it is!


Can anyone give me a helping hand please?

Thanks! :p

---

### Post by Cotopaxi on 2011-01-02
hey,

nobody ever installed asoundconf-gtk? ;)

---

### Post by kostkon on 2011-01-02
Have you removed PulseAudio from your system? If not, you need the *PulseAudio Volume Control* utility. You'll be able to set the input/output device for every app in your system and some other things.

Hope that helps.

---

### Post by Cotopaxi on 2011-01-02
Kostkon,

PulseAudio did the trick, thanks very much indeed! :popcorn:

I remember I removed PulseAudio some two years ago, because there was no way to make the USB headset work with Skype.

But now Skype works perfectly with PulseAudio.

Thank you very much indeed again!

---

### Post by harrisupstate on 2011-01-09
Hi all,

I'm having the same problem with the USB headset I'm trying to use with Rosetta Stone (running it via WINE).

I have PulseAudio Volume Control, and it sees the headset just fine, but I can't see where I associate a device with an app.  Can someone explain that part?

Thanks!
Harris

---

