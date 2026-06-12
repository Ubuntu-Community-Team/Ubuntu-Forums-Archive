---
title: "MP3 Sound issue"
date: 2010-07-03
forum: Multimedia Software
---

### Post by Cambysese on 2010-07-03
Greetings all,
I've put in my fair share of troubleshooting web search concerning my issue, and basically have only found a lot dead end threads.
I am running Ubuntu 10.04 LTS - the Lucid Lynx and GNOME 2.30.0 on a Dell Inspiron 1100 equipped with (00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 01)), set to analog stereo output. For all intent and purpose the audio controller is working. However, after installing and un-installing REALPLAYER 11 I have the following problem: 
During and/or after streaming audio, typically from a Flash site, I have no mp3 audio in several programs presumably using gstreamer (i.e, VLC, mplayer, rhthmbox, QuodLibet). Although streaming web audio remains unaffected, and video in VLC and mplayer work fine, there is no mp3 audio outside of my browser, and it appears as though none of the program actually read the mp3 files on my HD. To remedy this I have reinstalled the programs, gstreamer, ALAC, and have tried tampering with the ALAC mixer, which on my machine has only the master volume, and PCM sliders. Both set to maximum. The only thing that works is rebooting, to listen to the mp3 data on my HD. 
Somebody, anybody, please help. Thanks in advance.

---

### Post by Dayofswords on 2010-07-03
have you installed the Ubuntu restricted extras from the software center?
that installs the mp3 stuff

---

### Post by Cambysese on 2010-07-03
@Dayofswords Yes. The extras were installed and now just reinstalled. No change.

---

### Post by Dayofswords on 2010-07-03
well if mp3s played before realplayer then something along the way broke


if you want to check the ubuntu restricted extras is installed or not, open the software center vis Applications > Ubuntu Software Center

in the Center type 'extras' into the search, the 4th one down (or so) should be 'Ubuntu Restricted Extras'. if it is installed, there should be a green circle with a white check on it. not installed it should have no check.

if it is already installed you try uninstalling it and then reinstalling it by click it, clicking more info. then 'Remove', wait wait wait, then go back to it(cant remember if it leaves the page...) and click install and provide your password

---

### Post by Yellow Pasque on 2010-07-03
Flash is probably grabbing the audio device and locking out other programs. See: [http://ubuntuforums.org/showthread.php?t=1455816](http://ubuntuforums.org/showthread.php?t=1455816)

---

