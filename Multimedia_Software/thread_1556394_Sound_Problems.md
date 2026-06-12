---
title: "Sound Problems"
date: 2010-08-19
forum: Multimedia Software
---

### Post by John A on 2010-08-19
I'm posting this again, and on another page again, as I got no help last time. I have the usual  problem of "My sound is not working". I'd love for any help. I have a  few images and my output from ```
lspci
``` ```
lspci -v
``` and ```
aplay -l
``` Please help me as soon as possible. Thanks, John.

P.S - I can't really do anything with the speaker as it is hidden in the case.
-------------------------------------------------------------------------------------------------------
john@john-desktop:/usr/src$ lspci
00:00.0 Host bridge: Intel Corporation 82Q963/Q965 Memory Controller Hub (rev 02)
00:01.0 PCI bridge: Intel Corporation 82Q963/Q965 PCI Express Root Port (rev 02)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HB/HR (ICH8/R) LPC Interface Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801H (ICH8 Family) 4 port SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
00:1f.5 IDE interface: Intel Corporation 82801H (ICH8 Family) 2 port SATA IDE Controller (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc RV516 [Radeon X1300/X1550 Series]
01:00.1 Display controller: ATI Technologies Inc RV516 [Radeon X1300/X1550 Series] (Secondary)
03:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5754 Gigabit Ethernet PCI Express (rev 02)
-------------------------------------------------------------------------------------------------------
john@john-desktop:/usr/src$ lspci -v
00:00.0 Host bridge: Intel Corporation 82Q963/Q965 Memory Controller Hub (rev 02)
    Subsystem: Dell Device 01da
    Flags: bus master, fast devsel, latency 0
    Capabilities: <access denied>
    Kernel modules: intel-agp

00:01.0 PCI bridge: Intel Corporation 82Q963/Q965 PCI Express Root Port (rev 02)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
    I/O behind bridge: 0000d000-0000dfff
    Memory behind bridge: dfd00000-dfefffff
    Prefetchable memory behind bridge: 00000000c0000000-00000000cfffffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
    Subsystem: Dell Device 01da
    Flags: bus master, medium devsel, latency 0, IRQ 16
    I/O ports at ff20 [size=32]
    Kernel driver in use: uhci_hcd

00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
    Subsystem: Dell Device 01da
    Flags: bus master, medium devsel, latency 0, IRQ 17
    I/O ports at ff00 [size=32]
    Kernel driver in use: uhci_hcd

00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02) (prog-if 20)
    Subsystem: Dell Device 01da
    Flags: bus master, medium devsel, latency 0, IRQ 22
    Memory at dfffbc00 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
    Subsystem: Dell Device 01da
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at dfffc000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
    I/O behind bridge: 00001000-00001fff
    Memory behind bridge: dfc00000-dfcfffff
    Prefetchable memory behind bridge: 00000000d0000000-00000000d01fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 02)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
    I/O behind bridge: 00003000-00003fff
    Memory behind bridge: dfb00000-dfbfffff
    Prefetchable memory behind bridge: 00000000d0200000-00000000d03fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
    Subsystem: Dell Device 01da
    Flags: bus master, medium devsel, latency 0, IRQ 23
    I/O ports at ff80 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
    Subsystem: Dell Device 01da
    Flags: bus master, medium devsel, latency 0, IRQ 17
    I/O ports at ff60 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
    Subsystem: Dell Device 01da
    Flags: bus master, medium devsel, latency 0, IRQ 18
    I/O ports at ff40 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02) (prog-if 20)
    Subsystem: Dell Device 01da
    Flags: bus master, medium devsel, latency 0, IRQ 23
    Memory at ff980800 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev f2) (prog-if 01)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=04, subordinate=04, sec-latency=32
    Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801HB/HR (ICH8/R) LPC Interface Controller (rev 02)
    Flags: bus master, medium devsel, latency 0
    Capabilities: <access denied>
    Kernel modules: iTCO_wdt

