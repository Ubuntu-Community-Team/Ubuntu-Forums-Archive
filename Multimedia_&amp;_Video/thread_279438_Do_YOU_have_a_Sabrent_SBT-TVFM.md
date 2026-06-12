---
title: "Do YOU have a Sabrent SBT-TVFM???"
date: 2006-10-18
forum: Multimedia &amp; Video
---

### Post by insub2 on 2006-10-18
does anybody have a Sabrent SBT-TVFM tv tuner pci card?
it is a Phillips PCI Capture (SAA7130) chipset.
i've checked the forums and have concluded that it probably wont work out-of-the-box.  Could you tell me (in most direct terms) the steps taken to get this card working. and have you gotten it fullyfunctional?

thank you.



Also...
any luck with the FM tuner?

---

### Post by lesemi on 2006-11-17
Not sure if this is going to help - it took me a few weeks of playing and reading.

i got the card to work for regular TV (analog) no sound.

the hard part is getting the tuner working

sudo dmesg modprobe | grep saa713
look for the card type - sabrent should be 42

sudo vi /etc/modprobe.conf  (vi is my preferred text editor.. can use gedit)
options saa7134 card=42 tuner=17

for a list of tuners refer to:
[http://lisa.cs.uni-potsdam.de/lxr/source/include/media/tuner.h#L49](http://lisa.cs.uni-potsdam.de/lxr/source/include/media/tuner.h#L49)

i found that link helpful

the only problem- i don't have sound.. working on it though

---

### Post by insub2 on 2006-11-18
> **lesemi said:**
> the only problem- i don't have sound.. working on it though

that's kinda make or break for me.  if you get it working, let me know.

is the FM tuner working?


Thanks for the reply!!

---

### Post by lesemi on 2006-11-19
i'm still sort of a newb.. 
i got it to work for awhile.
now i get no signal what soever - 
and i didn't change any of the settings.


i guess that's what you get for a $25 card.

if you make any progress with this card.. let me know.

I did find however find this link which may explain why we have these issues:
[http://themikecam.com/blog/2005/08/29/sound-for-sabrent-sbt-tvfm-composite-and-s-video-in-linux/](http://themikecam.com/blog/2005/08/29/sound-for-sabrent-sbt-tvfm-composite-and-s-video-in-linux/)

---

### Post by tripalexan on 2007-03-08
I know that this is kind of an old post, and I am certainly a noob, but I managed to get mine to work with the following...

sudo rmmod saa7134_alsa
sudo rmmod saa7134
sudo modprobe saa7134 card=42 tuner=9 alsa=1

Audio, video, but no capture which I really don't care about.

 One issue is that I can't tune beyond channel 51.  I've tried all the other tuner settings and this seems to give me to most channels.  I kind of miss the History Channel but I get all the news and  ESPN...All I really need in my office.

Hope this helps someone....

---

### Post by jxd on 2007-04-25
Experiment with different tuners. Some tuners will limit you at 51, i'm pretty sure you;ll find a tuner that goes all the way.

Start off by finding the list of tuners from video4linux, then only consider the ones that match ur profile (NTSC, PAL, DVB etc).

then do: sudo rmmod saa7134-alsa
                sudo rmmod saa7134
                sudo modprobe saa7134 card=42 tuner=<here u try different numbers>
                tvtime            

Keep repeating until you can see beyond channel 51. Some won't work at all. You don't have to use tvtime, u can use ur current tv program. Good luck :)

---

### Post by observative on 2008-01-04
jxd is correct, here's a good [HOWTO]("http://ubuntuforums.org/showthread.php?t=408654") to further the installation and use of your TV tuner card. It saved me a lot of time figuring out the card number and tuner number.
[http://ubuntuforums.org/showthread.php?t=408654](http://ubuntuforums.org/showthread.php?t=408654)

I found this [thread]("http://ubuntuforums.org/showthread.php?t=408307") useful because of the newb approach and info for using command prompts and making scripts to set up the TV tuner.
[http://ubuntuforums.org/showthread.php?t=408307](http://ubuntuforums.org/showthread.php?t=408307)

One more consideration is whether or not you are receiving an analog or digital signal. For those living out in the country, you probably still receive analog and those closer to cities will get a mix if not entirely digital broadcasts. It is the intent of broadcasters to entirely and globally convert to digital terrestrial by 2020 (could be sooner).
> The point is that my new card was not working under tvtime (analogic receiver) but after installing the DVB-T drivers (digital receiver for digital terrestial TV broadcast) I could perfectly access the DVB-T broadcasts using Kaffeine (the Kubuntu player one can install from Synaptic).
If you are in an area receiving them and your antenna is able you could try this alternative. [cblanquer]("http://ubuntuforums.org/showpost.php?p=2745298&postcount=41")[http://ubuntuforums.org/showpost.php?p=2745298&postcount=41](http://ubuntuforums.org/showpost.php?p=2745298&postcount=41)

I hope this helps others looking for the answers on installation and use of their Sabrent SBT-TVFM TV tuner card (ie the Phillips SAAxxxx chipset cards -  this includes more than the Sabrent models).

---

