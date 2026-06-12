---
title: "Using soundcard and usb headset?"
date: 2006-06-05
forum: Multimedia &amp; Video
---

### Post by eRoot on 2006-06-05
Hello all!

I'm a fanatic Enemy Territory (game) player and am also playing in a clan.
Now, to be able to talk to eachother, through TeamSpeak, gives a great tactical advantage. The problem, however, is that my usb headset doesn't seem to be able to process two streams (one from the game, one from TeamSpeak) in linux. When I start up TeamSpeak and then Enemy Territory, TeamSpeak gets the sound. It has worked in WinXP, so I'm guessing it must be linux.

Is there any known method to solve this issue?

Some other info:
I'm using the "echo "et.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss" command to get sound working in Enemy Territory.
The sound driver I use in TeamSpeak is the default "oss /dev/dsp"
I do have an el-cheapo sweex soundcard along with a set of speakers... If it is impossible to use the usb headset for both apps, maybe the soundcard+speakers could be used for the TeamSpeak stream and the headset for Enemy Territory and the headset mic for talking in TeamSpeak?

---

### Post by eRoot on 2006-06-06
/bump... So many new threads already.

---

### Post by eRoot on 2006-06-06
I've reviewed my original post, coming to the conclusion that I might have stated my problem in a rather unclear manner.

Please allow me to rephrase.

I am using a "640U Silverline Headset USB".
I'd like to use it to play both a game (Enemy Territory) and TeamSpeak at the same time.
At the moment I **can** get both working but **not** at the same time. 
For ET I am using the "echo "et.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss" command to get sound working.
For TeamSpeak I am using the default "oss /dev/dsp" sound driver.

My question is simple this time: Is it possible to play two sound sources with this software/hardware combination? 
Any pointer to a solution would be greatly appreciated.
Also, if anyone would need more information to come to a conclusion, please say so.

Thank you for your time (again).

---

### Post by spartan777 on 2006-06-07
yeah, just follow this simple walkthrough;

[http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+Sound](http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+Sound)

(im kidding of course, i've barely gotten into this. i have your same exact problem).

---

### Post by eRoot on 2006-06-10
Thanks alot \\:D/ 
I'll be back later, reporting the results.

---

### Post by eRoot on 2006-06-10
Allright, I've come a bit closer to a solution.

As I just found out, my USB Headset can only proces one combined playback/recording device (eg. using TeamSpeak)
```
root@box:/home/barry# cat /proc/asound/cards
 0 [default        ]: USB-Audio - C-Media USB Headphone Set
                      C-Media USB Headphone Set   at usb-0000:00:07.2-1, full speed
 1 [CMI8738        ]: CMI8738 - C-Media PCI CMI8738
                      C-Media PCI CMI8738 (model 37) at 0xe800, irq 12
root@box:/home/barry# cat /proc/asound/devices
  0: [ 0]   : control
 16: [ 0- 0]: digital audio playback
 24: [ 0- 0]: digital audio capture
 32: [ 1]   : control
 33:        : timer
 40: [ 1- 0]: raw midi
 48: [ 1- 0]: digital audio playback
 49: [ 1- 1]: digital audio playback
 50: [ 1- 2]: digital audio playback
 56: [ 1- 0]: digital audio capture
 58: [ 1- 2]: digital audio capture
root@box:/home/barry#
[COLOR="Red"]## As you can see the default card (usb headset) only has one relevant device (0- 0)[/COLOR]
```
So, basically, I am forced to use my usb headset for TeamSpeak with this hardware. Ok, no problem. Now I just have to find a way to get Enemy Territory working on my pci-card.
As I said before, the echo "et.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss" command enables sound on my usb headset. 
I figured the two numbers (0 0) represent the device and the card (card0/) represents... well, the soundcard ^^.
Now I want to use the 1 0 device, so I tried the command "echo "et.x86 1 0 direct" > /proc/asound/card1/pcm0p/oss"
I get the "Could not mmap /dev/dsp" error, so clearly this is not working.

What am I doing wrong here?

---

