---
title: "Getting video INTO Ubuntu (Kino) - SOLVED"
date: 2007-12-20
forum: Multimedia Production
---

### Post by ChasHutch on 2007-12-20
I found this to be interesting and I wanted to share:

I am brand new to video editing, meaning I have NEVER even attempted it before this morning.  My wife had taken video on her old Sony Handycan (DRC TRV730) of our son's christmas concert.  I have a 7.10 Ubuntu box, we don't run Windows in our house other than our work laptops.  So, I was limited in my choices.

Here is what I did:

1.  Searched these forums for a software recommendation (found Kino)
2.  Installed it - sudo apt-get install kino <--  not to tough, huh?
3.  Ran it (pretty simple so far)
4.  Pluged in the Firewire cable from the PC to the camcorder, nothing spectacular happend but I was not sure what to expect.

I had NO idea how to get the video from the camcorder INTO Kino.  I searched the forums.  Found that there were a few things still needed to be loaded:

sudo modprobe dv1394 
sudo modprobe video1394 
sudo modprobe raw1394 
sudo modprobe ohci1394 

I did this and all of a sudden the "Capture" button CAME ALIVE.

5.  I mashed the capture button and was asked to "Press play on the camcorder"
6.  I press play...  9..8..7..6.....  2..1..  "Could not capture video."

Whoops... now what ??  Well, all good IT Techs know to look at the most basic things first.

7.  Checked the cable, the IEEE cable which plugs into the camera did not seem like it was in all the way.
8.  Removed the cable
9.  LOOKED at the cable end.
10.  Grabed a razor blade and hacked away the "extra" plastic/rubber stuff around the cable.  This took about 30 seconds
11.  Plugged the cable back into the camcorder.  It went all the way in without the extra plastic around the connection.
12.  Kino IMMEDIATELY recognized the camera and I got a new set of buttons on the bottom of the Kino GUI.  "Play, FF, REW, Pause, etc)".

While I was writting this, Kino sucked the video into itself and I am now staring at a very nice video in kino.  I have no idea what to do now to get it to dvd but, with the help of those who have gone before me, I will figure it out.

Total time invested from plugging in the camera to actually having the video ready to be edited in Kino...  about 30 minutes.

The moral of the story ?  Read the forums...  and have a sharp razor.

Thanks to all of you that give of your time to review posts and share your experience!  It really does make a difference.

---

### Post by crush304 on 2007-12-22
sudo apt-get install devede

you can create an dvd compatible iso and then burn that to a dvd,

I've just been running kino as root, and I have access to my camera, I don't know if that is better than all the modprobe stuff or not?

---

### Post by LCDR_Kahuna on 2007-12-24
sudo modprobe dv1394
sudo modprobe video1394
sudo modprobe raw1394
sudo modprobe ohci1394 

got as far as typing them in the terminal, still nothing on my jvc GR-d270u :(

---

### Post by granny6989 on 2008-03-19
WOW!!

I have been screwing with this forever. I have not ever gotten Kino (or Ubuntu) to recognize my camcorder. I tried lots of other patches and hacks (and other programs for that matter), but to no avail. Dvgrab would work from command line, but I wanted the graphic interface. I've had Kino installed, but didn't have the capture function. I just typed in the mentioned terminal commands, started Kino, and immediately my camera was there and fully controllable. Awesome, Thanks so much.

For the record:

I have a Sony DCR-TRV30, mini DV camera.
Connected with Firewire to a Pinnacle PCI card.
Running Gutsy 7.10
AMD64 running on 32bit packages.....

Linux is the WAY.

:lolflag::guitar::popcorn::-({|=:biggrin::biggrin:):P:p

PS - make sure your camera is on and in VCR mode.!

---

### Post by hufemj on 2008-04-05
I had a similar experience with my JVC camcorder and Kino. Did a Google and found that Kino needs to be started as root. Try the following from a terminal window:

sudo gksudo kino

I think there was some firewire security issue or something that makes firewire unavailable to Kino by default.

---

### Post by eks on 2008-05-29
What exactly these commands does??

[QUOTE=ChasHutch]sudo modprobe dv1394
sudo modprobe video1394
sudo modprobe raw1394
sudo modprobe ohci1394 
[/QUOTE]

And I've read this:

[https://launchpad.net/ubuntu/+source/kino/+bug/35693](https://launchpad.net/ubuntu/+source/kino/+bug/35693)

Which, WTH, I just gave 777 permissions for the user that uses Kino (my wife). I don't get it, if the fireware port has only root permission because of security issues, why USB does not?


eks

---

### Post by eks on 2008-05-29
And why hasn't this issue made into a sticky here at the forums?

Capturing DV video over the desktop should be straightforward, just like downloading pictures from a camera. The Firewire port should be usable by programs just like the USB port. This is directly related to bug #1.


eks

---

### Post by andyburlow on 2008-05-29
Thanks ChasHutch. Have finally got some of my DV collection from my Sony TRV22E onto my Hardy machine and off again in the form of an ISO burned all by using this thread. Good work.
DVD is playing a bit choppy on fast movement but this might be a Devede setting as the Kino input capture file looked OK, Audio is fine. I couldnt get this working over USB in XP so I am well happy. Thanks!

---

### Post by hodenkat on 2008-06-02
I solved the problem too!


Plugged my camcorder into the port running Hardy, nothing happened.

Launched Kino and got an error on the IEEE1394 control tab saying something about raw1394 not loaded or no read write access.

Rebooted into Windows, plugged camcorder in, dialog box came up asking if I wanted to capture video using Windows Movie Maker...
so I did!

The End.:popcorn:

---

