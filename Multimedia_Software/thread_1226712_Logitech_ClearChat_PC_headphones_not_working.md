---
title: "Logitech ClearChat PC headphones not working"
date: 2009-07-29
forum: Multimedia Software
---

### Post by Archoniam on 2009-07-29
Well, I just came back to Ubu with the release of 9.04 and I have to ask a quick question about my headphones. My ALSA mixer for my Logitech ClearChat PC Wireless headphones, my preferred mixer, has this error pop up when I test it:
```

audiotestsrc wave=sine freq=512 !
audioconvert ! audioresample ! gconfaudiosink:
Could not open audio device for playback.

```
I attempted to use the OSS mixer, which did work, but I can not set them via Volume Control. The OSS mixer did not show up there. Anyone willing to help will shower in awesomeness. [SIZE="1"](not really.)[/SIZE]
It'll hurt a bit.
But it's worth it.

Thanks in advance,
Arch

---

### Post by Archoniam on 2009-07-29
Bumpity.

Can anyone help? Anyone at all? I'm pretty sure this is a simple fix...

---

### Post by Archoniam on 2009-07-29
*sigh* I hate bumping, but, whatever...
Bumpity bump bump, bumpity bump bump, look at the topic go,
Bumpity bump bump, bumpity bump bump, down to the bottom of the page... as usual...

Seriously. I know someone is out there that can help me with this.

EDIT: I checked LPSCI and it's not showing my headphones, although this is not a PCI sound card or an onboard sound card, it's a wireless USB headset... What now?!?

---

### Post by Archoniam on 2009-07-29
To heck with this. I can find better service at LinuxQuestions.org....

---

### Post by igorzwx on 2009-07-30
What are you going to do with your ClearChat?

If you want to use Skype, an ideal solution is:

1. a mic for 10$
2. OSS4

[https://help.ubuntu.com/community/OpenSound](https://help.ubuntu.com/community/OpenSound)

check if your hardware is supported by OSS4
**Does OSS Support My Hardware?**

 Check the list [here]("http://mercurial.opensound.com/?file/6bf18b4a87d6/devlists/Linux"). Some devices may not have full functionality (e.g. the X-fi module is limited to stereo output at the time of this writing, and jack sensing may not work on Azalia-compliant "High-Definition" devices, which are very common on motherboards and laptops today). If you're in doubt, consult the "Additional Support" sources found towards the end of this document. 
 
[B]
[/B]

---

### Post by Archoniam on 2009-07-30
For one, ClearChat headsets already have built-in mics... why would I want to do that?
Yes, I want to run Skype, but my other applications do not have sound and SKYPE DOES!
And I just ran the tutorial you sent, and now it shows my headset as a generic USB device. OSS does not seem to recognize it. I tried soundoff and soundon, and OSS could not be shut off. Great.

EDIT: I restarted OSS. Still shows a generic USB device. My device IS SUPPORTED. I know, it says on the compatibility chart for OSS. Thanks for screwing up my sound system even farther.

---

### Post by igorzwx on 2009-07-30
USB devices are not supported by OSS4.
If you have a lot of free time and you want 
to combat problems, you do not need OSS4 at all.
Stay with ALSA and PulseAudio, and
you may be busy for years solving problems.

---

### Post by Archoniam on 2009-07-30
So you're saying that all three sound systems are screwed? That post made no sense.

---

### Post by igorzwx on 2009-07-30
you may read this, if you want to know more
[http://en.wikipedia.org/wiki/Open_Sound_System](http://en.wikipedia.org/wiki/Open_Sound_System)

[LIST]
[*][Sorry State of Sound in Linux]("http://insanecoding.blogspot.com/2007/05/sorry-state-of-sound-in-linux.html")
[*][State of sound in Linux not so sorry after all]("http://insanecoding.blogspot.com/2009/06/state-of-sound-in-linux-not-so-sorry.html")
[*][OSS is dead. Long live OSS!]("http://4front-tech.com/hannublog/?p=5")
[/LIST]

---

### Post by Archoniam on 2009-07-30
OK seriously. All you're doing is confusing me because your last post appeared to make the point that ALSA, OSS4 and PulseAudio look like they will not run my headset, and now you're suddenly linking me information about OSS?

---

### Post by Archoniam on 2009-07-30
Now I reinstalled ALSA. My headphones are working in the sound test, but not working when other sounds are played. WHAT IS GOING ON WITH THIS THING?!?

---

### Post by igorzwx on 2009-07-30
It was not a joke.
You see, your time is valuable too.
You want, perhaps, to have sound working,
and good quality, of course.

Let us forget, for a wile, about your [B]Logitech ClearChat PC headphones.
Is it more important than anything else?

Check if your soundcard is supported by OSS4

[/B]**Does OSS Support My Hardware?**

 Check the list [here]("http://mercurial.opensound.com/?file/6bf18b4a87d6/devlists/Linux"). Some devices may not have full functionality (e.g. the X-fi module is limited to stereo output at the time of this writing, and jack sensing may not work on Azalia-compliant "High-Definition" devices, which are very common on motherboards and laptops today). If you're in doubt, consult the "Additional Support" sources found towards the end of this document. 

If it is supported, **install another Ubuntu 9.04 in dual boot** (for experiments).
Then install OSS4, following this howto:
[https://help.ubuntu.com/community/OpenSound](https://help.ubuntu.com/community/OpenSound)

This is my advice.
Try both sound systems, and see which you like more.

---

### Post by Archoniam on 2009-07-30
Sorry, already have it solved. Good work, I just used PulseAudio and it works now. Thanks for not helping me...

---

### Post by JacquiOh on 2009-07-31
Hi,

Can you tell me how to get these working using Pulse Audio? I'm a total newbie and just bought these.

Thanks!

---

