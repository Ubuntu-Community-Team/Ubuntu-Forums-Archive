---
title: "How to setup Ubuntu to works with AirPort Express"
date: 2009-10-16
forum: Multimedia Software
---

### Post by sj_ on 2009-10-16
post with screenshots here [http://www.1ph0ne.com/?p=402](http://www.1ph0ne.com/?p=402)

Hi, guys. I’ve found the great solution to stream all your local sounds to AirPort Express, which connected to your multimedia sound system. Frankly speaking it was almost in the default installation of Ubuntu. All you need is to install the latest Pulse Audio and Pulse Audio Volume Control

    sudo apt-get install pulseaudio pavucontrol paprefs padevchooser pulseaudio-module-raop

Go to the top menu System -> Preferences -> PulseAudio Preferences

Choose in the top menu

Applications -> Sound & Video -> PulseAudio Volume Control

In the Playback tab choose an application you want to stream and select Stream on dropdown menu your AirPort Express

This is the one way you can do it. But i prefer the following solution. Click with right mouse button on the Sound Volume icon in the application tab and select Sound Properties

In the Output tab select your AirPort Express device and that it. Everything should play well and you can manage volume right from Ubuntu Volume Control or using your hard keyboard button. That works very nice for me even better than in Windows or Mac OS X cause you can stream every application you want and control volume control using your system settings. One more thing i would like to mention is that there is no way to use your iPhone with Remote application


Have a fun

---

### Post by onemoreday on 2009-10-18
This sounds interesting. If this works, it will remove the last thing that is keeping me with my Mac as my primary computer.

Can anybody confirm that this works?

---

### Post by sj_ on 2009-10-18
This is works for me. In Windows or Mac you can stream only your iTunes library. But with that pulseaudio raop module you can stream any application you want e.g. i stream last.fm. It evern works with system sounds, streaming audio tracks from video files and games, but this it's not usable cause you need synchronizations because of wireless delay

---

### Post by onemoreday on 2009-10-18
So it works a little like Airfoil for Mac and Win, only for Linux?

[http://www.rogueamoeba.com/airfoil/](http://www.rogueamoeba.com/airfoil/)

---

### Post by sj_ on 2009-10-18
Right, exactly the same way! Just installed that application under Windows 7 to make sure. 

ps. You don't need to run specified app and pay 25 bucks :)

---

### Post by onemoreday on 2009-10-19
Oh. That is exciting.

I could actually go 100% Ubuntu now. Hmmm...

---

### Post by vraicovi on 2010-02-06
Anyone have any luck with an Apple TV?  This works fine on my Airport Express, but I'm not having luck with either of my Apple TVs.  They're listed as an output device alongside the AEX, but nothing streams to them.

---

### Post by raffraffraff on 2010-11-01
I'm not sure if it's because I have a later version of the AirPort Express, but this doesn't work well for me. The sound drop every 3 second or so. It's very precdictable; you get about 3 seconds of audio, then a 1 second drop, then 3 seconds of audio... rinse and repeat ad nausaem.

Has anybody got this working *reliably*? 

I was complaining about this to a friend (who is a bit of a fanboy) and I realised that what I should have done was purchase a bunch of those FM transmitters that you can buy for your car. My amp has a tuner on it. And there's absolutely NO lag. Lo-fi is the way to go sometimes...

---

### Post by hoogland on 2010-11-01
I have the same issue of interrupted playback (few seconds sounds, few seconds drop, repeated) from flash-based players in my browser. However, playing music from Rhythmbox works fine.

---

### Post by brekker on 2010-11-25
Hi all!
My problem starts from the beginning. I can see Apple network, but I can't connect to it: "impossible to get IP address".

How can I solve? Tnx.

---

