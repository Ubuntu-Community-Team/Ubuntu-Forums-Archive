---
title: "Jack goes insane with Xruns"
date: 2007-02-10
forum: Multimedia &amp; Video
---

### Post by Dylnuge on 2007-02-10
Hello,

I installed all of the Ubuntu Studio packages. I try to start Jack using the Ubuntu Studio settings, and it stops after two seconds. I unchecked the realtime option, and it seems to work, but generating at least 150 xruns every second. I have only been running it for a few minutes, and already my xrun count is at 40,000. Now, I have not compiled my own kernal, but it should not be that bad, should it? I have decent hardware, actually pretty nice (XPS M1710), and I expected better from JACK.

Can anyone point me in the direction of something that may be wrong. The following may help:

lspci:
```
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express PCI Express Root Port (rev 03)
00:1b.0 **Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller** (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 01)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 01)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controller IDE (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
01:00.0 VGA compatible controller: nVidia Corporation Unknown device 0298 (rev a1)
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd Unknown device 0832
03:01.1 Class 0805: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
03:01.2 System peripheral: Ricoh Co Ltd Unknown device 0843 (rev 01)
03:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
03:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)
09:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5752 Gigabit Ethernet PCI Express (rev 02)
0c:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
```

Anyone have any suggestions?

---

### Post by Dylnuge on 2007-02-11
Anyone?

---

### Post by Dylnuge on 2007-02-11
Sorry for bumping, but I really need help with this situation.

Thanks

---

### Post by albesan on 2007-02-13
Can't help you, but since I've got the (x)runs as well I thought I'd help you bumping it again.

a.

---

### Post by Dylnuge on 2007-02-15
In my search for other posts, I found people complaining that their systems ran with about 10 xruns a second.

Never heard anything more about 160. Doesn't seem like anyone knows, so I will search elsewhere.

---

### Post by jbeach on 2007-04-08
I'm running edgy on an XPS M1710 as well and I'm having the same issue with jackd - it'd be great if we could get this resolved - any luck?

[edit]: here's the relevant part of my messages window when I run jackd with realtime checked:

loading driver ..
apparent rate = 48000
creating alsa driver ... hw:0|hw:0|128|2|48000|0|0|nomon|swmeter|-|16bit
control device hw:0
configuring for 48000Hz, period = 128 frames, buffer = 2 periods
nperiods = 2 for capture
nperiods = 2 for playback
14:08:45.748 Server configuration saved to "/home/joe/.jackdrc".
14:08:45.748 Statistics reset.
14:08:45.749 Client activated.
14:08:45.749 Audio connection change.
14:08:45.750 Audio connection graph change.
14:08:45.773 XRUN callback (1).
14:08:47.787 XRUN callback (100 skipped).
jackd watchdog: timeout - killing jackd
zombified - calling shutdown handler
14:08:48.984 Shutdown notification.
14:08:48.999 Client deactivated.
14:08:49.000 JACK was stopped successfully.
cannot read result for request type 7 from server (Connection reset by peer)
cannot send request type 7 to server
cannot read result for request type 7 from server (Broken pipe)


and here's the message window when I uncheck realtime:

loading driver ..
apparent rate = 48000
creating alsa driver ... hw:0|hw:0|128|2|48000|0|0|nomon|swmeter|-|16bit
control device hw:0
configuring for 48000Hz, period = 128 frames, buffer = 2 periods
nperiods = 2 for capture
nperiods = 2 for playback
14:10:12.985 Server configuration saved to "/home/joe/.jackdrc".
14:10:12.986 Statistics reset.
14:10:13.045 Client activated.
14:10:13.060 Audio connection change.
14:10:13.062 Audio connection graph change.
14:10:13.062 XRUN callback (1).
14:10:15.092 XRUN callback (100 skipped).
14:10:17.125 XRUN callback (100 skipped).
14:10:19.165 XRUN callback (100 skipped).
14:10:21.202 XRUN callback (100 skipped).
14:10:23.237 XRUN callback (99 skipped).
14:10:25.277 XRUN callback (100 skipped).
14:10:27.085 Client deactivated.
14:10:27.086 JACK is stopping...
jack main caught signal 15
no message buffer overruns
14:10:27.346 JACK was stopped successfully.

