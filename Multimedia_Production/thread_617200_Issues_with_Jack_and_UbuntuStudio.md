---
title: "Issues with Jack and UbuntuStudio"
date: 2007-11-19
forum: Multimedia Production
---

### Post by SupraBlur on 2007-11-19
> **Stochastic said:**
> well from my experience firefox and swiftweasel sometimes has host apps and plugins that occupy the sound server.  try shutting swiftweasel down.  If you're ready to toss out ubuntu based on Jack not working I'd suggest installing UbuntuStudio, for the most part it Jack is setup to work out of the box.  It solved many issues I was having with regular ubuntu.

Actually on second thought why don't you start a new thread on your particular problem rather than re-hashing someone else's that has already been solved.

To re-cap, here's what happens when I try to start Jack Control:

01:26:45.522 Patchbay deactivated.
01:26:45.536 Statistics reset.
01:26:45.679 Startup script...
01:26:45.680 artsshell -q terminate
01:26:45.899 MIDI connection graph change.
JACK tmpdir identified as [/dev/shm]
JACK tmpdir identified as [/dev/shm]
can't create mcop directory
Creating link /home/raydius/.kde/socket-raydius-desktop.
01:26:46.479 Startup script terminated with exit status=256.
01:26:46.479 JACK is starting...
01:26:46.479 /usr/bin/jackd -dalsa -dhw:0 -r44100 -p1024 -n2
01:26:46.481 JACK was started with PID=6922 (0x1b0a).
jackd 0.103.0
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK compiled with System V SHM support.
loading driver ..
SSE2 detected
apparent rate = 44100
creating alsa driver ... hw:0|hw:0|1024|2|44100|0|0|nomon|swmeter|-|32bit
control device hw:0
control open "hw:0" (No such device)
ALSA lib pcm_hw.c:1351:(_snd_pcm_hw_open) Invalid value for card
ALSA lib pcm_hw.c:1351:(_snd_pcm_hw_open) Invalid value for card
ALSA: Cannot open PCM device alsa_pcm for playback. Falling back to capture-only mode
cannot load driver module alsa
no message buffer overruns
01:26:46.494 JACK was stopped successfully.
01:26:46.494 Post-shutdown script...
01:26:46.494 killall jackd
jackd: no process killed
01:26:46.682 MIDI connection change.
01:26:46.709 Post-shutdown script terminated with exit status=256.
01:26:48.710 Could not connect to JACK server as client. Please check the messages window for more info.
JACK tmpdir identified as [/dev/shm]

---

I tried to install UbuntuStudio... and I think I succeeded -- I restarted it and my X server wouldn't start, so I had to rebuild the Kernel and then download the restricted nVidia drivers for real-time desktop (not sure why).  Upon getting back into X, I'm not really sure what was different other than now I have a whole bunch of new applications installed... which is fine, but I don't understand how that warranted the kernel issues.  Everything still looks and feels the same as I did prior to the UbuntuStudio install, so I'm not sure what I actually did other than the batch install.

Soo... that brings me up to date.  I still get that same error when running Jack Ctl and as a result can't run Ardour, which is my primary goal.

Any ideas before I reformat the whole thing and install WindowsXP?  The goal is to buy an M-Box before Christmas and be productively recording away...

-Ray

---

### Post by SupraBlur on 2007-11-19
I suppose it also helps to note that my ALSA driver works fine with playback on all apps that I've tried running, the actual sound card for now is a SoundBlasterLive USB.  The rest of the setup is a very basic Gutsy 64-bit install running on almost all Intel hardware (it's a Dell PowerEdge with a pair of Clovertowns).

-Ray

---

### Post by Stochastic on 2007-11-19
Well I'd like to note that when I said earlier to install UbuntuStudio I meant that you should give the distro a try, not just the meta packages that you have installed as then you'll have a fresh install that should be setup for audio.  YMMV.
And to further clarify, you were earlier claiming that the issue you had was similar to the other poster's thread (device busy error) but it doesn't look that way so I wouldn't worry too much about the swiftweasel thing.

