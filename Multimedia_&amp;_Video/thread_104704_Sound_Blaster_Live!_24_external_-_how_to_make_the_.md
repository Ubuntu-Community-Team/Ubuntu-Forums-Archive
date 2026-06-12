---
title: "Sound Blaster Live! 24 external - how to make the surround work?"
date: 2005-12-16
forum: Multimedia &amp; Video
---

### Post by tsktsk on 2005-12-16
I've seen that there are already a few threads concerning problems with external (usb) sound cards, but no one of them has helped me solving my problem.

**What it's ok:** I've plugged in the cable, done a reboot, and the sound card was recongnised and working fine. I have no problems in playing music with totem or mplayer. **What I'd like** to do, is to have the full **5.1 surround sound** (this is working in windows, but I have no output from the rear speakers in ubuntu).

I read [this documentation]("http://www.alsa-project.org/alsa-doc/alsa-lib/pcm_plugins.html") in order to understand how to modify the **.asoundrc** properties, and I followed all the advices I found in this forum, but with no success :???:  (the alsa documentation is ok, but... I could not make it work).

The output of cat /proc/asound/cards is
```

0 [I82801BAICH2   ]: ICH - Intel 82801BA-ICH2 Intel 82801BA-ICH2 with AD1885 at 0xd800, irq 17
1 [External       ]: USB-Audio - SB Live! 24-bit External Creative Technology SB Live! 24-bit External at usb-0000:00:1f.2-2, full speed

```

...and lsusb produces
```

Bus 002 Device 001: ID 0000:0000
Bus 001 Device 002: ID 041e:3040 Creative Technology, Ltd
Bus 001 Device 001: ID 0000:0000

```

If I try with alsamixer -c 1 (my external sb has id 1), the only channel that I can modify is called PCM.

Did anyone succeed in having the surround working with a usb sound blaster live?
Any ideas of what I could do?

thanks in advance

---

### Post by tsktsk on 2005-12-17
by the way, the test ```
speaker-test -c6 -D plug:surround51
``` doesn't give any sound.

---

### Post by gigake on 2006-01-16
I have the same soundcard... i see only one channel -  PCM
Where are the others?
I can't record :(

---

### Post by danrien on 2006-07-18
i can't use my 5.1 channels either.... i think it might be because ubuntu just uses standard usb drivers for sb live! external.  sucks.

---

### Post by sebastfr on 2006-08-31
I managed to have four speakers working on my SB Live! 24 usb (which you can't control separately).

For a test, edit /etc/asound.conf, and add the following lines:



##########

pcm.dshare {
    type dmix
    ipc_key 2048
    slave {
        pcm "hw:0"
        rate 44100
        period_time 0
        period_size 1024
        buffer_size 8192
        channels 4
    }
    bindings {
        0 0
        1 1
        2 2
        3 3
    }
}

pcm.themall {
    type plug
    slave {
        pcm "dshare"
        channels 4
    }
    ttable.0.0 1
    ttable.1.1 1
    ttable.0.2 1
    ttable.1.3 1
}


pcm.frontx {
    type plug
    slave {
        pcm "dshare"
        channels 4
    }
    ttable.0.0 1
    ttable.1.1 1
}

pcm.rearx {
    type plug
    slave {
        pcm "dshare"
        channels 4
    }
    ttable.0.2 1
    ttable.1.3 1
}

######

If your Live! card is #1 (instead of #0), replace 'hw:0' with 'hw:1'

Now test you have sound working on rear and front speakers:

~> aplay -Dthemall [whatever WAVE file]

Or try only on rear or front speakers:

~> aplay -Drearx [Whatever WAVE file]

~> aplay -Dfrontx [Whatever WAVE file]

tada!

If this worked and you want to keep the 4-speaker settings as default on your system, rename 'pcm.themall' with 'pcm.!default'.

I've been trying to make this card work better under linux (eg. have the remote working, capture & playback at the same time, having the knobs on the front panels to do something etc.) but unfortunately have little time to do this on my own... if someone is motivated enough, I'd be happy giving a hand (even if we need to tweak the snd-usb driver etc.)

Seb.

---

### Post by luopio on 2006-09-16
So any news? Just purchased mine. Of course I failed to notice this: > Note - I own a Sound Blaster Extigy, but we're all using the same driver. Just remind yourself to never purchase another Creative Labs sound card again, because they really only optimally work best in Windows - go figure. in the gentoo howto here: [http://gentoo-wiki.com/HOWTO_Install_Creative_Sound_Blaster_Live_24-bit_external_(usb](http://gentoo-wiki.com/HOWTO_Install_Creative_Sound_Blaster_Live_24-bit_external_(usb)) before buying it :-P 

I'd be happy even if the Master volume control appeared on the mixer. I would be ready to help with the driver as well. I'm a competent programmer (CS student), but I have no experience what so ever on kernel/module-programming. 

A start for a project perhaps?

[EDIT] nevermind, succeeded in swapping the sb for a terratec aureon 5.1 usb, which works quite nicely =D> [/EDIT]

---

### Post by SiD|NA on 2006-11-24
Hi folks,
asking Google for Creative Extigy and Ubuntu brought me here, but also revealed a URL of a German magazine, featuring an article about the extigy and its Linux support. Long story short: [This]("http://exaudio.sourceforge.net/") is an OS-Driver for the Extigy and should bring full surround + remote features.
Maybe helps ;)
I'm just testing atm...

