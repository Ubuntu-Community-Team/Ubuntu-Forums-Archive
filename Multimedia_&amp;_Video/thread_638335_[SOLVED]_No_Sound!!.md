---
title: "[SOLVED] No Sound!!"
date: 2007-12-11
forum: Multimedia &amp; Video
---

### Post by blue_gibbon on 2007-12-11
Dear All,

         Problem: No sound plays on my PC.

            I have :
                       Audigy SB0090 Sound card 
                       Via controller.
                       AMD Processor
                       GA-7VAX BOard
                       Upgraded to UBuntu 7.10

Following instructions from here:
[https://help.ubuntu.com/community/DebuggingSoundProblems](https://help.ubuntu.com/community/DebuggingSoundProblems)

geek@geek-desktop:~$ cat /proc/asound/cards
 0 [V8235          ]: VIA8233 - VIA 8235
                      VIA 8235 with ALC650E at 0xc000, irq 20
 1 [UART           ]: MPU-401 UART - MPU-401 UART
                      MPU-401 UART at 0x330, irq 5
 2 [Audigy         ]: Audigy - Audigy 1 [SB0090]
                      Audigy 1 [SB0090] (rev.3, serial:0x531102) at 0xa800, irq 21
geek@geek-desktop:~$ 

NOTE>> AUDIGY IS MY SOUND CARD 


             My alsa-base file:
          # autoloader aliases
install sound-slot-0 /sbin/modprobe snd-card-0
install sound-slot-1 /sbin/modprobe snd-card-1
install sound-slot-2 /sbin/modprobe snd-card-2
install sound-slot-3 /sbin/modprobe snd-card-3
install sound-slot-4 /sbin/modprobe snd-card-4
install sound-slot-5 /sbin/modprobe snd-card-5
install sound-slot-6 /sbin/modprobe snd-card-6
install sound-slot-7 /sbin/modprobe snd-card-7

# Cause optional modules to be loaded above generic modules
install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe --quiet snd-ioctl32 ; : ; }
install snd-pcm /sbin/modprobe --ignore-install snd-pcm && { /sbin/modprobe --quiet snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer && { /sbin/modprobe --quiet snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq && { /sbin/modprobe --quiet snd-seq-midi ; /sbin/modprobe --quiet snd-seq-oss ; : ; }
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi && { /sbin/modprobe --quiet snd-seq-midi ; : ; }
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe -Qb saa7134-alsa ; : ; }

# Load snd-seq for devices that don't have hardware midi;
#   Ubuntu #26283, #43682, #56005; works around Ubuntu #34831 for
#   non-Creative Labs PCI hardware
install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe -Qb snd-seq ; }
# Prevent abnormal drivers from grabbing index 0
options snd-bt87x index=-2
options cx88-alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-0   >>>>>>>> EDITED LINE
options snd-usb-usx2y index=-2
options snd-usb-caiaq index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388




>>>>options snd-usb-audio index=-0<<< This line i added No matter what i do audigy stays at the lowest doesnt come to card 0 ,am i on the right method?

Windows i would add the drivers from the CD how do i do it with 
Ubuntu ? It has it own collection of drivers?


geek@geek-desktop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: V8235 [VIA 8235], device 0: VIA 8235 [VIA 8235]
  Subdevices: 4/4
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
card 0: V8235 [VIA 8235], device 1: VIA 8235 [VIA 8235]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: Audigy [Audigy 1 [SB0090]], device 0: emu10k1 [ADC Capture/Standard PCM Playback]
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
card 2: Audigy [Audigy 1 [SB0090]], device 2: emu10k1 efx [Multichannel Capture/PT Playback]
  Subdevices: 8/8
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
card 2: Audigy [Audigy 1 [SB0090]], device 3: emu10k1 [Multichannel Playback]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
geek@geek-desktop:~$ 

geek@geek-desktop:~$ lspci -v

PARTIAL LIST

MY sound card
00:0b.0 Multimedia audio controller: Creative Labs SB Audigy (rev 03)
        Subsystem: Creative Labs SB0090 Audigy Player/OEM
        Flags: bus master, medium devsel, latency 32, IRQ 21
        I/O ports at a800 [size=32]
        Capabilities: <access denied>




UBUNTU IS WOW

---

### Post by linuxwizard on 2007-12-12
Have you tried this
check that your switches are set correctly - for instance that if you use the analog output the analog switch is set ON or that the digital or S/PDIF switch is set OFF.

To get to the switches > right click speaker icon on gnome panel > open volume control > click on switch tab > you could have 3 or 4 settings there look for the one analog/digital unmark it > try playing something

---

### Post by blue_gibbon on 2007-12-12
WOW IT WORKS I WENT TO VOLUME CONTROL ON TOP RIGHT CORNER OPENED SWITCHES
UNCHECKED THE CHECKBOX THERE NOW IT WORKS OK ,There was only one checkbox there
>>Audigy Analog/Digital Output Jack

THANX MATE

---

### Post by linuxwizard on 2007-12-12
You're Welcome Glad to hear that it worked for you. Please mark thread solved.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

### Post by blue_gibbon on 2007-12-12
Dear All,

Hey its not working again sound has just stopped kindly advice.
I kinda got it working twidling around with sound buttons.
BUt did the same settings today wont work KIndly advice.

The  sound comes after restarting my pc a couple of times ??

Or it doesnt ?
whats wrong anyone please advice.

---

### Post by blue_gibbon on 2007-12-16
Working now.I had to disable my on board sound card in the BIOS.
Didn't notice I had an on board card.
Thank You All.:popcorn:

---

### Post by shadyedsan on 2007-12-16
here is a quick guide that i found here on ubuntu forums (can't remember which user it was though?) which helped me get sound back all the time.

In terminal type

less /proc/asound/modules

That will show you which soundcards occupy which slot and what their names are.

My output is

 0 snd_cmipci
 1 snd_mpu401
 2 snd_via82xx

Now identify which cards you don't want to use and note their names.

In terminal now type

sudo gedit /etc/modprobe.d/alsa-base

Find the place where it says something like
# Prevent abnormal drivers from grabbing index 0
and in the list below add
options snd_whateveryourcardnameswere index=-2

(replace whateveryourcardnameswere with the soundcard you don't want to use, also snd_ may appear as snd- )

If you have two cards you want to blacklist then you add two lines with different names.

Now save /etc/modprobe.d/alsa-base and reboot the computer. It *should* now set the "wrong" sound cards to slot -2 (thus, making them disabled) and the correct soundcard should thus grab slot 0 and work.

---

### Post by hoanglinh9466 on 2007-12-16
I 'm using Kubuntu, and since I reinstall Kubuntu, I can't hear any sound from my computer. In Window, I still hear sound normally. In KMix, I have already set Master and PCM to max, in switch tab, I checked Lineln and IEC958.

Someone can help me ???

---

