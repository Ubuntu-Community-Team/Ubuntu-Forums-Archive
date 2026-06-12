---
title: "No Sound on Acer Aspire 4930 with Ubuntu 10.10"
date: 2010-11-25
forum: Multimedia Software
---

### Post by Iwada on 2010-11-25
I just Installed Ubuntu 10.10 on my Acer Aspire 4930 Laptop. Every other thing works well apart from the Fact that there is no Sound. Checked and Tried Most Solutions rendered to no avail.Had 10.04 Working with sound. Any Help will be appreciated.

---

### Post by Suhaib58 on 2010-11-25
> **Iwada said:**
> I just Installed Ubuntu 10.10 on my Acer Aspire 4930 Laptop. Every other thing works well apart from the Fact that there is no Sound. Checked and Tried Most Solutions rendered to no avail.Had 10.04 Working with sound. Any Help will be appreciated.

I have a similar problem installed ubuntu 10.04 on dell i7. no sound..any one could suggest how to rectify

---

### Post by lidex on 2010-11-27
> **Iwada said:**
> I just Installed Ubuntu 10.10 on my Acer Aspire 4930 Laptop. Every other thing works well apart from the Fact that there is no Sound. Checked and Tried Most Solutions rendered to no avail.Had 10.04 Working with sound. Any Help will be appreciated.

Install or upgrade?
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---

### Post by kurtis99 on 2011-03-03
Got same issue after clean install to 10.10.

