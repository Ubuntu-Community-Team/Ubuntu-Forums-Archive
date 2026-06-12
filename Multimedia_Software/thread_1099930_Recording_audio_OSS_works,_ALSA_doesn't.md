---
title: "Recording audio: OSS works, ALSA doesn't"
date: 2009-03-18
forum: Multimedia Software
---

### Post by pgmer6809 on 2009-03-18
Hi All, just a quick update.
Running Gutsy (I know, but any later release of Ubuntu has bugs in the Ethernet drivers and wont work with my LAN).
Have a Creative Labs Audigy2 ZS Platinum sound card.

After months of trying to get recording to work using ALSA Mixer etc. etc. finally went to 4Front Technologies [http://www.opensound.com/]("http://www.opensound.com/") and downloaded the .deb package for their version 4.1
Installled per the instructions:

```
sudo dpkg -i  oss-linux-4.1-1051_i386.deb 
# ignore testing errors.
cd /etc/modprobe.d
sudo ln -s /lib/linux-sound-base/noALSA.modprobe.conf blacklist-alsa
sudo rm blacklist-oss

```
and reboot.
Go to system->preferences->sound to make sure that oss/dsp is the audio device. Ok.
Now run ```
osstest
```
works fine.
Start Audacity and edit preferences to use the oss/dsp as the preferred device. 
Click Record.
Presto. No problems. No hassle. No fiddling with volume controls and check boxes. 
After months and months problem solved.

---

### Post by Justbill on 2009-03-23
I'm still having trouble getting Audacity to work, even after downloading from 4Front. I checked my preferences in Audacity and they *seem* right.

I'm trying to record through my "Firewire" on the front of the computer.
My Computer is a :  Compaq Presario SR1426NX.

I'm running "Ubuntu 8.10 Intrepid"

This worked for me when I was using ultimate edition, I really don't know whats wrong, or what I overlooked.

I am trying to record guitar music. I am coming out of the line out, on my amp, and plugging into the front of the computer

Any suggestions will be GREATLY appreciated!

---

### Post by pgmer6809 on 2009-03-24
Sorry I am afraid I cannot help. I am just using line in on the back of the sound card.
Are you using firewire from the mobo or firewire from a sound card?

I presume that firewire is digital already, so that you do not really need a sound card;
How do you normally r/w through the firewire? Would the dd command, or the cat cmd work?
Then you could just start dd to read in all the guitar music to a file, and then use audacity to open the file.
pgmer6809
The other suggestion is to make sure that /dev/dsp points to your firewire device.
here is mine:
 /dev/dsp -> /dev/oss/oss_sblive0/pcm0

I notice that even though my audigy has a firewire on it, my OSS mixer does not have it as one of the options to choose as a device.

pgmer6809

---

### Post by Justbill on 2009-03-24
I am currently using the "onboard" sound, through the intel chipset.
When I had "Ultimate Edition" on here it just worked, so  I can't really say "how" I got it working last time, I just plugged into the front and it worked.

I am not at a stand still on my project (recording and mixing multiple instruments, on multiple tracks), as everything is working in winXP. I dual boot. I just HATE using windows!

Thanks for trying. I may be interested and need to go back to ALSA, how would I do that?

Thanks in advance

---

### Post by Justbill on 2009-03-24
And how do I make sure that /dev/dsp/ is pointing to "firewire"? Is that in Audacity preferences?

---

### Post by markbuntu on 2009-03-24
freebob and ffado are the sound servers for firewire devices, much like oss and alsa are for sound cards.

If you are heavy into recording you should really try ardour and jack or the entire ubuntustudio-audio suite. jack will give you better performance and low latencies and ardour is a professional quality recording daw. jack has built in firewire support. You can read about all that here


[http://en.wikipedia.org/wiki/JACK_Audio_Connection_Kit](http://en.wikipedia.org/wiki/JACK_Audio_Connection_Kit)

[https://help.ubuntu.com/community/UbuntuStudio/GettingStarted](https://help.ubuntu.com/community/UbuntuStudio/GettingStarted)

[http://www.ubustu.com/globe/2007/05/29/how-to-configure-jack-in-ubuntu-studio/](http://www.ubustu.com/globe/2007/05/29/how-to-configure-jack-in-ubuntu-studio/)

[http://hubpages.com/hub/Recording-in-Linux-aka-Free-and-Open-Source-Digital-Audio-Workstation](http://hubpages.com/hub/Recording-in-Linux-aka-Free-and-Open-Source-Digital-Audio-Workstation)

Excellent ardour tutorial here:

[http://out-of-order.nfshost.com/tutorials/ardour/](http://out-of-order.nfshost.com/tutorials/ardour/)

If you are wondering how to sync applications together through jack:

[https://help.ubuntu.com/community/HowToQjackCtlConnections](https://help.ubuntu.com/community/HowToQjackCtlConnections)

[http://www.ubustu.com/globe/2007/09/19/how-to-sync-hydrogen-with-ardour/](http://www.ubustu.com/globe/2007/09/19/how-to-sync-hydrogen-with-ardour/)

[http://www.rosegardenmusic.com/](http://www.rosegardenmusic.com/)

---

