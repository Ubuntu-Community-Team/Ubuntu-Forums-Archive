---
title: "Bizarre E-mu 0404 PCI/ALSA playback issue - sound files playing too fast?!"
date: 2010-11-17
forum: Multimedia Software
---

### Post by robcowley on 2010-11-17
Hi all,

I am new to this forum and have recently switched to Ubuntu.  The OS installed without a hitch and was able to get video card, wireless internet installed with relative ease.  However, I have encountered a problem installing my E-mu 0404 PCI sound card via the ALSA packages in Synaptic.

```
04:03.0 Multimedia audio controller [0401]: Creative Labs SB0400 Audigy2 Value [1102:0008]
```

As you can see once the packages were installed the OS could see the hardware ok, but when I tried playing a standard MP3 file (16 bit, 44.1khz, 192kbps) in Totem it started playing the file back around 15-20% faster than normal?  To me it sounds as if the software is playing the audio back at higher sample rate than 44.1khz hence the faster speed, though I'm not 100% on that.

The next thing I tried was playing the same file back in VLC and it was exactly the same (15-20% too fast), but this time it was horrible and glitchy as well, almost as if the audio buffer size was set to small.

The same thing happened when I tried playing back some flac and wav files (all 16 bit, 44.1khz) also.

I have searched google (and read the comprehensive sound card guide on this forum) and read several forums, guides, etc. for anybody posting the same issue with this particular card but could find nothing. From all reports I've read this card should work fine under ALSA.

For the record I'm using Ubuntu 10.10 64bit kernel running on a Dell Dimension 9200 (Intel Core2Duo E6400 2.13ghz) with 2GB RAM.

If anybody has experienced this same problem and/or can offer any pointers I would be extremely grateful as my Ubuntu experience up-to-now has been great!

Thanks,

Rob

---

### Post by robcowley on 2010-11-17
UPDATE

There was something I forgot to test, and it has made the issue all the more bizarre.

Youtube videos are playing back too fast as well!

The strange thing is the video and audio are still perfectly in sync so the video playback must be fast also.

Anybody else have these same problems?  Thanks

---

### Post by cchhrriiss121212 on 2010-11-17
> However, I have encountered a problem installing my E-mu 0404 PCI sound card via the ALSA packages in Synaptic.
What is it you installed from synaptic? Normally you should not need to install anything extra to get your sound working (Ubuntu ships with ALSA installed). Did you try using the card before installing anything?

---

### Post by robcowley on 2010-11-17
Hi, thanks for the reply.

I didn't try playing anything right after the clean install of Ubuntu as no hardware was listed under System > Admin > Sound > Hardware so I assumed no hardware had been detected.  

What little previous experience I do have of Ubuntu was on a much older Dell machine which had on-board sound (AC-97 I think) and the on-board hardware was detected automatically and worked fine without any further intervention needed.  As a result I was under the assumption that this would be the case for the E-mu 0404 but turns out it's not. The PC I'm using now does have on-board sound but this is disabled in the BIOS.