00:1f.2 IDE interface: Intel Corporation 82801H (ICH8 Family) 4 port  SATA IDE Controller (rev 02) (prog-if 8f [Master SecP SecO PriP PriO])
    Subsystem: Dell Device 01da
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 20
    I/O ports at fe00 [size=8]
    I/O ports at fe10 [size=4]
    I/O ports at fe20 [size=8]
    I/O ports at fe30 [size=4]
    I/O ports at fec0 [size=16]
    I/O ports at ecc0 [size=16]
    Capabilities: <access denied>
    Kernel driver in use: ata_piix

00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
    Subsystem: Dell Device 01da
    Flags: medium devsel, IRQ 9
    Memory at dfffbb00 (32-bit, non-prefetchable) [size=256]
    I/O ports at ece0 [size=32]
    Kernel modules: i2c-i801

00:1f.5 IDE interface: Intel Corporation 82801H (ICH8 Family) 2 port  SATA IDE Controller (rev 02) (prog-if 85 [Master SecO PriO])
    Subsystem: Dell Device 01da
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 20
    I/O ports at fe40 [size=8]
    I/O ports at fe50 [size=4]
    I/O ports at fe60 [size=8]
    I/O ports at fe70 [size=4]
    I/O ports at fed0 [size=16]
    I/O ports at ecd0 [size=16]
    Capabilities: <access denied>
    Kernel driver in use: ata_piix

01:00.0 VGA compatible controller: ATI Technologies Inc RV516 [Radeon X1300/X1550 Series]
    Subsystem: Dell Device 0402
    Flags: bus master, fast devsel, latency 0, IRQ 27
    Memory at c0000000 (64-bit, prefetchable) [size=256M]
    Memory at dfde0000 (64-bit, non-prefetchable) [size=64K]
    I/O ports at dc00 [size=256]
    Expansion ROM at dfe00000 [disabled] [size=128K]
    Capabilities: <access denied>
    Kernel driver in use: radeon
    Kernel modules: radeon

01:00.1 Display controller: ATI Technologies Inc RV516 [Radeon X1300/X1550 Series] (Secondary)
    Subsystem: Dell Device 0403
    Flags: bus master, fast devsel, latency 0
    Memory at dfdf0000 (64-bit, non-prefetchable) [size=64K]
    Capabilities: <access denied>

03:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5754 Gigabit Ethernet PCI Express (rev 02)
    Subsystem: Dell Device 01da
    Flags: bus master, fast devsel, latency 0, IRQ 28
    Memory at dfbf0000 (64-bit, non-prefetchable) [size=64K]
    Expansion ROM at <ignored> [disabled]
    Capabilities: <access denied>
    Kernel driver in use: tg3
    Kernel modules: tg3

---

### Post by jabeavers on 2010-08-19
I'm no expert, but have you tried alsamixer and turned up all the outputs?

---

### Post by John A on 2010-08-19
> **jabeavers said:**
> I'm no expert, but have you tried alsamixer and turned up all the outputs?

Yes, again I have an image to show.

---

### Post by jabeavers on 2010-08-19
Can I see the output of aplay -l, please? Also, do you have an /etc/asound.conf or ~/.asoundrc file?

---

### Post by John A on 2010-08-19
> **jabeavers said:**
> Can I see the output of aplay -l, please? Also, do you have an /etc/asound.conf or ~/.asoundrc file?

Sorry, I thought I had put the output from aplay -l. Also, I dont have a file 
/etc.asound.conf and I don't have a folder with a **~** as it's name.
----------------------------------------------------------------------------------------------------------
john@john-desktop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: AD198x Digital [AD198x Digital]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
----------------------------------------------------------------------------------------------------------

---

### Post by jabeavers on 2010-08-19
Ok, not having /etc/asound.conf is not a problem. Sorry about the confusion, on linux, the tilde ~ refers to your home directory. Your home directory is usually /home/<yourusername>. From your posts, it looks like your home directory will be in /home/john/ Also, any file that starts with a period will be a hidden file. So, to see if you have a file called .asoundrc in your home directory, type the following:

cd ~
ls -a

cd ~ will put you in your home directory and ls -a will list all the files (even hidden ones) in your home directory. Please see if you have the file .asoundrc in your home directory. If you do have it, can you post the contents of that file. It's ok if you don't have it.

Thanks.

---

