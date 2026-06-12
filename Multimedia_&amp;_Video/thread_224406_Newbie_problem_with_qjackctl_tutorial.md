---
title: "Newbie problem with qjackctl tutorial"
date: 2006-07-27
forum: Multimedia &amp; Video
---

### Post by christian.convey on 2006-07-27
Hi,

I've got a HP laptop with audio that works fine, and it's got a pretty clean install of Dapper.  I'm new to linux audio.

When I went through this tutorial for qjackctl:
[http://ubuntustudio.com/wiki/index.php/QjackCtl_Connections](http://ubuntustudio.com/wiki/index.php/QjackCtl_Connections)
everything seemed to go ok, except at the end.  When I click on the laptop's keyboard, the virtual MIDI keyboard keys light up as they should.  But I see no indication that ZynAddSubFX is trying to make any sound in response to the virtual MIDI keys I'm hitting.

Any suggestions where to go from here?

Thanks,
Christian

---

### Post by kellogs on 2006-07-28
zynaddsubfx has some problems connecting to jack... its a little buggy  using it with connections. go to jack control (qjackctl) and press the connect button. its better to open qjack first and then zynadd. now connect zynnad to alsa_pcm or alsa thing. go to zynadd and press a key, it should work. if you open zynadd alone it always works but youll need jack to make some use of it with programs.

---

### Post by christian.convey on 2006-07-28
Thanks.  I did what you said, but no luck.  It seems like I have several problems with potentially different root causes:

1) When I run ZynAdd, and just click on keys on its built-in GUI keyboard, the output volume indicators at the bottom of its window show nothing at all.  I don't know what to make of this.  Is this ZynAdd's way of telling me that it's unable to write data to whatever audio backend it thinks it's supposed to use?

2) When I followed your suggestion for the MIDI stuff, I still see no signs that ZynAdd is receiving the MIDI events from Virtual Keyboard.  I guess if ZynAdd doesn't light up its own GUI's keyboard keys in response to received MIDI events then it's possible that ZynAdd really is receiving the events and I'm unaware of it because of Problem #1 described above.  I have no experience with ZynAdd to know if that's a possibility.

Any other suggestions?

Thanks again,
Christian

---

### Post by christian.convey on 2006-07-28
OK, I've made a tiny bit of progress:

I started zynadd from the command-line with its  "-A" option, which tells it to use ALSA/OSS rather than Jack.  When I did that, zynadd works great.  Using its virtual keyboard, I can generate sounds that I can hear and whose volume levels are indicated at the bottom of the zynadd GUI.

So apparently there's some issue with zynadd and jack, or perhaps jack in general, on my computer.

I don't know if it's noteworthy or not, but when started with "-A" zynadd can generate sound regardless of whether or not esd is running at the time.  But even with esd running, I cannot hear any sound when I try to play the system event sounds in Gnome's System -> Preferences -> Sound dialog.

Any suggestions from here?  Is there perhaps a program that plays better with Jack than ZynAdd does that I can use to see if Jack's basic functions work on my computer?

Thanks,
Christian

---

### Post by dolson on 2006-07-28
You could try another synth application to test that you got JACK stuff going.. amsynth or mx44 should work.

Do you have the snd-seq module loaded?

Also, Zyn.. Do you have the channels enabled? Perhaps somehow they are all disabled, and you just have to enable one for it to work. There should be a checkbox or so. I haven't looked at it in a while.

---

### Post by christian.convey on 2006-07-28
> **dolson said:**
> You could try another synth application to test that you got JACK stuff going.. amsynth or mx44 should work.

Do you have the snd-seq module loaded?
Yup.   lsmod | grep snd gives me this:

snd_seq_dummy           3908  0
snd_seq_oss            37216  0
snd_seq_midi            9600  0
snd_rawmidi            26848  1 snd_seq_midi
snd_seq_midi_event      7520  2 snd_seq_oss,snd_seq_midi
snd_seq                58160  13 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_seq_device          9228  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd_intel8x0           35772  4
snd_ac97_codec        100224  1 snd_intel8x0
snd_ac97_bus            2400  1 snd_ac97_codec
snd_pcm_oss            56448  0
snd_mixer_oss          20544  1 snd_pcm_oss
snd_pcm                96708  5 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              26884  2 snd_seq,snd_pcm
snd                    60004  19 snd_seq_oss,snd_rawmidi,snd_seq,snd_seq_device,snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              10784  1 snd
snd_page_alloc         11304  2 snd_intel8x0,snd_pcm


> Also, Zyn.. Do you have the channels enabled? Perhaps somehow they are all disabled, and you just have to enable one for it to work. There should be a checkbox or so. I haven't looked at it in a while. 
When I launch amsynth manually (and when jackd isn't running), amsynth seems to work as designed.  That is, I can pull up its virtual keyboard (launched by amsynch as a child process I'm guessing), and amsynth gets sound to my speakers

When I do have jackd running (started through qjackctl), and then I launch amsynth, amsynth appears smart enough to manually connect itself to the "alsa_pcm" port.  At least, that's what I see when I look at qjackctl's Connections dialog.

However, when I'm running amsynth in this mode, I get audible sound neither when I try to drive it by a Jack-connected Virtual Keyboard, nor when I try to drive it via the built-in Virtual Keyboard that amsynth is capable of bringing up.

So jack must be at least PARTIALLY working, or else I won't see tool appearing in the Connections dialog of qjackctl, and amsynth wouldn't have been able to autoconnect to alsa_pcm device, right?  And yet, I can't seem to get midi connections working and I can't actually coax jack into emitting a single squeak on my speakers.

Would this be a good time to just determine if the sound is getting lots (a) before it gets to jackd, or (b) as it gets internally routed within jackd, or (c) as it goes from jackd to also, or (d) as it goes from alsa to my soundcard/speakers?

I doubt it's (d) since amsynth and zynadd can produce sound no problem when running against ALSA, but I guess it's still a possibility.  Are there any good tools available so a non-expert like me can debug where the sound stream is getting dropped?

Thanks again for all your help.
- Christian

---

### Post by kellogs on 2006-07-28
did you follow the configuration for jack on the ubuntustudio wiki? maybe its related to some bad configuration... make sure you have it exactly like on the image in the jack part of the wiki. and make sure jack starts succesfully ...

check jack messages, and check it does start well, so it does not tell you about hw device busy or something like that (can be fixed killing esd if it  does complain).

sorry I cant think of something better now...


Edit: start jack on a console and observe the messages.... may be you can get the problem there... try to start jack and then zynadd... you will see connection messages and if there were problems,.. midi connection messages, etc...

---

### Post by christian.convey on 2006-07-29
SUCCESS!!!

When I just run "jackd -d alsa" from the command line (after killing esd), everything works like a charm!

I'll start working on figuring out exactly which of the jackd command-line switches employed by qjackctl were causing the problem.  But for now, life is good!

Thanks a lot for your help.

- Christian

---

