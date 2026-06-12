---
title: "karmic surround sound confusion"
date: 2009-11-08
forum: Multimedia Software
---

### Post by Lucky75 on 2009-11-08
Hey all,

I'm rather confused as to what I'm doing with the whole sound thing in 9.10. I managed to somewhat hack the sound together on hardy way back when, but I just did a clean install and am having issues getting surround sound to work.

It seems that ALSA works okay when I change the output to analog stereo, but digital doesn't really seem to work, and I have no idea how to get my 5.1 surround working. Am I even using ALSA? or pulse? Firefox/Flash seems to be using ALSA, and so does VLC (since I set it that way), so I guess I don't really care if pulse is installed. 

How can I get my surround sound working though?

Here is a full list of all my audio settings/hardware:
[http://www.alsa-project.org/db/?f=94c2b0eea443e9f8a7626b4d69ad7c75ec4eb20c](http://www.alsa-project.org/db/?f=94c2b0eea443e9f8a7626b4d69ad7c75ec4eb20c)


Thanks!

---

### Post by Lucky75 on 2009-11-09
bump

---

### Post by Lucky75 on 2009-11-10
up

---

### Post by xzero1 on 2009-11-10
> **Lucky75 said:**
> Hey all,

I'm rather confused as to what I'm doing with the whole sound thing in 9.10. I managed to somewhat hack the sound together on hardy way back when, but I just did a clean install and am having issues getting surround sound to work.

It seems that ALSA works okay when I change the output to analog stereo, but digital doesn't really seem to work, and I have no idea how to get my 5.1 surround working. Am I even using ALSA? or pulse? Firefox/Flash seems to be using ALSA, and so does VLC (since I set it that way), so I guess I don't really care if pulse is installed. 

How can I get my surround sound working though?

Here is a full list of all my audio settings/hardware:
[http://www.alsa-project.org/db/?f=94c2b0eea443e9f8a7626b4d69ad7c75ec4eb20c](http://www.alsa-project.org/db/?f=94c2b0eea443e9f8a7626b4d69ad7c75ec4eb20c)


Thanks!

Pulse audio is the new sound system. ALSA, oss etc run under pulse audio so that it will be compatible with their respective apps. The karmic sound applet has no button to switch from analog to digital output but this can be done with some cards using the old alsamixer. For 5.1 passthrough, temporarily select the profile "off" or a non-digital profile for your soundcard using the applet.

---

### Post by michaelzap on 2009-11-10
> **xzero1 said:**
> For 5.1 passthrough, temporarily select the profile "off" or a non-digital profile for your soundcard using the applet.

This doesn't get me 5.1 sound on my Lenovo Y530. I've also tried messing with all available channels in alsamixer to no effect. Anyone else have suggestions?

---

### Post by xzero1 on 2009-11-10
> **michaelzap said:**
> This doesn't get me 5.1 sound on my Lenovo Y530. I've also tried messing with all available channels in alsamixer to no effect. Anyone else have suggestions?

Of course turning the sound off won't give 5.1 sound. What it does is enable 5.1 passthrough. After this, assuming your soundcard is device 0, then use something like this:

 mplayer -ao alsa:device=hw=0.0 -ac hwac3  FILENAME

---

### Post by michaelzap on 2009-11-10
> **xzero1 said:**
> Of course turning the sound off won't give 5.1 sound. What it does is enable 5.1 passthrough. After this, assuming your soundcard is device 0, then use something like this:

 mplayer -ao alsa:device=hw=0.0 -ac hwac3  FILENAME

That plays the file, but in stereo not 5.1.

If it had worked I'd be asking how to set this up for all GUI apps (Exaile, VLC, Urban Terror), since mplayer is not how I usually listen to audio.

---

### Post by xzero1 on 2009-11-10
That is strange because this commandline uses hardware spdif passthrough. Does mplayer show a 5.1 ac3 stream is being played back?

---

### Post by michaelzap on 2009-11-10
> **xzero1 said:**
> That is strange because this commandline uses hardware spdif passthrough. Does mplayer show a 5.1 ac3 stream is being played back?

Nope. I was playing a stereo mp3. I was expecting that it would play in all speakers regardless (since that's what it used to do in Jaunty).

I don't know that I have a 5.1 ac3 file... In any case this would probably be just an exercise for me, since what I want is for my surround sound to work all the time from any app (and to be able to control it using the volume keys and/or panel app). There must be a way to pipe all audio through ALSA by default, no?

Anyway thanks for your suggestion.

---

### Post by Lucky75 on 2009-11-10
Well, firefox for example is saying that any flash is using the ALSA plugin. How would I get that to use pulse then? And don't I need to set channels=6 somewhere for alsa or something like that? I thought that I still had to set surround sound through alsa somewhere, even if I was using pulse?

And my digital output won't even work, only analog does. Even in alsamixer, it's only saying:
```

Card: HDA NVidia                                                         
Chip: Analog Devices AD1986A                                                
View: [Playback] Capture  All                                               
Item: Master [dB gain=0.00, 0.00]  

```

And how do I set the profile off? What profile? And I don't see any extra channels in alsamixer for surround sound (picture attached).

Sorry if I sound confused haha.

---

### Post by fooman on 2009-11-10
sorry,  are you using an spdif output to a stereo? ...or a 5.1 channel speaker system hooked up to your computer's soundcard?

if using 5.1 speakers to your computer's soundcard...

have you tried right-clicking the volume/speaker icon in the top panel > sound preferences > hardware tab 

in the bottom of the window,  click the up/down arrow at the end of the profile line and choose analog 5.1 output.

then open a terminal and type or copy/paste the following into it to test the speakers:

```
speaker-test -c6 -twav
```

hope that helps.

---

### Post by Lucky75 on 2009-11-10
> **fooman said:**
> sorry,  are you using an spdif output to a stereo? ...or a 5.1 channel speaker system hooked up to your computer's soundcard?

if using 5.1 speakers to your computer's soundcard...

have you tried right-clicking the volume/speaker icon in the top panel > sound preferences > hardware tab 

in the bottom of the window,  click the up/down arrow at the end of the profile line and choose analog 5.1 output.

then open a terminal and type or copy/paste the following into it to test the speakers:

```
speaker-test -c6 -twav
```

hope that helps.

I'm attempting to use a 5.1 speaker system hooked up to my soundcard.

I have no analog 5.1 output. I only have analog/digital stereo input/output/duplex. That's what is causing me some issues.

Is it because I only have 3 input jacks and need to say somewhere that I need to use the mic in as output? How would I do that.

Running the speaker test only works for the front two speakers, since I don't seem to have an option to use 5.1 anywhere in the hardware tab.

---

### Post by xzero1 on 2009-11-10
You still seem confused.  Pulse plays the sound; everything else hooks to it. To get multichannel sound via a digital output the sound *must* be pre-encoded multichannel sound i.e. 5.1 movies soundtracks. To play this sound spdif passthrough is used which sends the original encoded sound to the amplifier which decodes it to multichannel. Ubuntu and pulse supports multichannel sound using analog outputs.

---

### Post by Lucky75 on 2009-11-10
> **xzero1 said:**
> You still seem confused.  Pulse plays the sound; everything else hooks to it. To get multichannel sound via a digital output the sound *must* be pre-encoded multichannel sound i.e. 5.1 movies soundtracks. To play this sound spdif passthrough is used which sends the original encoded sound to the amplifier which decodes it to multichannel. Ubuntu and pulse supports multichannel sound using analog outputs.

Ah, I see. So how do I actually do it then?

---

### Post by michaelzap on 2009-11-10
> **xzero1 said:**
> To get multichannel sound via a digital output the sound *must* be pre-encoded multichannel sound i.e. 5.1 movies soundtracks.

This sentence is confusing: In Jaunty, my laptop played stereo sound through all five speakers (as it does in Vista), which is not the same as true surround sound but ought to be possible in Karmic as well.

---

### Post by xzero1 on 2009-11-10
> **michaelzap said:**
> This sentence is confusing: In Jaunty, my laptop played stereo sound through all five speakers (as it does in Vista), which is not the same as true surround sound but ought to be possible in Karmic as well.

Without encoding, it is not possible with the *digital* (coax or spdif) output.

---

### Post by Lucky75 on 2009-11-10
> **xzero1 said:**
> Without encoding, it is not possible with the *digital* (coax or spdif) output.

Well, if the video is encoded to use it? How would I do it?

And how would I get analog to play though all 5 speakers?

---

### Post by michaelzap on 2009-11-10
> **xzero1 said:**
> Without encoding, it is not possible with the *digital* (coax or spdif) output.

Aha! I see.

---

### Post by xzero1 on 2009-11-10
> **Lucky75 said:**
> Well, if the video is encoded to use it? How would I do it?

And how would I get analog to play though all 5 speakers?

If the video is encoded use spdif passthrough (see my earlier post on this thread.

For analog to play there must be seperate connections to each speaker. Usually 2 channels per connection and 3 connectors. The card and amplifier usually has connections for 2 front,2 rear and center/subwoofer.

---

### Post by Lucky75 on 2009-11-10
> **xzero1 said:**
> If the video is encoded use spdif passthrough (see my earlier post on this thread.

For analog to play there must be seperate connections to each speaker. Usually 2 channels per connection and 3 connectors. The card and amplifier usually has connections for 2 front,2 rear and center/subwoofer.

Umm, I've had surround sound working since 8.04 until my disk died a few days ago, and I only have 3 inputs, one of them being for a mic.

So I have to use digital then? Digital doesn't even seem to be working for stereo at the moment. Or are you suggesting that I CAN use analog with 3 inputs. How would I do that? And if not, how would I use spdif? I didn't really understand what you were suggesting in your earlier post. Are there step-by-step instructions anywhere?

> 
For 5.1 passthrough, temporarily select the profile "off" or a non-digital profile for your soundcard using the applet.


How do I turn the profile off? Or select a non-digital profile? Just select analog?

> 
After this, assuming your soundcard is device 0, then use something like this:
mplayer -ao alsa:device=hw=0.0 -ac hwac3 FILENAME


I've never had to do that before though....what's changed? I've had some form of surround sound working since 8.04, but I've never really had to specify it for every program. Even flash used to work as surround, but it doesn't now. Simply doing that passthrough you were suggesting wouldn't fix that, would it?

Thanks for the help!


Edit: To add, these are the only options I have in the hardware tab. Which one should I use?


Off -This is what you mean?
Analog Stereo input
Digital Stereo duplex (IEC958)
Digital stereo output (IEC958) + Analog Stereo input
Analog Stereo output
Analog Stereo Duplex

Currently I'm using Analog Stereo output.

---

### Post by xzero1 on 2009-11-10
> **Lucky75 said:**
> Umm, I've had surround sound working since 8.04 until my disk died a few days ago, and I only have 3 inputs, one of them being for a mic.

So I have to use digital then? Digital doesn't even seem to be working for stereo at the moment. Or are you suggesting that I CAN use analog with 3 inputs. How would I do that? And if not, how would I use spdif? I didn't really understand what you were suggesting in your earlier post. Are there step-by-step instructions anywhere?



How do I turn the profile off? Or select a non-digital profile? Just select analog?



I've never had to do that before though....what's changed? I've had some form of surround sound working since 8.04, but I've never really had to specify it for every program. Even flash used to work as surround, but it doesn't now. Simply doing that passthrough you were suggesting wouldn't fix that, would it?

Thanks for the help!


Edit: To add, these are the only options I have in the hardware tab. Which one should I use?


Off -This is what you mean?
Analog Stereo input
Digital Stereo duplex (IEC958)
Digital stereo output (IEC958) + Analog Stereo input
Analog Stereo output
Analog Stereo Duplex

Currently I'm using Analog Stereo output.

First let me make a correction. I said it is not possible to get surround sound on digital without encoding. This is true but some amplifiers create it from a simple stereo signal. So the amplifier may have a surround mode to create something from the stereo signal.

For analog you need an amplifier or connection to speakers from all (3) outputs.

You can do passthrough with analog stereo out selected.

It would be helpful if you posted the output of aplay -l.

Can you get any sound from the digital output?

---

### Post by Lucky75 on 2009-11-10
> **xzero1 said:**
> First let me make a correction. I said it is not possible to get surround sound on digital without encoding. This is true but some amplifiers create it from a simple stereo signal. So the amplifier may have a surround mode to create something from the stereo signal.

For analog you need an amplifier or connection to speakers from all (3) outputs.

You can do passthrough with analog stereo out selected.

It would be helpful if you posted the output of aplay -l.

Can you get any sound from the digital output?

I have my 5 speakers hooked up to the sub, which then has 3 inputs to the motherboard/soundcard. Not sure if that's what you mean by all (3) outputs, but there are three connections currently going  into the mobo from the speakers.

No sound at all from digital, but I swear I used to have digital sound working. 

```

aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: AD198x Digital [AD198x Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

There's a more extensive breakdown of everything related to the audio in my first post if that helps :S

---

### Post by xzero1 on 2009-11-10
> **Lucky75 said:**
> I have my 5 speakers hooked up to the sub, which then has 3 inputs to the motherboard/soundcard. Not sure if that's what you mean by all (3) outputs, but there are three connections currently going  into the mobo from the speakers.

No sound at all from digital, but I swear I used to have digital sound working. 

```

aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: AD198x Digital [AD198x Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```There's a more extensive breakdown of everything related to the audio in my first post if that helps :S

Ok good now try:
speaker-test -c 6 -D surround51 -t wav
from the command line.

Describe the results.

---

### Post by Lucky75 on 2009-11-10
Odd..

Doing your command:
```

speaker-test 1.0.20

Playback device is surround51
Stream parameters are 48000Hz, S16_LE, 6 channels
WAV file(s)
Channels count (6) not available for playbacks: Invalid argument
Setting of hwparams failed: Invalid argument

```

Another command gives me output only on front left and front right. This is with analog output set under hardware tab. Do you want me to change that?

```

speaker-test -Dplug:surround51 -c6 -l1 -twav

speaker-test 1.0.20

Playback device is plug:surround51
Stream parameters are 48000Hz, S16_LE, 6 channels
WAV file(s)
Rate set to 48000Hz (requested 48000Hz)
Buffer size range from 64 to 16384
Period size range from 32 to 8192
Using max buffer size 16384
Periods = 4
was set period_size = 4096
was set buffer_size = 16384
 0 - Front Left
 4 - Center
 1 - Front Right
 3 - Rear Right
 2 - Rear Left
 5 - LFE
Time per period = 8.365185

```

---

### Post by michaelzap on 2009-11-11
Hooray! I was able to get my Lenovo Y530 surround sound working by adding 
options snd-hda-intel model=lenovo-sky
to the end of
/etc/modprobe.d/alsa-base

---

### Post by Lucky75 on 2009-11-11
so, for me I should add what? nvidia?

Right now I just have:
options snd-hda-intel power_save=10 power_save_controller=N

00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)

---

### Post by michaelzap on 2009-11-11
I got the info on what to enter in that file from [this old thread]("http://ubuntuforums.org/showpost.php?p=5460960&postcount=2").

I did not reinstall ALSA, since Karmic has a recent version, but that thread says where to look for sound card codes.

---

### Post by Lucky75 on 2009-11-11
mmm, yea, only for lenovo models. 

If anyone have any other suggestions, I'd really appreciate it. Thanks!

---

### Post by Maheriano on 2009-11-11
3 pages and not one person mentioned that a mp3 will not play in surround sound because it's only recorded in stereo. What you're looking for is Dolby ProLogic on your receiver which will emulate surround sound. You need to play a DVD if you're going to be troubleshooting AC3.

---

### Post by michaelzap on 2009-11-11
I see now that the location that poster gave for the model codes is from the ALSA download that I didn't do, but you can also find that info here:
[http://www.alsa-project.org/main/index.php/Matrix:Main](http://www.alsa-project.org/main/index.php/Matrix:Main)

---

### Post by michaelzap on 2009-11-11
> **Maheriano said:**
> 3 pages and not one person mentioned that a mp3 will not play in surround sound because it's only recorded in stereo. What you're looking for is Dolby ProLogic on your receiver which will emulate surround sound. You need to play a DVD if you're going to be troubleshooting AC3.

Well, there may be a confusion in terms then. In my case I just wanted all five of my speakers to work; whether or not they actually played "surround sound" wasn't the issue. Now that I have configured ALSA to use my audio chip as it was intended, I do get sound out of all five speakers when playing a stereo mp3.

---

### Post by Lucky75 on 2009-11-11
Yeah, exactly. I just want all 5 speakers to work if the mp3/video/dvd wasn't recorded in surround sound, and for actual surround sound to work if it was.

How do I do that?


@Michaelzap, I think what I'm looking for is [http://www.alsa-project.org/main/index.php/Matrix:Vendor-Nvidia](http://www.alsa-project.org/main/index.php/Matrix:Vendor-Nvidia) the HDA one? Can anyone confirm that with the specs that I've posted? Not too sure what to put as a module, or if that will help at all.

---

### Post by michaelzap on 2009-11-11
> **Lucky75 said:**
> Yeah, exactly. I just want all 5 speakers to work if the mp3/video/dvd wasn't recorded in surround sound, and for actual surround sound to work if it was.

How do I do that?

Well, I did it by adding my sound card code to the ALSA config file, as mentioned [here]("http://ubuntuforums.org/showpost.php?p=8294868&postcount=25").

And [here]("http://www.alsa-project.org/main/index.php/Matrix:Main") is where you can find info on your sound card.

---

### Post by Maheriano on 2009-11-11
> **michaelzap said:**
> Well, there may be a confusion in terms then. In my case I just wanted all five of my speakers to work; whether or not they actually played "surround sound" wasn't the issue. Now that I have configured ALSA to use my audio chip as it was intended, I do get sound out of all five speakers when playing a stereo mp3.
None of that matters. If you're getting the sound file out of your computer to your receiver, it doesn't matter how it gets there, nor in which format it's in when it's there. It's your receiver's duty to decode the stream to ProLogic or whichever format you like.

---

### Post by michaelzap on 2009-11-11
> **Maheriano said:**
> None of that matters. If you're getting the sound file out of your computer to your receiver, it doesn't matter how it gets there, nor in which format it's in when it's there. It's your receiver's duty to decode the stream to ProLogic or whichever format you like.

Er. As I mentioned, I'm playing this audio on a laptop with 5.1 sound (four speakers and a subwoofer). Only two of the speakers were working previously, no matter whether the audio file was 5.1, stereo, or mono.

---

### Post by Lucky75 on 2009-11-11
> **michaelzap said:**
> Well, I did it by adding my sound card code to the ALSA config file, as mentioned [here]("http://ubuntuforums.org/showpost.php?p=8294868&postcount=25").

And [here]("http://www.alsa-project.org/main/index.php/Matrix:Main") is where you can find info on your sound card.

Yeah, I was there. I just don't know where on the site to look...

I was thinking the nvidia one that I posted a link to, but it still doesn't give any information for the model or anything like that, just redirects me to the nvidia website.

> **Maheriano said:**
> None of that matters. If you're getting the sound file out of your computer to your receiver, it doesn't matter how it gets there, nor in which format it's in when it's there. It's your receiver's duty to decode the stream to ProLogic or whichever format you like.

Ok, clearly it's possible to have all 5 speakers outputting sound. That's what I was looking for. **How do I do that? ** Of course, if the audio is encoded for surround, I'd like to do have it play as proper surround sound too. I don't see what you're trying to point out, as it doesn't really matter, does it?

---

### Post by michaelzap on 2009-11-11
> **Lucky75 said:**
> Yeah, I was there. I just don't know where on the site to look...

I was thinking the nvidia one that I posted a link to, but it still doesn't give any information for the model or anything like that, just redirects me to the nvidia website.


[This page]("https://help.ubuntu.com/community/HdaIntelSoundHowto") gives you info on identifying your sound card.

And then you should be able to find it in the ALSA matrix.

There is some possibly related info [here]("http://alsa.opensrc.org/index.php/NVidia").

---

### Post by Lucky75 on 2009-11-11
I still can't figure out which one to use. I just don't understand lol.

This is my motherboard, using integrated audio: [http://hothardware.com/articles/Asus-P5NSLI-NVIDIA-nForce-570-Intel-Edition/](http://hothardware.com/articles/Asus-P5NSLI-NVIDIA-nForce-570-Intel-Edition/)

> 
 _Chipset_
NVIDIA nForce 570 SLI Intel Edition
- NB: C19SLI
- SB: MCP51 

 _Audio_
ADI AD1986A SoundMAX 6-channel CODEC
Jack Sensing and Enumeration
S/PDIF out interface 


and

```

cat /proc/asound/card0/codec#* | grep Codec
Codec: Analog Devices AD1986A

```

and

```

aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: AD198x Digital [AD198x Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

Any idea which one I should use? I don't know, even after reading the guide.

From your last link, it's telling me to use the intel8x0 alsa driver? Where do I specify that, and what model?. I can't figure out which one to choose.

Instead of "options snd-hda-intel"  do I use "options snd-intel8x0" or something?

---

### Post by michaelzap on 2009-11-11
It's clear as mud, isn't it?

You might try
options model=3stack

and have you tried running alsamixer from the command line to see if you have a "4ch" option in there?

---

### Post by michaelzap on 2009-11-11
This old message has some useful info:
[https://lists.ubuntu.com/archives/ubuntu-users/2008-August/157220.html](https://lists.ubuntu.com/archives/ubuntu-users/2008-August/157220.html)

---

### Post by Lucky75 on 2009-11-11
> **michaelzap said:**
> It's clear as mud, isn't it?

You might try
options model=3stack

and have you tried running alsamixer from the command line to see if you have a "4ch" option in there?

Haha, yeah. Thanks, I'll give 3stack a try. DO I just sudo alsa force-reload? 

There didn't seem to be any channel options in alsamixer. I posted a screenshot earlier in the thread, but yeah, I don't think there was.

Thanks for all the help :)

---

### Post by michaelzap on 2009-11-11
> **Lucky75 said:**
> DO I just sudo alsa force-reload?
Not sure; I just restarted.

---

### Post by Lucky75 on 2009-11-11
Aha! So close! Thanks! It seems to have worked!

I got it to play with this command: speaker-test -Dplug:surround51 -c6 -l1 -twav


Now I just have to figure out why it isn't giving me surround in VLC. Should I set it to use ALSA? or pulse?

---

### Post by michaelzap on 2009-11-11
> **Lucky75 said:**
> Aha! So close! Thanks! It seems to have worked!

I got it to play with this command: speaker-test -Dplug:surround51 -c6 -l1 -twav


Now I just have to figure out why it isn't giving me surround in VLC. Should I set it to use ALSA? or pulse?

Well, Pulse uses ALSA, and in Karmic I think you're stuck with Pulse anyway...

Do you now see other Profiles in the Hardware tab of your Sound control panel?

---

### Post by Lucky75 on 2009-11-11
> **michaelzap said:**
> Well, Pulse uses ALSA, and in Karmic I think you're stuck with Pulse anyway...

Do you now see other Profiles in the Hardware tab of your Sound control panel?

No, unfortunately I don't. Still only stereo. Alsamixer gives me extra channels though, which I've set.

---

### Post by michaelzap on 2009-11-11
Is this what you added to your ALSA config file?
```
options snd-hda-intel model=3stack
```
I left out the middle bit before.

---

### Post by Lucky75 on 2009-11-11
> **michaelzap said:**
> Is this what you added to your ALSA config file?
```
options snd-hda-intel model=3stack
```
I left out the middle bit before.

yeah

```
options snd-hda-intel power_save=10 power_save_controller=N model=3stack
```

Where'd you get 3stack from anyways?

It's odd, I get channels showing up in alsamixer (Attached), and the speaker test gives me surround, but VLC and flash both give me stereo.

---

### Post by michaelzap on 2009-11-11
> **Lucky75 said:**
> Where'd you get 3stack from anyways?

It was mentioned in that old message I linked to [here]("http://ubuntuforums.org/showpost.php?p=8298150&postcount=40") (among other places).

I think that you need to see surround sound profiles in your Sound Preferences control panel before Pulse Audio will use it. In my case I had other profiles right away, but I had played with alsamixer a bunch before changing my config file (so maybe that helped). I would turn everything on in alsamixer and see if PA gets a clue.

Other than that, maybe 3stack isn't the right model code? The ALSA site seemed to say to use the board model name, which might be AD1986A. That's a guess, though, so maybe some Googling would help.

---

### Post by michaelzap on 2009-11-11
Oh - you might also try installing the other pulse audio utilities from Synaptic. The Pulse Audio Device Chooser in particular might be useful. I have those installed, and although I haven't really used them they might help.

I also installed linux-backports-modules-alsa-karmic as suggested [here]("http://drowninginbugs.blogspot.com/2009/10/caveats-for-audio-in-910.html").

---

### Post by Lucky75 on 2009-11-11
> **michaelzap said:**
> 
I think that you need to see surround sound profiles in your Sound Preferences control panel before Pulse Audio will use it. In my case I had other profiles right away, but I had played with alsamixer a bunch before changing my config file (so maybe that helped). I would turn everything on in alsamixer and see if PA gets a clue.

Everything is on. I attached a screenshot above. But yea, no other profiles under the hardware tab, which is odd.

> 
Other than that, maybe 3stack isn't the right model code? The ALSA site seemed to say to use the board model name, which might be AD1986A. That's a guess, though, so maybe some Googling would help.

I've looked on google before I came here :) I don't think it would recognise AD1968A, perhaps AD196X though, as it said when I did aplay -l.


> **michaelzap said:**
> Oh - you might also try installing the other pulse audio utilities from Synaptic. The Pulse Audio Device Chooser in particular might be useful. I have those installed, and although I haven't really used them they might help.


Yeah, padevchooser is installed. Not too sure what other pulse utilities would be of use if alsa is still having issues with the surround sound and the hardware tab won't show anything new.

> 
I also installed linux-backports-modules-alsa-karmic as suggested [here]("http://drowninginbugs.blogspot.com/2009/10/caveats-for-audio-in-910.html").

> 
    * Use Karmic's kernel, not Jaunty's. A lot of you with Realtek and IDT/Sigmatel HDA codecs are being bitten by /boot/grub/grub.cfg not being updated properly, resulting in Jaunty's 2.6.28 kernel being used instead of Karmic's 2.6.31. Jaunty's kernel has pretty subpar performance for PulseAudio, and you should not incorrectly blame PulseAudio.

I'm suing 2.6.31 by default I think already. Seems to have come like that.
> 
    * Check that slmodemd is not running if you're seeing a dummy/null sink in the volume control applet. Arguably PulseAudio's module-udev-detect should allow the device instead of bailing when detecting it, and an approach is under discussion for future versions. In the meantime, you can either instead load module-detect in /etc/pulse/default.pa (or ~/.pulse/default.pa) or kill slmodemd.

Perhaps? Don't really know what slmodemd is though, and I'm not sure what it means by seeing a dummy sink in the volume control applet.
> 
    * Install linux-backports-modules-alsa-karmic (then reboot) if you have a very new computer, because that package enables audio on quite a few very new laptop models and contains much improved support for microphone auto-switching.

Computer's about 3-4 years old.


It doesn't seem to be any of those. What do you think?

---

### Post by michaelzap on 2009-11-11
I'm also running the latest Release Candidate for the kernel (2.6.32-rc6) as found here:
[http://ubuntuforums.org/showpost.php?p=8263419&postcount=135](http://ubuntuforums.org/showpost.php?p=8263419&postcount=135)

Couldn't hurt to try that. Just download the .deb files for the headers and kernel that match your architecture (i386 or amd64) and the "all" headers file and install them. Then reboot and choose that kernel from Grub.

My Karmic installation didn't work at all until I did that, so I didn't even try to get surround sound working before using it.

---

### Post by Lucky75 on 2009-11-11
mmm, maybe I'll wait for the release of the kernel for that one :) I try not to install RC or beta kernels ;)

Mind you, here are some of the changes apparently:

> 
      ALSA: hda - Fix capture source checks for ALC662/663 codecs
      ALSA: dummy - Fix descriptions of pcm_substreams parameter
      ALSA: hda - Don't check invalid HP pin
      ALSA: hda: Use quirk mask for Dell Inspiron Mini9/Vostro A90 using ALC268
      ahci: Add the AHCI controller Linux Device ID for NVIDIA chipsets.
      ALSA: hda_intel: Add the Linux device ID for NVIDIA HDA controller

      ALSA: sound: Move dereference after NULL test and drop unnecessary NULL tests
      ALSA: sound/parisc: Move dereference after NULL test
      ALSA: pcsp - Fix nforce workaround


---

### Post by michaelzap on 2009-11-11
> **Lucky75 said:**
> mmm, maybe I'll wait for the release of the kernel for that one :) I try not to install RC or beta kernels ;)

Shouldn't really cause an issue though, I would think.

The worst thing that can happen is it doesn't work well for you and you reboot with your existing kernel (and uninstall it if you like).

---

### Post by Lucky75 on 2009-11-11
> **michaelzap said:**
> The worst thing that can happen is it doesn't work well for you and you reboot with your existing kernel (and uninstall it if you like).

Hm, that's true. Maybe I'll give it a try tomorrow. Still don't really think that it is the problem though. There's got to be something missing somewhere..

---

### Post by michaelzap on 2009-11-11
> **Lucky75 said:**
> Hm, that's true. Maybe I'll give it a try tomorrow. Still don't really think that it is the problem though. There's got to be something missing somewhere..

I'm not sure that it is either, but the current "stable" kernel is kind of a mess so it might be.

---

### Post by xzero1 on 2009-11-12
> **Maheriano said:**
> 3 pages and not one person mentioned that a mp3 will not play in surround sound because it's only recorded in stereo. What you're looking for is Dolby ProLogic on your receiver which will emulate surround sound. You need to play a DVD if you're going to be troubleshooting AC3.

You might want to learn how to read.:p

---

### Post by Lucky75 on 2009-11-12
WOO!!

The combination of 3stack and the new kernel got it working! MUCH THANKS :)

---

### Post by michaelzap on 2009-11-12
> **Lucky75 said:**
> WOO!!

The combination of 3stack and the new kernel got it working! MUCH THANKS :)

EXCELLENT! Please mark the thread as solved so that others are more likely to find it if they have a similar problem.

---

### Post by Lucky75 on 2009-11-12
Way ahead of you :) Yay for kernels that aren't broken.

---

### Post by michaelzap on 2009-11-12
> **Lucky75 said:**
> Yay for kernels that aren't broken.

Ain't THAT the truth!

---

### Post by PsyWolf on 2009-11-29
i added model=3stack to my /etc/modprobe.d/alsa-base.conf and I installed the new kernal (rc8), but surround sound still isn't working for me.

Am I missing something, or does that mean the fix just isn't working for me.  Any suggestions?

---

### Post by michaelzap on 2009-11-29
> **PsyWolf said:**
> i added model=3stack to my /etc/modprobe.d/alsa-base.conf and I installed the new kernal (rc8), but surround sound still isn't working for me.

Am I missing something, or does that mean the fix just isn't working for me.  Any suggestions?

Well, it's hard to say for sure, but the following things might be helpful:

[LIST]
[*]Have you tried running alsamixer from the command line and seeing if you can set more channels or boost the levels of ones that are at zero?
[*]Make sure that the syntax for the model definition is correct (see previous posts in this thread)
[*]Perhaps 3stack isn't the right model definition for your hardware?
[*]I also installed linux-backports-modules-alsa-karmic as suggested [here]("http://drowninginbugs.blogspot.com/2009/10/caveats-for-audio-in-910.html"), and I don't know if that helped
[/LIST]

---

### Post by pappfer on 2009-12-20
It's a great topic, I had the same problem. I've put model=3stack to my alsa-base.conf file and after that some new fields appeared in my alsamixer and also 5.1 surround sound appered in the sound preferences. There I selected 5.1 surround sound but it only gives sound from my front speakers unless I set "line jack" (subwoofer) and "mic jack" (rear speakers) to line out. So I have to always change them to line out. Why? Is it possible to make it always line out?
[Screenshot]("http://pappfer.se-portal.hu/temp/alsamixer.png")

---

### Post by pappfer on 2010-01-05
Any idea?

---

### Post by sports.car.guy on 2010-01-17
Reading would be a good thing. It sounded like an Alsa mapping issue to me which is what I had been dealing with until moments ago. Pulseaudio does really stink. It is more then configuration issues by the user which is what someone stated earlier in this post. It is lets keep adding and not work on what we have so far to make sure it is bug free.

That is the way it seems lately with Linux in general. I have found so many bugs and issues since I upgraded from kubuntu 9.04 to 9.10 it is far from funny and pulseaudio had some of the major ones. I did everything online suggested to fix the chirps I was getting, the conflicts and issues with MythTV, along with almost every media player. These were issues for the most part not there in 9.04 for me. It was a completely clean install so couldn't be caused by configuration conflicts either.

Mythbuntu was another area filled with bugs on the note of coding. Their control center choked on me God only knows how many times and when I finally ran it from a terminal I found out why. It couldn't find a couple of icons. Now that is sad, and something you see in Windows because WYSWYG programming is fun. 

I used to be a programmer back in the day, and I never relied on files being on a system. I would include them with the install as a separate file or have them internally stored in the binary like it is possible with Windows' executables. I will say this, so far it seems most of the bugs are minor ones, nothing end of the world.

For the person out here who was trying to get the sound working on your laptop. It is not 5.1. It is 4.1 when you have 4 speakers and a sub. One thing I would strongly suggest your doing and actually to everyone with 2.1 through 7.1 speaker systems set up on their computers, is to setup low and high pass filters for them. It is not as easy as all the pages I referred to claim it is with upmixing or with just passing each channel into the filters, but well worth it.

Especially with a system like this laptop you were trying to get working. Those speakers were never meant to handle the frequencies from a full range signal and will overdrive leading to premature failure. I am thinking of creating a post with my asound.conf explaining how to get it all working right, whether it is 2.0 upmixed to 5.1 or if it is just being played channel for channel like 5.1 from a movie, even down mixing 5.1 to 4.0.

I have the upmixing part of my asound.conf complete that includes low and high pass filters. I had to use like three or four different references to get this to work right due to changes in LADSPA not addressed as of late with this. The audio needs to have a format conversion done by a LADSPA plugin before its filter plugins can be applied. Then a conversion needs to happen again in order to pipe it out to the speakers.

This is not exclusive to hardware either, but so people know, I am running a Creative x-fi Fatality Pro Titanium. I have had it working beautifully with Alsa for some time and noticed that pulseaudio wasn't doing what I was expecting it to do on the note of upmixing, like frequency filtering on audio channels. It makes all the speakers sound muddy. This can be addressed with alsa as well.

I am hoping people will find the post I am going to make helpful.

---

### Post by sports.car.guy on 2010-01-17
> **pappfer said:**
> It's a great topic, I had the same problem. I've put model=3stack to my alsa-base.conf file and after that some new fields appeared in my alsamixer and also 5.1 surround sound appered in the sound preferences. There I selected 5.1 surround sound but it only gives sound from my front speakers unless I set "line jack" (subwoofer) and "mic jack" (rear speakers) to line out. So I have to always change them to line out. Why? Is it possible to make it always line out?
[Screenshot]("http://pappfer.se-portal.hu/temp/alsamixer.png")


If you are running pulseaudio like Ubuntu does and Kubuntu does not out of the box, you need to edit /etc/pulse/daemon.conf to get it working. Kubuntu install pulseaudio if you want the easy way out with drawbacks. It does not let you set the levels on individual channels and does not apply any frequency filters to what is coming out of the speakers. It also does have some issues with software at times as well, one being MythTV.

For pulse audio all you need to do is uncomment the line below and change the 2 to a 6 ( The 6 letting pulseaudio know you have 5 satellite speakers and a sub) like i said in /etc/pulse/daemon.conf

; default-sample-channels = 2

 default-sample-channels = 6

This will enable pulseaudio with 5.1 and upmixing.

I am going to be making a post shortly with how to do upmixing with Alsa using ~/asound.rc or in /etc/asound.conf configuration files. It will show how to get upmixing with low and high pass frequency filters working first. I still have to get the high and low pass filters setup for 5.1. This way can work with pulseaudio as well with providing low and high pass filtering.

If you are looking to go the route where your sound is properly sent to your speakers with a crossover in frequencies you will find the post I am making useful regardless if you are using pulse or not.

Here is the link to it.

[http://ubuntuforums.org/showthread.php?p=8678028#post8678028](http://ubuntuforums.org/showthread.php?p=8678028#post8678028)

---

### Post by pappfer on 2010-01-17
Thanks for your reply but it didn't make any difference for me.
I have added model=3stack to my */etc/modprobe.d/alsa-base.conf* file and default-sample-channels = 6 to my */etc/pulse/daemon.conf* file.

Now I see 5.1 output in sound preferences / hardware tab (it's since i've added model=3stack). When I sturt up my notebook it only gives sound from front left and front right. Then i have to always go to terminal/alsamixer and set both *line jack* and *mic jack* to *line out*. After I do this I get sound from all of my speakers but my subwoofer.

So my problems are:
- can't get subwoofer to work
- have to always go to alsamixer everytime i start up my notebook
- have to swap orange (sub and centre) and black (rear speakers) line to work properly (this is not a (big) problem)

Just a note: I was always telling proudly to my friends that Ubuntu is so cooool, my 5.1 was working after I went to sound preferences and just checked a checkbox which said "set mic as output". Everything was working fine, I got sound from all of my speakers without having to edit any files. It was in Jaunty. Now I'm using Karmic form months and I read a lot about it but still I haven't been able to make all my speakers work.

Don't take me wrong, Ubuntu is a great OS, I really love it but I frankly have a feeling that it's getting regressive.
I really think that a notebook which also comes with Ubuntu on it by default should work out of the box. Not mentioning the [load_cycle_bug which seems to come back]("http://ubuntuforums.org/showthread.php?t=1338751") on a notebook which Dell also sells with Ubuntu... I'm still looking the forums, reading, learning but if I can't get over these things I'll have to swithc to either an older Ubuntu or another Linux distro.

---

### Post by rmkimathi on 2010-04-19
My media PC is as follows:
Gigabyte GA-EP45-UD3R Rev1.1, ALC889A  Sound, LinuxMint 8 (helena) same as Ubuntu 9.10, VLC 1.0.5, Yamaha 5.1  Receiver, using optical audio

Two issues are the problem:

Fix  1: Sound preferences > uncheck "enable window and button sounds"  > check mute on "alert volume" > "output volume" to 100%

Fix  2: VLC preferences > show settings simple > Audio > check "use  S/PIF when available" > "Output Type" = ALSA audio output >  Effects uncheck "Volume normalizer" > show settings All > "Audio  output frequency (Hz) = 48000 > "Replay gain mode" = None >  Uncheck "peak protection"

Leave all other settings as default.  The Dolby Digital 5.1 sound now will be flawless on VLC and SMPlayer.  Enjoy and look forward to LinuxMint 9!!

Cheers

---