### Post by John A on 2010-08-19
> **jabeavers said:**
> Ok, not having /etc/asound.conf is not a problem. Sorry about the confusion, on linux, the tilde ~ refers to your home directory. Your home directory is usually /home/<yourusername>. From your posts, it looks like your home directory will be in /home/john/ Also, any file that starts with a period will be a hidden file. So, to see if you have a file called .asoundrc in your home directory, type the following:

cd ~
ls -a

cd ~ will put you in your home directory and ls -a will list all the files (even hidden ones) in your home directory. Please see if you have the file .asoundrc in your home directory. If you do have it, can you post the contents of that file. It's ok if you don't have it.

Thanks.

Unfortunately, I don't have a file called .asoundrc after looking. The closest thing to anything audio-related is Pulse which another post said to download.

---

### Post by jabeavers on 2010-08-19
When you did alsamixer, did you push the right arrow to see more sliders, or is that all there was to see?

Are you using external speakers?
Are you using the analog out or the digital out?
Is your external speaker volume turned up?

Please type the following and see what happens:
$speaker-test -c 2 -t pink

You push control-C to stop the test. Post any output if it doesn't make sound.

---

### Post by John A on 2010-08-19
> **jabeavers said:**
> When you did alsamixer, did you push the right arrow to see more sliders, or is that all there was to see?

Are you using external speakers?
Are you using the analog out or the digital out?
Is your external speaker volume turned up?

Please type the following and see what happens:
$speaker-test -c 2 -t pink

You push control-C to stop the test. Post any output if it doesn't make sound.

The image below shows the only things that were there.
My speakers are inside the case, so I wouldn't call them external.
I am using the digital output. Look at the image below.
Again, they're not external.

The output was:
john@john-desktop:~$ $speaker-test -c 2 -t pink
No command '-test' found, did you mean:
 Command 'ztest' from package 'zfs-fuse' (universe)
 Command 'stest' from package 'stage' (universe)
 Command 'ctest' from package 'cmake' (main)
 Command 'ptest' from package 'parmetis-test' (multiverse)
 Command 'ptest' from package 'pacemaker' (universe)
 Command 'mtest' from package 'parmetis-test' (multiverse)
 Command 'test' from package 'coreutils' (main)
-test: command not found

---

### Post by jabeavers on 2010-08-19
Sorry, the "$" in front of the command is your command prompt. It is standard practice on linux forums to put the dollar sign before commands to indicate that you type the command at a command prompt. I forgot them in my pervious post, but if you see them, they are not usually part of the command. Try it again without the dollar sign.

Ok, now I'm confused about the internal speakers. Do you mean speakers inside the case (as in, that little speaker that is used for the beep)? I'm used to soundcards that have jacks on the back which connect to an external amplifier and speakers. If you have some, can you try plugging in some headphones into the analog outputs on your card and see if you can hear anything?

Again, try the speaker-test command.

Thanks

---

### Post by John A on 2010-08-19
> **jabeavers said:**
> Sorry, the "$" in front of the command is your command prompt. It is standard practice on linux forums to put the dollar sign before commands to indicate that you type the command at a command prompt. I forgot them in my pervious post, but if you see them, they are not usually part of the command. Try it again without the dollar sign.

Ok, now I'm confused about the internal speakers. Do you mean speakers inside the case (as in, that little speaker that is used for the beep)? I'm used to soundcards that have jacks on the back which connect to an external amplifier and speakers. If you have some, can you try plugging in some headphones into the analog outputs on your card and see if you can hear anything?

Again, try the speaker-test command.

Thanks

There are two speakers in the case. One for the beep, and one Dell gives you the option to put inside the case for a Optiplex 745. One beeps, one plays music.

After removing the dollor sign, the output was:
-------------------------------------------------------------------------------------------------------
john@john-desktop:~$ speaker-test -c 2 -t pink

speaker-test 1.0.22

Playback device is default
Stream parameters are 48000Hz, S16_LE, 2 channels
Using 16 octaves of pink noise
Rate set to 48000Hz (requested 48000Hz)
Buffer size range from 96 to 1048576
Period size range from 32 to 349526
Using max buffer size 1048576
Periods = 4
was set period_size = 262144
was set buffer_size = 1048576
 0 - Front Left
 1 - Front Right
Time per period = 14.958534
-------------------------------------------------------------------------------------------------------
I "still" have no sound. ](*,)

