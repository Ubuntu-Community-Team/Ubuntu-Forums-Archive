---
title: "Slightly distorted sound on Thinkpad R60e"
date: 2008-02-05
forum: Multimedia &amp; Video
---

### Post by the_lex on 2008-02-05
Hi,

I'm running Ubuntu Gutsy on my Thinkpad R60e. Had been using Feisty before but did a clean install for Gutsy. My problem is that the sound being played from my laptop, whether through its own speakers, external speakers, or headphones, is slightly distorted. It doesn't matter what application I'm using. The login sound is distorted so I think it's a problem with my basic sound drivers or something. I have found that by turning the volume down in an application, then turning up the external speakers or the volume on the laptop's hardware switch does reduce the distortion somewhat, but this isn't really a solution. I've tried switching between ALSA, OSS, ESD etc. in System > Preferences > Sound Preferences, but to no avail.

Any ideas anyone?

Thanks in advance

---

### Post by pieisgood4589 on 2008-02-05
I too have a Thinkpad, they rock!

Gutsy somehow removes specific sound files on purpose, so on the update from Feisty, just select it to not remove obsolete files. :KS

---

### Post by the_lex on 2008-02-05
Yes they are wonderful machines. I will guard the honour of my trackpoint to the death! Love the "full size" keyboard too :D

Alas, it is too late for stopping Gutsy butchering my sound files, as rather than having the hassle of upgrading, I wiped and did a clean install so there's no going back really.

---

### Post by rje_nc on 2008-02-06
Open the full Sound mixer app and see what the PCM setting is.  I am found that often with the PCM value at 100% sound can get distorted.  Turn it down to 90% or so and see if it helps any.

Bob

---

### Post by the_lex on 2008-02-06
Sorry to ask such a stupid question, but - full Sound mixer app? What exactly would that be? I have gone to Preferences > Sound, but there is no kind of mixer/volume control in that dialogue. I've also tried getting alsamixergui from synaptic and all I get is a blank screen if I load that up (which is clearly a problem at my end, but I'm not sure if that is the app you're talking about anyway so it may be irrelevant)

---

### Post by pieisgood4589 on 2008-02-06
Synaptics helps...:lolflag:

---

### Post by defenestratos on 2008-02-06
You could open a terminal and type 
alsamixer and scroll using the arrow keys to the PCM meter. 
Or you could do a weird thing and add the volume control applet to the taskbar and right click it to bring up your mixer. Option 1 is much better I think

---

### Post by the_lex on 2008-02-06
*sigh* I knew I'd seen that mixer before! In fact I had even used it, and somehow managed to forget about it over the course of this problem... I've done much more complex stuff, but sometimes for some reason the simplest thing evades you :lolflag:

Turning down PCM works, but I have to take it down to about 40% to cure the distortion and then bump up the master to compensate. Thankfully my external speakers are loud enough to still pump out enough volume so this is a workable solution. Having to turn down the PCM this much does suggest some kind of problem, but as I have a workaround I guess that will do for now. 

Also, my PCM level seems to change each time I restart the laptop. The PCM is tied to the laptop's hardware volume buttons, but does not always turn the volume up/down by the same amount - in fact it is completely random. Sometimes the PCM volume gets to full within one press of the button, sometimes it increases gradually over several presses. I will continue to scour the interwebs for this problem as it's likely tied to the distortion...

Anyone who has any other ideas is most welcome to contribute however :D

---

### Post by defenestratos on 2008-02-07
Is it because your internal microphone is turned up? You can kill that in the mixer as well and see if it changes anything. If it is distorting it means that input somewhere in your system is clipping. Is there a special jack input into your speakers?

---

### Post by the_lex on 2008-02-07
No I always have the mic muted. No kind of special jack input into the speakers, and I have the distortion problem on the laptop's built-in speakers and with headphones, so it's not even an issue with the speaker jack. Also, I should point out that I don't have this problem in Windows, so it's something to do with Ubuntu...

Many thanks for you suggestions so far though :)

---

