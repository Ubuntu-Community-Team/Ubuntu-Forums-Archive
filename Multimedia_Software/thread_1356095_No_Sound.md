---
title: "No Sound"
date: 2009-12-15
forum: Multimedia Software
---

### Post by heyniceaddress on 2009-12-15
Hi, everybody!

I believe this must be a question frequently asked, but I need assistance with getting my sound working. I had this problem once before two years ago and spent months researching how to fix it, and eventually did ... but, like I said, that was two years ago, and I've since forgotten. Now I've decided to ask for some help this time around.

I just got rid of XP today and installed 9.04, and knew something was wrong when I didn't get that little sound when the sign-in box appears, and also when the drums didn't play at start-up.

My desktop shows that the volume is on and up (it's not muted on the icon).

I went into BIOS and turned on the integrated sound card, and thought I'd solved it, but it made no difference.

I went into Volume Control and clicked on the "switches" tab and checked the box after reading a thread on this problem, but it made no difference.

Any ideas?

Thank you in advance for your time.

---

### Post by RedSingularity on 2009-12-15
Go to a terminal and type 

alsamixer

Make sure its all the way up.

Also, do you have pulseaudio installed?

---

### Post by heyniceaddress on 2009-12-15
I went to alsamixer and turned up the Master, which was the only one partly down; it was in the green, but I went ahead and cranked it up to the max.

As for pulseaudio: no, I haven't installed that.

Is there any specific method for installing it that you prefer? I ask because, after reading your reply, I searched for how to install it and looked at three different links, each with different methods of installing it.

Thanks in advance.

---

### Post by RedSingularity on 2009-12-15
You probably have pulseaudio installed by default.  Look in Apps>Sound and Video>Pulseaudio volume control.  Make sure everything is turned up in the different tabs.

---

### Post by heyniceaddress on 2009-12-15
I went into Applications and then to Sound & Video, but Pulseaudio isn't listed. However, when I went to System, Preferences, Sound, I see the Sound playback is listed as Autodetect, and one of the choices in its drop-down menu is Pulseaudio, so it must be in my OS.

---

### Post by RedSingularity on 2009-12-15
No no autodetect is fine....you need to install the volume control.  Here do this in a terminal.......

sudo apt-get install pavucontrol

Then you will see it there.

---

### Post by heyniceaddress on 2009-12-15
Thank you!

haha, of course there has to be something that goes wrong ... I went to Apps>Sound&Video and clicked on PulseAudio Volume Control, and a box pops up saying "Connection failed: Connection refused"

Any ideas why?

Thanks again.

---

### Post by RedSingularity on 2009-12-15
Go to System>Prefs>Pulseaudio Prefs.  

In the first tab check the first 3 boxes.

In the second tab Dont check any.

In the third tab Check the one box.

Then see if you can do the volume chooser....PS:  Try doing a comp restart as well.

---

### Post by heyniceaddress on 2009-12-15
I did that and restarted and now have access ... thanks.

All the volume configurations were turned up.

I don't know how to find out what kind of soundcard I have. I can't remember exactly, but I think it's a Creative Audigy Soundblaster something or other. I don't know if that helps at all...?

---

### Post by RedSingularity on 2009-12-15
See if the folowing command gives you anything..........

lspci | grep Audio

---

### Post by heyniceaddress on 2009-12-15
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)

---

### Post by RedSingularity on 2009-12-15
Remember where is said "autodetect"?  Change the various settings there and hit the test button.  See if any work.

---

### Post by heyniceaddress on 2009-12-15
I tried that already, haha ... but I did it again just now in case it might work, but it didn't. There were six different options, and two of them had error messages pop up when I tried testing them.

---

### Post by RedSingularity on 2009-12-15
Lets try removing pulse alltogeather then.........

sudo apt-get autoremove pulseaudio

Then reboot and see if you have sound.

---

### Post by heyniceaddress on 2009-12-15
No luck :(

---

### Post by RedSingularity on 2009-12-15
You removed pulseaudio and still no sound hu?  Maybe your sound card is not compliant with ALSA.

---

### Post by heyniceaddress on 2009-12-15
ALSA sounds familiar ... I remember switching to Ubuntu two years ago and having this problem, and it was something about maybe I needed drivers to get it running ... but then I reinstalled XP so that I could play Fallout 3, and recently discovered malware, spyware, &c., and decided to switch back ... but I remember finding something that made sound work, and then it seemed like Ubuntu released a version where sound actually worked on here.

Maybe I'll try installing 9.10, and see if that works.

---

### Post by RedSingularity on 2009-12-15
It is recommended that if your sound doesn't work after a fresh install, file a bug report.

---

### Post by RedSingularity on 2009-12-15
One more thing....post the output of

aplay -l

---

### Post by heyniceaddress on 2009-12-15
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

---

### Post by RedSingularity on 2009-12-15
In a terminal do the folowing

sudo modprobe snd-hda-intel

Then do 

alsamixer again to make sure volume is up and then test it out.

---

### Post by heyniceaddress on 2009-12-16
This will sound lame ... but it took me forever to find my thread on here :( I'm such a newbie.

Anyway, I actually found what I did before and fixed it. I found an e-mail I'd sent to myself that I'd archived over a year ago that told me what to do in case this happened ... of course the link I had sent myself to a file was dead, so I did a Google search, and found that someone else had posted a step-by-step walkthrough of the same ordeal. It worked!

[http://ubuntuforums.org/showpost.php?p=3768914&postcount=60](http://ubuntuforums.org/showpost.php?p=3768914&postcount=60)

---