---

### Post by jabeavers on 2010-08-19
Ok, try this.
$speaker-test -D hw:0,1 -c 2 -t pink

I think that command is correct. See if that does anything.

---

### Post by John A on 2010-08-19
> **jabeavers said:**
> Ok, try this.
$speaker-test -D hw:0,1 -c 2 -t pink

I think that command is correct. See if that does anything.

The output was strange. It was as the sound card was busy, "even though" it can't play sound. The output is below:
-------------------------------------------------------------------------------------------------------
john@john-desktop:~$ speaker-test -D hw:0,1 -c 2 -t pink

speaker-test 1.0.22

Playback device is hw:0,1
Stream parameters are 48000Hz, S16_LE, 2 channels
Using 16 octaves of pink noise
Playback open error: -16,Device or resource busy
Playback open error: -16,Device or resource busy
Playback open error: -16,Device or resource busy
Playback open error: -16,Device or resource busy
Playback open error: -16,Device or resource busy
Playback open error: -16,Device or resource busy
Playback open error: -16,Device or resource busy
Playback open error: -16,Device or resource busy
Playback open error: -16,Device or resource busy
Playback open error: -16,Device or resource busy
Playback open error: -16,Device or resource busy
Playback open error: -16,Device or resource busy
^C
-------------------------------------------------------------------------------------------------------
I stopped it as it seemed to repeat itself.

---

### Post by jabeavers on 2010-08-19
Yes, you did good to stop it. Do you have pulseaudio installed? Something might have the device already open. Try it like this:

$pasuspender speaker-test -D hw:0,1 -c 2 -t pink

This will suspend pulseaudio while the speaker test operates.

---

### Post by John A on 2010-08-19
> **jabeavers said:**
> Yes, you did good to stop it. Do you have pulseaudio installed? Something might have the device already open. Try it like this:

$pasuspender speaker-test -D hw:0,1 -c 2 -t pink

This will suspend pulseaudio while the speaker test operates.

I remember installing pulse earlier this day. The output is below:
----------------------------------------------------------------------------------------------------------
john@john-desktop:~$ pasuspender speaker-test -D hw:0,1 -c 2 -t pink
pasuspender: invalid option -- 'D'
----------------------------------------------------------------------------------------------------------

---

### Post by jabeavers on 2010-08-19
Oh sorry, that was my fault. Try it like this:

$pasuspender -- speaker-test -D hw:0,1 -c 2 -t pink

I doubt this will work, but let's try. Also, i'm not real familiar with the pasuspender command, I *think* I have the command right now.

---

### Post by John A on 2010-08-19
> **jabeavers said:**
> Oh sorry, that was my fault. Try it like this:

$pasuspender -- speaker-test -D hw:0,1 -c 2 -t pink

I doubt this will work, but let's try. Also, i'm not real familiar with the pasuspender command, I *think* I have the command right now.
 The output is below:
-------------------------------------------------------------------------------------------------------
john@john-desktop:~$ pasuspender -- speaker-test -D hw:0,1 -c 2 -t pink

speaker-test 1.0.22

Playback device is hw:0,1
Stream parameters are 48000Hz, S16_LE, 2 channels
Using 16 octaves of pink noise
Rate set to 48000Hz (requested 48000Hz)
Buffer size range from 64 to 1048576
Period size range from 32 to 524288
Using max buffer size 1048576
Periods = 4
was set period_size = 262144
was set buffer_size = 1048576
 0 - Front Left
 1 - Front Right
Time per period = 10.951625
^CGot SIGINT, exiting.
-------------------------------------------------------------------------------------------------------

---

### Post by jabeavers on 2010-08-19
No sound? The program is doing its job correctly, the sound is just not going anywhere. Did you try headphones? I think the easiest fix would be to plug in external speakers into your pc. You can buy some for as little as $5 online (then you have to pay shipping which defeats the point... sigh), however, if you can find a site that has the cheap speakers with free shipping... that might work.

Honestly, I would try the headphones in the ananlog output on the soundcard. If you hear stuff from them, buy a speaker system that you like and you will have sound. If you don't want to buy extra speakers, I will do some research and try and help you.

---

