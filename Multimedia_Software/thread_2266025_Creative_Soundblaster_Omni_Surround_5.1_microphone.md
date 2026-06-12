---
title: "Creative Soundblaster Omni Surround 5.1 microphone"
date: 2015-02-19
forum: Multimedia Software
---

### Post by baltic on 2015-02-19
Hi!


The device works fine, out of the box in ubuntu 14.04, including the volume knob. Just for the record, if someone googles whether it is compatible with linux. 
But i don't see the microphone at the **Settings->Sound->Input** tab, when i connect it through the sound card.
When i launch **gstreamer-properties** i am able to select the mic and test that it works well. In my case **pipeline** says: **alsasrc device="hw:1,1"**

Now the question: How to make ubuntu see the mic?

Ok. I made it work
```
pacmd load-module module-alsa-source source_name=input device=**hw:1,1**
pacmd set-default-source input
```
But only till first reboot. To make changes permanent
```

sudo gedit /etc/pulse/default.pa

```
and add the commands to the end of file
```

load-module module-alsa-source source_name=input device=**hw:1,1**
set-default-source input

```

---

### Post by nazar-pc on 2015-02-23
Does microphone really works?
I just bought this sound card. After commands you wrote I see microphone in settings, but still nothing goes from it, silence.
Any thoughts about this?
I'm on Ubuntu 15.04 now.

---

### Post by baltic on 2015-02-24
Did you actually launch **gstreamer-properties** and found out what the alsa device it is in your case? e.g. the **hw:1,1** in mine case?

---

### Post by tal_kg on 2015-03-27
Have the same problem  you can see mic in pauvcontrol after adding it but not working.
I've checked correct device in gstreamer-properties

---

### Post by trinaldi on 2015-04-12
> **tal_kg said:**
> Have the same problem  you can see mic in pauvcontrol after adding it but not working.
I've checked correct device in gstreamer-properties

I had the same issue: pavucontrol showed me the SB Omni Mic but no sound input.

Besides doing the procedures from OP, I had to:

Enter ```
alsamixer
``` and change the sound card by pressing F6:
[IMG]http://i.imgur.com/EoBbpmH.png[/IMG]

Changed it to 'SB Omni Surround 5.1':
[IMG]http://i.imgur.com/BQ0d9zz.png[/IMG]

Notice that the 'PCM Capture Source' is set as 'Line'. Pressing the Up/Down Arrow key, the source changes to 'Mic':

[IMG]http://i.imgur.com/UTt2VdL.png[/IMG]


After that I exit alsamixer by pressing ESC.
Just in case, I reloaded ALSA (not sure if necessary, though):
```
sudo alsa reload
```

Now pavucontrol show some input from the Mic:
[IMG]http://i.imgur.com/z5TuxuL.png[/IMG]

That's it!
I should point out that the input is coming from the Internal Built-in Mic, I don't have one to test it =/


(Sorry the long post, but this is the first result from Google and I hope more people can solve this)

---

### Post by tal_kg on 2015-09-10
Thanks for howto int worked for me till last week. Now if I start alsamixer there's in PCM Capture Source "Unit 19" and can't change it to anything else like "Line" or  "Mic"
there is aslo in dmsg an error
usb 6-1.3: parse_audio_format_rates_v2(): unable to retrieve sample rate range (clock 18)

Anyone has similar issues with mic ?

---

