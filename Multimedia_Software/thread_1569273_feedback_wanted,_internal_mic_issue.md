---
title: "feedback wanted, internal mic issue"
date: 2010-09-06
forum: Multimedia Software
---

### Post by BrockStrongo on 2010-09-06
Can someone read through this long post and tell me what they think?
   I am working my way through every available fix to try and get the internal microphone on an acer aspire 6930 to behave properly. I'm not looking for easy answers I just want some extra minds to help me work through this.

   I have edited the alsa-base.conf file so many times with no success, I have gone through almost every option for the alc888 codec. I have adjusted every slider and tab in alsamixer, sound preferences, pavucontrol, pavchooser, every mixer I can think of.
   My end result has been getting the microphone to pick up sound but with lots of static over top of it. Upon close inspection I have found that the sound I have recorded is coming through the right channel only. 
 Acer (according to their website) utilizes two internal microphones on this laptop to create a zone/stereo recording environment. So, as far as I can tell, one of the two mics is picking up sound while the other is either not working/not configured properly, or alsa is trying to use one of the speakers as a microphone creating this static.

What do you think? 
Does this sound like I could be onto something?      
Do you have any suggestions

quote from acer website "Acer PureZone technology with two built-in stereo microphones, featuring beam forming, echo cancellation, and noise suppression technologies. "

---

### Post by BrockStrongo on 2010-09-06
Another odd thing, when "mic boost" is turned up my speakers emit a static sound, almost like the speaker is getting boosted, not the mic

---

### Post by mtnova on 2010-10-02
Hi,

I have the same problem. It is definitely something with alsa wrong pin configuration

One interesting thing :

If you stop pulseaudio and after that open sound recorder (provided that in the gstreamer-properties you have selected alsa as input source) then in the alsamixer there is immediately new input source( digital). Now, if you select Front Mic as Capture then sound is recorded i.e Internal MIC WORKS!!!!!

However if you restart pulse, then digital is lost from alsamixer.

So, there is something wrong ALSA--PULSEAUDIO communication.

Any info from your side?


Cheers 

mtnova

---

### Post by lidex on 2010-10-02
Reference this page for 6930:
[http://www.linlap.com/wiki/acer+aspire+6930](http://www.linlap.com/wiki/acer+aspire+6930)

Scroll down to read all the comments.

---

### Post by mtnova on 2010-10-03
Thank you LIDEX for your reference.But that is a very old info.

As i said WITHOUT pulse everything works including the internal mic. The solution via that link is without pulse.

The problem is that with pulse internal MIC is not working. There is a strong noise and NO posibility in ALSA for digital input.

So, as said before, i guess that there is something wrong in ALSA ---- PULSE communication (its either ALSA wrong pin config or ALSA is suplying wrong info to PULSEAUDIO)

Any help on the issue will be really appreciated since PULSEAUDIO is deeply integrated in UBUNTU.

Cheers,
mtnova

---

### Post by lidex on 2010-10-03
> **mtnova said:**
> Thank you LIDEX for your reference.But that is a very old info.

As i said WITHOUT pulse everything works including the internal mic. The solution via that link is without pulse.

The problem is that with pulse internal MIC is not working. There is a strong noise and NO posibility in ALSA for digital input.

So, as said before, i guess that there is something wrong in ALSA ---- PULSE communication (its either ALSA wrong pin config or ALSA is suplying wrong info to PULSEAUDIO)

Any help on the issue will be really appreciated since PULSEAUDIO is deeply integrated in UBUNTU.

Cheers,
mtnova

Yeah, I didn't read it too closely. You may have to debug this yourself, possibly using 'hda-analyzer'. Reference this document->

---

### Post by mtnova on 2010-10-08
Thank You Lidex.

Just got back from holiday hence the late reply. Will try the attachment and will post the findings for the rest who might have simillar problem.

Best regards
mtnova

---

### Post by mtnova on 2010-10-15
Ok. Finaly is fixed.

As suspected the problem is NOT in ALSA but PULSE.

Additional tweak of PULSEAUDIO is required.

Since this is an old post i don't know if anyone still need the fix.

Internal MIC is fully functional on Aspire 6930 and 6930g.

Ask here if you still need the fix and i will post it.

Cheers 
mtnova

---

### Post by BrockStrongo on 2010-10-15
> **mtnova said:**
> Ok. Finaly is fixed.

As suspected the problem is NOT in ALSA but PULSE.

Additional tweak of PULSEAUDIO is required.

Since this is an old post i don't know if anyone still need the fix.

Internal MIC is fully functional on Aspire 6930 and 6930g.

Ask here if you still need the fix and i will post it.

Cheers 
mtnova

Yes please! If you wouldn't mind posting your fix, or if i missed it, reiterate. Thank for getting to the bottom of this your hard work and diligence is greatly appreciated. You are making linux better. Thank again

---

### Post by mtnova on 2010-10-16
Here You go:

It is guaranteed that it works with ubuntu Maverick and Lucid as well , ALsa 1.0.22 or neweron Acer Aspire 6930g 

You DO NOT HAVE to edit anything in /etc/modprobe.d/alsa.conf BUT if you want you can input options snd-hda-intel model=auto (with me it works better with model=auto)

You EDIT as root

> gksudo gedit /etc/pulse/daemon.conf

Find in it:

> ;default-sample-format = s16le
;default-sample-rate = 41600
;default-sample-channels = 6
;default-channel-map = front-left,front-right

and make it like this:

default-sample-format = s16le
default-sample-rate = 48000
default-sample-channels = 6
; default-channel-map = front-left,front-right

SAVE, Reboot and that is it.

Check it should work now,the internal MIC.

Simple is it? ( it took me 2 months to realize that this was the problem since pulseaudio is poor documented)

Please post your result for me and others to know if it worked (it should)

Take care
mtnova

---

### Post by BrockStrongo on 2010-10-16
It works!  At first nothing was working than I noticed the semicolons. I had not removed them. I take it the semicolons are like comments eg. //* or ##. Also, my default-sample-channels was 2 not 6. I changed it to 6.
   Adding  options snd-hda-intel model=auto to alsa-base.conf resulted in no subwoofer (Acer Tuba). The only options that appear to work for me are either model=acer-aspire6930 or omitting the line altogether. 
   HOWEVER. When listening back to the recording I notice it is much louder in the right channel than it is in the left. This leads me to believe that only one half of the zone/stereo microphone array is functioning. 
  This is the closest I have been to getting the mic to work properly, I am definitely happy with this fix. Thank you very much. Maybe a bit more poking around and I can mark this thread a solved.
THANKS MTNOVA AND LIDEX.

---

### Post by mtnova on 2010-10-16
Cheers,

I'm happy that it works for you as well.

Yes ,the semicolons are like # (comment out) and you need to uncomment.

As for the channels, (6 or 2) i think it depends as to what you have in alsabase.conf i.e if you have model=auto and alsa recognize your card as 6 channel then you should use 6. But try with 2 as well, if its better use it.

I think that you should use model= whatever works best for you (6930). 

As for the stereo MIC I think that that was what was making the problem (pulse does not recognize stereo mic and the result was noice).

But if you check in Skype, the mic with this fix appears to be perfect.

Cheers and take care.

mtnova

---