[EDIT]
Works... fine ;) Added even bass and treble control to the mixer - btw. works with ALSA then ;)
[/EDIT]

---

### Post by whashnez on 2007-05-18
This is the first time I write to this forum...If you want to have full surround with your creative sound blaster live 24-bit external usb card,edit your /etc/asound.conf so it looks like this:

pcm.dshare {
type dmix
ipc_key 2048
slave {
pcm "hw:0"
rate 96000
period_time 0
period_size 1024
buffer_size 8192
channels 6
}
bindings {
0 0
1 1
2 2
3 3
4 4


5 5
}
}

pcm.!default {
type plug
slave {
pcm "dshare"
channels 6
}
ttable.0.0 1
ttable.1.1 1
ttable.0.2 1
ttable.1.3 1
ttable.0.4 1
ttable.0.5 1
}


pcm.frontx {
type plug
slave {
pcm "dshare"
channels 6
}
ttable.0.0 1
ttable.1.1 1
}

pcm.rearx {
type plug
slave {
pcm "dshare"
channels 6
}
ttable.0.2 1
ttable.1.3 1
}

it worked for me...

Warning!
If you have edited an ~/.asoundrc file (the one that the wiki recomends)
just delete it...

---

### Post by julupanter on 2007-06-09
uff, for me only works the code of sebastfr, and i'm very happy for this advance, but the last code for the 6 channels sound doesn´t work.

it's a pity does ubuntu does not recognize this great sound card ...

---

### Post by Soarer on 2007-06-23
I have downloaded and compiled the exaudio 1.66, run load.sh and set the Extigy as the default sound card.

I can get no sound at all. Totem just exits when asked to play soemthing, and Amarok freezes and needs to be killed.

The error log says:
```
/var/log/syslog:Jun 23 08:59:11 localhost kernel: [ 4748.064810] exaudio_remote: initializing driver on probe of interface 0
/var/log/syslog:Jun 23 08:59:11 localhost kernel: [ 4748.064829] exaudio: This extigy's layout is not known to me (firmware mismatch?)
/var/log/syslog:Jun 23 08:59:11 localhost kernel: [ 4748.064834] exaudio: wTotalLength=483 bNumInterfaces=4
/var/log/syslog:Jun 23 08:59:11 localhost kernel: [ 4748.065088] exaudio: probe of 2-2:1.1 failed with error -5
/var/log/syslog:Jun 23 08:59:11 localhost kernel: [ 4748.065138] exaudio: probe of 2-2:1.2 failed with error -5
/var/log/syslog:Jun 23 08:59:11 localhost kernel: [ 4748.065179] exaudio: probe of 2-2:1.3 failed with error -5

```

