---
title: "mp3, game sounds and system sounds"
date: 2006-02-06
forum: Multimedia &amp; Video
---

### Post by svar on 2006-02-06
then I play mp3 and starts a game (pingues exs), game sound is off and so is system sound. If I close xmms and start a game  get game sounds, but if I then starts xmms it tells me the soundcard is bussy.

Isent it possible to get sound fron 2 or more sources whid 1 sound card in linux? :???:

---

### Post by joft on 2006-02-06
Hi,

[QUOTE=svar]Isent it possible to get sound fron 2 or more sources whid 1 sound card in linux? :???:[/QUOTE]

The problem here is mixing of two or more sources. And most cheap soundcards/chips just support one (by hardware).

- **First possibility**:  **ONLY** use sound applications which output to ALSA and support ALSA's dmix plugin. Then your sound will get mixed by the ALSA library.
Note: Some apps don't support dmix, some even don't support ALSA: e.g.: apps that only support OSS (skype, ts2, some games, audacity).

- **Second possibility**: Use a sound server (today every linux distro does this): esd (GNOME), artsd (KDE). Now configure all apps to output to your sound server.
Note: Some apps don't support sound servers, some only support some of them, but most at least support artsd and esd. For OSS apps you will have to use wrappers (artsdsp, esddsp) which reroute all sound to your sound server.

Ubuntu's default configuration is AFAIK to use ALSA with enabled dmix and esd, while esd is using ALSA to output its sound.

- **Third possibility**: Use/buy a real soundcard with a real soundchip which does mixing in hardware.

.........

- **Another possibility**, if you use many OSS-only apps/games (Skype, ET, TS2, audacity) and apps which support JACK (another sound server) you could try my HOWTO:

