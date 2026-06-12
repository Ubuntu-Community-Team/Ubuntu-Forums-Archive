---
title: "Disabled audio device"
date: 2007-06-06
forum: Multimedia &amp; Video
---

### Post by moeFinley on 2007-06-06
I've just bought a Thinkpad T41 of eBay and I'm sure the sound was working when I first installed Fiesty.  But now nothing seems to get it to work.  

I noticed that it's disabled but I don't know what this means or how to change it?

```
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
        Subsystem: IBM Unknown device 0537
        Flags: bus master, medium devsel, latency 0, IRQ 5
        I/O ports at 1c00 [size=256]
        I/O ports at 18c0 [size=64]
        Memory at c0000c00 (32-bit, non-prefetchable) [size=512]
        Memory at c0000800 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

```

Thanks for any help

---

### Post by mlind on 2007-06-06
are you sure you don't have any important sound channels muted?
Try launching **alsamixer** from a terminal and check this out.

---

### Post by eggdeng on 2007-06-06
Not completely sure this is the same chip as mine
```
Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
```
but you might want to check out [http://ubuntuforums.org/showthread.php?t=314383](http://ubuntuforums.org/showthread.php?t=314383)
Have you checked your user is a member of the audio group?

---

### Post by moeFinley on 2007-06-07
Thanks for the help.  I'm at work at the moment so I'll try some of the things in that thread this evening.

How do I check if I'm a member of the audio group?

---

### Post by eggdeng on 2007-06-07
System -> Administration ->Users and Groups, select the Groups tab, scroll down to audio and click Properties. Your username should appear in the members field.

---

### Post by moeFinley on 2007-06-08
Under my account properties - user privileges I have 'use audio devices' checked and I couldn't find anything else related.  I tried adding 'options snd-hda-intel model=laptop-eapd' because I guess IBM and Lenovo are the same thing?  But none of this worked.

So I tried installing the latest ALSA but that went horribly wrong and now it can't even find any audio devices :(

Here the compile error got after running make:
```
from /home/moefinley/alsa-driver-1.0.14rc1/acore/pcm.c:1:
/home/moefinley/alsa-driver-1.0.14rc1/include/sound/pcm.h: In function &#8216;snd_pcm_mmap_data_open&#8217;:
/home/moefinley/alsa-driver-1.0.14rc1/include/sound/pcm.h:977: error: dereferencing pointer to incomplete type
/home/moefinley/alsa-driver-1.0.14rc1/include/sound/pcm.h: In function &#8216;snd_pcm_mmap_data_close&#8217;:
/home/moefinley/alsa-driver-1.0.14rc1/include/sound/pcm.h:983: error: dereferencing pointer to incomplete type
make[3]: *** [/home/moefinley/alsa-driver-1.0.14rc1/acore/pcm.o] Error 1
make[2]: *** [/home/moefinley/alsa-driver-1.0.14rc1/acore] Error 2
make[1]: *** [_module_/home/moefinley/alsa-driver-1.0.14rc1] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-16-generic'
make: *** [compile] Error 2
```

What's the best way to get ALSA back the way it was.  I tried a reinstall in Synaptic but it didn seem to make any difference.

---

### Post by eggdeng on 2007-06-08
If you got an error running make, then you never installed the new driver, right? So you've been re-installing the driver you had anyway.The compile errors may be down to your not having installed a package called build-essential first. ```
sudo apt-get install build-essential
```
Sorry not to be of more help but if you did have that package installed, it looks as if you will have to start over again  - the general help section at [http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide](http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide)
is probably a good place to start.

---

### Post by Espionage724 on 2007-06-08
lol thank you. I have a HDA Intel sound card in my computer and I used alsamixer and fixed it :)

---

### Post by moeFinley on 2007-06-08
> **Espionage724 said:**
> lol thank you. I have a HDA Intel sound card in my computer and I used alsamixer and fixed it :)

I went through all the controls and made sure nothing was muted?  Which setting did you change to get your sound working?

I did 'sudo apt-get install build-essential' before the build so I guess it was something else.  I decided to re-install so I could get ALSA back up and running and thought why not give Kubuntu a go.  I did and everything is working.

I don't know if I'll keep it though, I'm used to Gnome.

---

### Post by moeFinley on 2007-06-09
I've just installed LinuxMint and everything is working perfectly.  LinuxMint isn't that different, it's just Fiesty with a few nice extras.  So why is there a difference trying to use an sound device in an old laptop?

Anyway I'm happy now ;)

---

### Post by moeFinley on 2007-06-10
I just noticed something weird which hopefully someone can shed some light on.  When I booted my latop back up from hiberantion the sound didn't work even though everything looked fine?!  Even when I did a full restart it didn't come back?

I shut down, waited a bit and booted back up and my sound was back.  This suggests that something is changed with the hardware in hibernation?  What could that be?

---

### Post by mlind on 2007-06-10
> **moeFinley said:**
> I just noticed something weird which hopefully someone can shed some light on.  When I booted my latop back up from hiberantion the sound didn't work even though everything looked fine?!  Even when I did a full restart it didn't come back?

I shut down, waited a bit and booted back up and my sound was back.  This suggests that something is changed with the hardware in hibernation?  What could that be?

I recall seeing a bug in launchpad in which user(s) reported sound not working correctly after hibernation. I'm not 100% sure, but you should search launchpad.net about the bug report, it could be a kernel problem.

---

### Post by moeFinley on 2007-06-10
I found the bug report on Launchpad.  Looks like it is a kernel issue.  
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/25896]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/25896")

I guess I can wait for a fix and do without hibernation for the time being.

---

