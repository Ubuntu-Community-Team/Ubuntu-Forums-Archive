---
title: "Need help getting surround working correctly"
date: 2007-09-18
forum: Multimedia &amp; Video
---

### Post by other guy on 2007-09-18
I am working with a CA0106 based card (Creative Live! 24bit 7.1), with the newest Ubuntu I can download.

I have read the stickies, wikis and threads. :biggrin: It helped me a lot I should mention. Thank you to anyone who wrote anything I read along my way getting this far.

Now for my issue. At first I had no sound. Now I do. With one thing. Only one speaker makes sounds. The System | Administration | Sound - does produce tones. Just not as one setup. Each is it's own output. Which is a good sign I think...

I cannot do this one part. When I get to #3  I do not have the option.

[quote=mgmiller]
To turn on surround sound:
1) Open the volume control by double clicking the speaker icon in the top panel.
2) Click on edit preferences.
3) Put check marks in both the surround and channel mode boxes.
(you will have to scroll down the list to find channel mode)
4) Make sure the slider for surround is turned up and not muted.
5) On the Options tab, select 4ch, 6ch or 8ch as appropriate. 
[/quote]

It's not that I cannot do it really. It is that option for surround does not exist for me.   Also running the sound test *speaker-test -Dplug:surround71 -c8 -l1 -twav * give an error of some sort.
Playback open error: -16,Device or resource busy


Any ideas how I can correct this issue? It is not very useful to only have one speaker at a time.

---

### Post by other guy on 2007-09-18
ttt

---

### Post by HilliBilly on 2007-10-04
have you been able to fix all this?

although i could tell you how to get sound on all speakers, i am struggling with this "Playback open error: -16,Device or resource busy" too. it has to do with the software mixer i guess, ESD in >system>preferences>sound>sounds has to be disabled, but this alone didn't solve the problem for me.

