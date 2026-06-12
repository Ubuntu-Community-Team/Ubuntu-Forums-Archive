---
title: "Ableton Live 8.11"
date: 2010-09-10
forum: Multimedia Software
---

### Post by Vigh on 2010-09-10
Hi, just thought I would let you guys know out there, I have managed to get Ableton Live 8.11 working to GOLD/PLATNIUM standard. 

DO NOT PIRATE SOFTWARE IT IS ILLEGAL- I PAID FULL PRICE FOR MY SOFTWARE PACKAGE- DO NOT ATTEMPT TO INSTALL A CRACKED VERSION IT WILL NOT WORK!

In order to successfully install you need to set up winetricks- [http://wiki.winehq.org/winetricks](http://wiki.winehq.org/winetricks)
enter this in terminal after installing wine-tricks 

env WINEPREFIX=~/.winetest winetricks mfc40
env WINEPREFIX=~/.winetest winetricks vcrun2008

need to copy 3 .dll files to wine/system32 msvcp90, msvcr90 and mfc90

dll files must look exactly like this- MSVCP90.DLL MSVCR90.DLL mfc90.dll

once installed- browse c: in wine
up top click make bookmark for the folder
download offline authorization file
open with other application
custom command
browse to ableton executable
click ok
ableton should now be authorized

"SOFTWARE"
Setup- maverick-35-22
Wine 1.2-stable
Ableton Live 8.11
ALSA-1.0.23 with pulse-audio
jackd1 ONLY! jackd2 is broken at the moment.
wineasio-0.75
audacity-1.2.6- anything later doesn't work with jack 

"HARDWARE"
XIOSYNTH- As primary sound-card.
TOSHIBA M800 Portege- Intel Graphics, 4GB RAM, 2.4Ghz CORE 2 DUO
ANALOG FACTORY EXPERIENCE CME MIDI-CONTROLLER

Wine-settings are let window manager take control of window. Hardware acceleration OFF. You don't need it for Ableton and it runs alot smoother and faster without it on. Audio has ALSA and jackd both ticked.

Requirements- A screen resolution of 1280 x 960 or greater, otherwise the bottom bit of the program gets cut off. You can solve this and use lower resolutions by unticking window manager control, but then Ableton will always be on top of screen.

What works?
AUDIO
MIDI
VST
EXTERNAL AUDIO EDITOR- Audacity
SAVING PROJECTS

My MIDI-controller is working perfectly with ALSA and I get smooth clear sound output from Ableton. 

Another thing I did was add the dynamic link library into wine config- msvcr90

AUDIO EXPORT- Doesn't work due to not being able to run wine as sudo user.

You can render your finished audio production by routing the audio through jackd to audacity and record directly in audacity. The sound frequency resolution must be set at 48000Hz. The highest value for frames must be set in jackd and then compensated for with driver error compensation in ableton to 0ms, sound will be clear then. The other option of course is to run RT-Kernel.

Also installed quick-time in wine, not sure if this helped or not but working fantastic now.

Turn multicore processing off. To set up external editor/vst select /usr/bin/audacity and your vst folder respectively. Use another MIDI-controller, not the Novation XIO-SYNTHs MIDI, will glitch if you use XIO-synth audio as well as MIDI at the same time.

NOTE-VSTs MUST BE INSTALLED INTO THE C: /.WINE DIRECTORY, OTHERWISE VSTs WILL NOT BE DETECTED PROPERLY IF AT ALL

---

### Post by Vigh on 2010-09-10
Working to a satisfactory level. Of note- Native Instruments Audio Kontrol 1 soundcard works with some tweaking.

*AUDIO-KONTROL-1 appears to crash audacity
*NOVATION XIO-SYNTH sound module is class compliant, inputs seem to work on the XIO-SYNTH

VSTs may work or not work- 

Of note-
Arturia VSTs work but with graphical display issues, sound is perfect but it can be tricky working with the VST as the background goes completely black on linux.
NI VSTs- namely Komplete 5 All VSTs work perfectly.
Other VSTs to be tested.

Working on RT-Kernel now, runs smoother, less latency, zero x-runs when configured properly in JACK. Need to render at high resolutions and then convert to standard playback format from there.

---

### Post by Vigh on 2010-09-13
SOUNDCARD = Novation Xiosynth

ADD TO /etc/security/limits.conf
@audio   -  rtprio     99
@audio   -  memlock    unlimited
@audio   -  nice      -15

My current JACK-settings on Maverick-Kernel

Realtime - Ticked
Unlock Memory- TIcked
Force 16-bit- Ticked

Priority- 15
Frames/Period- 2048
Sample Rate- 48Khz
Periods/Buffer- 5
Port Max- 512
Timeout- 8000ms
Interface- hw:1
Dither- Triangular
Audio- Duplex

Rest are set to defaults.

0 Driver Error Compensation in Ableton.

---

### Post by Rasa1111 on 2010-09-13
wow niiice!
Ableton (and MixMeister) are the only things I wish I could run on my Ubuntu,
Maybe Ableton is a go now! woot! 

 MixMeister would be really sweet to use on it also. 

I stopped using both of them because I use only Ubuntu now. 

 Niice work! Thanks! <3

---

### Post by Vigh on 2010-09-14
Yeah its definately at a workable level now, i've already produced a couple of tracks on the ubuntu system, unfortunately though, there are some drawbacks, skype drops-out occasionally on the xio-synth as a soundcard. Trying to figure out at the moment how to have 2 sound-cards running at the same time, 1 for skype- the onboard, the xiosynth for mixxx and ableton. Crashed the computer in the process! LoL! But its all a big learning curve, I really think that Ubuntu and linux is really turning into a good alternative to mainstream operating systems.

ha ha so easy!!! skype works perfect now and so does ableton!!! just have to go into pulseaudio volume controls and set skype to use onboard sound as default soundcard

skype = onboard soundcard
everything else = usb soundcard (aka novation xio)

upcoming tests- Ableton 8.15

---

### Post by Vigh on 2010-09-14
Live 8.15- working with JACKD1 only

---

### Post by Vigh on 2010-09-17
Appears to be an internal error regression in wine1.2, wine 1.3dev should fix this. Testing now.

NO WINE REGRESSION! JACKD2 is broken.

---

### Post by Rasa1111 on 2010-09-17
hey, what about mixmeister?
ever have any luck with that?

---

### Post by Vigh on 2010-09-17
whats mixmeister? 

NOTE- jackd with pulseaudio support appears to break jackd, installed latest version of jackd, seeing if this helps

LATEST VERSION OF JACKD, JACKD2 IS BROKEN, ONLY USE JACKD1- running wine1.2 working perfectly with JACKD1

temporary fix- remove jackd2 from synaptic if running maverick kernel

---

### Post by Rasa1111 on 2010-09-17
it's a siik program. 
[http://www.mixmeister.com/](http://www.mixmeister.com/)

---

### Post by Vigh on 2010-09-17
had a look at the website, looks like a cool software package, unfortunately I do not own the software so I can't try to get it to work on wine for you, I presume it would be a similar process to Ableton

---

### Post by kimyo on 2011-02-05
not being able to record within ableton is a real joykiller.

even tho ableton seems to create folders with spaces in their names just fine, i wonder if the record problem could be related to spaces in the filenames?

or, do you guys think this is a permissions issue?

i'm a happy, paying ableton user.  i'd really love to use it on wine/unbuntu instead of windows.

---

### Post by xpertvision on 2011-04-06
any updates? ableton still works in ubuntu?

i have ableton 8.2.2 and ubuntu 10.10

---

