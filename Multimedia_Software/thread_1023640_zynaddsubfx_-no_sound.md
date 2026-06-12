---
title: "zynaddsubfx -no sound"
date: 2008-12-28
forum: Multimedia Software
---

### Post by plus on 2008-12-28
I discovered that programmm some time ago and i think it is of the best,but recently i dont have any sound coming from it.
The sound is ok for other applications,only for zynaddsubfx there seems to be a problem.
I uninstalled it and reinstalled it,normally without doing anything with the parametres it should have sound,i checked again zynaddsubfx`s volume controll and ubuntu`s ,but there is no sound.
I really cant understand it,so i would appreciate any help.
i amm running ubuntu 8.10, gnome, 32bit version.

---

### Post by xc3RnbFO8P on 2008-12-28
Read this and check if you can use this information:
[http://ubuntuforums.org/showthread.php?t=164429]("http://ubuntuforums.org/showthread.php?t=164429")

---

### Post by plus on 2009-01-19
i am afraid,i could not make any use of it,the programms loads ,i have no trouble to see it in the applications menu,but there is no sound at all.

---

### Post by xfearxnxloathing on 2009-10-10
i'm having the same problem, clean install, application open flawlessly just no sound, can anyone help?

---

### Post by gareththomasnz on 2010-01-09
same here - installed yesterday & it was perfect - today its dead.

---

### Post by munimula on 2010-03-23
Hello,

I have the same problem but maybe some useful information.

I tried to configure zynaddsubfx and started "->file->settings". I googled a little bit for "OSS Wave Out Device" where the standard setting is "/dev/dsp". I found out that sometimes problems occur with opening this file.

So I had the idea that there are problems which are not printed out and I started zynaddsubfx in a shell. The program opens without problems again and I can also do everything, but I get the error message:

**ERROR - I can't open the /dev/dsp/**

I googled again and found this link: [http://ubuntuforums.org/showthread.php?t=171182](http://ubuntuforums.org/showthread.php?t=171182) but it doesn't help. Seems to be a solveable problem. Maybe someone has an idea now or someone found the solution in between?

---

### Post by munimula on 2010-03-24
For me I got the solution here: 

[http://www.kvraudio.com/forum/viewtopic.php?p=4028732#4028732](http://www.kvraudio.com/forum/viewtopic.php?p=4028732#4028732)

---

### Post by gamhead on 2011-02-26
I got my solution here;

[http://www.khattam.info/solved-cant-open-devdsp-in-ubuntu-10-10-maverick-meerkat-2010-06-09.html#disqus_thread](http://www.khattam.info/solved-cant-open-devdsp-in-ubuntu-10-10-maverick-meerkat-2010-06-09.html#disqus_thread)

---

### Post by rodion raskolnikov on 2011-03-29
It is better to use Jack. Just instal jack control and start jack.

---

### Post by Ultrax1 on 2011-10-23
?

---

### Post by tru infini on 2011-11-05
Here is my output when I run zynadd in terminal
ZynAddSubFX - Copyright (c) 2002-2009 Nasca Octavian Paul and others
Compiled: Sep  3 2011 19:55:32
This program is free software (GNU GPL v.2 or later) and 
it comes with ABSOLUTELY NO WARRANTY.

Try 'zynaddsubfx --help' for command-line options.
Sound Buffer Size = 	256 samples
Internal latency = 	5.8 ms
ADsynth Oscil.Size = 	1024 samples

ERROR: Cannot make a jack client (possible reasons: JACK server is not running or jackd is launched by root and zynaddsubfx by another user.).

Using OSS instead.
ERROR - I can't open the /dev/dsp.

It worked fine when I was on 1004 but then I accidentally upgraded to 10.10 and it stopped working. so I figured why not poke around on 11.11 for a bit until I decide that 10.04 is where it's at to get all the programs I like to run just fine.
I don't get why they have to change everything like that. I've never had to run zynadd with jack before and I don't think a person should *HAVE* to do it only a certain way. (because that's why we all left Windows, right?) all I want is to be able to open up zynadd, pull up the virtual keyboard and jam away. is that so hard to ask?

---

### Post by tru infini on 2011-11-18
bump
[http://xkcd.com/979/](http://xkcd.com/979/)

---

### Post by tru infini on 2011-11-30
> **tru infini said:**
> bump
[http://xkcd.com/979/](http://xkcd.com/979/)

bump again

---

### Post by MoreOrLess on 2011-11-30
It's choking on finding legacy OSS devices (because they were removed in Maverick)
> Using OSS instead.
ERROR - I can't open the /dev/dsp.
You can emulate /dev/dsp witth padsp (and it usually works well):
```
sudo apt-get install pulseaudio-utils
padsp zynaddsubfx
```

---

### Post by cornflake000 on 2012-01-01
> **MoreOrLess said:**
> It's choking on finding legacy OSS devices (because they were removed in Maverick)

You can emulate /dev/dsp witth padsp (and it usually works well):
```
sudo apt-get install pulseaudio-utils
padsp zynaddsubfx
```

This does not work here.  I have the same problem as posted.

---

### Post by 80770m on 2012-01-15
Briefly got sound whilst messing around replacing "/dev/dsp" in zyn settings, with output from
> ls /dev/snd | grep pcm
but did not last.

Just install Qjackctl. 
> sudo apt-get install qjackctlNo config required. Just start it and fire up zyn. You'll get sound. Just be aware that jack likes to be shutdown properly, so use the stop and quit buttons.

---

### Post by SonnyE on 2012-07-10
No, that is not true. I don't get sound from zynaddsubfx using qjackctl, even though I get sound from QSynth using qjackctl and either vmpk, Rosegarden, or Audacious to provide the midi signals qjackctl patches.

zynaddsubfx has a default output to /dev/dsp, the problems with that are: (1) There isn't any /dev/dsp on my system (Lubuntu 12.04 desktop i386, which is supposed to be the same core as Ubuntu 12.04) and (2) I haven't found any instructions yet about how to get sound output from zynaddsubfx in general or what else to set its output to besides "dev/dsp". I just find comments about it not working in particular cases on various systems, including on its official support forum:  [http://www.kvraudio.com/forum/viewforum.php?f=47](http://www.kvraudio.com/forum/viewforum.php?f=47)

I'm inclined to think right now that the whole thing is a trick and a joke that never makes sound for anyone, that people just tease other users with by claiming it works for them.

---

### Post by SonnyE on 2012-07-11
Solved the problem I just posted in the comment above. Sound produced from zynaddsubfx now.

All I did was install alsa-oss using the Synaptic package manager. So the answer is: The drivers that used to make dev/dsp available have been blacklisted in Ubuntu, and [**Open Sound System (OSS) support has been removed from the kernel since Meerkat**]("http://administratosphere.wordpress.com/2011/07/06/oss-audio-support-removed-in-ubuntu-maverick-meerkat/"). Instead of enabling those drivers, it's said to be better to emulate dev/dsp. You can use PulseAudio and the command that's recommend for that is padsp, but you can use [**Alsa**]("http://www.alsa-project.org/main/index.php/Main_Page") instead, and for that you need alsa-oss.

I wanted to use Alsa only, because the Rosegarden developers prefer that and users have had problems combining PulseAudio and Rosegarden. After that one step of installing alsa-oss, when I started JACK Audio Connection Kit, in Messages where the usual since I installed Linux a few days ago included:

> Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started

instead I received, for the first time:

> Tue Jul 10 20:17:56 2012: New client 'qjackctl' with PID 4119

Then ZynAddSubFX played sound for the first time too.

I hope that's enough information to help anyone else who has similar trouble getting the sound started. The sound is real.;)

---

### Post by chkneater on 2012-07-29
> **tru infini said:**
>  I've never had to run zynadd with jack before and I don't think a person should *HAVE* to do it only a certain way. (because that's why we all left Windows, right?) all I want is to be able to open up zynadd, pull up the virtual keyboard and jam away. is that so hard to ask?

For free? Yes.  I'm using 10.10 Studio and have zynadd up with jack and audacious and Hydrogen running and no xruns, so it is possible.

Just for my curiosity, open a terminal and : sudo qjackctl

let it load and check in setup the correct " Interface " for your soundcard is listed, if not correct it.  Either way, HIT the STOP button and THEN QUIT.  

Then from the menu open Jack Control, ignore messages about jackserver client stuff, hit START button.  Open zynadd and check the "connections" tab in jack that zynadd is connected to your input/output tell me you don't have sound now when you click on the keyboard. (you won't get sound from the keyboard until you depress a key with the mouse, dunno why)  

I hated jack before I realized that it wasn't getting sudo permissions to access devices, so I then tried sudo qjackctl and that seemed to work but had no sound, so I went back and tried the GUI version, and lo and behold, after giving it sudo permissions it worked fine, and zynadd worked with no virtual keyboard also, it seems to have it's own.

---