Here is my alsa-log
[http://www.alsa-project.org/db/?f=e8eef03f2140b719480699ddc6c064d622585dce](http://www.alsa-project.org/db/?f=e8eef03f2140b719480699ddc6c064d622585dce)

But I think that it could be kernel related issue, because when I choose to boot with 2.6.32-xx kernel, there is sound, but when I boot with 2.6.35, sound doesnt work at all.

---

### Post by lidex on 2011-03-04
> **kurtis99 said:**
> Got same issue after clean install to 10.10.

Here is my alsa-log
[http://www.alsa-project.org/db/?f=e8eef03f2140b719480699ddc6c064d622585dce](http://www.alsa-project.org/db/?f=e8eef03f2140b719480699ddc6c064d622585dce)

But I think that it could be kernel related issue, because when I choose to boot with 2.6.32-xx kernel, there is sound, but when I boot with 2.6.35, sound doesnt work at all.

Hmmm. Did you install backports or upgraded alsa modules on that kernel perhaps? What is this putput:
```
dpkg -l | grep "alsa"
```

---

### Post by kurtis99 on 2011-03-05
I've upgraded from 10.04 to 10.10 and 2.6.32 kernel left from previous Ubuntu version

Here is output:
```
ii  alsa-base                            1.0.23+dfsg-1ubuntu4                              ALSA driver configuration files
ii  alsa-utils                           1.0.23-2ubuntu3.4                                 Utilities for configuring and using ALSA
ii  bluez-alsa                           4.69-0ubuntu2                                     Bluetooth audio support
ii  gstreamer0.10-alsa                   0.10.30-2                                         GStreamer plugin for ALSA
```

---

### Post by lidex on 2011-03-06
Try resetting your pulse configuration.
Using a Terminal="Applications->Accessories->Terminal"
```

rm -r ~/.pulse ~/.asound* ~/.pulse-cookie 
sudo rm /etc/asound.conf
```
**Reboot**

---

### Post by kurtis99 on 2011-03-08
I've tried to do as you said but it doesnt help.

But some other issue seems strange to me. I wanted to test direct output to /dev/dsp and found that on 2.6.35 kernel there is no /dev/dsp. I booted again to 2.6.32 and /dev/dsp existed. 
Can this cause a problem with sound?

---

### Post by immaculance on 2011-03-08
I'm having a similar issue.  Seems like after my last update (been running 10.10 for a month or so), all sound has dropped out entirely! :( I booted the same machine to my Win7 disk, and audio is working just fine for everything under that OS, so I'm pretty certain it's not a hardware issue.  Rebooting and cold booting do nothing to resolve the issue.  Playing with settings & such is a no-go as well.

I've tried toggling between my on-board HDMI audio & my CA0106 Soundblaster card, but nothing.  Previously, when sound went out (it's always been finicky in Ubuntu), I could toggle between outputs and it would reset to my Soundblaster card.

There don't appear to be any drivers installed n stuff for this card, so I'm at a total loss on how to begin troubleshooting this from an Ubuntu OS perspective.  Any assistance would be greatly appreciated (first steps).

---

### Post by atentik on 2011-03-08
I have having similar issue. I tried installing OSS4, re-installing alsa-utils and re-installing pulseaudio but to no avail. Is there is simple solution to this no sound problem? When mine starts... is says Starting Open Source Sound .......[[COLOR="Red"]Failed[/COLOR]]:o

---

### Post by immaculance on 2011-03-08
I did some digging myself with lidex's link to the Ubuntu-bug audio link, which takes you to the following wiki:

[https://wiki.ubuntu.com/DebuggingSoundProblems](https://wiki.ubuntu.com/DebuggingSoundProblems)

I ran a debug on it and provided the report & opened a bug in launchpad.  Looks like others are experiencing the same problem, specifically for my sound card as well; but I've already concluded that it's not a hardware issue entirely, as mine still functions in my Win7 environment.  This repeated instability of sound leaves a little to be desired with this OS.

Just sharing what I'm doing so far.  Hopefully one of the community developers will be able to assist.

---

### Post by immaculance on 2011-03-08
> In the interim - as a workaround - try this to get your sound back:
```
sudo alsa force-reload
```

Tried it... Didn't work.

---

```
**sudo fuser -v /dev/dsp* /dev/snd/* /dev/seq***
Specified filename /dev/dsp* does not exist.
Specified filename /dev/seq* does not exist.
                     USER        PID ACCESS COMMAND
/dev/snd/controlC0:  jason      8409 F.... pulseaudio
/dev/snd/pcmC0D0p:   jason      8409 F...m pulseaudio
/dev/snd/pcmC0D1p:   jason      8409 F...m pulseaudio
/dev/snd/pcmC0D2p:   jason      8409 F...m pulseaudio
/dev/snd/timer:      jason      8409 F.... pulseaudio
```

```
**pkill pulseaudio; sleep 2; pulseaudio -vv**
I: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
I: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
D: core-rtclock.c: Timer slack is set to 50 us.
D: core-util.c: RealtimeKit worked.
I: core-util.c: Successfully gained nice level -11.
I: main.c: This is PulseAudio 0.9.21-63-gd3efa-dirty
D: main.c: Compilation host: i686-pc-linux-gnu
D: main.c: Compilation CFLAGS: -g -O2 -g -Wall -O3 -Wall -W -Wextra -pipe -Wno-long-long -Winline -Wvla -Wno-overlength-strings -Wunsafe-loop-optimizations -Wundef -Wformat=2 -Wlogical-op -Wsign-compare -Wformat-security -Wmissing-include-dirs -Wformat-nonliteral -Wold-style-definition -Wpointer-arith -Winit-self -Wdeclaration-after-statement -Wfloat-equal -Wmissing-prototypes -Wstrict-prototypes -Wredundant-decls -Wmissing-declarations -Wmissing-noreturn -Wshadow -Wendif-labels -Wcast-align -Wstrict-aliasing=2 -Wwrite-strings -Wno-unused-parameter -ffast-math -Wp,-D_FORTIFY_SOURCE=2 -fno-common -fdiagnostics-show-option
D: main.c: Running on host: Linux i686 2.6.35-27-generic #48-Ubuntu SMP Tue Feb 22 20:25:29 UTC 2011
D: main.c: Found 2 CPUs.
I: main.c: Page size is 4096 bytes
D: main.c: Compiled with Valgrind support: no
D: main.c: Running in valgrind mode: no
D: main.c: Running in VM: no
D: main.c: Optimized build: yes
D: main.c: All asserts enabled.
I: main.c: Machine ID is facd0ce3e07ab66df6d123654b51c38f.
I: main.c: Session ID is facd0ce3e07ab66df6d123654b51c38f-1299555129.76587-1280268204.
I: main.c: Using runtime directory /home/jason/.pulse/facd0ce3e07ab66df6d123654b51c38f-runtime.
I: main.c: Using state directory /home/jason/.pulse.
I: main.c: Using modules directory /usr/lib/pulse-0.9.21/modules.
I: main.c: Running in system mode: no
E: pid.c: Daemon already running.
E: main.c: pa_pid_file_create() failed.
```

---

### Post by lidex on 2011-03-08
@immaculance
Can you post the link to that bug report please?
One possible work-around:
```
echo "options snd-hda-intel model=acer-aspire-4930g" | sudo tee -a /etc/modprobe.d/alsa-base.conf
``` **Reboot**

Also I am seeing problems with suspend/hibernate killing sound and a reboot not re-initializing it. Try booting into windows then restarting into ubuntu without shutting down. Or cycling suspend/resume.

---

### Post by immaculance on 2011-03-09
I shouldn't have tried to hijack this thread.  I don't even have an Acer.  I'm tracking my issues under this other more generic thread that has a bit more activity on it:

[http://ubuntuforums.org/showthread.php?t=1593095](http://ubuntuforums.org/showthread.php?t=1593095)

One question though... You say you're seeing problems with suspend/hibernate killing sound & a reboot not re-initializing it... Are you saying that you're observing this based on some of the feedback I posted above, or you're saying that you're experiencing this yourself?  I assume it's the former, but not sure based on how you worded your statement.  I definitely have this problem on my windows session, but I heard that's a known Win7 issue that hasn't been addressef (another reason why I'm trying to totally jump ship from MS & Win - but I'm still filling little gaps with Ubuntu to get me off it, and this new no sound hurdle is not helping me transition off any quicker).

Thanks for your time & assistance :]

---

### Post by imstatic on 2011-04-02
Hi Guys!!!
After hours of searching, someone finally gave me the answer. I was seriously considering returning to windows 7 with this sound issue.

[https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/647970](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/647970)

Thanks gbhuvanesh!!

By the way, if anyone knows how to get the fingerprint to work, please send me a message.

[gbhuvanesh]("https://launchpad.net/%7Ebhuvaneshksg")             wrote             on 2010-10-12:                                                             [ #7]("https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/647970/comments/7")                                                        Hi langmarp, you could try modifying the alsa-base.conf
 In terminal, type:    sudo nano /etc/modprobe.d/alsa-base.conf
 Add the following 2 lines at the end of the file, save and restart.
 alias snd-card-0 snd-hda-intel
options snd-hda-intel model=auto
 after this change, sound playback now works fine on my Acer 4930  using Ubuntu 10.10.  Since you have a different Acer model, your results  might vary.
 If this doesn't work, try changing the value of model to 'acer' instead of 'auto'.
 If nothing works, you might try installing the fix mentioned here
 [https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/617647/comments/27](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/617647/comments/27)
 Though I did have any success (Acer 4930), folks having Acer 7736G  reported positive results after installing the above mentioned fix.

---

### Post by lidex on 2011-04-02
Any helpful information you guys come up with 
for this model would be most appreciated by others having issues with same.
If so inclined you can post that info here:
[http://www.linlap.com/wiki/acer+aspire+4930g](http://www.linlap.com/wiki/acer+aspire+4930g)

---

