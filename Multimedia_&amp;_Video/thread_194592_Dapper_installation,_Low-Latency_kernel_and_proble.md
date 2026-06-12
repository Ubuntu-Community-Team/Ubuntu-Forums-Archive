---
title: "Dapper installation, Low-Latency kernel and problems with Real-Time scheduling"
date: 2006-06-11
forum: Multimedia &amp; Video
---

### Post by Germel on 2006-06-11
Hello List,

I'm new to Ubuntu and new to this list. Up to now I used a DeMuDi installation. I have installed the Dapper/Kubuntu 6.06 release with Low-Latency kernel and Real-Time scheduling on an AMD Athlon Board and I like to tell you my experience. As a first note: I had problems to get the Real-Time extension work with Jack.

After the pure installation of Dapper (without any hassle), I followed strictly the advices on
  [http://ubuntustudio.com/wiki/index.php/Dapper:Studio_Preparation](http://ubuntustudio.com/wiki/index.php/Dapper:Studio_Preparation)

(BTW: the command "sudo apt-get install ardour" as described in the above link does not work, the package is called "ardour-gtk-i686" or "ardour-gtk"!)

To get a Low-Latency kernel, I fetched the Vanilla kernel, patched, compiled and installed it exactly like described on:
  [http://ubuntustudio.com/wiki/index.php/Dapper:Vanilla_Kernel_With_Realtime_Preemption](http://ubuntustudio.com/wiki/index.php/Dapper:Vanilla_Kernel_With_Realtime_Preemption)
but without applying the NVIDIA patch.

Then I changed the file "/etc/security/limits.conf" to get Real-Time support for Joe User for the Audio group like described also in the link. AND THAT ISN'T IT!

After launching qjackctrl and starting Jack (for all three sound cards I own) I got the error message:

--------------- snip ---------------------------
12:22:21.474 /usr/bin/jackstart -R -P80 -t1000 -dalsa -r44100 -p1024 -n3 -D -Chw:0 -Phw:0 -S
12:22:21.480 JACK was started with PID=5255 (0x1487).
jackstart: cannot get realtime capabilities, current capabilities are:
           =ep cap_setpcap-ep
    probably running under a kernel with capabilities disabled,
    a suitable kernel would have printed something like "=eip"
back from read, ret = 1 errno == Success
jackstart: could not give capabilities: Operation not permitted
--------------- snip ---------------------------

Amazingly this happend to root too.

It followed a long trial and error phase of more patching and meanwhile I can not exactly tell you what has solved the problem in the end. In each case I have done the following: 

in the configuration process for the kernel compilation I had to switch on 

  CONFIG_SECURITY_CAPABILITIES=m
and
  CONFIG_SECURITY_REALTIME=m

what was not the case for me per default.

Furthermore I installed the "capabilities" patch like described in:
  [http://ardour.org/system_requirements](http://ardour.org/system_requirements)
and
[http://lists.debian.org/debian-devel/2003/11/msg00888.html](http://lists.debian.org/debian-devel/2003/11/msg00888.html)

I also launched the following commands
  # echo "options realtime any=1" > /etc/modprobe.d/realtime
  # echo "realtime" >> /etc/modules
to start the realtime module during boot.

And Bingo: qjackctrl now gives the following output:
--------------- snip ---------------------------
12:15:07.923 /usr/bin/jackstart -R -P80 -t1000 -dalsa -r44100 -p1024 -n3 -D -Chw:0 -Phw:0 -S
12:15:07.933 JACK was started with PID=7736 (0x1e38).
back from read, ret = 1 errno == Success
--------------- snip ---------------------------
GOOD!

I could have done a few more things for this stuff to work I don't remember anymore but with all the links in this post you should have enough information to follow. I have not yet tested the stuff under high load but hope, it'll make it.

Further Links:
[http://tapas.affenbande.org/?page_id=6](http://tapas.affenbande.org/?page_id=6)
[http://tapas.affenbande.org/?page_id=40](http://tapas.affenbande.org/?page_id=40)
[http://esaracco.free.fr/documentations/linuxaudio/linuxaudio/obtaining-realtime-privileges.html](http://esaracco.free.fr/documentations/linuxaudio/linuxaudio/obtaining-realtime-privileges.html)

So folks, sorry for my bad English but I had to tell you this story in the hope, it could help someone.

Gerhard

---

### Post by dolson on 2006-06-13
> 19:10:36.852 /usr/bin/jackd -R -P60 -dalsa -r48000 -p128 -n2 -D -Chw:0,2 -Phw:0,0 -S
19:10:36.858 JACK was started with PID=7742 (0x1e3e).
jackd 0.100.0
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK compiled with System V SHM support.
loading driver ..
apparent rate = 48000
creating alsa driver ... hw:0,0|hw:0,2|128|2|48000|0|0|nomon|swmeter|-|16bit
control device hw:0
configuring for 48000Hz, period = 128 frames, buffer = 2 periods
nperiods = 2 for capture
nperiods = 2 for playback
19:10:37.059 MIDI active patchbay scan...
19:10:37.063 MIDI connection change.
19:10:37.264 MIDI active patchbay scan...
19:10:39.076 Server configuration saved to "/home/dana/.jackdrc".
19:10:39.077 Statistics reset.
19:10:39.111 Client activated.
19:10:39.138 Audio connection change.
19:10:39.152 Audio connection graph change.
19:10:39.341 Audio active patchbay scan...

I do not get the same errors as you. I have followed the wiki as I am the one who created it.

My kernel config automatically had the first module built, 

> dana@polly:~$ grep CAPABI /boot/config-2.6.16-rt26
CONFIG_SECURITY_CAPABILITIES=m

Are you sure you copied the default kernel config file as instructed in the wiki? Because it is definitely enabled on Dapper's default kernel (speaking about i386, don't know about anything else).

> dana@polly:~$ grep CAPABI /boot/config-2.6.1*
/boot/config-2.6.15-23-386:CONFIG_SECURITY_CAPABILITIES=m
/boot/config-2.6.16-rt26:CONFIG_SECURITY_CAPABILITIES=m

For whatever reason (I imagine the option is deprecated) the second option does not exist in my kernel config, but is there in Dapper:

> dana@polly:~$ grep REALT /boot/config-2.6.1*
/boot/config-2.6.15-23-386:CONFIG_SECURITY_REALTIME=m

I don't know what possibly went wrong with your steps, except perhaps you didn't copy the old config.

By the way, the capabilities patch you refer to, that is from three years ago, and I am pretty sure it is for a 2.4.x kernel..

---

### Post by zetile on 2006-06-14
Dolson:

I am having the same issue that Germel explained.

I have performed all the steps several times, and each time I am having the same issue. The .config file was taken from the 2.6.15-23-amd64-k8 kernel though



security capabilities are enabled:
@elodia:~$ grep CAPABI /boot/config-2.6.1*
/boot/config-2.6.15-23-amd64-generic:CONFIG_SECURITY_CAPABILITIES=m
/boot/config-2.6.15-23-amd64-k8:CONFIG_SECURITY_CAPABILITIES=m
/boot/config-2.6.16-rt26:CONFIG_SECURITY_CAPABILITIES=m

@elodia:~$ grep REALT /boot/config-2.6.1*
/boot/config-2.6.15-23-amd64-generic:CONFIG_SECURITY_REALTIME=m
/boot/config-2.6.15-23-amd64-k8:CONFIG_SECURITY_REALTIME=m

But the CONFIG_SECURITY_REALTIME is only enabled in the ubuntu stock kernels.

I explicitly enabled added it to the .config file, but after the kernel is compiled it disappears.

---

### Post by dolson on 2006-06-14
Because I am sure that Ingo Molnar's patch deprecates that option. I'd have to ask him, and I am not real sure at the moment how to go about asking him a question such as that.. But it is definitely something to look into.

I am curious to know if it has to do with a 64-bit CPU/OS?

---

