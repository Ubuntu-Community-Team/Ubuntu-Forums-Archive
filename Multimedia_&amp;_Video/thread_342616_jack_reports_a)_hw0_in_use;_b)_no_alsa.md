---
title: "jack reports a) hw:0 in use; b) no alsa"
date: 2007-01-20
forum: Multimedia &amp; Video
---

### Post by engine on 2007-01-20
I've finally acquired a UM-1, and connected my Roland controller. I've installed muse, and I've installed jack. So far so good.

All I want to do is use the controller as an input device so I can record, quantize and save midi files. Playback (so I could hear my mistakes) would be a bonus <g>, but it ain't an essential.

By watching the console, I've decided that muse wants jack to be running before it'll even start.

Starting jack from the Apps menu fails, with messages I don't know how to respond to:

[LIST]
[*]the playback device "hw:0" is already in use. Please stop the application using it and run JACK again
[INDENT]I have no idea what hw:0, what it's doing or what is supposedly using it[/INDENT]
[*]cannot load driver module alsa
[INDENT]Poor jack ... I'd help if I could, but what do I have to do?[/INDENT]
[/LIST]

```
jackd -d alsa -d hw:1
``` comes up with other messages I still can't understand:
ALSA: Cannot open PCM device alsa_pcm for playback. Falling back to capture-only mode

Simple, step-by-step instructions would be very much appreciated!

eNG1Ne

---

### Post by sgx on 2007-01-20
> **engine said:**
> I've finally acquired a UM-1, and connected my Roland controller. I've installed muse, and I've installed jack. So far so good.

All I want to do is use the controller as an input device so I can record, quantize and save midi files. Playback (so I could hear my mistakes) would be a bonus <g>, but it ain't an essential.

By watching the console, I've decided that muse wants jack to be running before it'll even start.

Starting jack from the Apps menu fails, with messages I don't know how to respond to:

[LIST]
[*]the playback device "hw:0" is already in use. Please stop the application using it and run JACK again
[INDENT]I have no idea what hw:0, what it's doing or what is supposedly using it[/INDENT]
[*]cannot load driver module alsa
[INDENT]Poor jack ... I'd help if I could, but what do I have to do?[/INDENT]
[/LIST]

```
jackd -d alsa -d hw:1
``` comes up with other messages I still can't understand:
ALSA: Cannot open PCM device alsa_pcm for playback. Falling back to capture-only mode

Simple, step-by-step instructions would be very much appreciated!

eNG1Ne

Hi...try just
jackd -d alsa -r 44100

every audio app should be run by the same user, no mix-n-match allowed
now, install and run