---

### Post by naptastic on 2007-05-02
You need a kernel with the realtime preemption patch. This is the real reason that Ubuntu Studio is going to be such a big deal: you'll be able to have an -rt kernel right out of the box, or, failing that, it will at least be in the Universe repository.

The Ubuntu Wiki has a page about the realtime preemption patch with instructions on how to install a beta package, but I tried it earlier today and got no love. (It seems the package has been removed from the repository.)

---

### Post by drf_av on 2007-05-03
If you get xruns, is because your hw doesn't keep up with jack.
So follow naptastic's advice, if you still experience xruns, increase the period to 1024 frames.
If everything works, then lower it. But, if you're using an integrated, economic sound card, you can't expect miracles. You get low latencies just if you have good hardware. 
The only troubles Jack can get are: crappy hardware, not enough CPU, misconfiguration.
So start lowering the buffer size.

EDIT: I've just noticed (in the first message) that you're actually using an integrated sound card. I've never been able to get under 512 frames, so your trouble should be hardware. If you don't need anything professional, set frames/period to 1024 and you'll be ok. Otherwise, consider buying a professional soundcard.

---

### Post by mosteo on 2007-05-15
I had also the xrun problem with a cheap integrated card and changing the frames would do no good, not even going to ridiculous high values with huge latencies. However, upping the periods from 2 to 3 did wonders. Now I can get the frames down to 64 with less than 5ms latency, which is not bad I guess for a general purpose laptop.

This is with the lowlatency ubuntuStudio kernel, and running jackd with realtime priority.

---

### Post by MetalMusicAddict on 2007-05-15
Things to check:
[LIST]
[*]**sudo su -c 'echo @audio - rtprio 99 >> /etc/security/limits.conf'** needs to be applied
[*]Make sure you have the -lowlatency kernel installed.
[*]Play with your frame #.
[/LIST]

Also your sound card can play a BIG part in all of this. Lots of times a cheap sound card=higher latency.

---

### Post by Drophere on 2007-05-15
> **MetalMusicAddict said:**
> Also your sound card can play a BIG part in all of this. Lots of times a cheap sound card=higher latency.

Ironically I have the opposite problem. 

I've posted a couple of other threads in this and other forums looking for help with Qjackctl settings (no responses so far). By pure luck I stumbled across a setting tonight that works with the via chipset on my motherboard.  So now I have Ardour playing back audio via Jack and my onboard via chipset, but I'm unable to get Jack working with my RME Digi 96/8 PRO, or my Novation Speedio USB audio device.

Ubuntu Studio is a great leap forward as far as ease of installation, but so far I've found it just as hard as other Linux distro's I've tried when it comes to getting audio devices running. I'd be more than willing to try different settings/experiments to see if I can get Ubuntu Studio running with my gear, if someone is able to suggest things to try ...

Cheers,

Malcolm.

