---
title: "Jackd problem with rt-kernel"
date: 2008-07-12
forum: Multimedia Software
---

### Post by LeSid on 2008-07-12
Hi all

I can-t start jackd in real time mode as a user:

```
~$ /usr/bin/jackd -R -p128 -t5000 -dalsa -dhw:0 -r48000 -p64 -n2 -S -Xseq
jackd 0.109.2
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details

JACK compiled with System V SHM support.
cannot use real-time scheduling (FIFO at priority 10) [for thread 1208146528, from thread 1208146528] (1: Operation not permitted)
cannot create engine
```

I tried the following configurations of /etc/security/limits.conf and rebooted after changing the configuration:

```
#<domain>      <type>  <item>         <value>
#

#*               soft    core            0
#*               hard    rss             10000
#@student        hard    nproc           20
#@faculty        soft    nproc           20
#@faculty        hard    nproc           50
#ftp             hard    nproc           0
#ftp             -       chroot          /ftp
#@student        -       maxlogins       4

@audio           -       rtprio          95
@audio           -       memlock         250000
@audio           -       nice            -19

# End of file
```

```
#<domain>      <type>  <item>         <value>
#

#*               soft    core            0
#*               hard    rss             10000
#@student        hard    nproc           20
#@faculty        soft    nproc           20
#@faculty        hard    nproc           50
#ftp             hard    nproc           0
#ftp             -       chroot          /ftp
#@student        -       maxlogins       4

*                -       rtprio          95
*                -       memlock         250000
*                -       nice            -19

# End of file
```

I believe my user is in the audio group

```
~$ groups 
LeSid admin

``` [real username changed to "LeSid"]



However, as a superuser it works:

```
:~$ sudo /usr/bin/jackd -R -p128 -t5000 -dalsa -dhw:0 -r48000 -p64 -n2 -S -Xseq
jackd 0.109.2
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details

JACK compiled with System V SHM support.
loading driver ..
apparent rate = 48000
creating alsa driver ... hw:0|hw:0|64|2|48000|0|0|nomon|swmeter|-|16bit
control device hw:0
configuring for 48000Hz, period = 64 frames (1.3 ms), buffer = 2 periods
ALSA: final selected sample format for capture: 16bit big-endian
ALSA: use 3 periods for capture
ALSA: final selected sample format for playback: 16bit big-endian
ALSA: use 3 periods for playback
port created: in-14-0-Midi-Through-Port-0
port created: out-14-0-Midi-Through-Port-0
port created: out-128-0-TiMidity-port-0
port created: out-128-1-TiMidity-port-1
port created: out-128-2-TiMidity-port-2
port created: out-128-3-TiMidity-port-3
```

Mystem is a Powerbook G4 set up with an ubuntu minimal install, a vanilla kernel with the real time patch and fluxbox. 

Thanks for help!

---

### Post by malkonix on 2009-01-08
Hey Lesid!

the problem is your config in /etc/security/limits.conf

try this one. i have a powerbook g4 too and jackd works in realtime even if i haven't the rt-kernel.

> #<domain>      <type>  <item>         <value>
#

#*               soft    core            0
#*               hard    rss             10000
#@student        hard    nproc           20
#@faculty        soft    nproc           20
#@faculty        hard    nproc           50
#ftp             hard    nproc           0
#ftp             -       chroot          /ftp
#@student        -       maxlogins       4

@audio                -       rtprio          95
@audio                -       memlock         250000
@audio                -       nice            -10      # -10 <> 10

# End of file

i hope it work!

Malkonix

---

