---
title: "PC hangs during recording.  PVR-150 problems?"
date: 2008-02-15
forum: Mythbuntu
---

### Post by joshp on 2008-02-15
I've recently set up my first myth box.  Right now the hardware is:
[LIST]
[*]AMD Athlon(tm) 64 Processor 3400+
[*]1GB DDR ram
[*]gigabit mATX motherboard (with nvida 6150 onboard video)
[*]tuner:  hauppage pvr-150
[*]320GB sata drive, running in IDE mode I believe
[*]antec NSK2400 case
[/LIST]

I've been having a problem with the video capture.  Occasionally when capture starts, the video is blank (black screen) and there is no audio.  Associated with this the box hard locks, usually within about twenty minutes.  This occurs about once every 1-2 days.  I can not reliably reproduce it, it seems random and is not associated with load on the box.  I've scoured the logs and the only error I can find is:

```
mythtv kernel: [35867.401910] ivtv0: DMA TIMEOUT 00000001 0
```

I've heard about the DMA problems with this card: [http://ivtvdriver.org/trac/ticket/48]("http://ivtvdriver.org/trac/ticket/48"),
but the error message I get is different.  Also the symptoms are similar but not the same.  

I've changed the PCI latency on the hauppage to 252, and disabled the only other device on the PCI bus which was the firewire ports on the motherboard.

Does anyone have any suggestions?  I'm not sure where to go next?  Do I need a new card?

---

### Post by joshp on 2008-02-15
Ok, so I've done more googling and I've made some progress.  It seems that the problem is inherent to the PVR and is fixed in the latest version of the drivers:  [http://dl.ivtvdriver.org/ivtv/stable/ChangeLog-0.10]("http://dl.ivtvdriver.org/ivtv/stable/ChangeLog-0.10").

```
	- It turns out that the cx23415/6 DMA engine cannot do scatter/gather
	  DMA reliably. Every so often depending on the phase of the moon and
	  your hardware configuration the cx2341x DMA engine simply chokes on
	  it and you have to reboot to get it working again.

	  This change replaced the scatter/gather DMA by single transfers at a
	  time, where the driver is now responsible for DMA-ing each buffer.

	  Many thanks to Mark Bryars <mark.bryars@etvinteractive.com> for
	  discovering the link between scatter/gather and the DMA timeouts.
```

So how do I go about upgrading to ivtv 0.10.6?  Any help would be appreciated as I'm totally confused as to how to do this and it seems like a lot of others are as well on other forums.

Thanks,
-Josh

---

### Post by Slim Backwater on 2008-03-21
I'm a little late here, but maybe this can help.

I took a perfectly running ubuntu 7.10 server with mythtv-backend and a PVR 150 , upgraded the video card to an ATI X800 and broke ivtv with that same error, ivtv0: DMA TIMEOUT 00000001 0

I worked on it for a few hours and ended up pulling the X800 and reinstalling the Nvidia Quadro FX and now it works again.

The Nvidia Quadro FX is a non 3-d accelerated card and I was trying to convert the server into a workstation which is why i installed the X800.

The problem might not have been directly related to the video card, as it could have been a power supply issue.  I have 6 hard drives a PCI GigE card a PCI Promise Ultra133 TX2 and the Hauppage in this machine powered by a ThermalTake TR-430W, and it's possible that the X800 simply pulled too much power.

Also, I installed the machine with ubuntu server cd, but did an apt-get install ubuntu-desktop linux-generic after switching the video card so I initially thought the software changes were responsible.  Switching the cards back and getting it to work kinda indicates that it's the hardware in the machine.

---

