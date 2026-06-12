---
title: "Ardour/lexicon omega question"
date: 2007-11-27
forum: Multimedia Production
---

### Post by Bigdeath on 2007-11-27
I recently purchased a lexicon omega desktop recording interface. The awesome thing about it is that it "just works" with ubuntu. I configured it in jack and run ardour. It will let me asign the different inputs to tracks and record but when I play it back it sounds all distorted. Anyone got any ideas?

---

### Post by Bigdeath on 2007-11-27
Guess no one knows huh.

---

### Post by StanObuX on 2008-01-27
Sorry, I haven't been on in a while. . .  Sounds like a buffer issue.  I would look into that first.  I assume your pc is fast enough.  Been using the Omega for about 2 years.

Hotep


"As is above, so is below."

[www.myspace.com/stancliffbuxley](www.myspace.com/stancliffbuxley)
[www.myspace.com/buxleys](www.myspace.com/buxleys)

---

### Post by lamps06 on 2008-01-27
Hi bigdeath.  Perhaps you (or another knowledgeable person) can give me a hand.  I own a Lexicon Lambda that I am having difficulty getting to work with Ubuntu Studio 7.10.  I have the lambda plugged in and it shows up in my device manager so my computer is seeing it.  I run JACK with the following settings:

Driver: alsa
Real Time not checked
Sample Rate set to 48000
Periods/Buffer set to 3
Audio set to duplex
Input Device is set to hw:1 Lexicon Lambda
Output Device is set to hw:1 Lexicon Lambda
Input Channels: 2
Output Channel: 2

I click the Start button in Jack and it starts.  I get the following output:12:05:37.186 Startup script...
12:05:37.189 artsshell -q terminate
JACK tmpdir identified as [/dev/shm]
can't create mcop directory
Creating link /home/mateo/.kde/socket-Athlon.
12:05:37.531 Startup script terminated with exit status=256.
12:05:37.542 JACK is starting...
12:05:37.545 /usr/bin/jackd -v -dalsa -r48000 -p1024 -n3 -D -Chw:1 -Phw:1 -i2 -o2
12:05:37.565 JACK was started with PID=6096 (0x17d0).
getting driver descriptor from /usr/lib/jack/jack_oss.so
getting driver descriptor from /usr/lib/jack/jack_alsa.so
getting driver descriptor from /usr/lib/jack/jack_freebob.so
getting driver descriptor from /usr/lib/jack/jack_dummy.so
jackd 0.103.0
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK compiled with System V SHM support.
server `default' registered
registered builtin port type 32 bit float mono audio
registered builtin port type 8 bit raw midi
clock source = system clock via clock_gettime
loading driver ..
apparent rate = 48000
creating alsa driver ... hw:1|hw:1|1024|3|48000|2|2|nomon|swmeter|-|32bit
control device hw:1
new client: alsa_pcm, id = 1 type 1 @ 0x8059250 fd = -1
configuring for 48000Hz, period = 1024 frames, buffer = 3 periods
ALSA: final selected sample format for capture: 24bit little-endian
ALSA: use 3 periods for capture
ALSA: final selected sample format for playback: 24bit little-endian
ALSA: use 3 periods for playback
new buffer size 1024
registered port alsa_pcm:capture_1, offset = 4096
registered port alsa_pcm:capture_2, offset = 8192
registered port alsa_pcm:playback_1, offset = 0
registered port alsa_pcm:playback_2, offset = 0
++ jack_rechain_graph():
client alsa_pcm: internal client, execution_order=0.
-- jack_rechain_graph()
6096 waiting for signals
12:05:39.978 Server configuration saved to "/home/mateo/.jackdrc".
12:05:39.980 Statistics reset.
12:05:39.986 Client activated.
12:05:39.988 Audio connection change.
12:05:40.035 Audio connection graph change.
12:05:40.038 XRUN callback (1).
new client: qjackctl-6072, id = 2 type 2 @ 0xb7f27000 fd = 15
++ jack_rechain_graph():
client alsa_pcm: internal client, execution_order=0.
client qjackctl-6072: start_fd=5, execution_order=0.
client qjackctl-6072: wait_fd=10, execution_order=1 (last client).
-- jack_rechain_graph()
JACK tmpdir identified as [/dev/shm]

JACK continues to run, but I get a lot of something that look like warnings or errors in my message box:

12:06:24.451 XRUN callback (25 skipped).

And this repeats about every two seconds.  So my first question is:  what does this mean?  It seems like it cannot be a good thing, is there a way to correct it?  The Lambda is supposed to be able to record at 48kHz, 24bit resolution.  Maybe my computer is a little slow?

AMD Athlon XP 1800+ (running at 1.5GHz)
PATA 100 7200RPM hard drives (one for OS, one for recording)
2.5GB of PC 2700 RAM
FSB of 333MHz

At any rate, I have two more questions regarding Ardour 2.  Once I have Jack started I open Ardour and start a new session.  I add a mono track.  How do I assign the input to that track, ie how do I tell it which of the two Lexicon Lambda input channels to use?  And also, how in the world do I actually get it to record?  I click the little red record button on the track and then I hit the big red record button up top and it begins flashing, but nothing happens.  The time does not starting rolling and nothing is recorded.  Am I doing something wrong?  Do you think this is related to my Jack issue?

If anyone can offer me any help, that would be great.  I have spent the last two weeks switching over to Ubuntu with the sole intention of getting my computer set up to record and edit music.  Thanks!

---

### Post by StanObuX on 2008-02-11
At any rate, I have two more questions regarding Ardour 2. Once I have Jack started I open Ardour and start a new session. I add a mono track. How do I assign the input to that track, ie how do I tell it which of the two Lexicon Lambda input channels to use? And also, how in the world do I actually get it to record? I click the little red record button on the track and then I hit the big red record button up t . . .

You must press spacebar to begin recording. . . 
Go read the manual.  Best thing I ever did.

This device probably works like the Omega.  First, with jack, make your life more simple and install Qjackctl ( sudo apt-get install qjackctl )  It is the GUI front for jackd.  The program will appear in your Sounds & Videos in the Applications menu.  (For studio apps I use all the time along with a teminal, just drag to the menu bar for ease of use.  So first things first.  USB sound cards are all supported by coreaudio in linux; that's why it just works.  So, look at your personal audio setting in System > Preferences > Sound.   Make sure you have the proper sound card pegged for playback and recording.  Test it.  GREAT!  NOTE: you may have a conflict setting issue with integrated audio or a regular sound card that you should disable in your bios.  I had this issue and still had to tell Ubuntu Alsa what card I was using.  Refer to my first posts' link.

Everything should be working fine now. . .

BTW Just looked at all that crap that printed out.  And looks like jack IS trying to use your onboard audio card OR it is conflicting.  Disable onboard audio card in startup bios and then set alsa follow above link in previous post.  Hope this helps!

READ THE MANUAL for ARDOUR will ONLY help YOU!   Expecially if you really did switch FOR audio processing. . .  why wouldn't you?


Stancliff of Buxley

Hotep


[www.myspace.com/buxleys](www.myspace.com/buxleys)
[www.myspace.com/stancliffbuxley](www.myspace.com/stancliffbuxley)

"As is above, so is below."

---