In Synaptic I just searched under alsa and installed alsa-base and several other packages it said were required as well.  Would that be the correct package to install (apologies as I'm not a very experienced Linux user)?

Thanks again.

Nice avatar BTW, is it George Clinton?

---

### Post by cchhrriiss121212 on 2010-11-17
> Would that be the correct package to install (apologies as I'm not a very experienced Linux user)?
It's not that it is the wrong package, it's just that it should have already been installed by default (I assume you performed a regular install). Perhaps you just updated alsa-base?

In any case the issue seems to have a simple fix here:
[http://ubuntuforums.org/showpost.php?p=8576567&postcount=2](http://ubuntuforums.org/showpost.php?p=8576567&postcount=2)

P.S. Feel free to ask any questions you like on the forums, that is what they are here for. There is also plenty of great info in older threads so do a quick search and you may find an answer (i.e. in the link above).

---

### Post by robcowley on 2010-11-18
Thanks for this, I'd trawled google and read as many different threads a I could find but this one seems to have evaded me.

Anyway, problem solved and at least it confirms what I put in my original post re: sample rate.

Cheers!

---

### Post by Clockmender on 2010-11-18
Hi All

Having just torn out what little hair I had left with my Windows XP machine giving me grief again. I am at the point where I should change to Ubuntu - Like my Vaio laptop. However, I have an E-MU 0404 sound card, Studiologic TMK88 keyboard connected with midi and want to play music using the sound card, keyboard and some decent music package (like Reason from Propellerheads for example) Is it safe to go ahead and install Ubuntu or will I loose all capability to tinkle on the old piano keys?

---

### Post by cchhrriiss121212 on 2010-11-18
Hi Clockmender
As you can see from this thread, the card you have is functional (providing you set the sample rate) and MIDI should be no problem. You should first take a look at LMMS which is very easy to use but a bit basic. If you want to dive in at the deep end then look at what is in the Ubuntu Studio package which you can download from software center either as a big bundle or separately.

On linux there is no monolithic DAW type packages like you get with Mac/Windows (LMMS is the exception to the rule). Instead you have a modular system with different apps for different uses which can all work together through the jackd sound server. This means you have more freedom to send your audio where you like, but it also means it is fiddly to set up. 

If you just want to start playing a few synths, then get jack installed and play around with some of these:
Phasex
Zynaddsubfx
Bristol
AMS
Qsynth (loads lv2 soundfonts)

Then if you want to record look into Qtractor.

---

### Post by Clockmender on 2010-12-12
> **cchhrriiss121212 said:**
> Hi Clockmender
As you can see from this thread, the card you have is functional (providing you set the sample rate) and MIDI should be no problem. You should first take a look at LMMS which is very easy to use but a bit basic. If you want to dive in at the deep end then look at what is in the Ubuntu Studio package which you can download from software center either as a big bundle or separately.

On linux there is no monolithic DAW type packages like you get with Mac/Windows (LMMS is the exception to the rule). Instead you have a modular system with different apps for different uses which can all work together through the jackd sound server. This means you have more freedom to send your audio where you like, but it also means it is fiddly to set up. 

If you just want to start playing a few synths, then get jack installed and play around with some of these:
Phasex
Zynaddsubfx
Bristol
AMS
Qsynth (loads lv2 soundfonts)

Then if you want to record look into Qtractor.

OK have downloaded and installed LMMS but I still have no response from my keyboard and when ever I move a sub window in LMMS, my PC locks and the screen goes blank requiring a reboot to get it going again! what  should I try next?

---

### Post by cchhrriiss121212 on 2010-12-12
> what  should I try next?
I'm no expert on LMMS, but I can help you with jack if you like. First open alsamixer from a terminal and check your volume levels are not muted, also check the sample rate is 44.1kHz.

Now install jack and a synth like phasex from your preferred package manager. Start jack using the entry you should see under sound and video in the application menu. Use the setup window to select your emu 0404 as the interface. Then press OK, then the start button. Now open up your synth. 

Jack requires you to connect your audio and MIDI chain manually. Check the connection window to see your available ports, audio is under the audio tab, MIDI is under the ALSA tab. Connect the synth to your system playback under audio, and connect your MIDI port to the synth under ALSA.

There is also a program called patchage that I recommend you use. It does the same job as the jack connection window but is much easier to use. Patchage shows audio as blue boxes and MIDI as green boxes.

---

### Post by Clockmender on 2010-12-13
OK have loaded Jack and Phasex - machine now hangs every time I try to start Jack - not good perhaps I've done something wrong but cannot see what. How do you tell the system that you have a MIDI keybpard attached? Patchage shows Audigy MPU-401 (UART) and Audigy MPU-401 #2 (twice) and Midi Through Port 0 (again twice) and Emu10k1 Port0,1,2,3 under Emu10k1 Wave Table in green, which is my keyboard (if any) and where should I connect it to? Bizarely, I can play LMMS with my PC keyboard, with difficulty as one row of keys is part of the white notes and one part of the black notes, but the latency is good, just wish I could get the MIDI keyboard to do the same.

Thanks for help so far
PS should I reload Jack and see what happens?

---

### Post by cchhrriiss121212 on 2010-12-13
> machine now hangs every time I try to start Jack
I'm not sure what could be causing this. Do you mean it hangs when clicking on the menu entry, or when pressing the start button? Try opening qjackctl from a terminal, it may tell you any errors.

Could you post the result of aplay -l from a terminal? It looks like you have more than one soundcard attatched, is that right?

---

### Post by Clockmender on 2010-12-13
Results of aplay -l:
**** List of PLAYBACK Hardware Devices ****
card 0: EMU0404 [E-mu 0404b PCI [MAEM8852]], device 0: emu10k1 [ADC Capture/Standard PCM Playback]
  Subdevices: 32/32
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
  Subdevice #8: subdevice #8
  Subdevice #9: subdevice #9
  Subdevice #10: subdevice #10
  Subdevice #11: subdevice #11
  Subdevice #12: subdevice #12
  Subdevice #13: subdevice #13
  Subdevice #14: subdevice #14
  Subdevice #15: subdevice #15
  Subdevice #16: subdevice #16
  Subdevice #17: subdevice #17
  Subdevice #18: subdevice #18
  Subdevice #19: subdevice #19
  Subdevice #20: subdevice #20
  Subdevice #21: subdevice #21
  Subdevice #22: subdevice #22
  Subdevice #23: subdevice #23
  Subdevice #24: subdevice #24
  Subdevice #25: subdevice #25
  Subdevice #26: subdevice #26
  Subdevice #27: subdevice #27
  Subdevice #28: subdevice #28
  Subdevice #29: subdevice #29
  Subdevice #30: subdevice #30
  Subdevice #31: subdevice #31
card 0: EMU0404 [E-mu 0404b PCI [MAEM8852]], device 2: emu10k1 efx [Multichannel Capture/PT Playback]
  Subdevices: 8/8
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
card 0: EMU0404 [E-mu 0404b PCI [MAEM8852]], device 3: emu10k1 [Multichannel Playback]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

No errors reported by Jack Control when I opened it but it hung the machine when I tried to start it.....

Update - second attempt to start it worked.....

But there are no midi clients on the Midi tab...


Output from the ALSA tab...file:///home/alan/Desktop/Screenshot.png

---

### Post by cchhrriiss121212 on 2010-12-13
> But there are no midi clients on the Midi tab...
Thats because most MIDI clients will show up in the ALSA tab (confusing I know). This is because there is a jack MIDI driver and an ALSA MIDI driver. It is easier if you just use patchage, connect your green box from the emu to the green box from phasex.

---

### Post by Clockmender on 2010-12-13
[IMG]///home/alan/Desktop/Screenshot.png[/IMG]

How do I get this image in here??????????

---

### Post by Clockmender on 2010-12-13
Ok have connected Audigy MPU-401 UART to the Phasex Midi in and when I press a key it changes the patch!!!!!

Same happens with Horgand......

and Aeolus......

This is not my best day ever,,

Update - Connecting Virtual Keyboard to the Phasex works in that it produces notes when you "press" a key with the mouse - this is progress but not quite what I need yet.

---

### Post by Clockmender on 2010-12-13
OK so now I have some progress. I have installed Virtual Midi Piano (VMP) and KMidimon - yes all by myself!! I have connected them with Patchage and pressed three C keys on VMP and get this output in KMidimon:

Column headings are:
Ticks, Time, Source, Event Kind, Channel, Data1, Data2, Data3

3321,1373.7317,VMPK Output:0,1,Note on,C4:60,100,
3325,1373.7701,VMPK Output:0,1,Note off,C4:60,100,
4750,1376.7084,VMPK Output:0,1,Note on,C5:72,100,
4778,1376.7701,VMPK Output:0,1,Note off,C5:72,100,
6324,1379.9885,VMPK Output:0,1,Note on,C3:48,100,
6349,1380.0460,VMPK Output:0,1,Note off,C3:48,100,

Then I pressed tha same keys on my TTMK88 Keyboard and got this:

8887,1385.3270,E-mu 0404b PCI [MAEM8852]:0,1,Program change,Halo Pad:94,,
8958,1385.4801,E-mu 0404b PCI [MAEM8852]:0,1,Program change,Halo Pad:94,,
9317,1386.2211,E-mu 0404b PCI [MAEM8852]:0,1,Program change,Oboe:68,,
9373,1386.3401,E-mu 0404b PCI [MAEM8852]:0,1,Program change,Oboe:68,,
9899,1387.4324,E-mu 0404b PCI [MAEM8852]:0,1,Program change,Piccolo:72,,
9953,1387.5450,E-mu 0404b PCI [MAEM8852]:0,1,Program change,Fantasia:88,,

So now I know that my keyboard is working but sending programm changes to the monitor NOT key strokes - can anyone help with this problem????? Do I need some firmware or intermediate program to translate what the keyboard is sending into what the synth programmes expect?

Thanks again

Clock

---

### Post by cchhrriiss121212 on 2010-12-13
According to a comment left on [here]("https://bugtrack.alsa-project.org/wiki/wikka.php?wakka=emu&show_comments=1"), functional MIDI requires that you set the sample rate to 48kHz. You can do that with alsamixer as discussed earlier on this thread.

---

### Post by Clockmender on 2010-12-14
Chris my friend you are a genius

So if I set clock rate to 48K, the midi works correctly in Phasex, etc, If I then set the clock rate to 44.1K and disconnect from Jack in Patchage, Rythmbox plays back at the correct speed - I can live with this. Thanks a bunch for your help.

Happy Xmas
Clock

Now if I can only stop my screen from hanging and find a decent piano synth and get LMMS working and cure world poverty I'll be happy..........

OK getting back to LMMS, There is no mention of LMMS in the Jack Connections, either in MIDI or ALSA tabs and on the LMMS Settings/Midi one can select ALSA for the MIDI but it does not show a device other than default, How do you get the MIDI from the soundcard to talk to LMMS. When you open Patchage, LMMS Midi in is coloured RED and cannot be connected to anything, does anyone know what I am doing wrong and does anyone know of a great sounding Piano app to connect through Patchage?


Scrub that I just found this

[http://ubuntuforums.org/archive/index.php/t-1377518.html](http://ubuntuforums.org/archive/index.php/t-1377518.html)

LMMS now works with my keyboard!!!!! Basically you have to connect EACH track to the Midi keyboard, in my case to the MPU-401 UART, however if you connect lots of them, your CPU could become overloaded

Cheers Clock - would still like a piano though.......

Found these SoundFonts here: [http://freesoundvault.com/category/piano-organ/](http://freesoundvault.com/category/piano-organ/) But they are not as good as the Pianos in Reason (Yes I know I'm picky) but it's better than fighting with Wind'ohs all the time, which as we all know is utter pants. If anyone has found others...please let me know here.


All sorted now see [http://ubuntuforums.org/showthread.php?p=10249260#post10249260](http://ubuntuforums.org/showthread.php?p=10249260#post10249260) if this is of help yo you!

---