### Post by John A on 2010-08-19
> **jabeavers said:**
> No sound? The program is doing its job correctly, the sound is just not going anywhere. Did you try headphones? I think the easiest fix would be to plug in external speakers into your pc. You can buy some for as little as $5 online (then you have to pay shipping which defeats the point... sigh), however, if you can find a site that has the cheap speakers with free shipping... that might work.

Honestly, I would try the headphones in the analog output on the soundcard. If you hear stuff from them, buy a speaker system that you like and you will have sound. If you don't want to buy extra speakers, I will do some research and try and help you.

OMG, I hear sound! As for now, I will go to bed happy that after switching to analog output there is sound from my headphones. Luckily, there is an Asda, UK's Walmart, about a mile from here. Thank you so much! The only help you can give me is to tell me how to put [SOLVED] in this post...seriously.

---

### Post by jabeavers on 2010-08-19
Click on the "Thread Tools" link above the posts on this page to the right. If you started the thread (which you did) the last options should be to mark this as solved. I'm not real happy with the outcome, it's been working the entire time, just no speakers attached to the output to have sound come out of.

Have you had Windows on this box and had sound come out of the internal speaker??

---

### Post by John A on 2010-08-20
> **jabeavers said:**
> Click on the "Thread Tools" link above the posts on this page to the right. If you started the thread (which you did) the last options should be to mark this as solved. I'm not real happy with the outcome, it's been working the entire time, just no speakers attached to the output to have sound come out of.

Have you had Windows on this box and had sound come out of the internal speaker??

Yes I once had a propitiatory operating system on my computer which used my internal speakers well...I once had that.:p

---

### Post by jabeavers on 2010-08-20
I'm sure there is a way to route the sound to the internal speakers if that is what you want. How do you want to proceed from here?

---

### Post by John A on 2010-08-20
> **jabeavers said:**
> I'm sure there is a way to route the sound to the internal speakers if that is what you want. How do you want to proceed from here?

I'd like to know how to route the sound. But I don't think it's detecting the speaker *(along with other things that aren't being detected*)

---

### Post by jabeavers on 2010-08-20
What's the model of your pc? Surely there's some sort of header on the motherboard/soundcard with pins that connect to the speaker. I need to see the specs on your pc to see what might need to happen. I don't think the problem is software related, but I could be wrong. Honestly, this is slightly outside my range of experience, so we're both treding new ground from here on out.

---

### Post by John A on 2010-08-20
> **jabeavers said:**
> What's the model of your pc? Surely there's some sort of header on the motherboard/soundcard with pins that connect to the speaker. I need to see the specs on your pc to see what might need to happen. I don't think the problem is software related, but I could be wrong. Honestly, this is slightly outside my range of experience, so we're both treding new ground from here on out.

I use and love a Dell Optiplex 745. If the pin is disconnected, I won't be able to anything as I don't have my anti-static wrist band and I know well enough that it's better not to risk it. I accidentally broke a £3000 build after relying on the case's metal.

---

### Post by jabeavers on 2010-08-20
Ok, try this. In alsamixer, go to the last slider (mono) and turn it up all the way and make sure it is not muted (the MM under the slider). Press "M" or space bar to change the mute state. Then see if you get sound.

---

### Post by John A on 2010-08-20
> **jabeavers said:**
> Ok, try this. In alsamixer, go to the last slider (mono) and turn it up all the way and make sure it is not muted (the MM under the slider). Press "M" or space bar to change the mute state. Then see if you get sound.

That fixed it! WOOOOOOOOO!!!  :guitar:Now all my audio equipment is working. Yeah! Man are you good.

---

### Post by jabeavers on 2010-08-20
Wooo Hooo!! I got the idea from here: [http://www.ubuntumini.com/2009/03/fix-audio-in-ubuntu-904-on-dell-mini-9.html](http://www.ubuntumini.com/2009/03/fix-audio-in-ubuntu-904-on-dell-mini-9.html)

I'm glad it worked. I know the feeling of getting sound after not having it for a long time. Praise God. Have a great time with your speakers.

John

---

### Post by John A on 2010-08-20
I love it when a plan comes together!

[IMG]http://www.zenkimchi.com/FoodJournal/wp-content/uploads/2009/01/HannibalSmith.jpg[/IMG]

---

