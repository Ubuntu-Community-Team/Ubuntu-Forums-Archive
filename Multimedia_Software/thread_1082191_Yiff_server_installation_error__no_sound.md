---
title: "Yiff server installation error || no sound"
date: 2009-02-27
forum: Multimedia Software
---

### Post by Sifilis on 2009-02-27
this is the problem,
every time i try to install something (synaptic or updates) I get this message:

```
E: yiff-server: subprocess post-installation script returned error exit status 1

```

that was around for some time and I worry about that because it caused no problems, and when I tried to reinstall the yiff server it was not possible.

any ideas for the repair of Yiff server?

```
marko@marko-desktop:~$ yiff
Error while creating /var/run/yiff/yiff.pid: Permission denied!
marko@marko-desktop:~$ sudo yiff
/dev/dsp: Cannot open for playing.

```

Pulseaudio is already installed, but this is an example what happens at the end of every installation through terminal

```
marko@marko-desktop:~$ sudo apt-get install pulseaudio
Reading package lists... Done
Building dependency tree       
Reading state information... Done
pulseaudio is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up yiff-server (2.14.5-4) ...
Starting Y Sound Server: ERROR.
invoke-rc.d: initscript yiff-server, action "start" failed.
dpkg: error processing yiff-server (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 yiff-server
E: Sub-process /usr/bin/dpkg returned an error code (1)

```


I'm running Intrepid
If you need any other logs or something, I can provide. 
Cheers

---

### Post by Sifilis on 2009-02-27
Ok, solved this error simply, uninstall yiff server in synaptic.. no errors now..

thx, bye

---

### Post by EriQ_10 on 2009-06-26
hi,
I was having the same problem you described in your first post so i made sure i had pulse audio installed and uninstalled yiff like you said and now the sound wont work at all :(
I tried reinstalling but it didnt work could you please give me further instructions on how you did this???

---

### Post by the_felis_leo on 2009-08-18
try a first installation of yiff-server
then update /etc/yiff/yiffrc  to change from /dev/dsp to /dev/asdp (look for dsp)
then reinstall the package.

[URL="http://www.justlinux.com/forum/archive/index.php/t-116738.html"][quote=bwkaz (forum www.justlinux.com, 06-04-2004, 06:51 PM)]

/dev/adsp is the "alternate" DSP chip on a sound card. 
Usually "alternate" DSPs are for stuff like the OSS emulation [/quote][/URL]

but for me it is my hdmi output, not my primary audio, but it work.

---

### Post by mworkman on 2009-11-29
Yiff-server seems to have been a problem for a while now (I found [http://ubuntuforums.org/showthread.php?t=597657&highlight=yiff-server](http://ubuntuforums.org/showthread.php?t=597657&highlight=yiff-server) started in Oct, 2007).  It appears the project page is dead, as well.  From what I could gather, yiff provides a networked sound server (similar to esound?), wrapping access to OSS and ALSA, but not pulse-audio, which is where the problem lies.

I tried to get the yiff server to run via the padsp wrapper, which would provide pseudo-access to /dev/dsp for the underlying binary.  This failed, as did using LD_PRELOAD (since this is the method padsp uses, I believe, I expected this to fail as well).  This leads me to believe that yiff doesn't use shared libraries for its OSS access.  Running 'strings' on the yiff binary finds a direct reference to /dev/dsp (I didn't, but should have, run ldd on the binary, to verify it was not using shared libraries).  So it appears that yiff will just not play nice with pulse-audio.  Since yiff was only installed to support one game I wanted to try, and pulse-audio is weaved throughout the system, I know which one has to go.

```
sudo apt-get purge yiff-server
```Cleared yiff-server, and its configuration files, off my machine.  The game still plays, with no sound, but at least apt-get is happy again.

---