qjackctl
next, vkeybd
next, zynaddsubfx (or amsynth, mx44, fluidsynth/qsynth etc
next muse
next, make  your connections in the midi and audio panels of qjackctl
and   you should have tunes. You can install alsamixergui and alsaoss
as they bring good luck, alsamixergui shows all the audio ports some other
gui may miss some and if you match the numeric settings in the jackd
config file, with those in qjackctl, you can start jackd from there...if you
knew this stuff, its there for others who may have questions. Put ladspa,
all ladspa plugins,ecamegapedal, and creox in your system for tons of nice fx
hope this helps...
also, shutdown arts if   you are running kde, and still have no luck

---

### Post by sgx on 2007-01-20
ps
run qjackctl, press the 'connect' button, and the 'connections' window opens.
Here, in the audio panel, alsa_pcm on the right is your audio output, select both it, and the muse, (or zynaddsubfx mx44, fluidsynth etc) from the left side of the panel, and press the
'connect' button in this connections window. Click the midi tab, and vkeybd, your midi controller keyboard, and any softsynth you have started should be on the left and right sides, so select and connect as desired...MusE-1 should be in the left audio panel, MusE Sequencer in the left and right midi panels, and I assume if you have a synth loaded in Muse, connecting Muse will yield the desired sound output...(just installed muse, it shows up as I describe, so I have a new thang 2 twang! Have a great weekend!

---

### Post by engine on 2007-01-21
> Simple, step-by-step instructions would be very much appreciated!
and that's what you sent; thank-you.

However ... 
```
jackd -d alsa -r 44100
```
throws up the same sort of hw:0 problem:
[INDENT]JACK compiled with System V SHM support.
loading driver ..
apparent rate = 44100
creating alsa driver ... hw:0|hw:0|1024|2|44100|0|0|nomon|swmeter|-|32bit
control device hw:0
the playback device "hw:0" is already in use. Please stop the application using it and run JACK again
cannot load driver module alsa
no message buffer overruns
[/INDENT]
I already had all the software you mention loaded, too ...

More instructions please! <vbg>

---

### Post by sgx on 2007-01-21
the link at the bottom points to a page and kernel module for your Roland device(!)

Once you download the module, copy it to /dev and create an empty textfile /etc/modules, type in the name of the module, save the textfile, and run the command 
modprobe nameofmodule
which tells the kernel to load it. The textfile enables the kernel to see it after reboot...)
In the meantime, did you turn off arts or esd or any other sound system and 'system sounds' that might be installed and -on- ?
Have you gone into the bios and disabled un-needed things? 

For example, I  just started arts, the kde sound system, and when I type
jackd -d alsa -r 44100, I get -your- favorite error message too! I  know its 
a frustrating bugfarm, but go into gnome, kde, bios, and turn all that stuff
off...AC_97/motherboard soundchip, anything that might make a beep, anything that might steal some system energy  in a way that conflicts with jackd, any app like realplayer or amorok or totem that tries to be  the primadonna...once you have your sound, things can
be reintroduced one by one...don't give up. 

Have you re-installed  with the unit plugged in?

[http://michaelminn.com/linux/mmusbaudio/README.html](http://michaelminn.com/linux/mmusbaudio/README.html)

also, get a Knoppix, Mepis, Mandriva, and Suse live CDs for testing...its good luck

the google search 'roland um-1 linux' retrieved the above, and many other useful links!
hope this helps...

---

### Post by sgx on 2007-01-21
Just read the readme, you must follow his instructions to  build the module, they are easy
and normal, if you have gcc, automake, and binutils installed, should work...don't know if they are Ubuntu defaults...

---

### Post by engine on 2007-01-27
Clear instructions _and_ encouragement - thanks!

Next hurdle: I've checked (slocate) and do seem to have automake, gcc and binutils. I downloaded the mmusbaudio (once I'd worked round a few typos), and now I get some more messages:

```
me@box:/mmusbaudio$ sudo make
make -C /lib/modules/`uname -r`/build SUBDIRS=`pwd` modules
make: *** /lib/modules/2.6.15-27-386/build: No such file or directory.  Stop.
make: *** [mmusbaudio.ko] Error 2
```

I don't want to give up, but it's all pretty discouraging so far! I just don't know enough to interpret messages like this :-{

N

---

### Post by Coburn on 2007-02-03
Interesting...I am trying to get sound on vkeybd and ... say!  hw:0 is my _modem_ too!  Oops.

Well, sometime when I'm offline...

---

### Post by sgx on 2007-02-03
> **engine said:**
> Clear instructions _and_ encouragement - thanks!

Next hurdle: I've checked (slocate) and do seem to have automake, gcc and binutils. I downloaded the mmusbaudio (once I'd worked round a few typos), and now I get some more messages:

```
me@box:/mmusbaudio$ sudo make
make -C /lib/modules/`uname -r`/build SUBDIRS=`pwd` modules
make: *** /lib/modules/2.6.15-27-386/build: No such file or directory.  Stop.
make: *** [mmusbaudio.ko] Error 2
```

I don't want to give up, but it's all pretty discouraging so far! I just don't know enough to interpret messages like this :-{

N
This looks like a missing drawer that would contain 2.16.15-27-386...but I should have mentioned before, to install build-essential, and your kernel sourcecode too, which may both be installed by this command, 

sudo apt-get install build-essential linux-headers-`uname -r` 
which I dredged up on google in this thread

[http://justlinux.com/forum/archive/index.php/t-136106.html](http://justlinux.com/forum/archive/index.php/t-136106.html) 

your kernel-source should be available on your install cd/dvd too
I think the missing drawer will be installed as part of build-essential. But others with more experience
may offer better help (I hope so...)

also, in these threads listed below, there are misc tips to follow, remembering to replace any version numbers and naming conventions with ones used on your system. Some rpm info iis not applicable, I  get a notebook and copy what I think I''ll need, and  the info will be applicable in many future quests.
 
[http://www.linuxquestions.org/questions/showthread.php?s=&threadid=45094](http://www.linuxquestions.org/questions/showthread.php?s=&threadid=45094)
[http://www.linuxquestions.org/questions/showthread.php?s=&threadid=57108&highlight=k3b+option](http://www.linuxquestions.org/questions/showthread.php?s=&threadid=57108&highlight=k3b+option)
[http://www.linuxquestions.org/questions/showthread.php?t=71423](http://www.linuxquestions.org/questions/showthread.php?t=71423)
Out of the 3 steps
configure
make
make install
only make install needs root permissions...hope these threads lead to success!
If you can find luneo, and email him the code as an attachment, or give him the link, he
may build it for you if he has time, its worth a try...also, his custom realtime 2.6.19 kernel may be worth using on your system...

---

