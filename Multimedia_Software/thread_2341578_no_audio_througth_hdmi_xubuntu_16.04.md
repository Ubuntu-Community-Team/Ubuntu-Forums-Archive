---
title: "no audio througth hdmi xubuntu 16.04"
date: 2016-10-29
forum: Multimedia Software
---

### Post by jacksar on 2016-10-29
Hi everyone, I need you're help!
I have an old laptop with ATI Mobility Radeon HD 3400 Series and i have already installed xubuntu 16.04.
Everything works fine except one things, that is important for my purposes: audio througth hdmi.
Video works with no problem. Please, i have already searched and try almost everything, also tried to enable boot flags and reistall alsa and pulsaudio and so on.. pavucontrol said that hdmi is unplugged also if isn't.. Anyone can help me please? ](*,)

---

### Post by Russ_H on 2016-10-29
I have that problem and have not had a reply yet, hopefully soon!, Could you see if it's the same issue, check the sound on the internal test, just the left speaker and right speaker, that works on mine. The problem I have is as soon as an application starts it shuts down the audio stream, except if I then go to alsamixer and mute/unmute S/PDIF it works, unfortunately I have to do this every time an app changes or the app is left unused for a few minutes.

---

### Post by jacksar on 2016-10-29
I don't know if it's the same problem because I haven't any sound also during test on hdmi interface.. and alsamixer S/PDIF is unmute.. It's frustrating not solve this..](*,)](*,)](*,)

---

### Post by Russ_H on 2016-10-29
Yes, it was unmute on mine, it worked when I muted it and then I unmuted it, have you tried that?

---

### Post by sudodus on 2016-10-29
I run Lubuntu 16.04 LTS plus pulseaudio and pavucontrol.

I started ***pavucontrol*** to tweak the audio settings, but HDMI was 'unplugged' even when I plugged things into it.

I had to activate HDMI with ***lxrandr*** (I still use VGA video, but connected my earphones via an adapter to HDMI). Standard Ubuntu and other Ubuntu flavours have different tools to manage the same thing, and I guess it can be more or less automatic.

I checked the tabs for configuration and output, that there are signals. I had to select audio from HDMI in the playback tab (because I am normally using analog audio via an old Vortex card.

These instructions can be understood better, when you look at the attached screenshots.

---

### Post by Russ_H on 2016-10-30
I take it your audio is functioning correctly now?

---

### Post by sudodus on 2016-10-31
Are you asking me? Yes, it is working correctly.

---

### Post by jacksar on 2016-11-06
I gave up&#128542; thanks for help but anythings works for me.. I connect pc through vga and analog aux and use pc in this way..

---

### Post by Russ_H on 2016-11-27
My HDMI is not working, except when I mute and unmute in Alsamixer but any app change and it dies again, test sound L/R speaker always works, I can see when an app using audio starts it just shuts down the link. I have to use USB audio, its a real pain I am not sure why its not fixed yet.

---

### Post by sudodus on 2016-11-27
I think alsamixer is difficult to use, so I install pulseaudio and pavucontrol in Lubuntu. I find it easier to manage the audio settings with pavucontrol. (Pavucontrol is bundled with Xubuntu if I remember correctly.)

Recently I configured an HP laptop for a friend. It was as easy (or difficult) in Ubuntu as in Windows to configure the audio and the video via the displayport, an adapter and an HDMI cable to an HDMI port of the TV set.

---

