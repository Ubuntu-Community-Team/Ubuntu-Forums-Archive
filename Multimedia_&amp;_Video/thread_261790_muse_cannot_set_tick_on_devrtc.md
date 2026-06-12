---
title: "muse cannot set tick on /dev/rtc"
date: 2006-09-20
forum: Multimedia &amp; Video
---

### Post by zettberlin on 2006-09-20
Hello  folks,

I am testing edgy right now and my impressions are mixed. I have Zynadd starting, loading patches and playing complex stuff without any xruns :-) though there are crackles that i blame a bit on the inferior soundchip of the Toshiba Tecra an wich i run it...

At the other hand I have a major Problem with both muse and rosegarden and /dev/rtc. They complain, that they cannot set tick on /dev/rtc even though i have set permissions and max-user-freq as it works just great in dapper (8192 for max-user-freq).

What can this be...

---

### Post by dolson on 2006-09-20
Can you paste the actual complaint, as given by Rosegarden?

---

### Post by zettberlin on 2006-09-21
This complaint is given as a Messagewindow at Startup:

Rosegarden was unable to find a high-resolution timing source for MIDI performance.
This may mean you are using a Linux system with the kernel timer resolution set too low. Please contact your Linux distributor for more information.


and here the console:

Default device name for this device is MIDI input system device
AlsaDriver::setCurrentTimer((auto))
System timer is only 250Hz, sending a warning
    Current timer set to "system timer" with timer checks
    WARNING: using system timer with only 250Hz resolution!
AlsaDriver::initialiseMidi -  initialised MIDI subsystem

But the whole thing has changed with the yesterday night edgy update: now it connects with no problems to jack (wich it did not before) and it does not even try to get /dev/rtc.

hmmmm...
But now muse tells me this:

Trying RTC timer...
RtcTimer::setTimerFreq(): cannot set tick on /dev/rtc: Invalid argument
  precise timer not available
Trying ALSA timer..

This was the same message I get yesterday from RG too...

Timer is set like this:

 #sudo echo 8192 > /proc/sys/max-user-freq

---

### Post by zettberlin on 2006-09-21
found on the RG-Website:

[I]5.6.  What does "System timer resolution is too low" mean?

If you see this message in an error dialog when Rosegarden starts up, then you are probably using a Linux kernel that doesn't offer sufficiently high-resolution system timers for MIDI use.

Rosegarden uses ALSA sequencer queue scheduling (inside the Linux kernel) for its MIDI output. The sequencer queue can use a variety of timing sources, of which the default is the kernel system timer. The kernel system timer was 1000Hz in Linux 2.6 kernels up to 2.6.12, but as of 2.6.13 it's now 250Hz in mainline kernels. This is not good enough for good MIDI timing. 
[/I]

So it looks, like the edgy-kernel does not offer what we need here ?

---

### Post by zettberlin on 2006-09-21
This complaint is given as a Messagewindow at Startup:

Rosegarden was unable to find a high-resolution timing source for MIDI performance.
This may mean you are using a Linux system with the kernel timer resolution set too low. Please contact your Linux distributor for more information.


and here the console:

Default device name for this device is MIDI input system device
AlsaDriver::setCurrentTimer((auto))
System timer is only 250Hz, sending a warning
    Current timer set to "system timer" with timer checks
    WARNING: using system timer with only 250Hz resolution!
AlsaDriver::initialiseMidi -  initialised MIDI subsystem

But the whole thing has changed with the yesterday night edgy update: now it connects with no problems to jack (wich it did not before) and it does not even try to get /dev/rtc.

hmmmm...
But now muse tells me this:

Trying RTC timer...
RtcTimer::setTimerFreq(): cannot set tick on /dev/rtc: Invalid argument
  precise timer not available
Trying ALSA timer..

This was the same message I get yesterday from RG too...

Timer is set like this:

 #sudo echo 8192 > /proc/sys/max-user-freq

edit:
found on the RG-Website:

[I]5.6.  What does "System timer resolution is too low" mean?

If you see this message in an error dialog when Rosegarden starts up, then you are probably using a Linux kernel that doesn't offer sufficiently high-resolution system timers for MIDI use.

