---
title: "Root node has no children! - freebob"
date: 2007-11-18
forum: Multimedia &amp; Video
---

### Post by rafafredd on 2007-11-18
Trying to get my maudio ozonic going with ubuntustudio 7.10 using freebob... I think I've made some progress now, but still not working. At least I got another error message now. I'm getting root node has no children now. I did all the tests I could that are mentioned on freebob's FAQ:

 >   1.  Check if the device is connected to the PC and that it is powered up. BTW, it is better use a power supply and don't rely on bus power. Especially, if you are planning to use it for a live concert.
   2. Do not startup up the jackd immediately after you have attached the device. The device needs some time to boot itself.
   3. If you have more then on port on your FireWire interface card to connect to try another one. Alternatively you can tell freebob which port it should use first. By default freebob will look for devices on port 0. So if your device is on port 1 you have to tell freebob to enumerate devices on port 1. So instead of starting jackd like this 'jackd -dfreebob' use 'jackd -dfreebob -dhw:1'
   4. Check if gscanbus ([http://gscanbus.berlios.de/](http://gscanbus.berlios.de/)) sees your device.
   5. Check what test-freebob reports back. You can find this program in the libfreebob/tests directory if you have compiled your own libfreebob version. 

Gscan shows my M-audio ozonic just fine.

Couldn't do the freebob test (number 5  above). Does anyone knows where is this libfreebob directory?

Also, I've checked my libraw1394 at the Synaptic PM, and it's listed as libraw1394-8 1.2.1-3build1... But from reading the ffado homepage it seems that there is a 1.3.0 version out there. Althought automatic updates doesn't show this. Could this be the problem? What raw1394 do you have in your system, just to check.

Also, I've tried "system->administration->user and groups" and there is no audio group in my system, Should I create it and add me as a user?

Any other hints, you lucky guys that have this working...? Sorry for these many questions, but I've looked everywhere I could, and tried everything on the net...:confused:

---

### Post by rafafredd on 2007-11-19
](*,)](*,)

That's really how I feel. Now for some reason freebob says again that there is no ieee1394 driver in my system. Well, it's right cause when I run gscanbus it also cannot find the 1394 port anymore. So I'm walking backwards. And the bad thing is that I don't remenber what I did last time, but it seems whatever it was, it didn't persisted after booting. Oh boy. The question is... is anyone using freebob with gutsy? What did you do to make it work? I've tried it all, it seems. Could someone that has jack and freebob working, check their lib list in the synaptic and tell me what are the liraw1394 you have installed? I on ubuntustudio 7.10 and it says libraw1394-8 1.2.1-3bild1 ... I have a feeling that freebob and gscanbus are both looking for libraw1394 and not libraw1394-8, like I have in my system. So, I was able to download the latest libraw1394 release, the file libraw1394-1.3.0.tar.gz from [www.linux1394.org](www.linux1394.org) , but guess what... I don't have a clue how to unpack and install it. I've tried to read there, but it's really, really, really over my head.

The thing is that I bought a brand new laptop, and a brand new ozonic (I've checked before to see what were my options that were freebob compatible, and that's why I've bought an ozonic) and now they won't work together, so I'm in the point of getting crazy and sell it all, and maybe try a desktop and a delta 1010 for my ubuntustudio system. Would it work out of the box maybe? On the maudio site it says they provide a linux driver. Well, does this driver for the delta 1010 works with gnome/gutsy? Because really, I don't see freebob and ozonic working in my system aytime soon.. And right now I'm just sitting here, staring at my new laptop screen and my brand new ozonic and after all these days of hard work and no sound, I kinda wanna cry...

Thanks for any inputs, but I just give up. Maybe I wasn born for this linux world. I was really loving it, but it may be time to put my hands on my pocket, and maybe buy vista with cubase SX, or something alike, and get back on making music, because that's what's really important for me anyway. Sorry for the rant, I'm pretty newbie and I have ubuntu for over a week now only, but I would just like to know if someone could recommend a soundcard with ready to go drivers for ubuntustudio. I've heard about the old MAUDIO cards, like 1010 and 44, echo cards, lynx and also rme cards. What would be the easiest and more stable in ubuntustudio? I wanna buy my peace here. I don't wanna keep messing with feebob anymore. It just do not like me.

So, do you have a stable UBUNTU DAW working on your studio? Could you share the details, please, like mobo, soundcard, etc...?

Regards,

Rafael

---