It looks like qjackctl thinks that hw:0 is not a valid card address.  Try running ```
jackd -R -d alsa
``` from a terminal and post the results.  Is it the same error message?  I'm not sure how Soundblaster Live USB cards should be properly accessed by jack but you might want to look into that for solutions.

---

### Post by SupraBlur on 2007-11-19
> **Stochastic said:**
> 
It looks like qjackctl thinks that hw:0 is not a valid card address.  Try running ```
jackd -R -d alsa
``` from a terminal and post the results.  Is it the same error message?  I'm not sure how Soundblaster Live USB cards should be properly accessed by jack but you might want to look into that for solutions.

Here is my output from running the above command:

> 
jackd 0.103.0
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details

JACK compiled with System V SHM support.
loading driver ..
SSE2 detected
creating alsa driver ... hw:0|hw:0|1024|2|48000|0|0|nomon|swmeter|-|32bit
control device hw:0
control open "hw:0" (No such device)
ALSA lib pcm_hw.c:1351:(_snd_pcm_hw_open) Invalid value for card
ALSA lib pcm_hw.c:1351:(_snd_pcm_hw_open) Invalid value for card
ALSA: Cannot open PCM device alsa_pcm for playback. Falling back to capture-only mode
cannot load driver module alsa
no message buffer overruns


Does this provide any insight?  It occured to me that it might be related to the fact that it's a USB interface, but that's kind of a requirement since I'll be switching to a USB M-Box anyhow.  Any help is much appreciated.

-Ray

---