(and I hate to say it, but all 3 of these audio devices work happily together using Windows XP :(  )

---

### Post by drf_av on 2007-05-15
First of all check if they're supported @ alsa-project, if they aren't you're in trouble, otherwise you'll find on alsa website a how-to to make them work. If you have a Firewire audio card then check out Freebob to see if it is supported

---

### Post by Drophere on 2007-05-15
> **drf_av said:**
> First of all check if they're supported @ alsa-project, if they aren't you're in trouble, otherwise you'll find on alsa website a how-to to make them work. If you have a Firewire audio card then check out Freebob to see if it is supported

The RME is, but the Speedio is not, so I guess that cancels out the Speedio entirely.

I spent hours last night messing with different settings trying to get the RME card to work, but I didn't find any setting that got rid of the xruns. I guess the Ubuntu Studio main page claim of "It's easy. Just download, install, create" is a little premature. At least as far as pro audio goes.

Considering hardware support/drivers seems to be the only stumbling block, it's surprising that nobody seems to publish a list of working configurations.

---

### Post by drf_av on 2007-05-15
Forget the Speedio, about the RME, can you please tell me if it is a FireWire interface or not? (I'm not using RMEs here, but I've heard good things about them and also about their compatibility with Linux, maybe your problem can be easily solved)

---

### Post by 1ino1eum on 2007-05-16
> **MetalMusicAddict said:**
> Things to check:
[LIST]
[*]**sudo su -c 'echo @audio - rtprio 99 >> /etc/security/limits.conf'** needs to be applied
[*]Make sure you have the -lowlatency kernel installed.
[*]Play with your frame #.
[/LIST]

Also your sound card can play a BIG part in all of this. Lots of times a cheap sound card=higher latency.

hi
I just wonder :
would we have to do that (sudo su -c 'echo @audio - rtprio 99 >> /etc/security/limits.conf'), if we install ubuntustudio, or install the kernel-lowlatency from the ubuntustudio repo ? Or is it done automaticaly by installing ubuntustudio-audio ?
thankx

---

### Post by MetalMusicAddict on 2007-05-16
> **1ino1eum said:**
> hi
I just wonder :
would we have to do that (sudo su -c 'echo @audio - rtprio 99 >> /etc/security/limits.conf'), if we install ubuntustudio, or install the kernel-lowlatency from the ubuntustudio repo ? Or is it done automaticaly by installing ubuntustudio-audio ?
thankx

If you install from our disk you will not need the command. We do it for you. If you install the -lowlatency kernel (comes from the Ubuntu repos BTW) you will need the command.

---

### Post by tristan_koen on 2007-05-21
I have a similar problem, but I have found an easy workaround.
I only experience the problem if I start jack with Qjackctl. If I open a command window and execute

**jackd -R -dfreebob**

it works perfectly. I then use qjackctl to create whatever connections I want. 

I don't know why this happens or if this problem is specific to my installation. Would love to hear if anyone can replicate this.

---

### Post by eArquilla on 2007-05-23
I am currently getting very choppy playback when i try to play audio in ardour or even hydrogen when using jack.  I am using my stock audio card that came with my Jetta Jetbook 9700PX.

Would purchasing an audio interface (I'm looking at the Presonus Firebox) help this situation?
I saw the firebox as supported under freebob, how easy is it to get that up and running?

Thanks for any help

---

### Post by WestCoastSuccess on 2007-08-28
Try working with the suggested settings for the purposes of setup in brackets - you'll want to adjust some of these later to better your latency but you want a bigger latency to get the connection established:

-frames/period (512)
-sample rate (48,000)
-periods/buffer (3)
-input channels (2)
-output channels (2)
-interface (hw:0)
-latency (should show 32 ms with these settings)

The formula for latency is frames per period X periods per buffer divided by sample rate.

See also my posts here for more info - the question was specific to the M-audio Firewire Solo, however the general principles apply:

[http://ubuntuforums.org/showthread.php?t=509312&page=2](http://ubuntuforums.org/showthread.php?t=509312&page=2)

---

### Post by mwiseley on 2007-12-02
WestCoastSuccess - Thank you! I've been messing with qjackctl for days and wasn't getting anything better than a sputtering mess. Those settings just work. I was starting to lose hope.

I'm using the onboard card in a Dell Inspiron E1405. Some people in previous posts here have said "you should use a professional sound card"... can you elaborate... name a few that you know work well in linux? The alsa sound card matrix is way too much information. 

Matt

---

### Post by WestCoastSuccess on 2008-01-10
Glad you found it helpful, Matt!

I did a bunch of research a while ago on soundcards but can't recall too much (that kind of stuff gets erased from my short term memory as soon as the purchase is made...), but my M-Audio Firewire works great (rock solid at 2ms with real time kernel) and I've heard great things about the RME Hammerfall.

---

