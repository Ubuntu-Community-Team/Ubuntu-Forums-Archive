---
title: "How do I get USB audio to work on sites like YouTube with built-in video playing?"
date: 2007-11-02
forum: Multimedia &amp; Video
---

### Post by Jbanicar on 2007-11-02
I've posted this several times, and to date no one has been able to help me with it.... I'm starting to think that maybe no one else either uses a USB headset or all the hardcore Linux users are thinking to themselves, "Leik just use z speakers lolz!"

Anyway, humor aside, I have a Logitech USB Headset.  It works fine.  It is recognised.  It is selected in the audio options.  Yes, I have read endless google searchs, and tried several things.  Yes, the audio plays fine through them when playing a DVD using VLC or whatnot.  Yes, I have the MPLayer pluggin work on for when site videos allow it.  

Sites like YouTube or maybe gaming sites, however, have their own built-in video, so there is no option to select an audio out or audio device, and the sound just plays straight through the stock laptop speakers instead.  This is very frustrating, because while my experiences with Linux such as internet surfing, playing a video, or flipping my pretty 3D cube are all nice...

 I didn't believe those were the reasons why I wanted to try Linux in the first place... the reason being was so I could have my own, more personal experience, and enjoy a more secure envriroment, however, this is becoming less and less of the case, since my own ninche' ways of enjoying my PC time, are always thrawted by the platforms lack of things "just working."  

To date, among this USB Headset thing, is I would also love to be able to use my wireless ability that works perfectly fine under Windows.  I found Linux drivers for it, but I don't know how to install them, since there is no easy "Install here" or instructions on how to do so included in the read me.  I downloaded a "Windows Wireless Divers" program for Linux, and got the Windows drivers and "added" them that way, but it didnt make a difference.

So my experience is essentially dumbed down when using Linux, and while I am perfectly able to read guides, search google, and hop on IRC and ask endless questions during my spare time, I do not have several hours to do this every single day.  

My system is a Dell XPS_Gen2

---

### Post by daviddowney2 on 2008-05-19
HI,

I use a trends ud-10.

What I did was when I first installed it , I went to the preferences and chose usb audio as the default for playback.

It would not play in the browser so I did a asoundconf list and it gave me the two sound cards (sb and default).  I then did a sudo asoundconf set-default-card default and it works now.

---

