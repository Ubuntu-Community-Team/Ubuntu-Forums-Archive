---
title: "Soundblaster Live 5.1"
date: 2009-04-15
forum: Multimedia Software
---

### Post by achilleez13 on 2009-04-15
Hi all,I'm unfortunately having multiple problems installing this card in 8.10 .On the surface things appear to be fine I have sound,I can connect my guitar through the front panel,I have full control of volume over all the channels,(well all the ones I've tried).I first noticed a problem when I ran Hydrogen.The bass drum sounded terrible just not there at all,then I found I couldn't start Jack without being root.When I ran Alsamixer it only displays two channels one for playback and one for capture.So I went to the comprehensive sound problems thread and went through it step by step.The first thing that went wrong was when I entered sudo modprobe snd- I got FATAL: Module snd_ not found.So I tried re-installing using module assistant
and got the following :-

 /usr/src/modules/alsa-driver/acore/info.c: In function                     &#9618;
 &#9474; ‘resize_info_buffer’:                                                      &#9618;
 &#9474; /usr/src/modules/alsa-driver/acore/info.c:90: error: implicit              &#9618;
 &#9474; declaration of function ‘PAGE_ALIGN’                                       &#9618;
 &#9474; make[5]: *** [/usr/src/modules/alsa-driver/acore/info.o] Error 1           &#9618;
 &#9474; make[4]: *** [/usr/src/modules/alsa-driver/acore] Error 2                  &#9618;
 &#9474; make[3]: *** [_module_/usr/src/modules/alsa-driver] Error 2                &#9618;
 &#9474; make[3]: Leaving directory `/usr/src/linux-headers-2.6.27-11-generic'      &#9618;
 &#9474; make[2]: *** [compile] Error 2                                             &#9618;
 &#9474; make[2]: Leaving directory `/usr/src/modules/alsa-driver'                  &#9618;
 &#9474; make[1]: *** [build-stamp] Error 2                                         &#9618;
 &#9474; make[1]: Leaving directory `/usr/src/modules/alsa-driver'                  &#9646;
 &#9474; make: *** [kdist_image] Error 2

-----------------------------------------------------------

Stopped at 99%.If it makes a difference I have the ubuntu studio audio package and real time kernel installed also.Can anyone please shed any light on this for me.I only switched from XP last week,so I know very little about Ubuntu or Linux in general but have been really enjoying it so far apart from this hiccough.
Many Thanks in advance for any help.

---

### Post by khelben1979 on 2009-04-15
Maybe you should get a better sound card? The old [Sound Blaster Audigy2]("http://en.wikipedia.org/wiki/Sound_blaster#Sound_Blaster_Audigy_series") ZS is well supported by Linux.

---

### Post by achilleez13 on 2009-04-15
hmmm...I was kind of hoping to try and get this one working,as I'm on a tight budget.

---

### Post by dmn_clown on 2009-04-15
> **khelben1979 said:**
> Maybe you should get a better sound card? The old [Sound Blaster Audigy2]("http://en.wikipedia.org/wiki/Sound_blaster#Sound_Blaster_Audigy_series") ZS is well supported by Linux.

The Audigy uses a hacked SB Live driver and arguably the SB Live sounds better under linux, there is no need to purchase a new card.


To the OP the module you are looking for is snd NOT snd-

---

### Post by achilleez13 on 2009-04-15
Ok thanks for reply,I tried sudo modprobe snd and nothing happened just new line cursor

---

### Post by khelben1979 on 2009-04-15
Try this instead to see if it works better:

```
sudo modprobe sb
```

---

### Post by achilleez13 on 2009-04-15
Tried sudo modprobe sb and returns

FATAL: Error inserting sb (/lib/modules/2.6.27-11-generic/kernel/sound/oss/sb.ko): No such device

---

### Post by khelben1979 on 2009-04-15
> **dmn_clown said:**
> The Audigy uses a hacked SB Live driver and arguably the SB Live sounds better under linux, there is no need to purchase a new card.

I don't think so. Can you refer to a source which claims this? I have tried the Sound Blaster Live and Sound Blaster Audigy ZS 2 with Linux systems myself and the Audigy ZS 2 sounded better + that the cpu usage went down.

---

### Post by khelben1979 on 2009-04-15
delete this post. (irritating duplicate, bug!)

---

### Post by achilleez13 on 2009-04-15
Tried sudo modprobe sb and returns

FATAL: Error inserting sb (/lib/modules/2.6.27-11-generic/kernel/sound/oss/sb.ko): No such device

Sorry to bump this but please has anyone else got any ideas at all.

---

### Post by khelben1979 on 2009-04-15
Compile your own linux kernel would be something you could do. Then you will have the sound inbuilt in the kernel or as a module, depending on what you choose.

However.. I definitely think there must be an easier way than this, I just don't know what at this time.

---

