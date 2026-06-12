---
title: "I miss reaper and ASIO"
date: 2007-09-07
forum: Multimedia Production
---

### Post by staticvoid on 2007-09-07
Hi,
So, Post-linux when I had windows I could run a sweet little program called "REAPER" and used a plugin for ASIO. I have a US-122 Tascam audio interface and I really would appreciate some instructions from how you guys got acoustic recording setup. In the mean time I will be checking out ardour at: 

[https://help.ubuntu.com/community/HowToSeq24Introduction](https://help.ubuntu.com/community/HowToSeq24Introduction)

 and trying to set up JACK. But...I've heard you can run REAPER under wine. How do I do this? 

wants comfortable reaper software and asio driver for linux,
Saticcally void

---

### Post by eric71 on 2007-09-08
I've been using Reaper with Wine.  In some ways it performs even better in Linux. Noticibly lower latency with Jack. All of my VSTs work too. Here's a good tutorial on wineasio:

[http://www.sandgreen.dk/xt2/wineasio.html](http://www.sandgreen.dk/xt2/wineasio.html)

and a slightly more complicated tutorial, specific for installing Reaper:

[http://www.davehayes.org/2007/04/27/howto-reaper-on-ubuntu-linux-with-wineasio/](http://www.davehayes.org/2007/04/27/howto-reaper-on-ubuntu-linux-with-wineasio/)

Also, your audio interface requires a little extra work in Linux to work with alsa (which jack needs to see it):

[https://help.ubuntu.com/community/TASCAM_US-122](https://help.ubuntu.com/community/TASCAM_US-122)

I'm not sure how easy the tascam setup is, because I've never done anything like that before.  As far as wineasio and Reaper, I think the first tutorial will get you set up quickly, because they have the wineasio plugin pre-compiled. It's a little counterintuitive that you use the alsa driver in wine, and not the jack driver, but that is how it works. The Dave Hayes tutorial had this point wrong, but if you read the discussion afterwards it gets corrected.

Then just use wine to install reaper.  Use QJackCtl to get Jack running with low latency.  Occasionally I get some xruns when opening big VSTs, but rarely when actually recording.

I really would prefer to use a native DAW, and I do like both Ardour and Rosegarden, but in many ways Reaper gives me exactly what I'm looking for. Rosegarden is great for MIDI and barely adequate for audio, Ardour is great for audio but can't do MIDI (yet). I also have very little drive space on the computer I record with, and it's nice that I can record endless takes in very high quality ogg format and not fill my drive up.  Yes it's not exactly professional sound quality, but neither Rosegarden or Ardour will do that. I think that once Jokosher matures a little, and gets a way to link to soft synths (i.e. Jack compatibility) it might give Reaper a run for its money. But for now, I think Reaper with wineasio is the best DAW going on Ubuntu.

---

### Post by staticvoid on 2007-09-08
Hi,
Thank you a ton! It's so good to have forums where you can find people who have tried the same stuff.

So, I searched and searched on google and actually found that blog you were talking about :) I went through the tutorial and managed to get reaper running with linux using wine. I could not get ASIO to work though... 

That Tascam article looked PERFECT (I should've search help.ubuntu before posting here) but one thing... It cannot find:

[ftp://chuck.ucs.indiana.edu/pub/array2/linux/opensuse/distribution/SL-10.0-OSS/inst-source/suse/noarch/alsa-firmware-1.0.9-4.noarch.rpm](ftp://chuck.ucs.indiana.edu/pub/array2/linux/opensuse/distribution/SL-10.0-OSS/inst-source/suse/noarch/alsa-firmware-1.0.9-4.noarch.rpm)

Therefore I cannot convert the firmware. I cannot install it. And, I am stuck. :( so what do I do now? That tutorial is deffinatly what I need but, is there some where else I can get that rpm?

thanx,
StaticVoidly,
staticvoid

---

### Post by staticvoid on 2007-09-10
Hello,

So, here is as far as I have got with setting all this up:
I got REAPER installed under wine (easy...) then I got my US-122 tascam working. Even to the point that it recognizes it plug and play no problem. Then I dot the asiowine.dll and supposedly got it all set up. 
so heres my problem: JACK gives me an error when it is trying to use ALSA and wine config does not list "JACK" as an audio option. I got about that far in the tutorial, when it told me to select that, but I could not.

REAPER gives me the option of selecting ASIO sound and then wineasio, but It does not work... any tips? pointers?

STATIC VOID

---

### Post by nalmeth on 2007-09-10
Couple questions, 

Is wine + reaper/wineasio running when you try to start Jack? That would probably explain the error. Maybe you have to have jack running first, then start wine/reaper/asio. 

In qjackctl, go into setup, and take a look at the hardware device setting, just to make sure the right device is selected.

Can you post a screenshot of this window?

---

### Post by staticvoid on 2007-09-10
JACK has problems on its own. I have tried it with reaper open and without. Here is some visuals:
works with US-122 but has HUGE delay 
[IMG]http://i214.photobucket.com/albums/cc319/nathanpickles/Screenshot-REAPERPreferences.png[/IMG]

with ASIO, as you can see it does not recognize ins and outs [IMG]http://i214.photobucket.com/albums/cc319/nathanpickles/Screenshot-REAPERPreferences-1.png[/IMG]

my JACK setup [IMG]http://i214.photobucket.com/albums/cc319/nathanpickles/Screenshot-Setup-JACKAudioConnectio.png[/IMG]

my audio setup in wine [IMG]http://i214.photobucket.com/albums/cc319/nathanpickles/Screenshot-Wineconfiguration.png[/IMG]

Hope that helps :D

Static Void.

P.S. here is the most recent JACK error message:
Error Could not connect to Jack Server as client.











00:08:52.191 Patchbay deactivated.
00:08:52.549 Statistics reset.
00:08:52.635 Startup script...
00:08:52.635 artsshell -q terminate
00:08:52.699 MIDI connection graph change.
can't create mcop directory
Creating link /home/nathan/.kde/socket-freddy.
00:08:53.974 Startup script terminated with exit status=256.
00:08:53.974 JACK is starting...
00:08:53.974 /usr/bin/jackd -p128 -dalsa -ddefault -r44100 -p512 -n4
00:08:54.031 JACK was started with PID=14682 (0x395a).
00:08:54.233 MIDI connection change.
jackd 0.102.20
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK compiled with System V SHM support.
loading driver ..
apparent rate = 44100
creating alsa driver ... default|default|512|4|44100|0|0|nomon|swmeter|-|32bit
configuring for 44100Hz, period = 512 frames, buffer = 4 periods
ALSA: final selected sample format for capture: 32bit little-endian
You appear to be using the ALSA software "plug" layer, probably
a result of using the "default" ALSA device. This is less
efficient than it could be. Consider using a hardware device
instead rather than using the plug layer. Usually the name of the
hardware device that corresponds to the first soun
ALSA: cannot set period size to 512 frames for capture
ALSA: cannot configure capture channel
cannot load driver module alsa
no message buffer overruns
00:08:54.375 JACK was stopped successfully.
00:08:54.376 Post-shutdown script...
00:08:54.376 killall jackd
jackd: no process killed
00:08:54.660 Post-shutdown script terminated with exit status=256.
00:08:56.273 Could not connect to JACK server as client. Please check the messages window for more info.

jackd is in the right directory. but, I do not understand any of this. Tell me a few things I could try, Thank You

---

### Post by nalmeth on 2007-09-10
There are some clues in your error messages.

The message specifically mentioned the frames/period setting, although it is already quite high. Try to raise/lower this setting to see if you have any different results (or errors in this case :p ).

See what is available in the 'Interface', 'Input Device', and 'Output Device' sections in the qjackctl setup window. By default, I believe Jack will try to connect to your soundcard, so you may have to direct it to your USB device.  (I believe).
Sometimes it takes some tinkering in the Jack setup window to get it all going, and then more to get it going right.

As far as the wine/reaper situation, I can't help too much. I'm not familiar with wine-asio. Does it run on Jack, or just straight ALSA?
If Jack, I would guess none of the devices showed up in the second screenshot because Jack is not running, and therefore not presenting the audio_devices to wine. 

And as far as your old error message, even if reaper is closed, wine could still be persisting and hanging up ALSA.
killall wine and make sure reaper isn't still running.

All in all you seem to be having an unusual situation, did you follow any of the directions here? :
[https://help.ubuntu.com/community/UbuntuStudioPreparation](https://help.ubuntu.com/community/UbuntuStudioPreparation)

Anyway, I will try to help when I can. I will probably be able to look again later tonight (MNT Time)

---

### Post by staticvoid on 2007-09-11
Hi, so, I reinstalled everything, went through that tutorial and i am still getting this:
from jack: 

can't create mcop directory
Creating link /home/nathan/.kde/socket-freddy.
11:18:18.884 Startup script terminated with exit status=256.
11:18:18.960 JACK is starting...
11:18:18.960 jackstart -p128 -dalsa -ddefault -r44100 -p512 -n4
11:18:18.988 JACK was started with PID=8888 (0x22b8).
jackstart: cannot get realtime capabilities, current capabilities are:
           =ep cap_setpcap-ep
    probably running under a kernel with capabilities disabled,
    a suitable kernel would have printed something like "=eip"
jackstart: md5 checksum for /usr/bin/jackd does not match

and then in the Terminal:

nathan@freddy:~$ jack
This is jack 3.1.1 (C)2004 Arne Zellentin <zarne@users.sf.net>
 *warning* You have no standard location set, putting files into the current
           directory. Please consider setting base_dir in ~/.jack3rc.
 *error* Access of CD device /dev/cdrom resulted in error: No medium found
nathan@freddy:~$ 
 
It cannot find something...? Anyway, thjats after going through the tutorial. What you said was more helpful. Here's some quick screenshots I took:
[IMG]http://i214.photobucket.com/albums/cc319/nathanpickles/Screenshot-1.png[/IMG]
[IMG]http://i214.photobucket.com/albums/cc319/nathanpickles/Screenshot.png[/IMG]

It's nice to see my tascam interface recognized. I do not know why it is there. Jack still gives me errors. No matter how I set it up. The terminal output seems to give me hints. I do remember once having JACK up and working, somehow, with my sound card. Plus, somehow, reaper worked with Tascam, not with wineasio, but with extreme delay.

p.s.  and I changed the frames/period section and it still had problems. I don't think that is whats making run funny

---

### Post by Stochastic on 2007-09-17
Well I just recently retired my Tascam US-122 as when I did finally get it working in alsa it had a very noisy signal (sounded like the processor was altering the power rate that USB was giving the Tascam - might be an issue specific to my comp).  That being said, I do have some hints/tips to help you get things working.  

First, that tutorial is an OLD version and that's why you're not able to get the alsa firmware rpm that it tells you to get. Just do a google search for alsa firmware and download the newest version, better yet I think ```
 sudo apt-get install alsa-firmware alsa-firmware-loaders
``` should do the same thing.  But you still need to redo that whole tutorial from after getting alsa-firmware installed.

Furthermore, the Tascam US-122 that I had, had a sample rate of 16 bit 44100hz and it looks like you've got Jack attempting to read at 32bit in one of those graphics.

My jack setup was:
Frames/Periods: 1024
Sample Rate: 44100
Periods/Buffer: 3    <--Many tutorials say any USB audio should use 3 as the buffer size
Port Maximum: 256
Timeout: 500

Input Device: US-X2Y Audio #0
Output Device: US-X2Y Audio #0

I don't expect you to keep all of the same settings as I, but it might help you get things sorted out.

---

### Post by staticvoid on 2007-09-17
Hey, thank you so much :D
I have a dual boot of windows XP now just because I needed Reaper, but now that you said that I'll try to get It all working in Linux. I hope it doesn't give me a buzz.... :(
have a great day,

Static V.

---

### Post by noisesmith on 2008-04-08
> 
nathan@freddy:~$ jack
This is jack 3.1.1 (C)2004 Arne Zellentin <zarne@users.sf.net>
*warning* You have no standard location set, putting files into the current
directory. Please consider setting base_dir in ~/.jack3rc.
*error* Access of CD device /dev/cdrom resulted in error: No medium found
nathan@freddy:~$

That is not the jack audio daemon, that is a cd ripper named jack. He had the name first, and the jack audio daemon people did not know it.

I highly recommend running qjackctl instead of jackd directly, unless you already have your jackd set up perfectly, and want to save a bit of ram usage.
> 
can't create mcop directory
Creating link /home/nathan/.kde/socket-freddy.
11:18:18.884 Startup script terminated with exit status=256.
11:18:18.960 JACK is starting...
11:18:18.960 jackstart -p128 -dalsa -ddefault -r44100 -p512 -n4
11:18:18.988 JACK was started with PID=8888 (0x22b.
jackstart: cannot get realtime capabilities, current capabilities are:
=ep cap_setpcap-ep
probably running under a kernel with capabilities disabled,
a suitable kernel would have printed something like "=eip"
jackstart: md5 checksum for /usr/bin/jackd does not match



Is jack not starting up at all? The error message is fine, jackd is just a bit verbose is all.

Start up qjackctl and make sure jack is running before you start wine (even if you start jackd manually, qjackctl will show you the status of the daemon and let you configure it afterward).

hope this helps.

---

