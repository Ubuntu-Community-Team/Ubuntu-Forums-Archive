---
title: "Rosegarden without Jack on 13.10?"
date: 2014-04-18
forum: Multimedia Software
---

### Post by Qbeta on 2014-04-18
A few years ago I used Rosegarden to compose some music. I eventually stopped using it because of the need to run the Jack audio server which is apparently incompatible with Pulse audio. Basically, Jack takes over the sound system and often, even after you kill it, you need a reboot to get back to normal.  Jack was also generally flaky and crash-prone. Is there any way to get Rosegarden to just behave like a normal sound app and use the Pulse server (note I'm running 13.04 and plan to upgrade tonight to 13.10 but I assume it will still use Pulse). I understand there are certain advantages to Jack, particularly if running with realtime but I just don't feel like I need an app that screws with a major systen component like sound.

---

### Post by su:bhatta on 2014-04-19
Hi, I don't know how far back you tried, but Jack2 is better at connecting to Pulse audio. 
But you will have to try to see if it works well with your hardware.

Once Jack-Pulse audio sink is set up, you should not be any problems. 
You can use this guide for Jac-Pulse audio sink : [https://help.ubuntu.com/community/UbuntuStudio/ProAudioIntro/1204](https://help.ubuntu.com/community/UbuntuStudio/ProAudioIntro/1204)

As for using Rosegarden without Jack i will copy-paste this excerpt from  : [http://www.rosegardenmusic.com/wiki/doc:manual-en](http://www.rosegardenmusic.com/wiki/doc:manual-en)

> Rosegarden is built using [Qt]("http://qt.nokia.com")  &#8211; A cross-platform application and UI framework.  It uses ALSA to  provide MIDI support, and JACK for audio, both of which limit Rosegarden  to Linux for the time being, but that should hopefully change in the  future, with OS-X being the next most accessible platform, and Windows the most difficult to reach.

---

### Post by shantiq on 2014-04-19
or Qbeta    you can also totally forget about Jack and use Timidity if midi composition is what you are after
I have used [this route]("http://ubuntuforums.org/showthread.php?t=1700943&p=10528034#post10528034") for 3 or 4 years    and it has worked well

---

### Post by Qbeta on 2014-04-19
Thank you all for the advice. I'm upgrading to 13.10 this weekend actually (still running 13.04) so I will give Jack2 a try after that. Can't wait to hear to hear my compositions again :)

---

