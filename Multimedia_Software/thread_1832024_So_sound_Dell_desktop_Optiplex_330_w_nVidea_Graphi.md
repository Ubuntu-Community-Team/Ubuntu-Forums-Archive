---
title: "So sound: Dell desktop Optiplex 330 w nVidea Graphics card"
date: 2011-08-24
forum: Multimedia Software
---

### Post by nazaroo2 on 2011-08-24
Okay. This had sound working previously.


System / OS:** Ubuntu 10.04 (lucid)**
Kernel Linux 2.6.32-30-generic
**GNOME 2.30.**2
Hardware
**Memory: 2.0 GB**
Proc. 0 Intell Dual E2220 @ 2.4 GHz
Proc. 1 Intell Dual E2220 @ 2.4 GHz

Graphics Card:
**GeForce 8400 GS** (being run as dual monitor for productivity)

nothing else special except **wireless card** and xtra storage drive.
Using **FIrefox**.


Had some early (on OS install) sound problems, but these went away after installing Alsa-mixer.

Still refused to play some online movies, but hey, got a lot of work done, and** youtube worked** (off and on, with updates).

Son tried to install online free Linux(Wine) MMORPG.  *** Lord of the Rings Online*** (under **Wine**)

Somehow [COLOR=Red]***Alsa mixer now opens a window that remains blank***[/COLOR] (no sliders).

(Also, tried to install **Skype**, which didn't work properly with microphone at first *roll eyes* but son got it working... 
but headphones only worked in back-plugs, so have to manually unplug speakers to use Skype - stupid?)

At one point, got high-pitched wining sound instead of sound.
(One more observation: before Alsa-mixer died, microphone rapidly toggled on/off and couldn't wbe switched off:
Something to do with either Skype or MMORPG software. )
Then that stopped(?)  when I went into Wine-Config and switched back to 'Alsa" sound (maybe).


When updating and trying to reinstall alsa mixer from terminal, I get this message:

```


Couldn't find package linux-alsa-driver-modules-2.6.32-30-generic


```How can I have working sound again?


back to being frustrated monkey ...
nazaroo

P.S. 

I tried this from another thread just now:
> **Re: No sound & too many possibilities here**             
                                                                Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
     Code:
     wget [http://www.alsa-project.org/alsa-info.sh](http://www.alsa-project.org/alsa-info.sh) -O alsa-info.sh && bash alsa-info.sh 
[COLOR=Red]Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"][/COLOR]
I don't understand the last bit (in red), but I ran the line anyway in a terminal:

I got this on the terminal screen:
> 
cat: /proc/asound/version: No such file or directory
grep: /proc/asound/cards: No such file or directory
cat: /proc/asound/cards: No such file or directory
cat: /proc/asound/modules: No such file or directory
ls: cannot access /dev/snd/*: No such file or directory
grep: /proc/asound/cards: No such file or directory
/sbin/alsactl: save_state:1502: No soundcards found...
cat: /tmp/alsa-info.M5YVjnorLo/alsactl.tmp: No such file or directory


---

### Post by nazaroo2 on 2011-08-24
I ran[COLOR=Red]** lspci -v**[/COLOR] in terminal and got:


```

00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 01)
    Subsystem: Dell Device 0220
    Flags: bus master, fast devsel, latency 0, IRQ 11
    Memory at dfffc000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: [50] Power Management version 2
    Capabilities: [60] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
    Capabilities: [70] Express Root Complex Integrated Endpoint, MSI 00
    Capabilities: [100] Virtual Channel <?>
    Capabilities: [130] Root Complex Link <?>
    Kernel modules: snd-hda-intel

```

- which I presume is my soundcard.

---

### Post by nazaroo2 on 2011-08-24
I tried to perform the functions on this page:
[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

but ran into a snag when it came to:
> 
**[SIZE=2]sudo dpkg-reconfigure alsa-source[/SIZE]**

This package opened up. (blue box),
allowed me to choose "yes" and "yes" (or "no")
but there was no box "all" as described in page to unclick.
I did get a list of two different Intel modules though:

intel8x0,  (debugging), and
intel8x0m (non-debugging).

I couldn't get these to work however, or may not even have the files....

help!

---

### Post by nazaroo2 on 2011-08-24
I tried this:

>   [B] 

   sudo modprobe snd-  [/B]

Now, press the **TAB** key **BEFORE** pressing the **ENTER** key to see a list of modules. Try to find the module that matches the driver you found in step 3.

But there must be something wrong. 
I get an error message:
FATAL: Module snd_ not found.

When I try without the "-", I get nothing but a prompt. (no error).
When I try without "-" but add a TAB, nothing different happens. 

Something seems to be wrong with these instructions....

.........AAAAArrrrrrrrrrgh!

---

### Post by nazaroo2 on 2011-08-24
I was able to find a file from INTEL here:

[http://downloadcenter.intel.com/confirm.aspx?httpDown=http://downloadmirror.intel.com/7236/eng/intel8x0-alsa-1.0.1.sh.gz&lang=eng&Dwnldid=7236](http://downloadcenter.intel.com/confirm.aspx?httpDown=http://downloadmirror.intel.com/7236/eng/intel8x0-alsa-1.0.1.sh.gz&lang=eng&Dwnldid=7236)

File from Intel:
 intel8x0-alsa-1.0.1.sh

It is some kind of script file I suppose. 
I copied into Downloads, and into /etc/usr/ALSA 
after unzipping it, but I don't know what to do next.

Is this the name I am supposed to type after 

[B]sudo modprobe snd-

i.e., 

[/B][B]sudo modprobe snd-intel8x0-alsa-1.0.1.sh

????

What folder should I be sitting in while doing this from the terminal?

Why are things so difficult?

[/B]

---

