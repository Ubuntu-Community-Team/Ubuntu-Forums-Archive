---
title: "jack is broken"
date: 2007-08-06
forum: Multimedia Production
---

### Post by johnlee on 2007-08-06
i posted this in installation and upgrades, but i dont think anyone there uses jack
im getting this error
john@john-laptop:~$ qjackctl
qjackctl: error while loading shared libraries: libjack-0.100.0.so.0: cannot open shared object file: No such file or directory

ive tried reinstalling jack, auto remove then install
libjack just isnt where ever its looking, where do i find libjack?

thanks
john

---

### Post by fredj on 2007-08-06
How are you installing Jack. Try using the Administration->Synaptic Package
Manager to remove it and re-install it. This is a strange error that I've never seen
before.

---

### Post by thorgal on 2007-08-07
I guess you have the feisty version of jackd.

I installed jackd from svn (compiled it myself) and installed it in /usr/local
Look at the difference in the jack library naming :

Packaged version :

/usr/lib/libjack0.100.0 -> jack/
/usr/lib/libjack-0.100.0.so.0 -> libjack.so.0
/usr/lib/libjack.a
/usr/lib/libjackasyn.so.0 -> libjackasyn.so.0.11
/usr/lib/libjackasyn.so.0.11
/usr/lib/libjack.la
/usr/lib/libjack.so -> libjack.so.0.0.23
/usr/lib/libjack.so.0 -> libjack.so.0.0.23
/usr/lib/libjack.so.0.0.23


Compiled from latest svn :

/usr/local/lib/libjack.la*
/usr/local/lib/libjack.so -> libjack.so.0.0.28*
/usr/local/lib/libjack.so.0 -> libjack.so.0.0.28*
/usr/local/lib/libjack.so.0.0.28*



Now, if I do an ldd on my compiled  jackd, I get :

        linux-gate.so.1 =>  (0xffffe000)
        libjack.so.0 => /usr/local/lib/libjack.so.0 (0xb7f1b000)
        librt.so.1 => /lib/tls/i686/cmov/librt.so.1 (0xb7f12000)
        libm.so.6 => /lib/tls/i686/cmov/libm.so.6 (0xb7eec000)
        libpthread.so.0 => /lib/tls/i686/cmov/libpthread.so.0 (0xb7ed4000)
        libdl.so.2 => /lib/tls/i686/cmov/libdl.so.2 (0xb7ed0000)
        libc.so.6 => /lib/tls/i686/cmov/libc.so.6 (0xb7d87000)
        /lib/ld-linux.so.2 (0xb7f4b000)


and my guess is that your version would depend on /usr/lib/libjack0.100.0 which seems to me no longer necessary for more recent versions.

---

### Post by johnlee on 2007-08-12
alright ive installed jack, but it blows up and goes red, virtually unusable, how should i customize it to work with my old p3 laptop?

thanks guys

---

### Post by thorgal on 2007-08-12
in a shell, type 

uname -r

if you have a kernel that is not realtime or at least low-latency, then the first thing you will have to do is to install such a kernel (go for realtime if you don't mind a little bit of insecurity on your system - your laptop's not a server of some kind I would guess, so that should be fine). In synaptic, search for "linux-rt" and install the whole shebang, reboot with your rt kernel.

second thing (or actually, 1st thing) , what is your soundcard ?

type

lspci -v

what do you get in the line "Multimedia audio controller:" ?

see if it is supported by alsa (I would think it is if you have already tried jack). 

Then, see what jack options fit best to your h/w. My soundcard is a M-Audio Delta 1010LT in my desktop PC, I run jackd with these options :

/usr/bin/jackd -R -dalsa -dhw:0 -r48000 -p64 -n2 -H

note that the option -p64 might not be adequate for you. For me, given a sample rate of 48000, it is perfect, I get no xruns. ANd that ensures me a very low latency (~ 2.5ms according to jack). But I also benefit from the hardware monitoring of that card, so it means 0 latency. 

Anyway, a common setting is -r 44100 -p 1024 -n 2

In the latest version of jackd, there's a midi option : -X seq but I think it is only in the svn version (not a mainstream release) but I may be wrong on this. 


Good luck :)

---

