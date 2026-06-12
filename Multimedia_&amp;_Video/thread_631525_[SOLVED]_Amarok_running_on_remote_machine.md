---
title: "[SOLVED] Amarok running on remote machine"
date: 2007-12-04
forum: Multimedia &amp; Video
---

### Post by pwaldo on 2007-12-04
Hi all,

I use KDE running on a remote machine.  I connect to this server via a client PC running NX.  The server's KDE's Audio Device is set to Enlightened Sound Daemon.  The client used ESD within NX.  I can hear normal sounds OK on the client.

Now I'm trying to get Amarok to work on the server.  I have the Sound System set to "xine" (unfortunately the only choice) and Output Plugin is set to "Autodetect".  There seems to be no ESD plugin...  How can I get Amarok to send sound to my NX client?  

FWIW, the real problem is that Amarok does not pipe sound through KDE just like all other KDE apps....

Any help is appreciated!

Paul

---

### Post by Whiffle on 2007-12-04
If you go to the Sound system control, and click the Output Plugin dropdown, there is an entry for esd there.  (at least there is on this computer, which is running slackware but is the only thing i have access to right now)

---

### Post by pwaldo on 2007-12-04
Alas, my only options are 
[LIST]
[*]Autodetect
[*]alsa
[*]oss
[*]pulseaudio
[*]file
[/LIST]

---

### Post by Whiffle on 2007-12-04
do you have libao2 installed? (on the machine with amarok)

---

### Post by pwaldo on 2007-12-04
> **Whiffle said:**
> do you have libao2 installed? (on the machine with amarok)
I do:
```
$ dpkg -l libao2
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Installed/Config-f/Unpacked/Failed-cfg/Half-inst/t-aWait/T-pend
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name                     Version                  Description
+++-========================-========================-================================================================
ii  libao2                   0.8.8-2                  Cross Platform Audio Output Library

```

Also, I neglected to mention that I'm running 64-bit Kubuntu

---

### Post by pwaldo on 2007-12-14
Using pulseaudio solves my problem.  I installed the pulseaudio server and used pulseaudio as the output plugin and I'm rockin'!  Thanks to all!

---