Rosegarden uses ALSA sequencer queue scheduling (inside the Linux kernel) for its MIDI output. The sequencer queue can use a variety of timing sources, of which the default is the kernel system timer. The kernel system timer was 1000Hz in Linux 2.6 kernels up to 2.6.12, but as of 2.6.13 it's now 250Hz in mainline kernels. This is not good enough for good MIDI timing. 
[/I]

So it looks, like the edg-kernel does not offer what we need here ?

---

### Post by dolson on 2006-09-21
WARNING: using system timer with only 250Hz resolution!

Run this: grep CONFIG_HZ /boot/config-`uname -r`

You will see what HZ your kernel is set to. In Dapper, they have regressed and changed it to 250Hz suddenly. Kernel 2.6.15-23 is the last kernel I had with Dapper that had used 1000Hz timers. I am missing 2.6.15-24, but at 2.6.15-25 it was switched down to 250Hz. This has stuck through Edgy too.

You should probably open bug reports about this because they don't feel that users care about having hi-res timers, as nobody is complaining.

Also, I don't know where you heard about that max-user-freq thing, but on my Edgy system, it is located in /proc/sys/dev/rtc/max-user-freq. And it has a default value of 64.

Since sudo doesn't let you echo into files as root, you can change it with:
sudo sysctl -w dev.rtc.max-user-freq=1024

If you want it at bootup, you can put dev.rtc.max-user-freq=1024 in /etc/sysctl.conf.

---

### Post by zettberlin on 2006-09-21
> **dolson said:**
> WARNING: using system timer with only 250Hz resolution!



this give the answer:
CONFIG_HZ 250
#CONFIG_HZ 1000 is not set

> **dolson said:**
> 

You should probably open bug reports about this because they don't feel that users care about having hi-res timers, as nobody is complaining.


i´ll do

> **dolson said:**
> 
Also, I don't know where you heard about that max-user-freq thing, but on my Edgy system, it is located in /proc/sys/dev/rtc/max-user-freq. And it has a default value of 64.


Same here - I had a typo in the path, damned drag/drop keeps me from learning to be exact ;-)

> **dolson said:**
> 
Since sudo doesn't let you echo into files as root, you can change it with:
sudo sysctl -w dev.rtc.max-user-freq=1024


But it does: i use sudo echo on dapper and it works...

> **dolson said:**
> 
If you want it at bootup, you can put dev.rtc.max-user-freq=1024 in /etc/sysctl.conf.

Thanks for the hint, probably more standard-compliant then my way (I have the echo-line in /etc/boot/misc)

Well, thanks for the hints so far. I begin more and more to put my hope into Mubuntu. Though I would prefer a system fpor everybody that works for musicpeople too...

---

### Post by dolson on 2006-09-21
So I am adding this to the wiki now, as hi-res timers are needed, IMHO. And this gets around recompiling, if I understand correctly...

Also, about echo as root:

dana@jadis:~$ sudo echo blah >> /etc/sysctl.conf
bash: /etc/sysctl.conf: Permission denied

---

### Post by zettberlin on 2006-09-21
> **dolson said:**
> So I am adding this to the wiki now, as hi-res timers are needed, IMHO. And this gets around recompiling, if I understand correctly...

I fied a bug report on this at launchpad, will see, what it yields

> **dolson said:**
> 
Also, about echo as root:

dana@jadis:~$ sudo echo blah >> /etc/sysctl.conf
bash: /etc/sysctl.conf: Permission denied

you are right again - I was un-precise once more. I use sudo bash to get a rootshell, then the echo-stuff works.

---

### Post by dolson on 2006-09-21
You can also use: sudo su -c 'echo blah blah >> /file'
or
echo blah blah | sudo tee -a /file
(I think)

---

### Post by Pettman on 2006-10-30
Does this echo thing last over re-boot?

---

### Post by corevette on 2007-02-16
did any of you get this working? if so please tell me how by replying...or preferably email: [email]corevette@gmail.com[/email]

---

### Post by _user1_ on 2007-02-18
I also would like to know if anyone figured out how to resolve this?  thanks

---

