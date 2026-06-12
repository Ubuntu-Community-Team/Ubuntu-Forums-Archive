---
title: "Jack not working"
date: 2010-03-28
forum: Multimedia Software
---

### Post by Austin25 on 2010-03-28
I am trying to use qjackctl, but when I hit start, it gives me this:```
  p, li { white-space: pre-wrap; }  Could not connect to JACK server as client.
 - Overall operation failed.
 - Unable to connect to server.
 Please check the messages window for more info.

```
and the message window says:
```
  p, li { white-space: pre-wrap; }  [COLOR=#999999]15:03:36.171 Patchbay deactivated.[/COLOR]
 [COLOR=#999999]15:03:36.187 Statistics reset.[/COLOR]
 [COLOR=#66CC99]15:03:36.264 ALSA connection graph change.[/COLOR]
 [COLOR=#CCCC99]15:03:36.462 ALSA connection change.[/COLOR]
 [COLOR=#999999]15:03:41.573 Startup script...[/COLOR]
 [COLOR=#990099]15:03:41.575 artsshell -q terminate[/COLOR]
 sh: artsshell: not found
 [COLOR=#999999]15:03:41.983 Startup script terminated with exit status=32512.[/COLOR]
 [COLOR=#999999]15:03:41.983 JACK is starting...[/COLOR]
 [COLOR=#990099]15:03:41.984 /usr/bin/jackd -R -dalsa -dhw:0 -r44100 -p1024 -n2[/COLOR]
 no message buffer overruns
 jackd 0.116.1
 Copyright 2001-2005 Paul Davis and others.
 jackd comes with ABSOLUTELY NO WARRANTY
 This is free software, and you are welcome to redistribute it
 under certain conditions; see the file COPYING for details
 JACK compiled with System V SHM support.
 cannot use real-time scheduling (FIFO at priority 10) [for thread -1117399312, from thread -1117399312] (1: Operation not permitted)
 cannot create engine
 [COLOR=#999999]15:03:42.032 JACK was started with PID=17055.[/COLOR]
 [COLOR=#999999]15:03:42.037 JACK was stopped successfully.[/COLOR]
 [COLOR=#999999]15:03:42.038 Post-shutdown script...[/COLOR]
 [COLOR=#990099]15:03:42.039 killall jackd[/COLOR]
 jackd: no process found
 [COLOR=#999999]15:03:42.478 Post-shutdown script terminated with exit status=256.[/COLOR]
 [COLOR=#FF0000]15:03:44.115 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.[/COLOR]

```

---

### Post by Austin25 on 2010-03-30
bump

---

### Post by markbuntu on 2010-03-30
Are you using the rt kernel?
You need that to use real time scheduling. Alternatively you can go to jack control/setup and turn it off.

---

### Post by Austin25 on 2010-03-31
rtkernel?

---

### Post by g-raf on 2010-03-31
Go into synaptic and type in "rtkernel"...after you find that, try installing it. While rebooting, hit the ESC key and run the rtkernel (realtime kernel). That will help with low latency in qjackctl as well.

---

### Post by Austin25 on 2010-03-31
I have a kernel patch, It would be a bad idea to use a different kernel.

---

### Post by cchhrriiss121212 on 2010-03-31
Why is it a bad idea to use a different kernel? It would certainly be easier than applying your own patch. I just set up karmic today with this rt kernel:
[https://launchpad.net/~abogani/+archive/ppa/+packages]("https://launchpad.net/%7Eabogani/+archive/ppa/+packages")

The one in the repos did not work for me (rt 2.6.31-9), but if that happens to you then just go back to the generic and look for another one.

To get realtime priority working you also need to add yourself to the audio group and do this:
```
sudo su -c 'echo @audio - rtprio 99 >> /etc/security/limits.conf'
sudo su -c 'echo @audio - memlock unlimited >> /etc/security/limits.conf'
```

---

### Post by Austin25 on 2010-03-31
I have a touchsmart tx2, and I need a kernel module installed for the touchscreen/active digitizer to work. Is there a way to do it without modifying the kernel?

---

### Post by cchhrriiss121212 on 2010-03-31
I have seen it posted somewhere that realtime priority can be used in jack without running the realtime kernel, but this has never worked on my machine. Try out those commands I gave and see whether it will work anyway.

Alternatively just uncheck the realtime option in setup. You will get decreased performance though.

> 
I have a touchsmart tx2, and I need a kernel module installed for the touchscreen/active digitizer to work. Is there a way to do it without modifying the kernel?

I'm not sure I understand the problem you have. Once you boot to a new kernel can't you just install the same module? Installing a realtime kernel won't modify the one you have, you will have a choice of two when you boot up.

---

### Post by Austin25 on 2010-03-31
> **cchhrriiss121212 said:**
> I have seen it posted somewhere that realtime priority can be used in jack without running the realtime kernel, but this has never worked on my machine. Try out those commands I gave and see whether it will work anyway.

Alternatively just uncheck the realtime option in setup. You will get decreased performance though.



I'm not sure I understand the problem you have. Once you boot to a new kernel can't you just install the same module? Installing a realtime kernel won't modify the one you have, you will have a choice of two when you boot up.
I will try using the different setting, but It took a lot to get my computer working wwith the kernel module, and I would prefer not to go through that again.

---

### Post by Austin25 on 2010-03-31
Thank you, that worked.

---

