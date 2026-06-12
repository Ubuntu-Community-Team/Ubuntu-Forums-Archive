---
title: "No analogue input m-audio 2496 Ubuntu 10"
date: 2010-05-15
forum: Multimedia Software
---

### Post by mikerophone on 2010-05-15
Hey, guys, I'm struggling to get my card recording - at the moment analogue inputs aren't showing up (though outputs are).

M-audio Audiophile 2496
Ubuntu Studio 10

History - started with only digital ins and outs,
altered the file ICE1712.conf, adding 
[I]         slave.format S32_LE 
         slave.channels 10[/I]
to the "front" section, as advised by a previous thread.
That gave me analogue outs only.
I've removed Pulseaudio ('cause I did last time and everything was fine).

Any help would be much appreciated! Thanks.

---

### Post by lidex on 2010-05-17
Using a Terminal="Applications->Accessories->Terminal"
Open this file for editing:
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
```
Insert this line at the bottom:
```
 options snd-ice1712 model=audiophile 
```
Save. Close. Reboot. Check your levels in alsamixer.
```
 alsamixer 
```
Press <F6> to select the correct soundcard.
Press <F3> to show playback levels. <F4> selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.
Go to "System ->Preferences ->Sound" and make sure the correct soundcard is default.

BTW: Do you have the Envy24 mixer in use? If not install the 'alsa-tools-gui' package.

---

### Post by ezda on 2010-06-12
Hey lidex, thanks a lot for your detailed response. Since I switched to Ubuntu (from Xubuntu) for the 10.04 release, my card stopped working out of the box, but you've remedied the situation quite throroughly. Thanks again!

---

### Post by Rocket J Squirrel on 2010-11-30
Hi Lidex, thanks for looking into this. Sorry if I sound a but churlish, I was frustrated. 

Okay, after the changes, I can select a Multichannel Input/Output profile option. Sound Preferences shows signal on the Input page (signal generator applying test tone). 

ALSAMIXER's controls seem to have no effect on the little level meter in Sound Preferences. It's unclear which of the Capture controls are meant to adjust the analog input level, as the labeling is not clear -- I'd have expected one of the two ADC controls to apply, but neither do anything to the displayed level in Sound Preferences, while adjusting the output level of the signal generator does, so I know I am seeing signal. 

Envy24's Analog Volume shows ADC 0 and ADC 1, sliding either does change ADC and ADC 1 in ALSAMIXER, but again, no level change is reflected to the input level indicator in Sound Preferences. 

Does this sound like expected behavior?

Stepping back a bit, my goal his is to run some of the freeware or cheapware audio testing suites under WINE here. I've got a few installed, RealRTA, RightMark, ARTA, and a few others. So far, none of them seem to find the sound card. I can't view spectrum of input signal, and all of them claim that there is no output sound card to be found. I may have to switch the computer to Windows if I can't get them to work. 

Can you recommend a Linux/Ubuntu program that will let me record and playback from the card so I can determine if even Ubuntu is happy with it?

---

### Post by Rocket J Squirrel on 2010-12-02
Update:

I installed Audacity and it find, records from, and plays back through the Audiophile 2496 card's analog i/o's. 

So the issue here is that the Windows audio test suites I was hoping would run under WINE just ain't gonna be happy. 

**Soundcard Scope:** "No sounds device for playback found! Signalgenerator will not work!" (nor does it display the input signal)

**RightMark Audio Analyzer:** "Cannot open specified audio device for playback." Soundcard Ping reports that Playback failed, Recording OK. RightMark has dropdown boxes to select Playback/recording devices, but only "[MME] Wave mapper" appears in each case. 

**Arta:** "Output device absent or unsupported." Dropdown boxes to select input and output devices empty. 

**VA (Virtual Analyzer):** "Cannot detect a valid input device", "Cannot detect a valid output device." Dropdown boxes to select devices empty here, too. 

**TrueRTA:** Cannot see input signal, does not generate output signal.

Well darn. I was hoping to make this new shop machine a Linux one, but unless someone has some kind of swell idea, I gotta switch it to Windows.

---

### Post by Rocket J Squirrel on 2010-12-03
Anyone? I've got a Windows XP disk in my hand and I'm ready to pull the trigger . . .

---

### Post by cchhrriiss121212 on 2010-12-03
If all you want to run is Windows audio programs then just use Windows, it is much simpler than configuring WINE. If you expect Ubuntu to be a free version of Windows, then you will be disappointed. To use a food based analogy, what you are doing is going to an Italian restaurant and request they cook you some Chinese food.

What I would recommend is that you try the FOSS available for Ubuntu, which will be at least as good as what you have listed above. If you would like to use some Linux audio programs, then explain what you need to do and I can recommend you some. 

Regarding the Sound Preferences issue, yes that is normal. Sound preferences is a pulse configuration program, and alsamixer is ALSA configuration, Ubuntu use both pulse and ALSA together. 
If you think Ubuntu's audio is a mess, then I would agree with you.

---

### Post by Rocket J Squirrel on 2010-12-03
Hey cchhrriiss121212,

I normally do my audio testing with an Audio Precision System One -- a  dedicated audio (Windows) test box/software package. But that box is  going to another facility so I'm trying to tinker up rudimentary test  functions on a PC using a sound card. 

Running Windows audio test programs under Wine . . . hey, no harm in trying, first!

BUT if there are good FOSS programs then I'll happily check them out before changing the box over to Windows. 

The audio software I'm looking for will be used to generate input test signals for preamps and power amps, and measure things like:

1. Gain, in dB. This requires software that has calibrate functions so it know what signal levels the sound card is outputting and reading. 

2. Measured signal level in volts or watts (ref: 8-ohm load).

3. Frequency response sweeps. 

4. Drive power amps to clipping by stepping the generator amplitude from a low level to a high level and graph output level (in Watts vs thd). 

5. Real time spectrum analyzer and oscilloscope functions with access to generator level. If the software won't do (4, above) then I can at least increase the signal levels into power amps until I see clipping.  

I'm not even sure if all these handy functions can be found in cheap or free Windows software! I'm sure gonna miss my System One.

---

### Post by cchhrriiss121212 on 2010-12-03
I don't know of programs to handle that kind of testing on Linux, though envy24control has basic level in/out monitoring. As this is an Ubuntu Studio thread I assumed you were using music oriented stuff. You might find a few tools that can do this, but I would guess they won't be as user friendly as the Windows counterparts.

You should check the [WINE database]("http://www.winehq.org/") for these programs, but the results I found for these programs were [quite old]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=12430"), and WINE functionality goes up and down every 6 months. Good luck.

---

### Post by Rocket J Squirrel on 2010-12-03
Right on. Sorry about hijacking the thread -- I think I got it confused with the one I started over at [http://ubuntuforums.org/showthread.php?t=1633726](http://ubuntuforums.org/showthread.php?t=1633726) -- on that on I got referred to this one. Didn't notice the change.

Thanks for looking into this!

---

### Post by Kylotan on 2010-12-05
Hi, I'm having the same problem and thought I'd post here rather than creating a new thread.

I had to add the **options snd-ice1712 model=audiophile** line to get *any* sound at all, but it only exposes the analogue outputs in the Sound Preferences dialog, not the inputs. I also added the 'slave.format S32_LE' and 'slave.channels 10' lines recommended elsewhere.

Alsamixer shows DAC, DAC1, H/W Multi, and H/W Multi 1 on the capture page, but nothing shows up in Sound Preferences - is this some sort of mismatch between the Alsa layer and the PulseAudio layer?

Any ideas what else I could try?

---

### Post by lidex on 2010-12-05
> **Kylotan said:**
> Hi, I'm having the same problem and thought I'd post here rather than creating a new thread.

I had to add the **options snd-ice1712 model=audiophile** line to get *any* sound at all, but it only exposes the analogue outputs in the Sound Preferences dialog, not the inputs. I also added the 'slave.format S32_LE' and 'slave.channels 10' lines recommended elsewhere.

Alsamixer shows DAC, DAC1, H/W Multi, and H/W Multi 1 on the capture page, but nothing shows up in Sound Preferences - is this some sort of mismatch between the Alsa layer and the PulseAudio layer?

Any ideas what else I could try?
That is the same issue as OP, unfortunately that person hasn't followed up here. Perhaps you can contact the OP to see if issue was resolved. This is the same card?

---

### Post by Kylotan on 2010-12-06
It's the M-Audio Audiophile 2496, yeah. I've sent the OP a message but no reply as of yet.

---