[http://www.alsa-project.org/main/index.php/Matrix:Module-ca0106](http://www.alsa-project.org/main/index.php/Matrix:Module-ca0106)

nano ~/.asoundrc

pcm.dmix51 {
    type dmix
    ipc_key 1024
    slave {
        pcm "hw:0,0"
        rate 44100
        channels 6
        period_time 0
        period_size 1024
        buffer_time 0
        buffer_size 4096
    }
}

pcm.20to51 {
     type route
     slave.pcm surround51
     slave.channels 6
     ttable.0.0 1
     ttable.1.1 1
     ttable.0.2 1
     ttable.1.3 1
     ttable.0.4 0.5
     ttable.1.4 0.5
     ttable.0.5 0.5
     ttable.1.5 0.5
}

pcm.duplex {
    type asym
    playback.pcm "20to51" #muss als pcm.20to51 definiert sein
    capture.pcm "dsnooper"
}


sudo nano /etc/asound.conf

    code:
    pcm.ca0106 {
              type hw
              card 0
           }

           ctl.ca0106 {
              type hw
              card 0
    }

    pcm.snd_card {
            type hw
            card 0
            device 0
    }

    ctl.snd_card {
            type hw
            card 0
            device 0
    }



    pcm.dmixer {
        type dmix
        ipc_key 1024
        ipc_perm 0666
        slave.pcm "snd_card"
        slave {
            period_time 0
            period_size 1024
            buffer_size 4096
            rate 44100
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

    pcm.dsnooper {
        type dsnoop
        ipc_key 2048
        ipc_perm 0666 
        slave.pcm "snd_card"
        slave 
        {
            period_time 0
            period_size 1024
            buffer_size 4096
            rate 44100
        }
        bindings {
            0 0
            1 1
        }
    }

    pcm.duplex {
        type asym
        playback.pcm "dmixer"
        capture.pcm "dsnooper"
    }

    pcm.!default {
        type plug
        slave.pcm "duplex"
    }


reboot

speaker-test -c 6 -t wav -D surround51
aplay -vv /usr/share/sounds/ekiga/dialtone.wav

---

### Post by other guy on 2007-10-04
Thank you for replying.

No I did not get it going yet. Upon further reading I found there is something crazy bout the card and how it hardware mixes.

Since I am still rather new to Linux, I may not understand what  I have read so far. I did however find a rc of the ALSA that has some kind of fix for this card.
[http://www.alsa-project.org/main/index.php/Changes_v1.0.14_v1.0.15rc1#CA0106_driver](http://www.alsa-project.org/main/index.php/Changes_v1.0.14_v1.0.15rc1#CA0106_driver)

> 
** CA0106 driver**

  snd-ca0106:Add recognition for new variant. Fixes ALSA bug#3251  Coding style fix sound/pci/ca0106/ca_midi.h  ca0106: Add analog mute controls for cards with SPI DAC  ca0106: replaced control add sequences with macro  ca0106: power down SPI DAC channels when not in use  ca0106: Add more symbol SPI register names and use them  ca0106: remove extra commands in SPI DAC init sequence  I made an attempt to use the newer alsa, but broke my install doing it wrong :D.

---

### Post by HilliBilly on 2007-10-04
i do understand this bug but it might be not important for you. you can check it this way (this is my card):

**$ lspci -vvn**
05:01.0 0401: 1102:0007
        Subsystem: [COLOR="Red"]1102:1012[/COLOR]
        Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 32 (500ns min, 5000ns max)
        Interrupt: pin A routed to IRQ 19
        Region 0: I/O ports at d100 [size=32]
        Capabilities: <access denied>

[B]$dmesg | grep ca0106
[/B][   50.214475] snd-ca0106: Model [COLOR="Red"]1012[/COLOR] Rev 00000000 Serial 10121102

the red is important, only if your lspci output shows something like 1102:1013 then you have to use the 1.0.15rc1 release (afaik model 1102:1012 is handled by 1.0.14 correctly). btw ... the 1102 is the same for all cards, its the code for CL.

if you still have no sound, tell me which model you have, i might be able to help you.

---

### Post by other guy on 2007-10-05
I reinstalled the card. I was settling for onboard with the center non-functional. Though any hope of learning how leverage an issue I will do what I need to. Part of any issue is the fun of fixing it.

Pulled out my best line-fu and got the instructions going from text to command line. :D Via the alsa    snd-ca0106 matrix page.

After re-reading what you wrote and getting that from text to fingers ok.. Still only one speaker. I do admit it threw me off a bit on disabling the ESD. After rereading text. I got that part.


Here is the output.

dmesg | grep ca0106
[   31.991794] snd-ca0106: Model **[COLOR=Red]1006[/COLOR]** Rev 00000000 Serial 10061102

**lspci -vvn**
```
00:00.0 0600: 10de:00e1 (rev a1)
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0
        Region 0: Memory at f0000000 (32-bit, prefetchable) [size=128M]
        Capabilities: <access denied>

00:01.0 0601: 10de:00e0 (rev a2)
        Subsystem: 1458:0c11
        Control: I/O+ Mem+ BusMaster+ SpecCycle+ MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap- 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0

00:01.1 0c05: 10de:00e4 (rev a1)
        Subsystem: 1458:0c11
        Control: I/O+ Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Interrupt: pin A routed to IRQ 4
        Region 0: I/O ports at cc00 [size=32]
        Region 4: I/O ports at 1c00 [size=64]
        Region 5: I/O ports at 2000 [size=64]
        Capabilities: <access denied>

00:02.0 0c03: 10de:00e7 (rev a1) (prog-if 10 [OHCI])
        Subsystem: 1458:5004
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0 (750ns min, 250ns max)
        Interrupt: pin A routed to IRQ 16
        Region 0: Memory at fd002000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

00:02.1 0c03: 10de:00e7 (rev a1) (prog-if 10 [OHCI])
        Subsystem: 1458:5004
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0 (750ns min, 250ns max)
        Interrupt: pin B routed to IRQ 17
        Region 0: Memory at fd003000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

00:02.2 0c03: 10de:00e8 (rev a2) (prog-if 20 [EHCI])
        Subsystem: 1458:5004
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0 (750ns min, 250ns max)
        Interrupt: pin C routed to IRQ 18
        Region 0: Memory at fd004000 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

00:08.0 0101: 10de:00e5 (rev a2) (prog-if 8a [Master SecP PriP])
        Subsystem: 1458:5002
        Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0 (750ns min, 250ns max)
        Region 0: [virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]
        Region 1: [virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]
        Region 2: [virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]
        Region 3: [virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]
        Region 4: I/O ports at f000 [size=16]
        Capabilities: <access denied>

00:0a.0 0101: 10de:00e3 (rev a2) (prog-if 85 [Master SecO PriO])
        Subsystem: 1458:b002
        Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0 (750ns min, 250ns max)
        Interrupt: pin A routed to IRQ 16
        Region 0: I/O ports at 09f0 [size=8]
        Region 1: I/O ports at 0bf0 [size=4]
        Region 2: I/O ports at 0970 [size=8]
        Region 3: I/O ports at 0b70 [size=4]
        Region 4: I/O ports at c400 [size=16]
        Region 5: I/O ports at c800 [size=128]
        Capabilities: <access denied>

00:0b.0 0604: 10de:00e2 (rev a2) (prog-if 00 [Normal decode])
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
        Status: Cap- 66MHz+ UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 16
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=10
        Memory behind bridge: f8000000-faffffff
        Prefetchable memory behind bridge: e0000000-efffffff
        Secondary status: 66MHz+ FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort+ <SERR- <PERR-
        BridgeCtl: Parity- SERR+ NoISA+ VGA+ MAbort- >Reset- FastB2B-

00:0e.0 0604: 10de:00ed (rev a2) (prog-if 00 [Normal decode])
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
        Status: Cap- 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=128
        I/O behind bridge: 00009000-00009fff
        Memory behind bridge: fb000000-fcffffff
        Prefetchable memory behind bridge: 50000000-500fffff
        Secondary status: 66MHz- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort+ <SERR- <PERR+
        BridgeCtl: Parity- SERR+ NoISA+ VGA- MAbort- >Reset- FastB2B-

00:18.0 0600: 1022:1100
        Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Capabilities: <access denied>

00:18.1 0600: 1022:1101
        Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-

00:18.2 0600: 1022:1102
        Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-

00:18.3 0600: 1022:1103
        Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-

01:00.0 0300: 10de:00f1 (rev a2) (prog-if 00 [VGA])
        Subsystem: 1458:3150
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 248 (1250ns min, 250ns max)
        Interrupt: pin A routed to IRQ 20
        Region 0: Memory at f8000000 (32-bit, non-prefetchable) [size=16M]
        Region 1: Memory at e0000000 (32-bit, prefetchable) [size=256M]
        Region 2: Memory at f9000000 (32-bit, non-prefetchable) [size=16M]
        [virtual] Expansion ROM at fa000000 [disabled] [size=128K]
        Capabilities: <access denied>

02:09.0 0401: 1102:0007
        Subsystem: 1102:1006
        Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 32 (500ns min, 5000ns max)
        Interrupt: pin A routed to IRQ 21
        Region 0: I/O ports at 9000 [size=32]
        Capabilities: <access denied>

02:0a.0 0200: 10ec:8169 (rev 10)
        Subsystem: 1385:311a
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 32 (8000ns min, 16000ns max), Cache Line Size: 64 bytes
        Interrupt: pin A routed to IRQ 19
        Region 0: I/O ports at 9400 [size=256]
        Region 1: Memory at fc000000 (32-bit, non-prefetchable) [size=256]
        [virtual] Expansion ROM at 50000000 [disabled] [size=128K]
        Capabilities: <access denied>

```I got this card at wally world and it was a while ago. Honestly I expected a common card like this to fire right up and just go. Not the best out there, but common.

---

### Post by HilliBilly on 2007-10-05
this bug you have mentioned is not important for you. v1.0.14 should handle it correct. 

**$vi /usr/src/alsa/alsa-driver-1.0.14/alsa-kernel/pci/ca0106/ca0106_main.c**
 { .serial = 0x10061102,
           .name   = "Live! 7.1 24bit [SB0410]",
           .gpio_type = 1,
           .i2c_adc = 1 } ,
         /* New Dell Sound Blaster Live! 7.1 24bit. This does not have an AC97.  */

i think, this should be your's?!

sorry to hear that you still have only one speaker ... could you post a screenshot of your alsamixer?

please try this:
**$ speaker-test -c 2 -t wav**

btw... i saw that you have the same ethernet chip (Realtek RTL8169/8110 Family PCI Gigabit Ethernet NIC (NDIS 6.0)	8169:10ec) as it is on my motherboard. this chip is a little tricky, you know that? have a look here:
[http://ubuntuforums.org/showthread.php?t=143982&highlight=rtl8169](http://ubuntuforums.org/showthread.php?t=143982&highlight=rtl8169)
[http://ubuntuforums.org/showthread.php?t=427935&highlight=rtl8169](http://ubuntuforums.org/showthread.php?t=427935&highlight=rtl8169)


ps. "wally world" means wal-mart?

---

### Post by other guy on 2007-10-05
About 4AM (-4GMT) I got the card working correctly. There was a typo on my part and n00bish behaviour. Otherwise it is working as to be expected.

**I want to thank you for taking the time to assist me. I am very happy right now. **

I have not ran any other tests to see if sound card elements are not functioning. My music plays so does audio playback in video(s).

Edit:
The speaker test functions, but is not correct in its output. I am still happy it functions. I will work on it more later on.

I do have onboard gigabit networking. Though I have burrnt it out long ago(ooopsie). The replacement  card, is the same chipset oddly enough, It works without issue. It is a Netgear (311) card if memory serves me right. So far that is one of the only add on cards I own. That has not given me issues in any distro.

> 
ps. "wally world" means wal-mart?
Yes, It means Wal Mart.  :D

---

### Post by HilliBilly on 2007-10-05
sounds good! :-D

although ...

> The speaker test functions, but is not correct in its output.

what does 'not correct' mean? you should hear a voice saying 'front left' from the left speaker and a second later 'front right' from the right speaker. do you hear that?

you should run 'alsamixer' in a terminal and check that you have unmuted the right speaker(s). if this doesn't solve the problem, you could 'play' with the different device-settings in >systems>preferences>sound

---

### Post by other guy on 2007-10-05
I will try and explain how it is separating.

Front left test wave = Left(F&R)+Center+Right(R).  Only Right(F) is <test> muted in this phase. The sub is active as it should be during the run.

The right does the same in its own aspect. Just reversed as would be  expected.

There is no total separation of the channels. I normally do no use true surround. So it is not much of an issue to me.  It is outputting somewhat in stereo. At least two speakers are pure stereo. The rest are mono.


I am just *very happy* it works. Could be a better sounding card, but that was my choice purchasing it.
:guitar:

---

### Post by darck on 2008-02-06
@HilliBilly 
You showed some code from files  ~/.asoundrc and /etc/asound.conf
Why is it in 2 separate files? Alsa wiki says, that only difference is that config in /etc is system wide, but both files see each others code. So it can be written in just one file.

Code you showed can:
- turn on dmix - software mixing for ca106 
- can make so called surround - copy a stereo to all 8 channels.

My question is **how combine those 2 - make "surround" with software mixing. **

I've tried a lot, but failed. I was able to do it for my integrated card, but the same method doesn't work with ca106. My conclusions are:
- to make software mixing working is enaugh to delete ~/.asoundrc and /etc/asound.conf files and turn off ESD in System -> Preferences -> Sound
- any text in  ~/.asoundrc turns off software mixing

below code from  ~/.asoundrc which makes my integrated via8235 play on 4 channel with software mixing turned on. When I use the same method for ca106 I get error.
```
###################################    via8235
pcm.via8235-dmix {
	type dmix
	ipc_key 1024
	slave {
		pcm "hw:1,1"
		channels 4
		period_time 0
		period_size 1024
		buffer_time 0
		buffer_size 4096
	}
}

pcm.via8235 {
	type plug
	slave.pcm "via8235-dmix"
	slave.channels 4
	route_policy duplicate  #**this line causes error for ca106**
}

ctl.via8235 {
	type hw
	card 1
}
```

---

### Post by Greasy on 2008-03-22
I entered this in my .asoundrc file and the surround work beautifully.

```

pcm.!dmix {
   type plug
   slave {
       pcm surround51
       channels 6
   }
}
pcm.!default {
   type plug
   slave.pcm "dmix"
   slave.channels 6
   route_policy duplicate
}

```

Then after this shut down alsa and start it again, or log out and log in. And use this to test surround and see if it works.

```
speaker-test -c 6 -t wav -D surround51

```

Hope I helped.

---