### Post by markbuntu on 2009-04-15
First things first, reinstall alsa in case something got screwed up

(1) Remove the ALSA packages. From a terminal:
```

sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils

```
(2) Reinstall the same packages
```

sudo apt-get install linux-sound-base alsa-base alsa-utils

```
Packages gdm and ubuntu-desktop are also removed in this process if you are using Gnome. They need to be reinstalled:
```

sudo apt-get install gdm ubuntu-desktop

```
If you are using xubuntu this will also happen to you
```

sudo apt-get install gdm xubuntu-desktop

```
(3) Reboot.

next

aplay -l

to see if the sb driver is loaded

System/Administration/Users and Groups

make yourself a member of the group audio so you can use jack without sudo
More on jack ardour and hydrogen

[http://en.wikipedia.org/wiki/JACK_Audio_Connection_Kit](http://en.wikipedia.org/wiki/JACK_Audio_Connection_Kit)

[https://help.ubuntu.com/community/UbuntuStudio/GettingStarted](https://help.ubuntu.com/community/UbuntuStudio/GettingStarted)

[http://www.ubustu.com/globe/2007/05/29/how-to-configure-jack-in-ubuntu-studio/](http://www.ubustu.com/globe/2007/05/29/how-to-configure-jack-in-ubuntu-studio/)

[http://hubpages.com/hub/Recording-in-Linux-aka-Free-and-Open-Source-Digital-Audio-Workstation](http://hubpages.com/hub/Recording-in-Linux-aka-Free-and-Open-Source-Digital-Audio-Workstation)

[http://out-of-order.nfshost.com/tutorials/ardour/](http://out-of-order.nfshost.com/tutorials/ardour/)

[https://help.ubuntu.com/community/HowToQjackCtlConnections](https://help.ubuntu.com/community/HowToQjackCtlConnections)

[http://www.ubustu.com/globe/2007/09/19/how-to-sync-hydrogen-with-ardour/](http://www.ubustu.com/globe/2007/09/19/how-to-sync-hydrogen-with-ardour/)

[http://www.rosegardenmusic.com/](http://www.rosegardenmusic.com/)

---

### Post by achilleez13 on 2009-04-15
Have re-installed the entire OS this afternoon havn't yet installed studio package or rt kernel.Tried aplay -l and this was the readout :-

**** List of PLAYBACK Hardware Devices ****
card 0: Live [SBLive 5.1 [SB0060]], device 0: emu10k1 [ADC Capture/Standard PCM Playback]
  Subdevices: 32/32
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
  Subdevice #8: subdevice #8
  Subdevice #9: subdevice #9
  Subdevice #10: subdevice #10
  Subdevice #11: subdevice #11
  Subdevice #12: subdevice #12
  Subdevice #13: subdevice #13
  Subdevice #14: subdevice #14
  Subdevice #15: subdevice #15
  Subdevice #16: subdevice #16
  Subdevice #17: subdevice #17
  Subdevice #18: subdevice #18
  Subdevice #19: subdevice #19
  Subdevice #20: subdevice #20
  Subdevice #21: subdevice #21
  Subdevice #22: subdevice #22
  Subdevice #23: subdevice #23
  Subdevice #24: subdevice #24
  Subdevice #25: subdevice #25
  Subdevice #26: subdevice #26
  Subdevice #27: subdevice #27
  Subdevice #28: subdevice #28
  Subdevice #29: subdevice #29
  Subdevice #30: subdevice #30
  Subdevice #31: subdevice #31
card 0: Live [SBLive 5.1 [SB0060]], device 2: emu10k1 efx [Multichannel Capture/PT Playback]
  Subdevices: 8/8
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
card 0: Live [SBLive 5.1 [SB0060]], device 3: emu10k1 [Multichannel Playback]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

I installed hydrogen as this was what first alerted me to a problem.OSS driver gives good bass drum sound but when I switch to alsa it sounds awful.

---

### Post by achilleez13 on 2009-04-16
Sound is so nearly sorted apart from a few issues.I still think the card and driver aren't working together properly.Everything now works (I can start jack without being root,I can hook up my midi keyboard,all volume controls for card work correctly) but there are still these problems:-

:-  Alsa driver will not compile from module assistant

:-  When using alsa driver hydrogen sounds rubbish (fine with oss)

:-  Jack runs at high latency (lot of x runs)

:-  Alsamixer only displays two channels,capture and playback

Any ideas guys?

ps Installed rt kernel and can't start jack in rt mode..error :-

cannot use real-time scheduling (FIFO at priority 10) [for thread -1210575184, from thread -1210575184] (1: Operation not permitted)
cannot create engine

eek!

---

### Post by khelben1979 on 2009-04-16
> **achilleez13 said:**
> :-  Jack runs at high latency (lot of x runs)

And this will always be the case with this sound card. The sound processor in it isn't strong enough.

---

