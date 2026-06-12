---
title: "jackd will not start"
date: 2007-08-26
forum: Multimedia Production
---

### Post by ruhtranayr on 2007-08-26
Hi everyone

I'm running Ubuntu Studio 7.04
Mobo is a Gigabyte 965P-DS3 Core 2 Duo 2GHZ

Sound works fine but jackd wont start ! 

Here is the error i am getting from jackd

```
ryan@dualcore:~$ jackd -R -d alsa -d hw
jackd 0.102.20
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details

JACK compiled with System V SHM support.
cannot create /dev/shm/jack-1000 directory (Read-only file system)

cannot create server sockets
cannot create engine

```


this is what qjackctl outputs in messages: 
```
04:20:13.156 Startup script...
04:20:13.156 artsshell -q terminate
04:20:13.201 MIDI connection graph change.
can't create mcop directory
Creating link /root/.kde/socket-dualcore.
04:20:13.423 Startup script terminated with exit status=256.
04:20:13.423 JACK is starting...
04:20:13.423 /usr/bin/jackd -v -R -dalsa -dhw:0 -r44100 -p64 -n2 -m
04:20:13.425 JACK was started with PID=14814 (0x39de).
getting driver descriptor from /usr/lib/libjack0.100.0/jack_dummy.so
getting driver descriptor from /usr/lib/libjack0.100.0/jack_freebob.so
getting driver descriptor from /usr/lib/libjack0.100.0/jack_alsa.so
getting driver descriptor from /usr/lib/libjack0.100.0/jack_oss.so
jackd 0.102.20
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK compiled with System V SHM support.
server `default' registered
cannot create /dev/shm/jack-0 directory (Read-only file system)
cannot create server sockets
cannot create engine
cleaning up shared memory
cleaning up files
unregistering server `default'
04:20:13.450 JACK was stopped successfully.
04:20:13.450 Post-shutdown script...
04:20:13.450 killall jackd
jackd: no process killed
04:20:13.626 MIDI connection change.
04:20:13.670 Post-shutdown script terminated with exit status=256.
04:20:15.639 Could not connect to JACK server as client. Please check the messages window for more info.
```


more info:
```
ryan@dualcore:~$ uname -a
Linux dualcore 2.6.20-16-lowlatency #2 SMP PREEMPT Thu Jun 7 20:23:03 UTC 2007 i686 GNU/Linux
```


```
ryan@dualcore:~$ lspci | grep -i audio
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
```


```
ryan@dualcore:~/Desktop$ cat /proc/asound/cards
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xf9100000 irq 21
```


```
ryan@dualcore:~/Desktop$ cat /proc/asound/devices
  2:        : timer
  3:        : sequencer
  4: [ 0- 2]: digital audio capture
  5: [ 0- 1]: digital audio playback
  6: [ 0- 1]: digital audio capture
  7: [ 0- 0]: digital audio playback
  8: [ 0- 0]: digital audio capture
  9: [ 0]   : control
```

---

### Post by ruhtranayr on 2007-08-28
Okay I reinstalled to the 64-bit version of Ubuntu because I was running the 32-bit version. 

I found out however that Ubuntu Studio is 32-bit only! :confused:
What is happening with Ubuntu Studio? The site has been down for quite some time.

I installed the low latency kernel, and jack works even with RT enabled. However I am getting ridiculous amount of x-runs. And the sound is very grainy, poppy and crackly.

Any ideas?

---

### Post by christhemonkey on 2007-08-28
The sound being grainy poppy and crackly are what those xruns are, they are when the audio buffer is either emptied before its full or over filled before its emptied.

Try increasing your Frames/Period and decreasing your Periods/Buffer.

---

### Post by nick_m on 2007-08-29
jackd is saying that /dev/shm is read-only for your user. check in/etc/fstab to make sure it reads something like : 
none                    /dev/shm                tmpfs   defaults        0 0
then make sure your user or the members of your audio (jackusers?) group can write to /dev/shm.

---

### Post by ruhtranayr on 2007-08-30
> **christhemonkey said:**
> The sound being grainy poppy and crackly are what those xruns are, they are when the audio buffer is either emptied before its full or over filled before its emptied.

Try increasing your Frames/Period and decreasing your Periods/Buffer.

Actually decreasing Frames/Period to 64 and increasing Periods/Buffer to 8 seems to work.  However, after some time the sound quality gets grainy. Does this too when I load more than one audio app. I'll keep playing with the settings and let you guys know what happens.

My mobo is Gigabyte 965P-DS3 with onboard audio Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)

Before I upgraded my computer I was using a creative sound blaster live and it worked flawlessly on a P3.  I'm considering putting it my new box and disabling the onboard audio. Hmmm. Would this be silly seeing as I already have a better soundcard? I just NEED jack to WORK. 

Thanks for the tip nick_m. I would try that but I reinstalled. Good to know tho.

---

### Post by christhemonkey on 2007-08-30
I would definately use the non-onboard sound card as onboard sound cards tend to be of a lower quality anyway (as they are very near alot of other electrical components and easily pick up their electrical noise) 

Also, intel hda is known as a poorly designed specification, that left too much freedom to the implementers so each vendor had almost a different chip which the intel-hda alsa driver cant possibly implement all the known possible combinations. 

So to the point, you might be better off with your soundblaster than with the onboard sound.

---

### Post by ruhtranayr on 2007-08-31
I put the sound blaster in, disabled onboard audio, and it auto-detected my new card at boot. Jack is very stable now!  Thanks so much to all!

:guitar:

---

