---
title: "Sound Blaster XFI problems"
date: 2007-07-26
forum: Multimedia &amp; Video
---

### Post by johnnyg15 on 2007-07-26
Hi,

I am a newbie to UBUNTU so please forgive me if ia opened this post or another post on this topic already exists.

I was wondering has anyone had any look getting the sound blaster x-fi series to work. I have read there they might not be drivers.

I was wondering has anyone had any experience in getting the card to work and if so how they did it.

Thanks,

Johnny

---

### Post by pottsbgstv on 2007-08-19
Hi

From what i have researched, i don't believe there are X-Fi drivers for linux at the moment.

Have a nice day

---

### Post by ScottC2105 on 2007-08-19
Quoted from [here](http://opensource.creative.com/):

> April 30, 2007 -- Creative plans to make proprietary (closed source) drivers available for the X-Fi series of sound cards. SEE Soundcard Support for updated details. These drivers should have full support for ALSA (playback, recording, mixer, MIDI, synthesis) and OpenAL 1.1 (with EAX effects).

I am having to use my onboard sound until Creative [get off of their butts] make some drivers.

So, the answer to your question. No, there are no drivers at this time :(.

---

### Post by mephibosheth13 on 2007-11-09
> I am having to use my onboard sound until Creative [get off of their butts] make some drivers.

So, the answer to your question. No, there are no drivers at this time :(.

We can all thank M$ Vista for that!

There are "drivers" out that are currently in Beta.  I personally have not been able to get them working.  When I try it says that I need a 64bit OS.  I am running on an AMD64 so I don't get it!

Here's the site, if anyone has luck let me know :-)

[http://opensource.creative.com/](http://opensource.creative.com/)

---

### Post by Kriptonic on 2007-11-12
> **mephibosheth13 said:**
> We can all thank M$ Vista for that!

There are "drivers" out that are currently in Beta.  I personally have not been able to get them working.  When I try it says that I need a 64bit OS.  I am running on an AMD64 so I don't get it!

Here's the site, if anyone has luck let me know :-)

[http://opensource.creative.com/](http://opensource.creative.com/)


I have the same issues.  I even setup unbutu 64 bit os and it still gave me the same error.  I thought it was just me.

---

### Post by msjwozere on 2008-01-12
Sorry for digging up an old thread but....

I am pretty much a linux noob but I managed to work out that the first part of the installer is wrong (at least for my OS).

The line that reads: ```
platform=$(uname -i)
```
Needs to be changed to: ```
platform=$(uname -m)
```
In order to return the correct string to continue installing, once this has been done it goes through the installer but comes up with a bunch of other errors.

I dont know much about linux but I guess I'll work through them one at a time and see if I can shed any more light on the situation.

There seems to be alot of people out here with this same problem, if anyone knows of a work-around (or an ubuntu installer!) let me know. :)

---

