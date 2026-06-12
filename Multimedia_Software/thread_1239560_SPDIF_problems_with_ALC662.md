---
title: "SPDIF problems with ALC662"
date: 2009-08-13
forum: Multimedia Software
---

### Post by JimFlint on 2009-08-13
After much reading and searching I seem to have failed at getting SPDIF / PCM to output anything.
OS: CrunchBang 9.04 (Jaunty)
Kernel: 2.6.28-14
Mobo: Intel D945GCLF2
Sound: Realtek ALC662 rev1

The analog works fine and I have a connector to the mobo header socket for the SPDIF.

**aplay -l** shows the two sound devices (analog and digital)

**alsamixer** has the IEC958 and IEC958 defult turned ON.

but still I get nothing; although I do hear a feint click between tracks

Help :confused:

---

### Post by Osamabingandhi on 2009-08-13
This road of getting spdif to output everything in ubuntu is a hard one. Spdif and ubuntu is not a good combination. It has been a mess for the three years i have used ubuntu. Sometimes i get it to work but now i broke everything again. Reinstallation for the second time i think is my only solution.

I try not to install anything i really don't need. I usually only install vlc and in the settings spdif output and alsa is the way to go. In the codec appartment i put digital out. It is a bit of try and error in the settings. Mp3 support i really don't know which codec is best to use as not to brake the fragile fragile sound setup. Gstreamer seems as a big problem. Xine is not much better. I sometimes get it to work and sometimes it works a bit and i have to satisfy. Sometimes it works perfect till i brake it again and a reinstall is waiting yet again!

I can only wish you good luck, cause my solutions never work as they should...

---

### Post by JimFlint on 2009-08-14
[COLOR="Orange"]Update ![/COLOR]
Although not a *solution* yet, I have managed to get something out.

The command **aplay -vDspdif login.wav** produces something and
**aplay -vDplug:spdif login.wav** plays it at the correct rate.

Now, I guess, I need to get this set as the default

---

### Post by JimFlint on 2009-08-14
[COLOR="Orange"]S O L V E D[/COLOR]

Having read lots of forums, this should be useful to a lot of people.

Edit **/usr/share/alsa/alsa.conf**
Find the line that defines *pcm.default*
and change it to:
**pcm.default plug:spdif**

This seems to send the default PCM data to the SPDIF port - so you may have the possibility to override this.
The "plug:" bit seems to be the clever bit of converting the rate if it is wrong

---

### Post by Osamabingandhi on 2009-08-20
I also found a solution. It worked by typing this in terminal:

speaker-test -c2 --device cards.pcm.iec958 --rate 44100
speaker-test -c2 --device cards.pcm.iec958 --rate 48000

To end this i had to end the terminal. I use 8.04 version.

On this bugreport there is a few more ideas:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/25632](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/25632)

This solution i think most people found to work: 
iecset audio true

Hopes this helps also!

---

