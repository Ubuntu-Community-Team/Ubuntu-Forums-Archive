---
title: "Applications are blocking sound; they all seem to be using alsa, whats up?"
date: 2007-07-17
forum: Multimedia &amp; Video
---

### Post by Del Piero on 2007-07-17
As the title says, additional info:
> 
lspci
> 00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
00:01.0 PCI bridge: Intel Corporation 82865G/PE/P PCI to AGP Controller (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801EB (ICH5) SATA Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation GeForce 6200 (rev a1)
02:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:03.0 Multimedia audio controller: Cirrus Logic Crystal CS4281 PCI Audio (rev 01)

> 
Card: Cirrus Logic CS4281                                                    &#9474;
&#9474; Chip: Cirrus Logic CS4297 rev 3                                              &#9474;
&#9474; View: [Playback] Capture  All                                                &#9474;
&#9474; Item: Master      

Creative 128 Blaster PCI and i am sure it supports mixing...so now how do i play sound in multiple applications at the same time?

---

### Post by fredj on 2007-07-18
Open the Alsa mixer (doubleclick on the speaker icon). Go to the File ->Change Device menu and make sure
that your soundcard is selected and running through alsa.

---

### Post by Del Piero on 2007-07-18
thanks, i did that and it's already set on alsa...:confused:

---

### Post by Del Piero on 2007-07-18
Bump..

---

### Post by Del Piero on 2007-07-18
bump...

---

### Post by Del Piero on 2007-07-18
Bump....

---

### Post by Del Piero on 2007-07-18
Bump.....

Next bump after 8 hours..

---

### Post by Del Piero on 2007-07-19
Bump.....

Next bump in 2 hours..

---

### Post by Del Piero on 2007-07-19
Bump!!!!

I need help here please....

---

### Post by ChaoticMind on 2007-07-19
What do you mean, "blocking sound"? Does it do like a "scrambling" sound? Cause that's what i'm getting actually, and i'm clueless. It's not happening all the time though... 

For example if i play a video through firefox (youtube for example), rhythmbox would do this loud static sound. 
Also sometimes happens if i get a msg on gaim. Usually a pause/resume would fix it, but it's very annoying (and loud).

---

### Post by Del Piero on 2007-07-19
> **ChaoticMind said:**
> What do you mean, "blocking sound"? Does it do like a "scrambling" sound? Cause that's what i'm getting actually, and i'm clueless. It's not happening all the time though... 

For example if i play a video through firefox (youtube for example), rhythmbox would do this loud static sound. 
Also sometimes happens if i get a msg on gaim. Usually a pause/resume would fix it, but it's very annoying (and loud).

Blocking means no sound at all except from the application that been running first...thanks so much for at least replying. If i am playing rythmbox and decide to play a youtube video i have to stop rythmbox then play it. If i play xmms while youtube is playing something xmms tells me sound card is being blocked by another application. meaning i can play 1 thing at a time which is so retarded since my card support mixing since it's a dedicated PCI 128 creative blaster.

---

### Post by Del Piero on 2007-07-20
Not again...people i need help here please, i really do...

---

### Post by Del Piero on 2007-07-20
Bump...

---

### Post by clesage on 2007-07-20
I have the same problem, but there is no need to act entitled to an answer. Have you spent some time searching for yourself?

I just found this in 5 minutes of looking:

[http://ubuntuforums.org/showthread.php?t=32063&highlight=multiple+audio](http://ubuntuforums.org/showthread.php?t=32063&highlight=multiple+audio)
(Looks simple and promising)

[http://ubuntuforums.org/showthread.php?t=205449&highlight=multiple+audio](http://ubuntuforums.org/showthread.php?t=205449&highlight=multiple+audio)

[http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide#Getting_more_than_one_application_to_use_the_soundcard_at_the_same_time](http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide#Getting_more_than_one_application_to_use_the_soundcard_at_the_same_time)
(this looks incomplete, and a way to play a game through an Alsa driver. Not sure if this will help our case.)

[http://ubuntuforums.org/showthread.php?t=491984&highlight=multiple+audio](http://ubuntuforums.org/showthread.php?t=491984&highlight=multiple+audio)
(A method of running all Alsa output through Jack, which may work well for me, as a recording hobby musician.)

Search is your friend dude.
-sage

---

### Post by mrowth on 2007-07-21
Sorry, can't help you if you insist on the Soundblaster PCI 128's hardware mixing... otherwise I'd suggest an /etc/asound.conf or ~/.asoundrc similar to this one:

```
pcm.mysoundcard {
    type hw
    card 0 # assuming 0 is the correct card, of course
}

ctl.mysoundcard {
    type hw
    card 0 
}

# define a dmix plugin for software mixing (playback)
pcm.mydmixer {
    type dmix
    ipc_key 1024
    ipc_perm 0666 # allow other users to use dmix
    slave.pcm "mysoundcard"
    slave {
        period_time 0
        period_size 1024
        buffer_size 4096
        # adapt the sampling rate if necessary:
        # rate 48000 
        # some cards need the exact data format (e.g. ice1712):
        # format S32_LE
    }
    bindings {
        0 0
        1 1
    }
}

# define a dsnoop plugin to allow multiple applications to capture audio simultaneously
pcm.mydsnooper {
    type dsnoop
    ipc_key 2048
    ipc_perm 0666 
    slave.pcm "mysoundcard"
    slave 
    {
        period_time 0
        period_size 1024
        buffer_size 4096
        # rate 48000
        # format S32_LE
    }
    bindings {
        0 0
        1 1
    }
}

# make this the default for all ALSA-using applications
pcm.!default {
    type plug
    slave.pcm "myduplex"
}
pcm.myduplex {
    type asym
    playback.pcm "mydmixer"
    capture.pcm "mydsnooper"
}

```

Originally found it on a German website; it worked well for me*

More at [http://alsa.opensrc.org/index.php/.asoundrc](http://alsa.opensrc.org/index.php/.asoundrc)

Sorry, I suppose it's not what you were looking for


[SIZE="1"](* until I bought a new, allegedly "supported" soundcard (Terratec Aureon 7.1 PCI) :confused:)[/SIZE]

---

### Post by Del Piero on 2007-07-21
Hey man thanks alot although i wanna clarify that i do not think i am entitled to help, i was just reviving the thread to get interest. I am greatful for what you guys do on this board and i respect everyone here. Anyway i looked before but found solutions not related to my card or my problem in specific. Sometimes i am lucky sometimes i am not. Anyway thanks alot and the first like you posted worked.

---

### Post by gururise on 2007-07-29
I'm having the same problem on my NForce2 MB.  Just started happening recently, I'm not sure what got upgraded; however, now when I try to run Totem, I get the following error:

snd_pcm_open() failed:-16:Device or resource busy
>>> Check if another program already uses PCM <<<
audio_oss_out: Opening audio device...
audio_oss_out: audio.device.oss_device_name = auto, probing devs
audio_oss_out: Auto probe for audio device failed
audio_pulse_out: host (null) sink (null)
audio_pulse_out: ao_open bits=16 rate=44100, mode=8

By the way, I am using Totem-XINE... Isn't it suppose to use ALSA by default? Any ideas?

---

