---
title: "No sound"
date: 2008-06-03
forum: Multimedia Software
---

### Post by gatorbowls on 2008-06-03
I am running the latest version of harly. I have no sound what so ever. I know for a fact that I have realtek sound. I'm not sure what I need to do to enable it so I have sound or what.

---

### Post by gatorbowls on 2008-06-03
My head phones work when I plug them in, but my speakers dont...
Anyway please help...

---

### Post by gatorbowls on 2008-06-05
Anyone?

---

### Post by xc3RnbFO8P on 2008-06-05
Did you check Volume Control?

---

### Post by gatorbowls on 2008-06-05
Yep I did.
I should note i am running a Acer 5050 Laptop.

---

### Post by gatorbowls on 2008-06-05
I was told to do this:

```
 You need to give the 

snd-hda-intel kernel module a parameter. I created a 

file /etc/modprobe.d/sound containing:


alias snd-card-0 snd-hda-intel

options snd-hda-intel index=0 probe_mask=3 position_fix=3


Explanation:

‘index=0&#8242; just means ‘make this the first sound device’. Unnecessary, really.

‘probe_mask=3&#8242; indicates which codecs the driver should probe for. I found 

that the driver was finding 3 codecs on my hardware. The first is the modem, 

and the second is the audio. The third I think is spurious, and it’s the 

cause of the problems. The probe mask makes the driver just look for the 

first two codecs. ‘position_fix=3&#8242; suppresses a driver warning about its mode of operation not 

working by setting the mode to a mode that works for me. Again, you can 

safely leave it out.
```


Can anyone help me with this?

---

### Post by xc3RnbFO8P on 2008-06-05
In Volume Control> edit are all boxes checked?

---

### Post by gatorbowls on 2008-06-05
All the sounds are up and on.. but no sound coming on..
I just posted something above your post..im not sure how to make af file though...

---

### Post by xc3RnbFO8P on 2008-06-05
Can you try this:
>  Re: No sound on the Acer Aspire 5050
Quote:
Originally Posted by buried View Post
I got it working by going to prefences->surround!
YESS! thanks anyways!
Yes this works, I had to bump up the volume on SURROUND and enable SURROUND (even though there's only two speakers, it's because there's many inputs and outputs. If you plug headphones into the headphone jacks your sound will work out of the box but to get the speakers working you have to turn on SURROUND and pump up the volume (using the sound adjustment in the System menu) Modifying config files is not necessary.

---

### Post by madsere on 2009-02-11
Sorry to awake an old thread, but I have a similar problem trying to install Ubuntu on a Acer Aspire 5050.  

Everything else seems to work except sound.  I had a look under System > Preferences > Sound but none of the tests available produce any sound.

There does not seem to be any Volume Control anywhere. I looked both under Applications and System but nope. Maybe the volume control package didn't get installed for some reason?

---