[http://www.ubuntuforums.org/showpost.php?p=695990&postcount=6](http://www.ubuntuforums.org/showpost.php?p=695990&postcount=6)

---

### Post by kudu on 2006-02-06
Hi, sorry to butt in but I have a question along similar lines.

I'm using Cedega to run WinSPMBT which I have managed to configure to run almost perfectly. However, sound is not working properly. Apparently I'm only getting one sound channel playback and therefore sound is choppy at best. The game rquires multiple channels...I think 21.

The default Multimedia Systems Selector settings are ESD default sink output
and OSS default source input. On the whole sound seems to work fine, just this particular game doesn't work. Should I configure the Multimedia Selector for ALSA ? Not sure how to properly go about it. I've fooled with it in the past without really knowing what I was doing and didn't seem to change anything other than break the TEST button.

I have a Sound Blaster Live! card. Do I need an upgrade ? I'd really like to get this game working 100%.

Appreciate any advice.

kudu...out

---

### Post by joft on 2006-02-06
[QUOTE=kudu]
The default Multimedia Systems Selector settings are ESD default sink output
and OSS default source input. On the whole sound seems to work fine, just this particular game doesn't work. Should I configure the Multimedia Selector for ALSA ? Not sure how to properly go about it. I've fooled with it in the past without really knowing what I was doing and didn't seem to change anything other than break the TEST button.

I have a Sound Blaster Live! card. Do I need an upgrade ? I'd really like to get this game working 100%.[/QUOTE]

Due to the fact that the SBLive! does mixing in hardware, IMO you should definitly switch to ALSA (Multimedia Systems Selector) for input and output. (With hardware mixing you haven't the need for sound server or something else.)

AFAIK the Multimedia Systems Selector does only configure gstreamer. Cedega doesn't use gstreamer .... so ... You configured cedega to use ALSA, too, right? Then it's a good question, why sound is choppy ...

Did you ask Transgaming/Cedega staff about it? Perhaps it's a problem with this specific game ....

---

### Post by svar on 2006-02-06
It is amsn and xmms/bmp I have problemes whid get sound from bouth at a time. is it possible?

I have a ac97 soundcard on board, what cards do hardware mixing and do I get rid of all problems whid a better sound card?

---

### Post by kudu on 2006-02-06
[QUOTE=joft]Due to the fact that the SBLive! does mixing in hardware, IMO you should definitly switch to ALSA (Multimedia Systems Selector) for input and output. (With hardware mixing you haven't the need for sound server or something else.)

AFAIK the Multimedia Systems Selector does only configure gstreamer. Cedega doesn't use gstreamer .... so ... You configured cedega to use ALSA, too, right? Then it's a good question, why sound is choppy ...

Did you ask Transgaming/Cedega staff about it? Perhaps it's a problem with this specific game ....[/QUOTE]

OK...I'll try setting ALSA as default in Multimedia Selector and see if it works better. Is there anything else I nered to do to set it up properly ? I read a HowTo which speaks of creating an asound.conf file and starting ALSA manually at command line. Does the Multimedia Selector handle all that automatically, or what ?

I believe it has to do with this particular programs use of DirectShow for sound FX and necessity of multiple sound channels and may or may not have anything to do with Cedega support of DirectShow. I did post a support request with TransGaming but they are very slow. Also they don't support this type of wargame so much as FPS's etc. According to SP Camo the fact I get choppy sound implies Cedega does have DirectShow support. They think choppy sound due to only one channel used instead of multiple needed. Each sound is a single COM object.

Thanks for help. I'll let you know if ALSA settings correct the problem.

Regards,
kudu

---

### Post by joft on 2006-02-06
[QUOTE=svar]It is amsn and xmms/bmp I have problemes whid get sound from bouth at a time. is it possible?[/QUOTE]

Well, xmms does support ALSA/dmix .
bmp does support ALSA - don't know if it "supports" dmix .
amsn - don't know ... is there any setting, which tell you something about sound output? If it supports OSS only, you could use esddsp to wrap it and reroute it to esd (run by GNOME).

[QUOTE=svar]I have a ac97 soundcard on board, what cards do hardware mixing and do I get rid of all problems whid a better sound card?[/QUOTE]

I know that SBLive! supports hardware mixing. Look at ALSA soundcard matrix and search for "(3)", which means it supports it.

---

### Post by kudu on 2006-02-06
I set ALSA as default sink output and input in Multimedia Systems Selector and get the following error message when I try the test button for default source input:  Failed to construct test pipeline for 'ALSA - Advanced Linux Sound Architecture'

I rebooted after resetting to ALSA but get this failed message only for the source input test. Any ideas ? How do I fix this ?

kudu

---

### Post by svar on 2006-02-06
[QUOTE=joft]Well, xmms does support ALSA/dmix .
bmp does support ALSA - don't know if it "supports" dmix .
amsn - don't know ... is there any setting, which tell you something about sound output? If it supports OSS only, you could use esddsp to wrap it and reroute it to esd (run by GNOME).
[/QUOTE]

[here]("http://home.online.no/~svar/Skjermdump.jpg") you can see a picture of the amsn sound settings, it is only 2 lines not mutsh do do.

---

### Post by joft on 2006-02-07
[QUOTE=svar][here]("http://home.online.no/~svar/Skjermdump.jpg") you can see a picture of the amsn sound settings, it is only 2 lines not mutsh do do.[/QUOTE]

You could try and replace the command "play" with "esdplay", so that amsn will output its wave files over esd (which then uses ALSA). AFAIK package "esound-clients" contains esdplay, so will have to install this package.

This way amsn and xmms should work together = produce sound at the same time.

[QUOTE=kudu]I set ALSA as default sink output and input in Multimedia Systems Selector and get the following error message when I try the test button for default source input: Failed to construct test pipeline for 'ALSA - Advanced Linux Sound Architecture'[/QUOTE]

Ok - perhaps you should leave input setting alone. I can't tell you way this is not working. But it should definitely work for output.

---

### Post by svar on 2006-02-07
Then I change play to esdplay, I get no sound at all in amsn

---

### Post by joft on 2006-02-09
[QUOTE=svar]Then I change play to esdplay, I get no sound at all in amsn[/QUOTE]

The "esdplay" file is existing? (/usr/bin/esdplay)

Or your esd does not get started? Is

System -> Preferences -> Sound: Enable sound server at startup

checked?

Or esd is not able output to ALSA's sound device, because it's block by an other (dmix-incompatible) application .... Did run such an application in parallel or an application which uses OSS (which also blocks the whole sound device)?

---

### Post by svar on 2006-02-11
Nope dont have the file :???:

---

### Post by joft on 2006-02-12
[QUOTE=svar]Nope dont have the file :???:[/QUOTE]

Well, then you didn't do what I told you in post #10 : You have to install the package "esound-clients".
In case you don't know how to do this, open up a terminal and type:

```
apt-get install esound-clients
```

If

---

