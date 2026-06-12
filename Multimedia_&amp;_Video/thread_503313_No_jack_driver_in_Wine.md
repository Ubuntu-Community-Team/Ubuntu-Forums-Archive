---
title: "No jack driver in Wine"
date: 2007-07-17
forum: Multimedia &amp; Video
---

### Post by slavoy on 2007-07-17
Hello, I'm trying to run VST plugin hosts in Wine, but have no Jack audio driver displayed in winecfg.
Jack (and Alsa) is running in normal system (FF ubuntustudio lowlatency), audio card RME Hammerfall with ext. converters or Tapco USB audio card works normally, Ardour plays audio using jack....
I have the same result on my laptop with the same system: jack works, but now jack driver under wine.

I prepared wineasio (with one file from Steinberg SDK 2.2 by description here: [http://www.davehayes.org/2007/04/27/howto-reaper-on-ubuntu-linux-with-wineasio/]("http://www.davehayes.org/2007/04/27/howto-reaper-on-ubuntu-linux-with-wineasio/")
I left prefix in Makefile default to /usr.
Wineasio.dll was sucessfully created, copied to /usr/lib/wine and registered, symbolic link 
```
sudo ln -s /usr/lib/libjack-0.100.0.so.0 /usr/lib/libjack.so.0
```created...
Wine and jack versions:
```
wine-0.9.41
Qt: 3.3.7
qjackctl: 0.2.21
```

No serious jack error messages during winecfg startup, only:```
fixme:wave:ALSA_AddCaptureDevice Add support for DSCapture
fixme:mixer:ALSA_MixerInit No master control found, disabling mixer
fixme:mixer:ALSA_MixerInit No master control found, disabling mixer
```

I reinstalled Wine without success or changes.

I have to do anything wrong... Has anybody experience with similar situation? How can I add jack audio drivers to Wine manually? 
*Maybe this is key for me: how to add jack to wine manually, because I tried to find this without success...*

Thnx

---

### Post by fredj on 2007-07-18
The jack audio driver is a linux program, wine is for running windows programs. I don't think
you can add jack to wine.

---

### Post by slavoy on 2007-07-18
Thanks for answer, but as you can see on [http://www.davehayes.org/2007/04/27/howto-reaper-on-ubuntu-linux-with-wineasio/](http://www.davehayes.org/2007/04/27/howto-reaper-on-ubuntu-linux-with-wineasio/) 
this is possible - there you can see winecfg screen with possibility to select jack as an audio output device... But how to do this if this is missing after installation? Is current version of wine OK for this or have I do a downgrade to older version?

---

### Post by fredj on 2007-07-18
Don't know but maybe you have to start the jack audio server first before running wine.Worth a try.

---

### Post by ireneshusband on 2007-07-23
I seem to remember jack showing up as an option in winecfg a few weeks ago, but as Slavoj said, it doesn't show up now. That said, the wine I'm using is a backport from a 3rd party repository ([http://wine.lowvoice.nl/apt](http://wine.lowvoice.nl/apt)) and therefore not an official Ubuntu package.

One suggestion for how to get along in the meantime: download the latest wine sources (or those of any version of wine in which jack output is known to work) and compile them with flags set so that (a) the wine excutables install with different names (for instance you might want to enter "alt-wine" to execute /usr/local/bin/alt-wine as opposed to /usr/bin/wine) and (b) winejack is enabled. "./configure --help" should tell you how to do this, if I remember correctly. That will mean that you will have your own version of wine alongside the one that is updated automatically from the repository.

I don't know if I've got all the details right here, because I haven't done this yet (I'm planning to set up a dedicated audio workstation in the next week or so which will either be running JackLab or Ubuntu Studio), but something along those lines should do the job.

Then when you've got wine installed, you might want to [install wineasio]("http://www.davehayes.org/2007/04/27/howto-reaper-on-ubuntu-linux-with-wineasio/") to get certain asio-enabled audio apps running in wine.

---

### Post by reakin on 2007-10-22
I'm also having a similar problem.  I have downloaded wine-0.9.47, ./configure shows that jack headers are found, but once it is compiled and installed, winecfg does not show any option for jack.  I only get to choose from oss and alsa.

Also, I have jack running when running winecfg.

Does anyone know how to enable jack or a version where it works?

cheers,
rich

---

### Post by cargobidibulle on 2008-03-25
I had same problem: no jack checkbox in winecfg.

But I solved it by uninstalling wine and recompiling it from source.

---

### Post by Intangir on 2008-04-11
im having the same problem

jack isnt listed

i tried to build it locally on the machine then i had no alsa, no jack, no nas, and no artsd..

only oss..

how do i just get the damn jack working

---

### Post by Enverex on 2008-04-11
> **Intangir said:**
> im having the same problem

jack isnt listed

i tried to build it locally on the machine then i had no alsa, no jack, no nas, and no artsd..

only oss..

how do i just get the damn jack working

If you're going to build manually then you need to install ALL the dependencies Wine needs to compile correctly (check what you're missing with "./configure --verbose"). Other than that, check you have Jack installed and if you're on 64bit make sure you have the 32bit compatibility libraries installed.

Why do you need JACK in the first place may I ask?

---

### Post by Intangir on 2008-04-11
how can i get it to work without building the whole damn thing
theres alot of things required..

what im trying to do is.. i have a machine with NO SOUNDCARD
its a server, ith as a ******** of mp3s, i want to set it up to play XMMS and output out to jack

then i want wine to use that jack stream as input for wine so i can run ventrilo in wine and play stuff on the server out over ventrilo

i got both alsa, and other jack programs to use the jack steam from xmms as input
but for some reason wine wont seem to use the the alsa device i setup for jack (which works on arecord) and it wont let me try jack at all

---

### Post by deadgobby on 2008-04-11
Have you go into jackd and select OSS instead of ALSA?

---

