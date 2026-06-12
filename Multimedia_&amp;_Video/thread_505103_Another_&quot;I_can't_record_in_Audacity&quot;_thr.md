---
title: "Another &quot;I can't record in Audacity&quot; thread"
date: 2007-07-19
forum: Multimedia &amp; Video
---

### Post by maoglone on 2007-07-19
First off, I'm using a Compaq C500T series, feisty fawn, and just downloaded Audacity. I use it to record a podcast, and use the microphone jack/line in to plug a mixer in. Wasn't a problem in XP or Vista, but I'm getting nothing but an error message that says "Error while opening sound device. Please check the input device settingsl and the project sample rate."

I've installed alsa-oss, turned on everything in the Volume Control but still can't record. How do I set my devices so that this'll work and I'll be able to get the podcast up and running again? Got a show to do tomorrow evening and I can't miss it.

I opened audacity through the terminal and came up with this, too:

> Expression 'SetApproximateSampleRate( pcm, hwParams, sr )' failed in 'src/hostapi/alsa/pa_linux_alsa.c', line: 1108
Expression 'PaAlsaStreamComponent_InitialConfigure( &self->capture, inParams, self->primeBuffers, hwParamsCapture, &realSr )' failed in 'src/hostapi/alsa/pa_linux_alsa.c', line: 1659
Expression 'PaAlsaStream_Configure( stream, inputParameters, outputParameters, sampleRate, framesPerBuffer, &inputLatency, &outputLatency, &hostBufferSizeMode )' failed in 'src/hostapi/alsa/pa_linux_alsa.c', line: 1783
Expression 'SetApproximateSampleRate( pcm, hwParams, sr )' failed in 'src/hostapi/alsa/pa_linux_alsa.c', line: 1108
Expression 'PaAlsaStreamComponent_InitialConfigure( &self->capture, inParams, self->primeBuffers, hwParamsCapture, &realSr )' failed in 'src/hostapi/alsa/pa_linux_alsa.c', line: 1659
Expression 'PaAlsaStream_Configure( stream, inputParameters, outputParameters, sampleRate, framesPerBuffer, &inputLatency, &outputLatency, &hostBufferSizeMode )' failed in 'src/hostapi/alsa/pa_linux_alsa.c', line: 1783
So, what should I do? I'm very new to Ubuntu, and until yesterday wasn't really comfortable with the whole "Terminal" thing... so if you don't mind, please be gentle...

thanks!

---

### Post by ibanez88 on 2007-07-20
I assume you're using the onboard sound card?  Does everything work (sound card input as well as output) as expected in other sound applications or is it just a problem with Audacity?

---

### Post by dabl on 2007-07-20
Audacity is very picky and proprietary about the "output device".  For example, if Firefox is running on my system at the time that I attempt to use Audacity to play back a recording, about half the time Audacity gives me the same error you got.

Funny thing -- once it decides it doesn't have the output device, it won't change its mind, even after I close Firefox or Amarok or whatever seems to have been interfering.  I have to close Audacity and restart, and then it's happy.

So, I advise you to shut down anything that might conceivably have the ability to produce sound, then open Audacity and try it.  :)

---

### Post by maoglone on 2007-07-20
> **ibanez88 said:**
> I assume you're using the onboard sound card?  Does everything work (sound card input as well as output) as expected in other sound applications or is it just a problem with Audacity?

I am using the onboard sound card.  

The output seems to work in all programs, meaning I can play music in rhythmbox, sound recorder will play things, et cetera, but I can't record ANYTHING, no matter what I do.  I'm thinking that it's a hardware configuration problem more than anything else, probably coupled with the fact that the descriptions for the devices between OSS and ALSA are completely unclear, or, at best, incredibly difficult to understand.  Is  it possibly a device mapping problem?  How would I fix this?  Is there a way to figure out what device description is attached to what device (i.e., ALSA front->ext microphone port; ALSA Conexant Analog->output/speakers.  

No matter what I do, though, I'm getting the sound device error whenever I try to record.  It's frustrating.  and I've been working on it for 2 days.   (angry face)

---

### Post by fredj on 2007-07-21
Open the alsa mixer (double click on the speaker icon in the taskbar). Go to the File->Change Device menu.
Make sure that your soundcard (working under Alsa) is selected. Use the Edit->Preferences menu to make
sure that all the mic recording and mic boost controls are present etc.
Open Audacity, go to the Edit->Preferences-AudioIO menu and make sure that Alsa is selected.
Don't run Firefox while you are recording since it tends to grab exclusive access to the audio.

---

### Post by maoglone on 2007-07-21
> **fredj said:**
> Open the alsa mixer (double click on the speaker icon in the taskbar). Go to the File->Change Device menu.
Make sure that your soundcard (working under Alsa) is selected. Use the Edit->Preferences menu to make
sure that all the mic recording and mic boost controls are present etc.
Open Audacity, go to the Edit->Preferences-AudioIO menu and make sure that Alsa is selected.
Don't run Firefox while you are recording since it tends to grab exclusive access to the audio.

