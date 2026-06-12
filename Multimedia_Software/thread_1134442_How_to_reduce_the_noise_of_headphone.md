---
title: "How to reduce the noise of headphone?"
date: 2009-04-23
forum: Multimedia Software
---

### Post by dotabayohead on 2009-04-23
Hi. I've been using Ubuntu for a long time, but there is still a pain in the neck. When I listen music there is an annoying noise always sounds together. Even though there is no music, that noise still sounds, but it disappears when the sounds is set to mute, which means there must be a way to cancel that noise. Please help me on this, otherwise I always need to volume up the music in order to overcome the noise. I am picky for listening to music. Thank you

---

### Post by Godly on 2009-04-23
Speakers or headphones? Have you tried new one's? I had an old set of usb speakers that made a hum noise, got new ones and the hum went away.

---

### Post by markbuntu on 2009-04-23
Is your mic muted?

---

### Post by dotabayohead on 2009-04-23
> **Godly said:**
> Speakers or headphones? Have you tried new one's? I had an old set of usb speakers that made a hum noise, got new ones and the hum went away.

It is a headphone.When I used my headphone on iPod, I didn't hear any noise.

My mic is muted btw.

That noise appears when it is not in mute mode

---

### Post by sideaway on 2009-04-23
Sounds like you're experiencing feed back. try plugging the latop into the wall, that can sometimes earth the static.

Also, try plugging in some speakers (external power source) and see if the hum is still there. make sure the laptop and speakers are plugged into the same wall socket (multibox) If it is still there, it's the jack. If the hum isn't there, it's an earth problem.

---

### Post by mcduck on 2009-04-24
Most likely the noise simply comes from your motherboards integrated sound chip.

Motherboard just isn't the best possible place to locate audio hardware, as all the surrounding stuff causes lots of static and noise. Some motherboards have fairly OK integrated audio but in most cases they have more or less static in the sound.

The amount usually depends on how far away the codec chip is from your actual analog audio connectors, as the analog audio is the part that really suffers from interference from surrounding electronic components. Best motherboards locate the codec right next to audio connectors, or even on a completely separate card to get the codec further away from the motherboard.

You could try the earthing solution suggested by sideaway. It might help if earthing is really causing some extra static to your sound. If it doesn't help, you really just need to get a proper sound card (or motherboard with better integrated audio).

---

### Post by Danielaus on 2010-03-29
just noticed the same problem...googled a little with little result...
seems to be solved lowering cd volume from alsamixer to 0.00 db gain
try it! hope it helps! ;)

edit: ops! didn't read thread date correctly :-P

---

### Post by MorrisseyJ on 2010-07-20
Changing the CD volume worked for me in getting rid of the hush in the background - using headphones.

Can anyone tell me what the CD volume is for.

Thanks.

---

### Post by HHO_Cracker_59 on 2010-12-13
**[FONT=Arial][SIZE=3]I have a late 2006 model HP Pavillion notebook w/ Altec Lansing speakers, Windows XP; SP3, Conexant AMC audio card,[/SIZE][/FONT]**
**[FONT=Arial][SIZE=3][/SIZE][/FONT]** 
**[FONT=Arial][SIZE=3]Same problem:[/SIZE][/FONT]**
**[FONT=Arial][SIZE=3]Buzzing was coming out of both mic connections to speakers or headphones.[/SIZE][/FONT]**
**[FONT=Arial][SIZE=3][/SIZE][/FONT]** 
**[FONT=Arial][SIZE=3]Fixed it by muting Microphone.[/SIZE][/FONT]**

**[FONT=Arial][SIZE=3]Philips 40 Watt speakers sound killer now...;)[/SIZE][/FONT]**
**[FONT=Arial][SIZE=3]Rockin Alan Jackson...[/SIZE][/FONT]**
**[FONT=Arial][SIZE=3]peace...[/SIZE][/FONT]**

---

### Post by HHO_Cracker_59 on 2010-12-13
...

---

### Post by Jack Brown on 2011-01-19
ubuntu amplifies the mic signal.

you can still try changing volume settings in the alsamixer.  This time lower volume for MIC or FRONT Mic.

(it is possible that the mic volume control on ubuntu desktop panel does not change the computer FRONT panel mic settings)


How to access alsamixer on lucid:

go to terminal (ctrl+alt+t) and type in alsamixer.  Settings can be changed with arrow keys, 'M' for mute and number keys.

If you mute the FRONT mic in alsamixer, remember that you did so, so that next time you need to use the mic you can re-enable it.

---

### Post by Jack Brown on 2011-01-19
More Info:

ubuntu amplifies the mic signal.

2 more workarounds:

(1) still try changing volume settings in alsamixer.  This time lower volume for MIC or FRONT Mic.

(in some cases the mic volume control on ubuntu desktop panel does not change the computer FRONT panel mic settings)


How to access alsamixer on lucid:

go to terminal (ctrl+alt+t) and type in alsamixer.  Settings can be changed with arrow keys, 'M' for mute and number keys.

If you mute the FRONT mic in alsamixer, remember that you did so, so  that next time you need to use the mic you can re-enable it.

(2) when using a headphone with mic and the noise disappears when the mic jack is unplugged, a separate microphone can be tried. (one that is not connected to the headphone). plug the headphone jack in together with the separate microphone.


other info:
windows doesnt boost the mic levels so high by default, so there might be no noise audible on windows.

---

### Post by shikmehmet on 2011-02-07
G'day

Beleive i had this exact same problem, more noticiable with headphones, but perceivable definately through the laptop speakers aswell. 

It was like a constant low level white noise, but on top of that i could hear when i was scrolling with teh touch pad and also, i could watch the second counter of the clock and hear the dam ticks every second.

I had thought with Pulse there was now no alsamixer, but after actually typing it in, and low and behold it is there...  My cd volume was up way to high, i never use the cd volume, turned it down, and hey presto, sound is gone.

Been trying to get to the bottom of this for 3 days..... I just wonder what started it off in the first instance.

CHeers!

---

### Post by unadulterated on 2011-03-15
On ubuntu 10.10 after reducing the CD volume to 0, still the mic noise is there, do we have to restart the system?? Any ideas.

---

