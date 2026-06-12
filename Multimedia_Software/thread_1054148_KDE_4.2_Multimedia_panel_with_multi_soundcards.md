---
title: "KDE 4.2 Multimedia panel with multi soundcards"
date: 2009-01-29
forum: Multimedia Software
---

### Post by wd5gnr on 2009-01-29
I've had this problem consistently with the whole 4.x series of KDE running kubuntu 8.04 and 8.10. 

I have multiple soundcards (motherboard, 2 PCI cards, and several USB devices -- ham radio stuff).

Phonon shows the cards in the Multimedia panel and lets you set the device preferences. The problem is that the changes don't "take". Sometimes they seem to take but then they go back to their default settings after awhile. What's more things like notifications don't play unless I happen to use the soundcard that it defaults to.

As a workaround I just set the notifications to use playsound and have the ALSA default set correctly. But that doesn't help for other software that is Phonon-aware and won't use another backend (mercifully few programs). Doesn't seem to matter which backend (Xine or GStreamer) I select.

Filed a bug on kde.org regarding this, but haven't seen any changes. So I can't figure out if it is something peculiar to my set up or just a bug that doesn't show up when you have a single sound card.

---

### Post by markbuntu on 2009-01-29
I also have multiple sound cards and usb devices. I use pulseaudio in both gnome and kde. On Intrepid, since I installed KDE4 over gnome I already had pulseaudio so phonon defaulted to use pulseaudio. 

Pulseaudio is the only reasonable way I have found to control multiple hardware devices. Phonon might do it eventually.....

Phonon still seems to be very much a work in progress with much necessary functionality not fully functional yet.

---

### Post by wd5gnr on 2009-01-29
Yeah I have setup Pulseaudio. However, even then Phonon won't remember to default to Pulseaudio. So for everything that doesn't use Phonon, that's fine. But for anything (e.g. KDE system notification by default) that uses Phonon, you are still hosed.

---

### Post by markbuntu on 2009-01-29
Here's what I did to get PulseAudio managing all the sound in KDE4.

Pulseaudio does not start by default with KDE so you need to put a launcher in System Settings/Autostart. I also made a launcher for padevchooser.

Open System Settings/Advanced/Autostart. Select Add program, type pulseaudio -D in the box and select Run in Terminal and Do not close when command exits click OK. In permissions check Is executable. In Application/Name Pulseaudio and check that the Command is pulseadio -D so it starts with the defaults from default.pa. click OK

You can do the same thing with padevchooser to get the chooser in the panel.

Log out, log back in and pulseaudio should be running. 

In System Settings/Sound make default the first option and in Backend choose gstreamer. In Settings/Multimedia System Selector(gstreamer setup)/Audio/plugin select the PulseAudio Sound Server and set Device to Default. 

In Settings/Default Sound Card asoundconf.gtk choose PulseAudio. This will send all the alsa apps to PulseAudio. If you have libasound2 most oss apps will go there too.

I have not figured out yet how to get xine to default to pulseaudio but I am sure it is something fairly simple.

You may be missing some of the packages needed to get this working like gstreamer and the gstreamer backend for phonon and asoundconf.gtk

My 10,000 page guide to sound is here if you need more help

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

---

### Post by wd5gnr on 2009-01-29
Yes I've pretty much done all that you've described other than I have only done superficial testing with gstreamer. However, the problem is that the Phonon selector won't remember what the choice is which includes PulseAudio. Keep in mind that Alsa (and even PulseAudio) is working fine. It is just that the KDE sound system always resets to hw:0 no matter what I try to set it to. And yes, I've tried clearing the phonondevicesrc and so forth.

---

### Post by markbuntu on 2009-01-30
In the System Settings/Sound/Device Preference I just set it to default. There is no pulseaudio selection available there but I could have sworn I saw one there in the past.

Amarok2 uses phonon yes?
Seems to work fine with my setup. Pulseaudio says it is using the ALSA plug-in.

I noticed in Settings/Qt configuration there is a phonon tab but it does not seem to do anything. It says

 Phonon Gstreamer backend not available

Well this is getting very mysterious. I will try switching phonon back to xine backend and see what is going on. I will let you know what I find out.

EDIT: Well I tried it with Amarok playing and the amarok stream disappeared from pavucontrol when I hit apply to change phonon to xine. Amarok seemed to get hung up so I restarted it, hit play and the stream came back.

---

### Post by markbuntu on 2009-01-30
Well this conversation has prompted me to do a little more research and testing and make a guide for pulseaudio on KDE4. Please give it a read, comments, contributions, help, disparagements encouraged. 

[http://ubuntuforums.org/showthread.php?t=1055591](http://ubuntuforums.org/showthread.php?t=1055591)

---

