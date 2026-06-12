---
title: "Terratec EWX 24/96 &amp; Jack problems"
date: 2006-07-05
forum: Multimedia &amp; Video
---

### Post by MartynM on 2006-07-05
Firstly, hello to everyone, this is my first post here. I'm pretty new to Linux let alone Linux audio, so plese be gentle with me.

I've been trying to get Jack to use my Terratec soundcard, it runs the onboard (intel) card on my ASUS motherboard without a hitch, but when i try to start it using the Terratec as input & output device it won't start and I get this error message.

> 21:41:05.469 Patchbay deactivated.
21:41:05.518 Statistics reset.
21:41:05.644 MIDI connection graph change.
21:41:05.727 MIDI connection change.
21:41:07.642 Startup script...
21:41:07.642 artsshell -q terminate
sh: artsshell: command not found
21:41:07.851 Startup script terminated with exit status=32512.
21:41:07.851 JACK is starting...
21:41:07.851 /usr/bin/jackd -R -dalsa -r44100 -p512 -n2 -D -Chw:1 -Phw:1 -i2 -o2
21:41:07.855 JACK was started with PID=8773 (0x2245).
jackd 0.100.0
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK compiled with System V SHM support.
loading driver ..
apparent rate = 44100
creating alsa driver ... hw:1|hw:1|512|2|44100|2|2|nomon|swmeter|-|32bit
control device hw:1
configuring for 44100Hz, period = 512 frames, buffer = 2 periods
ALSA: cannot set channel count to 2 for capture
ALSA: cannot configure capture channel
cannot load driver module alsa
21:41:07.893 JACK was stopped successfully.
21:41:10.004 Could not connect to JACK server as client. Please check the messages window for more info.

Also, my default sound setting (in ubuntu preferences) keeps resetting itself to the onboard intel driver when I try to set it to use the Terratec, can I use both drivers, or do I have to have the default sound driver the same as the one Jack intends to use? If so, why won't it let me use the Terratec driver?

I hope somebody can shed some light on this for me, I'm getting very confused.:( 

Thanks in advance.

M

---

### Post by metasymbol on 2006-07-06
Welcome to the community ;)

What kind of Terratec card you are use? The best are the one with a envy24 chipset, other cards from terratec are difficult, because Terratec dosn't open specifications for the alsa developers. 

Did you try to disable your onboard soundchip in the bios?

---

### Post by MartynM on 2006-07-06
Hi, thanx for the reply.

My card is an EWX 25/96, and it does use the Envy drivers. I havn't tried disabling the onboard card in the bios, is it not possible to run them both at the same time? I'm at work at the moment so can't check that it works, I'll definately give it a shot later though.

Cheers

M

Update; Just tried disabling my onboard sound in the bios as suggested, no effect I'm afraid. The Terratec is working just fine as default soundcard, envy24control mixer (which is horrible) is working as it should, I don't understand it.

Ah well, I guess I'll just settle for using my onboard sound for now, it's less than ideal though.

Any Jack gurus out there?

---

### Post by metasymbol on 2006-07-06
I never seen this:

[COLOR="Red"]21:41:07.851 /usr/bin/jackd -R -dalsa -r44100 -p512 -n2 **-D -Chw:1 -Phw:1 -i2 -o2**[/COLOR]

This is the start from my JAD jackd:

[COLOR="Red"]22:47:44.366 jackd -R -dalsa -dhw:0 -r44100 -p128 -n2 [/COLOR]

So it looks like you have more options enabled on the Jack control (qjackctl) Setup then needed

So - only the rt option need to be enabled like here:

[img]http://www.jacklab.net/screens/qjacsetup1.png[/img]

---

### Post by SoftGround on 2006-07-07
There seems to be a problem with the way the Sound Prefrences set up the default card using .asoundrc.asoundconf.  There are a number of bug reports about this.  
e.g. [gnome-sound-properties generates broken alsa conf]("https://launchpad.net/distros/ubuntu/+source/control-center/+bug/44101")

It works with some things but jack has problems.

You need to do it at startup using modprobe to ensure that the correct card is card zero (hw:0).

in modprobe.d/alas-base you need to put some options index statements to ensure the correct order.

See here: [Sound blaster live]("http://ubuntuforums.org/showthread.php?t=114551") (same issue with SBLive)

Also:  [how to set dapper default sound card]("http://ubuntuforums.org/showthread.php?t=188148") (points to above thread)

---

### Post by zettberlin on 2006-07-07
The shortest Way to end the trouble would be to disable the onboardchip using the BIOS, if alsa has no choice, EWX-cards work right away.


anyway:

-D -Chw:1 -Phw:1 -i2 -o2

this should work, if the EWX is properly loaded as hw1 yet it looks like it does not and so i still recommend to switch off the onboardchip ;-)

---

### Post by MartynM on 2006-07-07
It turned out that the real problem was probably my IQ:rolleyes:  Metasymbol had the answer, I was trying to enable ins and outs that dont exist, leaving those fields blank and keeping the devices set to default completely fixed it. I wrongly thought I had to enable my cards channels, thats all it was.

I now have 65 samples of latency on a stock Dapper install, which I'm pretty happy about actually.

Many, many thanks to everyone who replied to this thread, especially Metasymbol.

Cheers all.

M

---

