---
title: "Can I get some basic recording advice, please?"
date: 2007-04-16
forum: Multimedia &amp; Video
---

### Post by dabl on 2007-04-16
I'm a 6-months experienced (K)Ubuntu user, and I'm planning to take some time off work and start recording some of my 200+ vinyl albums to digital.  The albums are in great shape, and I've got a very nice amplifier and turntable/stylus to use for the project, but driving the Linux side of it is going to be a total learning experience.

First question: my hardware is an Intel Core 2 Extreme CPU on an Intel D975XBX motherboard -- it has a pretty decent integrated audio chip. Here is the link to Intel's (Windows-oriented) marketing info about it:

[http://www.intel.com/design/chipsets/hdaudio.htm](http://www.intel.com/design/chipsets/hdaudio.htm)

So, do I have a shot at doing a decent quality job of capturing the analog output on this system, or am I condemned to go buy a special audio card?

Second question: What is the recommended software application for this project?  I see Ubuntu has both an ALSA channel and a OSS -- is there a reason to favor one or the other?  I was searching/browsing previous posts on setting these up for microphone use -- I'll be using "line in", but I think the nuts and bolts will be about the same, as far as setting the mixer -- right?

I have both a 64-bit Ubuntu Feisty installation, and a 32-bit Kubuntu Feisty installation -- I could use either one of them for this project -- whichever will work best is fine with me.

Are there words of wisdom that those more experienced can share?  I'll be very appreciative of all advice -- thank you in advance.  :guitar:

---

### Post by Ekril on 2007-04-16
I have never used Auido Recording with Computers in my whole life time. But i know there is a Multimedia Edition of Ubuntu "Ubuntu Studio" . It's aim is Audio and Multimedia editing and producing. In my opinion if i needed to edit some audio or video i would try them. 

The webpage of Ubuntu Studio is located at : [http://ubuntustudio.org/](http://ubuntustudio.org/) 

Go and Get it :)

Take Care..

---

### Post by christhemonkey on 2007-04-16
I would say definately get a proper soundcard if you really care about the quality of the recordings.

Nothing OTT, just something middle range, possibly PCI or USB. External being generally preffered to internal.


I'd say go with the 32 bit edition, purely because its the one i use (as i dont have any x64 equipment) and has a larger group of people providing support (just my general impression).

Personally for recording i would set up the Jack Audio Server and use ardour with it.
```
sudo apt-get install jackd ardour qjackctl
```

Qjackctl being a very nice interface to jack.

---

### Post by nalmeth on 2007-04-16
Yes, better that you are using line-in. 
I've never done this before, but without TOO much trouble, I think you can get some quality recordings done. It will be fun! Here is a learning experience if you want it:

Its hard to tell if the high-def intel audio is just buzz or for real, but I imagine you will get an acceptable quality from it, if the card doesn't pick up other noises from the PC..

Keep in mind, this will all take up a lot of space. 
_I don't have any solid numbers_, but *for me*, a one minute recording in Ardour takes up about 20 megs. That includes the project files. 
When you are done with the Ardour part, you export to wav. You can leave the files as wav, or compress them with the wonderful flac audio format, for lossless, compressed audio (or another codec of your choice).

Depending on your disc space, it might be one album at a time type thing :)

If you'd like to use Ardour for recording, read this page to prepare your system for low-latency: 
[https://help.ubuntu.com/community/UbuntuStudioPreparation](https://help.ubuntu.com/community/UbuntuStudioPreparation)

Scroll down to Real-time Support and run the commands (ignore the rest)

Then run:
sudo apt-get install qjackctl jackd jackeq ardour rezound

Jack is a low-latency audio server that runs on top of alsa. For many studio apps, it is required. It is controlled by qjackctl.

Rezound has a really neat feature ability to remove 'clips' from the track, where there are short bursts/blasts of noise above the comfortable dB range. You might not actually need this if you control the recording well :)

Open qjackctl, and go to this page to tweak it for your soundcard to achieve the best latency: [https://help.ubuntu.com/community/HowToJACKConfiguration](https://help.ubuntu.com/community/HowToJACKConfiguration)
Restart qjackctl, start jack, then open Ardour.

Session -> New
Session -> Add Track (add a STEREO track)
Click the 'h' on the new track to adjust its height (just for appearance)
Click the 'r' to arm the track for recording.

Open the Editor mixer (on the upper-left hand side) or 
Windows -> Mixer
Get a good volume level so that the meter doesn't go into the red or yellow (or zero on the meter).

Start recording!

The way that you want to go about dividing up your records will be your call. Ardour has a feature to make a long recording into a CD, divided up at certain points, but I'm not sure how to work that. You may want to stop after every song, or record the whole album, and cut each song individually.

_I_ would record the whole album, and then click the 'range' button to enable the range tool. Use it to highlight the beginning and end of each song, and then:
Session -> Export -> Export Range to audiofile

 OR IGNORE EVERYTHING ABOVE, and go with audacity. :) No installing and configuring jack, no extra engines, less complicated interface, but less control of the recording.
sudo apt-get install audacity

I hope I didn't leave anything out, and if you have questions, or if anything goes wrong, just reply in this thread.
Good luck!

---

### Post by reclusivemonkey on 2007-04-16
Audacity seconded. The noise removal is pretty good; you should be able to select a portion of "crackle" on your vinyl and remove it effectively. Unless of course this is something you wish to preserve =]

---

### Post by christhemonkey on 2007-04-17
Just to say, you dont need a low-latency audio system if you are just recording some thing, heck you dont even need to be running in realtime.

Just install jack and start it with qjackctl and then ardour.

But yes, i guess you could use audacity.

---

### Post by dabl on 2007-04-17
Wow -- this is _great_ feedback -- thank you very much folks.  Makes me remember why I switched to Linux!

:guitar:

---

### Post by sebas.rhcp on 2007-04-25
You should get a better soundcard... with via envy24

---