I don't have that high-pitched noise anymore, but it still won't record.  How should I set the devices in Audacity?

---

### Post by fredj on 2007-07-21
In Audacity go to Edit->Preferences->Audio I/O and make sure that your soundcard is selected as hw:0 
under Alsa. 
In the audio mixer under record controls make sure that the mic and mic boost are unmuted and selected 
and that a suitable volume level is set.

---

### Post by aysiu on 2007-07-21
I think this may be a bug in Feisty.

I've used Audacity in prior versions of Ubuntu (same computer), and it's worked fine.

I checked my audio settings in Gnome and in Audacity and tried just about every combination I can think of. I still get this error message when I try to playback what I've recorded.

I did [a Google search on the error message](http://www.google.com/search?hl=en&q=%22error+while+opening+sound+device%22+%22please+check+the+output+device+settings+and+the+project+sample+rate%22&btnG=Google+Search) and found no solution.

Should a bug report be filed on this? Or are there people who have successfully recorded and played back in Audacity using Feisty Fawn (7.04)?

---

### Post by maoglone on 2007-07-22
My thinking is that it might be a particular hardware-related problem dealing with the line-in/ext. microphone jack.  Everything else in Ubuntu has worked fine thus far for me; just not this.  Which is huge for me, considering I use a computer for 2 things and recording is 1 of them.  *shrug*

---

### Post by aysiu on 2007-07-22
> **maoglone said:**
> My thinking is that it might be a particular hardware-related problem dealing with the line-in/ext. microphone jack.  Everything else in Ubuntu has worked fine thus far for me; just not this.  Which is huge for me, considering I use a computer for 2 things and recording is 1 of them.  *shrug*
That wouldn't explain my situation, since Audacity has worked fine for me *on the same computer* with previous Ubuntu releases.

---

### Post by dabl on 2007-07-22
> **aysiu said:**
> Or are there people who have successfully recorded and played back in Audacity using Feisty Fawn (7.04)?

Yep, that would be me.  Just finished recording Beethoven's Concerto #5 in D-Flat Major, set of 5 78 rpm records, Columbia label, from the late 1930s.

I'm on an Intel mobo using their HDA SigmaTel system, running 7.04 with the low latency kernel:

```
dabl@ufeisty64:~$ uname -a
Linux ufeisty64 2.6.20-16-lowlatency #2 SMP PREEMPT Thu Jun 7 19:03:17 UTC 2007 x86_64 GNU/Linux
```

So, it's not a universal Feisty bug.  :)

---

### Post by aysiu on 2007-07-22
Thanks, dabl.

Is it possible, then, that it might be a Feisty bug for a particular set of hardware?

---

### Post by dabl on 2007-07-22
I would explore the ALSA setup, maybe install the package alsamixergui, and see if there's something amiss in ALSA.  I think Audacity will work if ALSA is OK.  :)

---

### Post by maoglone on 2007-07-26
Yahtzee.  Got audacity to work using an external mic--really, two mics plugged into a mixer which is then plugged into the ext. mic jack in the computer.  Here's how it seems to work for a Compaq Presario C500 (written for a dummy dunce newb like myself):

Download Audacity & all of the things that the synaptic tells you to (don't forget lame aint mp3 encoder).  
Download aoss.
Set up Volume control--turn on everything & turn everything up.
In Preferences->Sound, activate Int Mic INSTEAD OF Line-in.  Yes, this is completely counter-intuitive.  This is where my stuff was getting screwed up, I think.  
Start audacity from terminal using:

```
aoss audacity
```

Make sure that BOTH the output and input in edit->preferences in audacity are set to OSS.  Audacity *should* record, though I get the impression that Ubuntu works differently for different computers.  I can only vouch for the fact that I now have a recording of myself tapping a microphone and saying "hey" into it.  

This week's podcast should be recorded soon.  *Sweet*

Thanks for the help, y'all.  I appreciate it.

---

### Post by martinquested on 2007-11-17
Well, the solution in maoglone's last post works, sort of.

I can now get sound from an external source recorded on Audacity.  Unfortunately, selecting the software playthrough or play other tracks while recording options cause Audacity to hang.

Also, and this is a more crucial problem: the sound I get recorded is from the built-in mic AND the external source coming through the mic jack.  And neither KMix nor alsamixer seem to have any control over recording levels, nor are they able to disable the built-in mic.  This sounds to me like the driver isn't quite there yet with my sound card (MCP51, aka NVidia something or other, in a Compaq Presario V6030us / V6000 series).

Any thoughts anyone?

---

### Post by OldGrey on 2007-11-18
I used Audacity in Fiesty having installed alsa-oss and started Audacity using "aoss audacity". It also worked when I upgraded from Fiesty to Gutsy, but having recently performed a clean install to sort out compiz fusion I cannot get Audacity to work under any circumstances.

---

