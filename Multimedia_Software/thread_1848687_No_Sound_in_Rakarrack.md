---
title: "No Sound in Rakarrack"
date: 2011-09-23
forum: Multimedia Software
---

### Post by kerryhall on 2011-09-23
Hello,

I have this setup:
Guitar -> USB Audio interface -> Audacity

And I can record the raw guitar signal and play it back fine.

However, I close audacity and run rakarrack and there is no sound output. When I strum the guitar, I can see that there is input signal from the db meter. However, there is no output signal, nothing on the db meter. I have tried all the presets and adjusting the input and output levels. Sometimes I can get feedback, but no output sound! :(

Also, I have a feeling someone is going to mention jack. I can't see how jack should be involved in any possible way, as I am not trying to route audio from app to app. 

I have tried guitarix too, but it doesn't seem to work either. I just want an fx processor that works out of the repos!!

EDIT:
ok, now i realize that rakarrack for some stupid reason HAS to use jack.
I think the problem is that jack doesn't show my audio interface under "interfaces"
aplay -l:
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: USB [AudioBox USB], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

but for some reason qjackctl only shows:
plughw:0 
and 
hw:0

tried both, tried the setup here:
[http://rakarrack.sourceforge.net/imagenes/jack_conections.jpg](http://rakarrack.sourceforge.net/imagenes/jack_conections.jpg)

no luck!! any ideas?

Thanks!!

---

### Post by kerryhall on 2011-09-23
Alright, here is what I did for future reference. I could find almost no help on google, so hopefully someone with the same problem will find this.

My problem was trying to set the USB audio interface as the input device, and my computer's sound card as the output device in jack using qjackctl. What I ended up doing was setting the USB audio interface as the overall interface (top box on the right) and for some reason the audio output was routed through my computer's sound card. This was for an Audiobox USB interface by PreSonus. 

Rakarrack works great! There is still some noticeable latency, so I need to look into that.

---

### Post by xodus99 on 2013-04-23
@kerry I know this a really old thread, but I was facing a similar issue on my computer too.
I have a Behringer UCG106 USB Guitar Link to record my guitars. On Jack, I've put the interface to the USB and left the input and output to "default"
I use Rakarrak and I can see that there is input and output however, I get no sound from my computer. (My headphones are plugged into the computer's soundcard. I don't have the 1/4" headphones or adapter to use with the UCG106).

---

### Post by overdrank on 2013-04-24
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/misc.php?do=showrules")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