One odd thing - I believe the card is number 1, not 0 as shown here (EDIT: just noticed that's talking about the remote, which I am not using anyway)

Any ideas why (perhaps SiD|NA who has it working can help)?

Thanks.

---

### Post by jozwiak0 on 2007-11-07
Hey I need help total nube.

 I have the creative USB live sound card you are all talking about. 

I tried entering in that code into the asound.conf file, and nothing came of it.   When I goto the sound mixer  I can choose between my two cards under device.  I chose the SB LIVE card and the only sound option is PCM. 


PLEASE HELP

thanks in advance.

---

### Post by ezzieyguywuf on 2007-11-13
using Sebasfr's script, i now have all five speakers working on my sound blaster live! 24-bit usb sound card. I have not been able to test whether or not this is "true surround" because i seem to have misplaced all my dvds. a note to those that do not have it working, MAKE SURE you have the correct device selected. mine was hw:1 and that will prob be true for anyone who is using this external soundcard. to find out which device to put, type aplay -l (thats an L) into a terminal. it will list all you're sound cards. Each sound card will be preceeded by a Card #. that # is what you want to use. if you see two with the same number, its because one of them is a subset of the other (or something like that i'm not too sure.)

Now, what i'd like to know is if someone can add some code to that script so that my onboard card also works. For some reason, right now the only card that is working is my external, and i think this is because the asound.conf file is over-riding any other files which may exist pertaining to the configuration of the sound cards. this is what my onboard soundcard is listed as :  Intel [HDA Intel], device 0: AD198x Analog [AD198x Analog]
 with a sub-device (or w/e) Intel [HDA Intel], device 1: AD198x Digital [AD198x Digital] .

The first time i used this script, everything worked fine but then after a reboot i had NO sound. I figured i messed somethin up bad, and after tinkering around for a few days did a fresh install of gutsy. Now i have the 5.1 working, but like i mentioned, i think some code needs to be added to bring back the onboard soundcard. any advice?

btw, when i go to settings>>preferences>>sound and try to do a test with the analog device i get a "audiotestsrc wave=sine freq=512 !" error that i'm sure we're all familiar with. with the digital device i just get no sound. 

thanks for any help guys!

---

### Post by TheSheps on 2008-05-19
Hi all! Kinda new to Ubuntu, but thought I was struggling to set this up myself over the weekend, so thought I'd share what I found here.

I've been able to get all 6 channels of my SB Live! 24 bit external sound card working with ubuntu, by using the Pulseaudio drivers instead of ALSA. 

To do this, open the volume manager and select File/Change Device. Choose the PulseAudio Mixer. You may notice at this point that there are still only one or two channels listed, this is changed by altering the PulseAudio configuration file, as follows:

```
gksudo gedit /etc/pulse/daemon.conf
```

Uncomment the line that begins "default-sample-channels =" (remove the semicolon at the beginning of the line), and enter however many channels you need to use (in my case, 6).

Having performed these steps and restarted Ubuntu, you should find that you have full channel output (worked for me, anyways!)

If I've missed anything, or have grabbed the wrong end of the stick entirely, let me know!

---

### Post by snacho on 2008-05-22
> **TheSheps said:**
> 
To do this, open the volume manager and select File/Change Device. Choose the PulseAudio Mixer. You may notice at this point that there are still only one or two channels listed, this is changed by altering the PulseAudio configuration file, as follows:

```
gksudo gedit /etc/pulse/daemon.conf
```

Uncomment the line that begins "default-sample-channels =" (remove the semicolon at the beginning of the line), and enter however many channels you need to use (in my case, 6).

Having performed these steps and restarted Ubuntu, you should find that you have full channel output (worked for me, anyways!)

If I've missed anything, or have grabbed the wrong end of the stick entirely, let me know!

That also worked for me! you should also install all pulseaudio tools: [https://wiki.ubuntu.com/PulseAudio](https://wiki.ubuntu.com/PulseAudio)
after that I had to change default playback device from pulseaudio volume control. Then reboot and all should be fine. Pulseaudio rocks, everything works like a charm and there's many cool things like changing applications sound volume individually! I Recommend!

---

### Post by tsktsk on 2008-06-04
> **sebastfr said:**
> I managed to have four speakers working on my SB Live! 24 usb (which you can't control separately).

For a test, edit /etc/asound.conf, and add the following lines:



##########

pcm.dshare {
    type dmix
    ipc_key 2048
    slave {
        pcm "hw:0"
        rate 44100
        period_time 0
        period_size 1024
        buffer_size 8192
        channels 4
    }
    bindings {
        0 0
        1 1
        2 2
        3 3
    }
}

pcm.themall {
    type plug
    slave {
        pcm "dshare"
        channels 4
    }
    ttable.0.0 1
    ttable.1.1 1
    ttable.0.2 1
    ttable.1.3 1
}


pcm.frontx {
    type plug
    slave {
        pcm "dshare"
        channels 4
    }
    ttable.0.0 1
    ttable.1.1 1
}

pcm.rearx {
    type plug
    slave {
        pcm "dshare"
        channels 4
    }
    ttable.0.2 1
    ttable.1.3 1
}

######

If your Live! card is #1 (instead of #0), replace 'hw:0' with 'hw:1'

Now test you have sound working on rear and front speakers:

~> aplay -Dthemall [whatever WAVE file]

Or try only on rear or front speakers:

~> aplay -Drearx [Whatever WAVE file]

~> aplay -Dfrontx [Whatever WAVE file]

tada!

If this worked and you want to keep the 4-speaker settings as default on your system, rename 'pcm.themall' with 'pcm.!default'.

I've been trying to make this card work better under linux (eg. have the remote working, capture & playback at the same time, having the knobs on the front panels to do something etc.) but unfortunately have little time to do this on my own... if someone is motivated enough, I'd be happy giving a hand (even if we need to tweak the snd-usb driver etc.)

Seb.


[SIZE="3"]**Thanks very much!!**[/SIZE] ...I didn't even remember about this thread and today, when I googled for "sb live 24" I was pretty surprised to find "my" post at the first place in Google.
By the way, your solution worked for me as well! Thanks!

---

