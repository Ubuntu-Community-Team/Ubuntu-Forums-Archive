---
title: "Sound Blaster Live 24 Bit Microphone Problem"
date: 2008-05-28
forum: Multimedia Software
---

### Post by osarusan on 2008-05-28
I've read through the Comprehensive Sound Problems guide thread, and made countless forum searches and Google searches looking for the answer to this problem, but I'm totally stumped. I can't figure it out on my own, so I'm coming here for help.

I have a SB Live 24-bit. I'm using Ubuntu Hardy Heron. Audio seems to be working fine; I'm using the CA0106 driver, and I don't have trouble playing multiple sounds at once, or listening to music or movies, or anything like that. My problem is solely with the microphone.

It's most definitely on. Running alsamixer shows me that it's at full volume. (My alsamixer also has no mic boost option.) I do have an option to enable audio for mic feedback, and when I turn this volume up, I **can **hear my microphone through the speakers... so the jack is working and accepting sound. What isn't working is anything that uses the mic in Ubuntu. Sound recorder, the vumeter, Skype, etc. No matter what I do, I just can't figure out how to make these programs realize that the Mic jack is actually producing sound!

I've tried every combination of options in alsamixer and the gnome audio properties control panel. None of them change the fact that my mic can work through the speakers, but none of the software will recognize it.

Is there something simple I'm not doing? Can anyone help me please?

Thanks.

---

### Post by osarusan on 2008-05-29
I hate to just bump like this... but can nobody help?

---

### Post by pasaulais on 2008-06-13
I'm using the same sound card than you (Live! 7.1 24bit [SB0410] Sound Card) and I managed to get the mic working on Ubuntu (tested Sound Recorder, vumeter and TeamSpeak so far).

Here are the settings that work for me: (muting the other channels isn't required but I've tested the other settings to be required)

Mic plugged to the 'blue' port
Playback
    -> mute CAPTURE feedback
Capture
    -> mute line in, phone, aux
    -> enable sound/capture audio for mic and set the volume to the maximum
Options
    -> Analog Source: Mic
    -> Shared Mic/Line in: Mic in
    -> Digital Source: i2s in

Also digital (IEC958) output must be disabled, I am not sure but I think it is the default value.

Here's a small script to configure alsa to use these settings (if you don't want to use alsamixer to do that)

```
#!/bin/sh
# Configure CA0106 sounds cards (such as Sound Blaster Live! 24 bit) for using a mic

amixer cset name='Mic Capture Volume' 255,255 > /dev/null               #Maximum volume for Mic                
amixer cset name='CAPTURE feedback Playback Volume' 0,0 > /dev/null     #Mute Mic feedback
amixer cset name='Line in Capture Volume' 0,0 > /dev/null               #Mute Line in
amixer cset name='Phone Capture Volume' 0,0 > /dev/null                 #Mute Phone
amixer cset name='Aux Capture Volume' 0,0 > /dev/null                   #Mute Aux
amixer cset name='Analog Source Capture Enum' 1 > /dev/null             #Capture source : mic
amixer cset name='Shared Mic/Line in Capture Switch' 1 > /dev/null      #Mic in
amixer cset name='Digital Source Capture Enum' 3 > /dev/null            #i2s in
amixer cset name='IEC958 Playback Switch' off > /dev/null               #disable Digital (SPDIF) Output
```

Hope that helps :)

---

### Post by osarusan on 2008-06-15
Thanks so much! You know, I had a lot of that figured out... no IEC958 and the mic in the blue plug. I had been trying so many combinations and just eventually gave up. I don't know how you managed to find that correct combination, but THANKS! :-D You've saved me so much grief!

---

### Post by pasaulais on 2008-06-15
You're welcome, glad I could help someone :)

I've tested a lot of combinations too but the one that made it work (once I could hear the mic feedback) was setting 'Digital Source: i2s in' as mentioned in the alsa wiki page (which I had read a dozen time before without noticing it, go figure :P).

I spent a whole day trying to get my mic to work, first with most apps (sound recorder and such), but I never managed to make it work with Skype, so I ended up enabling my motherboard sound chipset and using it instead. 

Figuring out how to get it to work didn't really help me in the end, so I'm glad it hasn't been for nothing :) 

But wish I could figure out how to make it work with skype so I can ditch the sound chipset again..

---

### Post by osarusan on 2008-06-23
Yeah, I haven't been able to get it to work in Skype yet... that would really be wonderful. I have no idea why it won't work either, but any step is a good step. I also have an onboard sound card, so I might try using that one with Skype instead. What a mystery...

---

### Post by pasaulais on 2008-06-23
Reading your answer made me want to get it working at last so I tried again and finally managed to configure it properly :)

Adding these lines to ~/.asoundrc made it work for me with Skype:
```

pcm.Mux {
   type asym
   playback.pcm "dmix"
   capture.pcm "dsnoop"
}

```

Then in the Skype sound configuration page, I selected 'Mux' for inbound sound, outbound sound and the third item. Enabling or not 'Permit Skype to automatically adjust mixer settings' didn't seem to matter. 

Hope that helps :)

---

### Post by osarusan on 2008-06-29
Hmm... well I set it to use Mux for in, out, and ring, but the test call didn't seem to work. I'll try again later on and fiddle around with settings to see if I can get any results.

---

### Post by menixmatrix on 2010-03-29
Thanks, this works for me! I'm happy! :popcorn:

---

### Post by navaidfarooqui on 2011-10-27
wow... first of all thank you guys for this thread .... I normally don't post on forums but bcuz of this thread , I am now able to work MIC perfectly (on red connector) along with the 5.1 configuration....Not to mention on Skype too flawlessly.... here it goes

open the terminal

type alsamixer press enter

make sure on Playback(F3)

Mute all SPDIF (though i dun think does anything with mic)
Mute Capture Feedback

Now press F4 for Capture
Mute Line In,Phone and Aux
Stable Mic volume anywhere
on Analog Source column - select Mic
on Digital Source column - select i2s in
on Shared Mic - select Mic in

and bammm.... works perfectly with skype too

---

