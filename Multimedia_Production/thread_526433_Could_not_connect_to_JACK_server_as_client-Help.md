---
title: "Could not connect to JACK server as client-Help"
date: 2007-08-15
forum: Multimedia Production
---

### Post by GuilhermeBrant on 2007-08-15
I've been trying to start JACK here but it returns the following error message :

14:49:30.682 Startup script...
14:49:30.682 artsshell -q terminate
can't create mcop directory
Creating link /home/guilherme/.kde/socket-Guilherme.
14:49:30.922 Startup script terminated with exit status=256.
14:49:30.922 JACK is starting...
14:49:30.922 /usr/bin/jackd -R -dalsa -r44100 -p1024 -n2 -D -C/dev/dsp -P/dev/dsp -m -i2 -o2 -H -M
14:49:30.924 JACK was started with PID=5907 (0x1713).
jackd 0.102.20
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK compiled with System V SHM support.
cannot use real-time scheduling (FIFO at priority 10) [for thread -1210389632, from thread -1210389632] (1: Operation not permitted)
cannot create engine
14:49:30.939 JACK was stopped successfully.
14:49:30.939 Post-shutdown script...
14:49:30.940 killall jackd
jackd: nenhum processo morreu
14:49:31.150 Post-shutdown script terminated with exit status=256.
14:49:33.049 Could not connect to JACK server as client. Please check the messages window for more info

 I'm on Ubuntu 7.04 and on M-Audio Audiophile 2496 soundcard.It's my second day in linux,I'm used to recording in windows as well,and everything works perfectly.Here JACK always retrieve this error msg,misterously,it has run once.But just once.
  I know there are already a lot of topics about this,but none of them seems to  work for me.Can anybody help me out?
 Thank you

---

### Post by variona on 2007-08-15
Are you sure that /dev/dsp refers to your M-Audio Audiophile 2496?
If you use jackctl then check out the input/output device params in the settings dialog.
HTH
variona

---

### Post by GuilhermeBrant on 2007-08-15
Well,in the setup (by the way i use the jack control graphic interface),when i select this device,it's named M-Audio Delta Audiophile 2496.And as I said,it has run once,i dunno how.
 The ALSA mixer here,do not work also.

---

### Post by GuilhermeBrant on 2007-08-15
I have just figured out what the problem was.I just unchecked the option "Realtime" in the jack control setup panel.
 However,now i've got another problem.When I play music on XMMS,it's tuned down,and the tempo is altered too.I have already reinstalled XMMS,worked on the sound preferences,but nothing seems to fix this.
 What should I do?

---

### Post by gashcrumb on 2007-08-15
Can you check the main window of qjackctl, is there a red number underneath the yellow text that says "Started"?  It could be that you're getting xruns.  The only way to get rid of xruns is to install the low latency kernel package, or better still the realtime kernel from the ubuntu studio repositories.

---

### Post by fredj on 2007-08-16
You may be trying to play music recorded at 48khz at 44.1khz, this would have
the effect of down tuning it.
With regard to realtime you need to install the realtime kernel to use this, it gives
a much lower latency performance. Details in the sticky at the top of this forum
about real time kernel testing.

---

