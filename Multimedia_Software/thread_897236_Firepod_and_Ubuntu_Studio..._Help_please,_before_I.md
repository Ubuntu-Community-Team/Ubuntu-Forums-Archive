---
title: "Firepod and Ubuntu Studio... Help please, before I quit! :)"
date: 2008-08-21
forum: Multimedia Software
---

### Post by Julián Fernández on 2008-08-21
Hi guys... My first post here.

I installed Ubuntu (via Wubi) a couple of days ago and I was fascinated from day one... Everything seem to be good.
The problems started when I tried to install my Presonus Firepod... I tried every guide I found on this forums but I can't make it work...

The last guide I use was this one:

[http://ubuntuforums.org/showthread.php?p=2833020](http://ubuntuforums.org/showthread.php?p=2833020)

Right now this is the error I'm getting when I try to use Jack:

`default' server already active
00:51:24.332 JACK was stopped with exit status=1.

BTW, Jack won't let me choose the number of inputs and outputs of my FP... That must be wrong, right?

I need help, pleaseeeeeeee :) I don't wanna go back to Windows! :(

---

### Post by Julián Fernández on 2008-08-22
anyone? ):P

---

### Post by vivichrist on 2008-08-24
tried using hw:0 instead of (default) ?

---

### Post by Stochastic on 2008-08-24
I have my firepod up and running fine, hopefully I can help you do the same.

First, we'll try to narrow down where things are going wrong for you.
What happens when you run the following command from the terminal (after a fresh reboot of the computer while the firepod is on and plugged in): ```
jackd -R -dfreebob
```
Also, what's the output of this command:
```
uname -r
```

---

### Post by Julián Fernández on 2008-08-26
THANKS A TON! :)

After jackd -R -dfreebob i get this:

jackd 0.109.2
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details

JACK compiled with System V SHM support.
cannot use real-time scheduling (FIFO at priority 10) [for thread -1210530128, from thread -1210530128] (1: Operation not permitted)
cannot create engine

uname -r:

2.6.24-19-rt

BTW, When I updated to Ubuntu Studio (through Synaptic), after downloading an error occur... something like this:
E: ubuntustudio-audio: dependency problems - leaving unconfigured

What should I do about it?

Thanks again! :)

---

### Post by Stochastic on 2008-08-27
Okay it looks like you have run into the raw firewire permissions error.

First, let's try to get your ubuntustudio-audio package installed properly. Go to the terminal and make sure apt-get has finished installing all the packages you have previously asked it to: ```
sudo apt-get install -f
```
Then once it's finished, manually configure the ubuntustudio-audio package (the last command may have done this already, but it won't hurt to do it again for safety's sake)```
sudo dpkg -reconfigure ubuntustudio-audio
```

Now go ahead and try the jackd -r -dfreebob again, if you get the same "operation not permitted" error then do the one of the two following operations:

**1) GUI method (easier for beginners)**
-Open System->Administration->Ubuntu Studio Controls
-Check the box marked "Enable raw1394"
-(optional step) while you're there it's advisable to turn on memlock and adjust it to about 90% or so (mine's @ 95%)
-Click apply
-Click close

**2) Command Line method (helps gain better understanding of the process, and makes sure things are done properly)**
-Open a terminal and do ```
sudo gedit /etc/udev/rules.d/40-permissions.rules
```
-Find the lines that read something similar to: ```
KERNEL=="raw1394",                      GROUP="disk"
KERNEL=="dv1394*",                      GROUP="disk"
KERNEL=="video1394*",                   GROUP="video"
```
-Change it to:```
KERNEL=="raw1394",                      GROUP="audio"
KERNEL=="dv1394*",                      GROUP="audio"
KERNEL=="video1394*",                   GROUP="video"
```
-Save the file, and exit gedit


Now you should be able to get jackd running.  If you still get an error when you execute 'jackd -r -dfreebob', please post that error.  If it's the same permissions error, then try rebooting (I don't think a reboot is required but it may be to refresh the udev rules).

If you do have jackd running from command line, then try getting it running via qjackctl (aka. jack control); if that gives you an error then you need to adjust your settings in qjackctl's settings window.

Hopefully this all helps; post back with how far you get.

---

### Post by Julián Fernández on 2008-08-29
Thanks for your help man!

When I tried "sudo apt-get install -f"

I got this:

july@july-desktop:~$ sudo apt-get install -f
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
0 actualizados, 0 se instalarán, 0 para eliminar y 0 no actualizados.
2 no instalados del todo o eliminados.
Se utilizarán 0B de espacio de disco adicional después de desempaquetar.
Configurando timidity (2.13.2-19ubuntu1) ...
 * Starting TiMidity++ ALSA midi emulation...                                                                                                                                  ALSA lib confmisc.c:768:(parse_card) cannot find card '0'
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_card_driver returned error: No such file or directory
ALSA lib confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_concat returned error: No such file or directory
ALSA lib confmisc.c:1251:(snd_func_refer) error evaluating name
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib conf.c:3985:(snd_config_expand) Evaluate error: No such file or directory
ALSA lib pcm.c:2145:(snd_pcm_open_noupdate) Unknown PCM default
                                                                                                                                                                        [fail]
invoke-rc.d: initscript timidity, action "start" failed.
dpkg: error al procesar timidity (--configure):
 el subproceso post-installation script devolvió el código de salida de error 1
E: Sub-process /usr/bin/dpkg returned an error code (1)

I don't have problems reinstalling the whole system... tell me if it's gonna make things easier...
BTW, I already changed the KERNEL=="raw1394" and "dv1394*" to group audio (following an earlier tutorial...)

Thanks again!
Cheers!

---

### Post by markbuntu on 2008-08-29
This timidity thing is a bug with sound cards that have built in midi. It has been reported in launchpad. 

It will not otherwise cause problems with an UbuntuStudio install, everything else will install and work just fine. Remove Timidity with synaptic and UbuntuStudio desktop which it depends on. This has nothing to do with your jack problem.

---

### Post by Julián Fernández on 2008-08-30
Mark, I tried what you suggested...

Uninstalling the UbuntuStudio desktop caused the same error when I installed Ubuntustudio (E: ubuntustudio-audio: dependency problems - leaving unconfigured)... I removed Timidity but still can't make the Pod work... I still get the same error (cannot use real-time scheduling (FIFO at priority 10)...)

Thanks guys!

Can't wait to see it working! :)

---

### Post by Stochastic on 2008-09-01
Well this timidity bug shouldn't affect a fresh install - so that might fix things.  I'd also say you should do the apt-get install -f without your firepod plugged in (allow timidity to configure itself without it worrying about any firepod) - you may even want to remove other soundcards if that's feasible.  Out of curiosity, can you get jack started if you do ```
sudo jackd -R -dfreebob
``` all the other programs that use jack will also need sudo privileges so this isn't a secure way to go about working.

---

### Post by Julián Fernández on 2008-09-01
Stochastic, I just reinstalled Ubuntu and tried to re-install UbuntuStudio... I got the same error when finished(E: timidity: el subproceso post-installation script devolvió el código de salida de error 1
E: ubuntustudio-audio: problemas de dependencias - se deja sin configurar)

I couldn't do "sudo apt-get install -f" because I got the same error, too (with the FP disconnected)...

When I tried sudo jackd -R -dfreebob I got this:

jackd 0.109.2
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details

JACK compiled with System V SHM support.
loading driver ..
Freebob using Firewire port 0, node -1
libiec61883 warning: Established connection on channel 0.
You may need to manually set the channel on the receiving node.
libiec61883 warning: Established connection on channel 1.
You may need to manually set the channel on the transmitting node.
Cancelado


The onboard soundcard was turn off from the BIOS...
I have a pci Pinnacle PCTV Stereo card... Can it be the cause of the problems?

Btw, do you have any idea why I can't never complete the installation of OStudio?

Thanks!:)

---

### Post by Julián Fernández on 2008-09-07
Stochastic, are you still there? :)

---

### Post by zettberlin on 2008-09-07
> **Julián Fernández said:**
> 
timidity: el subproceso post-installation script devolvió el código de salida de error 1

Do you really *need* timidity?  More or less everything one can do whith it can be done with fluidsynth (use qsynth or a DSSI-plugin to control it). So I recommend to abandon timidity as it causes trouble...

> **Julián Fernández said:**
> 
E: ubuntustudio-audio: problemas de dependencias - se deja sin configurar)


You do not need the ubuntustudio-audio package but only some packages that are listed it such as jackd, Ardour, Rosegarden etc AND: the kernel-rt package of course.
So it is safe to remove ubuntustudio-audio, as long as you keep kernel-rt, its modules, jack and the audio-apps you really want to use.


> **Julián Fernández said:**
> 

When I tried sudo jackd -R -dfreebob I got this:

jackd 0.109.2
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details

JACK compiled with System V SHM support.
loading driver ..
Freebob using Firewire port 0, node -1
libiec61883 warning: Established connection on channel 0.
You may need to manually set the channel on the receiving node.
libiec61883 warning: Established connection on channel 1.
You may need to manually set the channel on the transmitting node.



To this point everything looks perfectly OK: after I get this message. I can work with my Presonus Firebox for houres...

But: the way you start jack is OK but should be somewhat more tuned for the fw-situation, I start the thing like this:

jackd --verbose -R -dfreebob -r96000 -p512 -n3

most important is "-n3" this is needed by most USB and FW devices to run properly.

> **Julián Fernández said:**
> 
Cancelado



That means, the system is installed OK and starts OK but has a serious problem when running, this can have several reasons:

1.) HW-Conflicts (disabeling everything you do not absolutely need, could help)
2.) Ubuntu-specific trouble (disable network-manager and every service/demon that is not absolutely vital) 

3.) A combination of the 2 above caused by the delicacy of the whole firewire realtime operation kind of thing. 

Please find out, what FW-controller chipset you use:

:~$ lspci |grep IEEE

This yields this result on my Laptop:

04:04.0 FireWire (IEEE 1394): O2 Micro, Inc. Firewire (IEEE 1394) (rev 02)

quite bad medicine for me since the O2Micro chipset is named third-best on the ffado-page. Thus my Presonus does NOT work with UbuntuStudio on my Laptop (at least not for more than 8 or so minutes).

BUT: I can work with my Firebox for houres stable and reliable with 64Studio on the very same machine.


Please post you output of lspci and we can try to help you further on the way 

;-)

---

### Post by Julián Fernández on 2008-09-07
Thanks for your help Zett! :)

I'm using a pci card with Via chipset (I figured that out right after buying the FP): 

04:05.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 46)

What do you say if I try to reinstall Ubuntu once again, and instead of upgrading to UbuntuStudio, just choose the apps that you mentiones? I don't like the idea of a corrupted version of UStudio...

In fact, I tried again sudo jackd -R -dfreebob I got an error about missing something about ALSA...

Maybe I should try again with a fresh install... seems like a good plan to you?

Thanks again!

---

### Post by zettberlin on 2008-09-08
> **Julián Fernández said:**
> Thanks for your help Zett! :)

I'm using a pci card with Via chipset (I figured that out right after buying the FP): 

04:05.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 46)


Your welcome :-)

VIA is second-best regarding the word I got from the ffado-people. But it should work, got a VIA-Chipset on my main-workstation and it works nearly perfect.

> **Julián Fernández said:**
> 
What do you say if I try to reinstall Ubuntu once again, and instead of upgrading to UbuntuStudio, just choose the apps that you mentiones? I don't like the idea of a corrupted version of UStudio...


Yeah - try this. Especially, if you have tried some hacks to make the installed system run - these tend to contradict each other and thus a fresh install could help.

> **Julián Fernández said:**
> 
In fact, I tried again sudo jackd -R -dfreebob I got an error about missing something about ALSA...


That should absolutely NOT be - freebob/ffado are independent of ALSA and they should not be influenced by it.
Another reason for a fresh install I guess.

---

### Post by Julián Fernández on 2008-09-08
Ok, here we go again... Just finished installing Ubuntu. :)

I'm not sure how to install the realtime kernel, and I don't which packages should I install with Synaptic... Can you help me with this too?

Cheers!

---

### Post by vivichrist on 2008-09-14
I'm currently using the 2.6.26-rt kernel of intrepid and this seems to have fixed the odd behavioural tendencies of jackd dyeing on me. but processing of audio and network seem to be quite high. like 30% just playing a wav file?

---

### Post by Sam the Wizer on 2008-09-22
Not sure if you got this resolved, but I went through much of the same thing the other night.  If you download ubuntustudio-audio from synaptic it should download the realtime kernel and all the programs you need (some you don't as well, but they're easily removed prior to install in synaptic).  I think the crucial elements are linuxrt (realtime kernel) jack, qjackctl, etc, and your recording interface (I use Ardour).  

I am also using a 1394 card with a VIA chipset (lucked out, didn't even research this before buying it).  I started getting the message that FIFO priority 10 was not allowed.  Basically you need to reset the priority to 60, but it won't allow you to do it through Qjackctl.  I'll have to find the command to reset it (on a windows machine right now).  The other things that were necessary were to allow raw firewire access and up the memory priority through the Ubuntustudio control.  After that I installed gscanbus which allows you to view various busses and reset them (which I have had to do occasionally since getting setup).  I'll edit this later when I'm on my Ubuntu machine and have time.  It took me a couple of hours of sifting through forums to get mine working, but now that it is, I'm very happy.  Stick with it it's worth it!

---

### Post by Julián Fernández on 2008-09-25
Thanks Sam!

I'm looking foward to try your tips!

Thanks!

BTW, Right now I'm on UbuntuStudio 64 and it keeps using the generic kernel... There's no rt kernel on the menu to choose...

Any idea how to make it boot with rt kernel?

---

### Post by Sam the Wizer on 2008-09-25
You can get the Realtime Kernal through Synaptic by searching for linux-rt.

[http://ubuntuforums.org/showthread.php?t=453486](http://ubuntuforums.org/showthread.php?t=453486)
Is the thread where I found how to reset the FIFO priority.  Metal Music Addict's post.

---

