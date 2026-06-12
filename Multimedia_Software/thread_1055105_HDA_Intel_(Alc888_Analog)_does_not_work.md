---
title: "HDA Intel (Alc888 Analog) does not work"
date: 2009-01-30
forum: Multimedia Software
---

### Post by nascentmind on 2009-01-30
Hi,
   I have installed ubuntu intrepid and I get this error from phonon when kde starts:

"the audio playback device HDA Intel (ALC888 Analog) does not work. Falling back to HDA ATI HDMI,ATI HDMI (HDMI Audio Ouput)" .

My sound does not work at all.

Kernel version : 2.6.27-11-generic

aplay -l gives


**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC888 Digital [ALC888 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

arecord -l gives :

**** List of CAPTURE Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 2: ALC888 Analog [ALC888 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


cat /proc/asound/cards gives :
0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xfe8f8000 irq 22
 1 [HDMI           ]: HDA-Intel - HDA ATI HDMI
                      HDA ATI HDMI at 0xfe9ec000 irq 17

cat /proc/asound/modules gives:
0 snd_hda_intel
 1 snd_hda_intel

 Please help me find a solution to this problem.

Thanks in advance.

---

### Post by nascentmind on 2009-02-02
SOLVED:

Changing to 6stack-dig under models worked for me.

Add -> options snd-hda-intel model=6stack-dig probe_mask=1 <-at the end of the line in file /etc/modprobe.d/alsa-base

---

### Post by fougas on 2009-05-03
I had the same i think problem with HD Intel (AD198x Analog) device and it seems that after adding the line you suggest the problem is gone. Thank you :)

---

### Post by rashko on 2009-06-13
Had the same problem with STAC92xx Analog, Kubuntu 9.04
Problem seems to be solved with that line. Thanks a lot!

EDIT: no sorry, still randomly have the problem from logon to logon.

---

### Post by nascentmind on 2009-06-14
If you are using kubuntu and then there is a bug in kubuntu notifications. Also are you getting your sound normally now?

---

### Post by ythaaa on 2009-07-06
may i know if someone has found the solution to this problem?     

i also experience it. after the notification, my sound does not work anymore.

---

### Post by nascentmind on 2009-07-06
Have you tried the above steps to make it work?

---

### Post by ythaaa on 2009-07-06
yes i have tried..... however... initially i thought is ok... but then after a while, the problem occur rather randomly.... sometimes when i start amarok the notification appear.... sometimes when i just log into kdm then the notification appear......  and everytime the notification appear, my sound does not work....

---

### Post by nascentmind on 2009-07-06
Make sure you don't have 2 applications sharing sound. It seems like a pulseaudio problem.

---

### Post by ythaaa on 2009-07-06
hi nascentmind,

i am not too sure what you mean by 2 applications sharing sound... can you elaborate more?? sorry....... i m rather new... i attached my multimedia setting snapshot where i see the pulseradio... 

i try to switch pulseradio from third to second but the problem still exist....

---

### Post by mattlach on 2009-07-15
Hmm..

I had sometimes sound and sometimes just crackeling until I added this module as described here.

Now I have no devices found.

My motherboard has the alc888 chipset.

Any ideas?

Thanks,
Matt

---

### Post by nascentmind on 2009-07-16
Matt,
    Can you please post your aplay -l?

---

### Post by mattlach on 2009-07-16
> **nascentmind said:**
> Matt,
    Can you please post your aplay -l?

Sure thing.

I removed the line above already, and I have sound back (sometimes, sometimes I just have static), but it only works if I configure it to use OSS.

Alsa produces nothing but error messages (Can not open audio device)

Aplay - l outputs the following:

```

aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC888 Digital [ALC888 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

Thank you for your help!

---

### Post by dajashby on 2010-03-03
I've got pretty much the same problem in Karmic (but different hda intel chip).  I succeeded in getting Amarok to work for about 2 days after I installed kubuntu (installed ubuntu and then added the kubuntu desktop), but then started getting these problems after I installed VirtualBox.  This may be a complete coincidence - it occurs without running VirtualBox.  I get the kubuntu startup sound, but after that no application produces sound at all, until I shut down.  Sound works okay when I log into gnome instead, but I prefer kde.

---

### Post by ak2766 on 2010-03-05
> **dajashby said:**
> ...  I get the kubuntu startup sound, but after that no application produces sound at all, until I shut down.  **Sound works okay when I log into gnome instead, but I prefer kde**.

Interesting you say that: I also run Ubuntu (not KUbuntu) and noted that when sound quit working and Kaffeine was shutdown, there was a remnant KDE related process hanging around the process tree as indicated below:
```

$ ps -ef|grep kaff
tkb       4572  4556  0 17:41 ?        00:00:00 kdeinit4: kio_file [kdeinit] file local:/tmp/ksocket-tkb/klauncherMT4557.slave-socket local:/tmp/ksocket-tkb/kaffeineKP4553.slave-socket

```After killing this application and restarting Kaffeine, sound was magically back!  Just though I'd mention that a reboot is not necessary if you are running Kaffeine under Gnome!

Cheers,
tkb.

---

### Post by heart_of_steel on 2010-05-05
I'm having the same problem periodically in Ubuntu Lucid with Amarok (and a different chipset). I'm quite new to Linux but I suspect it could be because Amarok seems to like KDE and I am running with Gnome, whatever that is.

---

### Post by gugel on 2010-05-10
I had the same problem and the fix suggested from ak2766 to kill the dangling processes worked for me. I want to elaborate on this solution so newbees can apply the workaround until the issue is fixed in (k)ubuntu.

1) Find the application which holds the lock for the audio device. In my case it was amarok, for others it may be kaffeine. Think about which sound-enabled application you use a lot.

2) Close these applications.

3) Find the blocking process. On a console, type

```
ps -ef|grep amarok
```

the output should be something like

```
username    2069  1770  0 12:11 ?        00:00:00 kdeinit4: kio_file [kdeinit] file local:/tmp/ksocket-username/klauncherMT1771.slave-socket local:/tmp/ksocket-username/amarokWy2002.slave-socket
```

You see that there is something in the process table about amarok which should not be there as the application is closed.

4) Kill the process. Execute on a console

```
kill -9 2069
```

The parameter -9 will kill the process forcefully and 2069 is the process id (pid) of the dangling process. The process id of your process is the first number on the output of the previous ps command.

These steps should help to enable sound again. Try it by starting the application in question and listen.

Regards,

Ricky

---

### Post by balthabuntu on 2010-05-14
Hello,

I've got the same problem with chip Alc888 and Kubuntu 10.4.
First I found a url's driver list here:
[http://doc.ubuntu-fr.org/audio_chipset_realtek](http://doc.ubuntu-fr.org/audio_chipset_realtek)

The trouble was resolved by download and install the good driver realtek-linux-audiopack-5.15, from Realtek website.

[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=14&PFid=24&Level=4&Conn=3&DownTypeID=3&GetDown=false](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=14&PFid=24&Level=4&Conn=3&DownTypeID=3&GetDown=false)

you must install manually, all is explain in the Readme.txt
It's running for me,
Hope it can help...

---

### Post by edkwok on 2010-08-27
When I upgrade to Kubuntu 10.04 the HDA Intel (ALC727 Analog) does not work message came. The sound on my Netbook was very low, and can not hardly hear it.  I follow the recommendation here and added a line in my /etc/modprobe.d/alsa-base.conf with options snd-hda-intel model=6stack-dig probe_mask=1 <-at the end of the line in file /etc/modprobe.d/alsa-base. It resolved my problem, but I have to use the "model=2stack-dig", the 6stack-dig didn't work. I think because I don't have 6 channels sound on this netbook.

---

### Post by sasky84 on 2011-12-18
I have the same problem. Message pops up, but everything is OK with the sound. weird!

---

