---
title: "FA-101 and Jack on Gutsy"
date: 2008-04-09
forum: Multimedia Production
---

### Post by loneshark on 2008-04-09
Hi there,

I have an Edirol FA-101 and I'm running Gusty Gibbon. I want to get this working with Jack and PD using freebob. I've tried a number of different ways of starting jackd -d freebob -r (samplerate) and also using qjackctl, and it is not happening for me.

There is a question about making the mcop directory in the output messages, and about the freebob driver. Here is the output from the qjackctl messages window:

JACK compiled with System V SHM support.
server `default' registered
loading driver ..
FreeBoB ERR: device (-d) argument not valid
cannot load driver module freebob
registered builtin port type 32 bit float mono audio
registered builtin port type 8 bit raw midi
clock source = system clock via clock_gettime
new client: freebob_pcm, id = 1 type 1 @ 0x806ebf0 fd = -1
starting server engine shutdown
freeing shared port segments
stopping server thread
last xrun delay: 0.000 usecs
max delay reported by backend: 0.000 usecs
freeing engine shared memory
max usecs: 0.000, engine deleted
no message buffer overruns
cleaning up shared memory
cleaning up files
unregistering server `default'
07:30:37.332 JACK was stopped successfully.
07:30:37.332 Post-shutdown script...
07:30:37.332 killall jackd
jackd: no process killed
07:30:37.547 Post-shutdown script terminated with exit status=256.
07:30:39.451 Could not connect to JACK server as client. Please check the messages window for more info.
:mad:

---

### Post by Stochastic on 2008-04-09
> **loneshark said:**
> 
JACK compiled with System V SHM support.
server `default' registered
loading driver ..
FreeBoB ERR: device (-d) argument not valid
cannot load driver module freebob

That's the first error, claiming that the device argument is not valid, which suggests that you're not even able to load the freebob driver with jack.  Do you have it installed? ```
sudo apt-get install libfreebob0
```
If so, have you had the FA-101 turned on and plugged in at time of boot (some firewire chipsets are not hot-pluggable).  After you've gone through that, can you post the output of ```
jackd -R -v -d freebob
```

---

### Post by jwmislan on 2008-04-21
Try this in a terminal 

jackd -R -P60 -p128 -t2000 -u -dfreebob -dhw:0 -r48000 -p256 &

---

### Post by loneshark on 2008-04-23
hi again,

Well the output of jackd -R -v -d freebob is thus:

JACK compiled with System V SHM support.
server `default' registered
cannot use real-time scheduling (FIFO at priority 10) [for thread -1210414400, from thread -1210414400] (1: Operation not permitted)
cannot create engine
cleaning up shared memory
cleaning up files
unregistering server `default'

The second, more specific post (with buffer sizes and samplerate set just gives

cannot use real-time scheduling (FIFO at priority 10) [for thread -1210414400, from thread -1210414400] (1: Operation not permitted)
cannot create engine

I'm thinking that there is some configuration option not set, but I'm not sure where to look. I'm a seasoned Fedora user who has recently switched to Ubuntu, but the FA-101 is new. Might this realtime error be because I am not running Ingo Molnar's patched kernel?

e

---

### Post by loneshark on 2008-04-23
Ah... forgot to run commands as a sudo ;-(

sudo jackd -R -v -d freebob
it registers all the input and output ports and then:

LibFreeBoB MSG: FreeBoB Streaming Device Init
LibFreeBoB MSG:  Using FreeBoB lib version libfreebob 1.0.10
LibFreeBoB MSG:  Device information:
LibFreeBoB MSG:  Device options:
LibFreeBoB MSG:   Port                     : 0
LibFreeBoB MSG:   Device Node Id           : -1
LibFreeBoB MSG:   Samplerate               : 48000
LibFreeBoB MSG:   Period Size              : 1024
LibFreeBoB MSG:   Nb Buffers               : 3
LibFreeBoB MSG:   Directions               : 0
LibFreeBoB ERR: Dropped packets on connection 1
FreeBoB MSG: xrun detected
load = 1.6360 max usecs: 698.000, spare = 20635.000
LibFreeBoB ERR: Dropped packets on connection 1
FreeBoB MSG: xrun detected
load = 2.4118 max usecs: 680.000, spare = 20653.000
Aborted (core dumped)

Then the more specific setup...
sudo jackd -R -P60 -p128 -t2000 -u -d freebob -d hw:0 -r44100 -p256 &


gives...
JACK compiled with System V SHM support.
loading driver ..
Freebob using Firewire port 0, node -1
libiec61883 warning: iec61883_cmp_create_p2p_output: Failed to set the oPCR[0] plug for node 0.
LibFreeBoB ERR: Could not do CMP for connection 0
FreeBoB ERR: Could not start streaming threads
DRIVER NT: could not start driver
cannot start driver
jackd watchdog: timeout - killing jackd

Hmmmm...

---

### Post by reakin on 2008-05-15
Hey,

I have the FA-101 and have it working in real-time on Gutsy

You need Ingo's patched kernel:

sudo apt-get install linux-rt

Then, you need to add yourself to the disk group:

sudo adduser USERNAME disk

Finally, you have to add some settings to your /etc/security/limits.conf file in order to allow regular users access to real-time privileges:

@audio          -       rtprio  99
@audio          -       memlock 2000000
@audio          -       nice    -19

This assumes you are in the audio group, which was the case for me when I installed Gutsy.  At this point, I could start the FA-101 from qjackctl as  a regular user, with real-time priority 70.

Hope this helps, I've definitely spent a good amount of time figuring out all this other times.  But it gets easier to find the info you need after a while.

cheers,
Rich

---

