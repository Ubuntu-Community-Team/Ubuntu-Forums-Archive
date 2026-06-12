---
title: "Getting different applications to play on different outputs"
date: 2017-02-07
forum: Multimedia Software
---

### Post by ARSR on 2017-02-07
Apologies if this question has been asked before, but I'm not getting any solutions from the other threads I found here.

I'm running 16.04 at this point. I'm attempting to get a setup going where I have VLC player on my 32" TV while using a wine-run .exe on my laptops monitor. While I have the display down, **the audio always comes out of one source only**. I'm trying to get VLC to play out of the HDMI connection, and the exe to play out of the internal speakers of my laptop. I've installed paprefs and pavucontrol, some solutions that where offered here, but I dont get a choice to switch outputs from these applications, they just kind of display what sound is coming from where and that's it.

Thanks in advance for any help.

---

### Post by papibe on 2017-02-07
Hi ARSR.

pavucontrol has that option.

Change the output on the Playback tab, and then go to Output tab and set the volume (which is usually low).

Also, you may need to resize the window as this app is very bad on setting a proper size to display all its content.

Hope it helps. Let us know how it goes.
Regards.

---

### Post by ARSR on 2017-02-07
Thanks papibe

As an update, pavucontrol did eventually show me the buttons but I had to run pulseaudio -k in terminal first. Now I'm running into the problem of not being given the other source as an option in the button. For example if I set my default source in system preferences to the internal speaker, I don't get the option for HDMI, and vice-versa.

Attached is a screen grab to help illustrate what I mean.

[https://drive.google.com/file/d/0B9wK4UOojdCWbk9YdVo3dEhqZjA/view?usp=sharing](https://drive.google.com/file/d/0B9wK4UOojdCWbk9YdVo3dEhqZjA/view?usp=sharing)

---

