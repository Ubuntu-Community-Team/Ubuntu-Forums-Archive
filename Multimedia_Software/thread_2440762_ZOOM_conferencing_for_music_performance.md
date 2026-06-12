---
title: "ZOOM conferencing for music performance"
date: 2020-04-15
forum: Multimedia Software
---

### Post by arst06d on 2020-04-15
Hi

During the lockdown a lot of us amateur musicians are trying to keep their local open mic nights going in the virtual world, and ZOOM seems to be the recommended forum - lots of participants allowed, multi-platform etc.

However, it is obviously built for conferencing, not music, and the quality when playing guitar and singing is not great (being kind).  The vocal seems to be OK but ZOOM does not like guitars it seems - or I haven't found a way to make it acceptable.  

There are a couple of settings I have read about such as

[LIST]
[*]Automatically Adjust Volume
[*]Noise suppression
[*]echo cancellation
[*]
[/LIST]

On my Linux client I only have the Automatically Adjust Volume which I have disabled (may appear as "Keep Original Sound" on other platforms).  I have no other noise shaping options.

Regarding my setup I have tried just singing and playing into my laptop webcam.
Then I tried a plug in mic into the mic jack.
Then I tried a Shure PGA59 Cardioid vocal mic connected to a Focusrite Scarlet interface, into the laptop ia USB
Tries the same with the guitar plugged into the other channel of the Focusrite.
Then tried a small mixer desk with the Shure mic with and without the guitar plugged in, connected to laptop via usb.

In all instances, vocal is OK, but guitar is choppy and vocal and guitar seem to fight each other.

Any musicians on here got any tips please?

Thanks in advance.

---

### Post by Autodave on 2020-04-15
When you say that it is choppy, I am assuming that you mean that what others hear is choppy.  If you record it on your machine, does it sound OK?  If so, I am guessing that your internet bandwidth is too small.

Understand that the human voice is soooo much simpler than a guitar's "voice".  The guitar gives off a tremendous amount of harmonics from the strings vibrating.  Your mic might be capable of capturing all of those harmonics, but your internet connection is not capable of transmitting all of that info and that is why it breaks up.

---

### Post by arst06d on 2020-04-17
Hi, and thanks for the response.
When I record into Audacity for example, all sounds great.
When I start a Zoom meeting with just myself as participant - and using the same setup - recording to my local drive has the problem so I have to assume it's a deficiency in Zoom, especially as it doesn't seem to have the same audio settings as the Windows clients.

---

### Post by Autodave on 2020-04-17
Realize that Zoom was never intended for great audio such as full range music.  

Now, having said that, I know very little about Zoom other than what I have used the free version for.  Perhaps in the pay versions there is better audio possible.  I know that there are quite a few versions out there, so maybe it is the old story of you get what you pay for: more money, better features.

---

### Post by arst06d on 2020-04-17
Yeah, realise it's for video conferencing but lots of groups are trying to use it for music.
I have the paid for pro version as the free version has a time limit on each meeting.

---

### Post by Holger_Gehrke on 2020-04-18
I don't use zoom, but whenever I run into audio problems the first thing I try is to take Pulse Audio out of the equation. Pulse is great if you want multiple programs producing sounds at the same time, but it introduces a lot of overhead. Find out the command to start zoom from the command line then run 'pasuspender **however-you-start-zoom**' (replace the bold part with the actual command ...). 'pasuspender' disables pulseaudio, starts the command given as argument and re-enables pulse after the command has finished. If zoom is written for direct access to ALSA (Advanced Linux Sound Architecture, the actual "close to the metal" driver layer) then two steps that can take some time (pulse "imitating" ALSA and then passing the sound data to the real ALSA) are skipped that way. On the other hand: if zoom is written to work with Pulse, then it wont work that way at all ...

Holger

---

### Post by SeijiSensei on 2020-04-19
Zoom's performance depends on the bandwidth available to the meeting convenor and the number of participants. I've no doubt that Zoom isn't the best choice for audio, but I also suggest that you have the person among you with the biggest Internet pipe host the meeting.  And connect the convenor's computer directly to the router with an Ethernet cable for best performance rather than using wifi.

---

### Post by TheFu on 2020-04-19
i would check which audio encoding Zoom uses. They might be using encoding that is specific to voices.  i know that Jistsi uses vorbis, which is used for music files all the time.  Can't hurt to test a little using meet.jit.si.  No time limits. No info requested. i don't know of any attendee limits, but any one can enable their mic and talk, so really need to have a friendly audience.

---

### Post by arst06d on 2020-04-29
The short answer I've found is ZOOM is crap on Linux.

Had to dual boot and install on Windows.

Thanks chaps.

---

### Post by lwalper on 2020-04-29
Not great on Windows either. However, It seems that the problem is with the auto levels and auto speech activation that doesn't work well with music. There needs to be a consistently high enough sound level to keep the mic open, otherwise the auto levels and speech activation cuts you off.

In the audio settings you can try turning off the "Automatically Adjust Volume" setting and then manually adjust the mike level to peak at about 3/4 of the peak level. Then make sure your audio input is consistently high enough to keep the mic open. in Windows there is also a "Advanced" button in the audio settings. Open that window and uncheck the suppress background noise options - both of them. 

Doesn't look like it plays well on Ubuntu anyhow. Tried Firefox and Chrome. Neither of those allow audio adjustments using Ubuntu. Works OK in Windows.

All your hardware looks OK. I'm using a Behringer Q1204 USB interface with Shure SM58 without any problems. I may also play some pre-recorded music or video through a second computer logged on as co-host. I found that you do need to maintain a high enough sound pressure to keep the ZOOM input active. There seems to be a fine line between keeping it active and overdriving. You may need to have someone on another computer in a different location listening to the levels guiding your adjustments.

---