### Post by deadgobby on 2007-11-19
Well one is your are running 64 bit and there is some bug issues with that. I use to run Ubie studio and things did not work. It is a great project, but at last it cause some midi issues. Thus I installed the programs that Ubie studio uses one by one. Thus wrks very well. 
For 64 bit users may I recommend  Studio 64. 
[http://www.64studio.com/](http://www.64studio.com/)
 It is a debian based system and uses Gnome as for desktop. It is geared toward 64 bit users. You can DL the live CD version and give it a try. If you get no sound at first. Just open up the terminal and run alsamixer and turn up the volume levels.
Gobby

---

### Post by SupraBlur on 2007-11-19
> **deadgobby said:**
> Well one is your are running 64 bit and there is some bug issues with that. I use to run Ubie studio and things did not work. It is a great project, but at last it cause some midi issues. Thus I installed the programs that Ubie studio uses one by one. Thus wrks very well. 
For 64 bit users may I recommend  Studio 64. 
[http://www.64studio.com/](http://www.64studio.com/)
 It is a debian based system and uses Gnome as for desktop. It is geared toward 64 bit users. You can DL the live CD version and give it a try. If you get no sound at first. Just open up the terminal and run alsamixer and turn up the volume levels.
Gobby

I would be inclined to blame the 64-bit distro if not for the fact that I'm getting a *parking lot* error while starting JACK, possibly the simplest component of the entire Ubuntu Studio.  I will look into Studio 64 but I have a feeling that I'm still going to be running into the same issues.

-Ray

---

### Post by nalmeth on 2007-11-20
You probably installed the low-latency kernel if you are on feisty, and you are using the proprietary ATI/NVIDIA driver. 
Just switch to the generic kernel on boot, or install the realtime kernel (sticky in this section).

I wouldn't assume 64-bit OS is necessarily to blame here. Your second error message says that hw:0 won't work.

Go into the Settings in qjackctl, and change the input device. Maybe your USB device will show in the list.

I can't guarantee your USB device will work, but often it just takes some tweaking of JACK settings to get it to start. 

BTW, firewire devices are known to work decently well, if you have any room for consideration. They are supported by FFADO (formerly FREEBOB). You can check their websites and see what they support.

---

### Post by Stochastic on 2007-11-20
> **deadgobby said:**
> Well one is your are running 64 bit and there is some bug issues with that. I use to run Ubie studio and things did not work. It is a great project, but at last it cause some midi issues. Thus I installed the programs that Ubie studio uses one by one. Thus wrks very well. 
For 64 bit users may I recommend  Studio 64. 
[http://www.64studio.com/](http://www.64studio.com/)
 It is a debian based system and uses Gnome as for desktop. It is geared toward 64 bit users. You can DL the live CD version and give it a try. If you get no sound at first. Just open up the terminal and run alsamixer and turn up the volume levels.
Gobby

I really don't mean to start any fights but every post I see of yours on here tends to be about how everyone should not use UbuntuStudio but rather Studio64.  Kinda strange for being on an Ubuntu forum.

Okay, in recent review of "your latest posts" option on the forum, I see that not every post of yours is slanted that way, just a couple.  Do you run UbuntuStudio or any form of Ubuntu?



Sorry, I'm getting a bit off topic with this thread, just as I told SupraBlur not to in the last thread.  SupraBlur: Nalmeth is right with the qjackctl settings bit but the bit about feisty is moot as you've already said you're using Gutsy.  64-bit shouldn't have any issues, mine works beautifully with a FADO device and all the M-Audio devices I've owned were solid under linux (though I didn't like their sound).

---

### Post by SupraBlur on 2007-11-20
> **nalmeth said:**
> 
Go into the Settings in qjackctl, and change the input device. Maybe your USB device will show in the list.

I can't guarantee your USB device will work, but often it just takes some tweaking of JACK settings to get it to start. 


This did the trick!  Oh what a silly thing for me to be stumped on.  I perused the Jack settings before but it all seemed like jargon to me, so I didn't delve into the details.  I definitely feel dumb about that, but am glad it's working now, as I do love my Ubuntu experience thus far and wouldn't want to kill it over this.

[quote=stochastic]
Sorry, I'm getting a bit off topic with this thread, just as I told SupraBlur not to in the last thread. SupraBlur: Nalmeth is right with the qjackctl settings bit but the bit about feisty is moot as you've already said you're using Gutsy. 64-bit shouldn't have any issues, mine works beautifully with a FADO device and all the M-Audio devices I've owned were solid under linux (though I didn't like their sound).
[/quote]

Real quick, was the dislike of the sound due to Linux, or due to the quality of the product?

-Ray

---

### Post by nalmeth on 2007-11-20
I should learn to read more carefully! :-\"

About 64 Studio, I would definitely recommend it if you are having too many difficulties with Ubuntu. 64 Studio has been doing multimedia production longer, and they have a good, mature product - great for 64-bit. 
On the other hand, I think Ubuntu is a great distro in other respects, and only requires a bit of tweaking to behave with audio production, and also runs well with 64-bit. And things are getting better.

Take a look at your Settings in qjackctl, and see if any changes will let JACK start. First I would look at your input device, the error message was complaining about that (hw:0)

I agree with Stochastic that its probably not a 64-bit problem, I have better performance with 64-bit. 

>  Any ideas before I reformat the whole thing and install WindowsXP?Leave enough space for Ubuntu/64 Studio! Dual-booting leaves the options open.

---

### Post by Stochastic on 2007-11-20
> **SupraBlur said:**
> 
Real quick, was the dislike of the sound due to Linux, or due to the quality of the product?

I think it was the quality of the product.  The sound was just a little too flat (not in frequency response, but rather in sound).  But that's to be expected in that price range.  I have heard stories that low-end gear like that is bad primarily because of lack of quality checking.  So in theory you could go through each M-Audio the store has in stock and take a listen until you find a nice sounding one, but many store clerks will laugh if you ask to do this.  When I was buying in the M-Audio price range I did buy M-Audio and I still think they're one of the better cards in the low-end for linux but don't expect to be getting amazing results with it.

---

### Post by SupraBlur on 2007-11-21
> **Stochastic said:**
> I think it was the quality of the product.  The sound was just a little too flat (not in frequency response, but rather in sound).  But that's to be expected in that price range.  I have heard stories that low-end gear like that is bad primarily because of lack of quality checking.  So in theory you could go through each M-Audio the store has in stock and take a listen until you find a nice sounding one, but many store clerks will laugh if you ask to do this.  When I was buying in the M-Audio price range I did buy M-Audio and I still think they're one of the better cards in the low-end for linux but don't expect to be getting amazing results with it.

Do you suppose the Digi M-Box is any better?  I had a Delta44 before and I kind of know what you mean by 'flat'.

-Ray

---

