---
title: "System Freeze on LiveTV"
date: 2008-08-24
forum: Mythbuntu
---

### Post by WiFlag on 2008-08-24
Been running Mythbuntu 8.04 for a month or so now, and I seem to have a persistent glitch I can't figure out. This is seriously hindering the wife acceptance factor.

I can leave the machine running without watching anything and it seems to chug along recording shows fine - tho I did get a freeze this weekend... but for the most part, no problems.
However, if you watch live TV and a scheduled recording comes up, it will crash maybe about 50% of the time. Sometimes it does it before popping up the window, sometimes after you've made a selection (even if you select No!).

I'm using a PVR-150 and nvidia, and I've read some stuff about graphics problems, so I disabled all the openGL items in the menus, using the Qt painter, and turned off everything that allowed transparency. Also have realtime threads turned off because I figured that would lead to hard locks, but no dice. 

I was meaning to try removing the GLX line from my xorg.conf next [EDIT: didn't work, still freezes when the next scheduled item comes up], so we'll see if that does anything - any other ideas? 
My logs near the latest crash are below - the major common factor seems to be that it's on a record boundary.

Thanks ahead for the help.

mythbackend.log:
```
2008-08-24 20:41:30.664 AFD: Opened codec 0x829f260, id(MPEG2VIDEO) type(Video)
2008-08-24 20:41:30.692 AFD: codec MP2 has 2 channels
2008-08-24 20:41:30.693 AFD: Opened codec 0x829f6d0, id(MP2) type(Audio)
2008-08-24 20:41:31.497 Preview: Grabbed preview '/var/lib/mythtv/recordings/111
1_20080824203000.mpg' 720x480@64s
2008-08-24 20:48:59.237 TVRec(1): Changing from WatchingLiveTV to None
2008-08-24 20:48:59.467 Finished recording Sweat Equity "Master Bedroom": channe
l 1111
2008-08-24 20:49:00.188 MainServer::HandleAnnounce Playback
2008-08-24 20:49:00.189 adding: pvr as a client (events: 0)
2008-08-24 20:49:00.192 TVRec(1): Changing from None to WatchingLiveTV
2008-08-24 20:49:00.197 TVRec(1): HW Tuner: 1->1
2008-08-24 20:49:01.593 ret_pid(0) child(6334) status(0x0)
2008-08-24 20:49:02.594 ret_pid(0) child(6334) status(0x0)
2008-08-24 20:49:03.595 ret_pid(0) child(6334) status(0x0)
2008-08-24 20:49:04.596 ret_pid(6334) child(6334) status(0x0)
2008-08-24 20:49:04.596 External Tuning program exited with no error
2008-08-24 20:49:05.728 MPEGRec(/dev/video0) Warning: Audio sample rate 32000 Hz
                        is not supported by ivtv driver, using 48000 Hz instead.
2008-08-24 20:49:05.733 AutoExpire: CalcParams(): Max required Free Space: 2.0 G
B w/freq: 15 min
2008-08-24 20:49:29.253 AutoExpire: CalcParams(): Max required Free Space: 2.0 G
B w/freq: 15 min

```

mythfrontend.log:
```
2008-08-24 20:48:59.497 TV: Changing from WatchingLiveTV to None
2008-08-24 20:48:59.523 DPMS Reactivated.
2008-08-24 20:49:00.187 TV: Attempting to change from None to WatchingLiveTV
2008-08-24 20:49:00.188 Using protocol version 40
2008-08-24 20:49:06.500 DPMS Deactivated
2008-08-24 20:49:07.210 AFD: Opened codec 0x8349210, id(MPEG2VIDEO) type(Video)
2008-08-24 20:49:07.210 AFD: codec MP2 has 2 channels
2008-08-24 20:49:07.210 AFD: Opened codec 0x84cd6c0, id(MP2) type(Audio)
2008-08-24 20:49:07.267 Opening audio device 'default'. ch 2(2) sr 48000
2008-08-24 20:49:07.267 Opening ALSA audio device 'default'.
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL /dev/mixer
2008-08-24 20:49:07.303 AudioOutput Warning: Mixer attach error -2: No such file
 or directory
                        Check Mixer Name in Setup: '/dev/mixer'
2008-08-24 20:49:07.321 VideoOutputXv: XVideo Adaptor Name: 'NV17 Video Texture'
2008-08-24 20:49:07.354 OSD Theme Dimensions W: 640 H: 480
2008-08-24 20:49:07.683 TV: Changing from None to WatchingLiveTV
greedyhdeint: size changed from 0 x 0 -> 720 x 480
2008-08-24 20:49:07.689 The realtime priority setting is not enabled.
2008-08-24 20:49:07.789 Video timing method: USleep with busy wait
2008-08-24 20:49:49.418 XMLParse::LoadTheme using /usr/share/mythtv/themes/bloot
ube-wide/ui.xml
2008-08-24 20:49:50.870 NVP: prebuffering pause

```

---

### Post by WiFlag on 2008-08-25
It was frozen again when I came home from work...

mythfrontend.log didn't have anything since 9pm the prior night

mythbackend.log:
```
2008-08-25 01:00:09.945 Using protocol version 40
2008-08-25 01:00:09.946 MainServer::HandleAnnounce Monitor
2008-08-25 01:00:09.949 adding: pvr as a client (events: 0)
2008-08-25 01:00:09.950 MainServer::HandleAnnounce Monitor
2008-08-25 01:00:09.951 adding: pvr as a client (events: 1)
2008-08-25 01:00:32.101 AFD: Opened codec 0x82009a0, id(MPEG2VIDEO) type(Video)
2008-08-25 01:00:32.105 AFD: codec MP2 has 2 channels
2008-08-25 01:00:32.106 AFD: Opened codec 0x8200e20, id(MP2) type(Audio)
2008-08-25 01:10:14.974 AutoExpire: CalcParams(): Max required Free Space: 2.0 G
B w/freq: 15 min
2008-08-25 01:25:15.078 AutoExpire: CalcParams(): Max required Free Space: 2.0 G
B w/freq: 15 min
```

Nothing really looks out of the ordinary to me here... any thoughts?

[EDIT: Another freeze tonight, it really seems to only happen if you are watching live TV when a scheduled recording wants to start]

[Another EDIT: saw some posts claiming issues requiring "sudo echo 1024 > /proc/sys/dev/rtc/max-user-freq" - tried it... no dice]

---

### Post by WiFlag on 2008-08-26
Further testing reveals that it will crash if you are watching either live TV or a recorded program when it wants to start recording a scheduled show. And the crash rate is pretty close to 100%

Hardware:
Mobo = MSI 945GT Speedster-A4R
CPU = Intel Celeron M 410 Yonah 1.46GHz
Video = eVGA GeForce 6200
Capture = Hauppauge PVR-150

---

### Post by newlinux on 2008-08-26
when you say crash what do you mean? Computer crashes, frontend crashes, backend crashes? how many tuners do you have? If the system is crashing you might want to look at /var/log/syslog and/or /var/log/messages.

---

### Post by WiFlag on 2008-08-26
Worse than a crash - it's a system freeze - screen locks up the display, accepts no input from mouse or keyboard, doesn't respond to pings.

Just the one tuner.

---

### Post by WiFlag on 2008-08-28
Full reinstall just now... still have the same problem.

I get freezes occasionally in other situations too (once during install, a couple times while on the main menu) but it is nearly 100% chance to freeze if i'm watching TV at the time.

---

### Post by jaakan on 2008-08-29
Since that motherboard has a built in GPU, does it crash with the eVGA GeForce 6200 removed?

---

### Post by ian dobson on 2008-08-29
Hi,

Try sticking your Hauppauge PVR-150 into a different PCI slot, sounds like you have a hardware conflict.

Maybe try creating a file /etc/modprobe.d/ivtv.conf with the text options ivtv enc_mpg_buffers=9 ivtv_yuv_mode=2 

commands:-
echo "options ivtv enc_mpg_buffers=9 ivtv_yuv_mode=2" > /etc/modprobe.d/ivtv.conf

The reboot the system afterwards so that the changes take effect.

Regards
Ian Dobson

---

### Post by mocha on 2008-08-29
2 things I can think of.  Run cat /proc/interrupts check what irqs are being shared.  Run some heavy I/O tests on your hard drive, look at the bonnie++ package in synaptic for that.  You might also want to run memtest.

---

### Post by WiFlag on 2008-08-29
Yeah this weekend I was planning to start the hardware swap dance... but then I saw that lastest post - looked like a pretty easy check... 

results:
           CPU0
```
  0:        219   IO-APIC-edge      timer
  1:          2   IO-APIC-edge      i8042
  4:          2   IO-APIC-edge
  6:          2   IO-APIC-edge      floppy
  8:          7   IO-APIC-edge      rtc
  9:          0   IO-APIC-fasteoi   acpi
 12:          4   IO-APIC-edge      i8042
 14:     354131   IO-APIC-edge      libata
 15:          0   IO-APIC-edge      libata
 16:     611707   IO-APIC-fasteoi   uhci_hcd:usb4, HDA Intel, ivtv0, nvidia
 17:          0   IO-APIC-fasteoi   uhci_hcd:usb3
 18:        423   IO-APIC-fasteoi   uhci_hcd:usb2
 20:          2   IO-APIC-fasteoi   uhci_hcd:usb1, ehci_hcd:usb5
 21:          2   IO-APIC-fasteoi   ohci1394
218:       2808   PCI-MSI-edge      eth0
219:      10171   PCI-MSI-edge      eth1
NMI:          0   Non-maskable interrupts
LOC:    1088096   Local timer interrupts
RES:          0   Rescheduling interrupts
CAL:          0   function call interrupts
TLB:          0   TLB shootdowns
TRM:          0   Thermal event interrupts
SPU:          0   Spurious interrupts
ERR:          0
MIS:          0

```

I'm assuming this tells me IRQ16 is handling both the PVR-150 and the video card

I'll try swapping the pvr-150 around tonight, and the ivtv.conf trick, short puts. 
If those don't work, I'll be trying out the onboard video and/or the video card in my desktop.

---

### Post by WiFlag on 2008-08-30
First try was 
```
echo "options ivtv enc_mpg_buffers=9 ivtv_yuv_mode=2" > /etc/modprobe.d/ivtv.conf
```

This showed some promise with the first recording during live TV not freezing, but the following one still froze.

So I swapped the PVR-150 to another PCI slot, and it stopped being detected. At the same time I had disabled the floppy drive in the BIOS (I don't have one) and for some reason that killed the ability to see the PVR-150. A fun red herring.

I have the system up and running now with the video card still on IRQ16, and the PVR-150 (ivtv0) moved to IRQ20. So far I've done three tests for freezes, all successful. Looks like this may be solved - I'll report back later after more tests.

---

### Post by WiFlag on 2008-08-31
It still has problems. 
It looks like it will randomly freeze after watching LiveTV for a while. This was happening before, but didn't generally pop up due to the scheduled recodings freezing it first. Doesn't appear that the freezes are lined up with the start of new recordings now, which is a big improvement. 

Logs do not indicate anything going on, just froze up at quarter of the hour after maybe 30-40 min of Live TV. No scheduled programs until hours in the future.

I'm hesitant to remove the video card until I've exhausted other options - last time I messed around with it xorg locked me into xorg.conf.failsafe and wouldn't let me out. For now, I've upped the enc_mpg_buffer to 16 meg (max). We'll see if that helps. 

Are there any options I can play with for LiveTV to help? I have only one drive, partitioned 220G of XFS and 20G of ext3, so I'm guessing moving liveTV's writes to ext3 wouldn't buy me anything. Are there options governing what liveTV's quality should be or how much to hold before expiring it?

---

### Post by SniperKIng on 2008-08-31
Hey 

My mythbuntu install also freezes like this but at any time usually within a minute of boot though it has done it when starting to watch live tv its very annoying now.i had to turn acpi=off inorder to boot but now dont have to it just freezes when it wants.As i dont realy know what acpi is im not sure if it would help in this situation.
Tuners - Nova-t 500 (Dual) and some other conexant one.
GPU - Nvidia 8400GS

---

### Post by ian dobson on 2008-08-31
> **SniperKIng said:**
> Hey 

My mythbuntu install also freezes like this but at any time usually within a minute of boot though it has done it when starting to watch live tv its very annoying now.i had to turn acpi=off inorder to boot but now dont have to it just freezes when it wants.As i dont realy know what acpi is im not sure if it would help in this situation.
Tuners - Nova-t 500 (Dual) and some other conexant one.
GPU - Nvidia 8400GS

Are you using EPG from your capture cards?
Try swapping PCI cards around, you could have an IRQ conflict.

PVRs (150/500) are very sensitive to interrupt conflicts/delays or dodgy chipsets (VIA anyone).

Do you see any messages in syslog about setting "latency timer"?

Regards
Ian Dobson

maybe a lspci might help abit to see what hardware you have.

---

### Post by SniperKIng on 2008-08-31
Right i cheacked and it freezed whilst i was doing so lol its a strange freeze though i can still move the mouse but nothing responds.In the syslog it mentioned VIA in some places, it also mentioned (PCI:settings latency timer ect) on a number of occasions.

The IRQ test showed that cx88 and nvidia were both on one line

---

### Post by WiFlag on 2008-08-31
Ok the freeze on scheduled recording glitch I'm going to call solved. But it still freezes :(

Looks like it can run for about 1 hour and 10-20 minutes before it freezes. I checked syslog and I have a whole bunch of setting latency to 64 messages, yet I checked lspci -v for latencies:

Mem controller hub: 0
PCI bridge - root port: 0
onboard audio: 0
PCIe ports 1,5,6, and nvidia card: 0
USB controllers: 0
SATA IDE controller: 0
PVR-150: 128
onboard video: 0
IEEE 1394: 64

video card should be fine, if I recall, latency is irrelevant for PCIe, but that SATA latency is concerning - shoudl that be higher? and why are they almost all 0 when syslog reports 64?
[EDIT: addendum: no VIA chipset for me, my MSI uses Intel N/S bridge]

---

### Post by ian dobson on 2008-08-31
Hi,

I have a PCI latency of 64 for my PVR500 (Dual PVR150). 
128 seems abit high to me maybe someone else can help abit. For me the PVR500 was a plugin and play card.

Maybe you could try increasing the size of the enc_mpg_buffers to maybe 12 or 16mb

Regards
Ian Dobson

---

### Post by WiFlag on 2008-08-31
I have enc_mpg_buffers=16 
Tried latency of 252 (whatever the max is, below 255), and 64, both still froze up in the same timeframe (30 min). 
Tried setting the SATA latency to 64, but it won't take, so I assume that it, like the PCIe card, just doesn't get a latency setting.

---

### Post by WiFlag on 2008-08-31
I pulled the nvidia card and it works now - been watching live tv for 4-5 hours without any freezes. 
So this leads to two scenarios - either I need to figure out hwo to get this nvidia card working or how to get my onboard Intel GMA 950 to do 1280x720 (currently it's sitting in 4:3 aspect 800x600).

[EDIT: Scratch that, I just found 915resolution, I have widescreen now - I will stress test tomorrow, and if it still makes it, this baby is solved.]

---

### Post by SniperKIng on 2008-09-01
Hey i too have, for the time being, stopped the freezing.I did this by turning acpi=off at boot this may help you too its worth a try.

---

### Post by WiFlag on 2008-09-01
Further tests with the new resolution show that it's working now, thanks everyone for their help. 

Others who try this out may want to take a stab at APIC disabling (pretty sure that's what the previous poster meant), but I'm coming up on a hard stop after today - may have the courage to dive back into it after I get back from a business trip next week. SniperKing, I'd be happy to hear if yours continues to work.

---

### Post by klc5555 on 2008-09-02
For what it's worth, I began to have frequent system freezes of exactly this sort (sometimes frontend only, when I could log in remotely and soft-restart the machine; sometimes everything would lock up) in June when the weather began to get warmer, and the room where my Mythbuntu system was would occasionally get to the upper 70s.

I ditched my eVGA GeForce 6200 (with its little heat sink) in favor of a (fan-cooled) GeForce 7300 and have not experienced a single  freeze up on that machine since.

On the other hand, the remote frontend I cobbled together out of spare parts in July and threw the old GeForce 6200 into does lock up in this fashion from time to time despite additional cooling. So as I rebuild the frontend machine this autumn, the 6200 is going to disappear completely in favor of something a bit newer.  

Cheers.

---

