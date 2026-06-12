---
title: "VXPocket 440 PCMCIA Soundcard"
date: 2010-04-12
forum: Multimedia Software
---

### Post by weematt on 2010-04-12
Hello Everyone,

I am trying to get my pcmcia pro-audio card working.  I'm using Ubuntu 9.10.  The card seems to be seen by the system at the level of 'pccardctl ls', but not recognized as an audio card.  I should also mention that I am using this pcmica card in a desktop through a pcmcia-to-pci adapter.

Any help (even in terms of commands to run to try to search for more information) would be much appreciated.  Here is what I've learned so far.

pccardctl seems to see the card, but not know what it is good for.

```
~$ pccardctl -v -v ls
Socket 0 Bridge:   	[yenta_cardbus] 	(bus ID: 0000:03:06.0)
	Configuration:	state: on	ready: unknown
			Voltage: 5.0V Vcc: 5.0V Vpp: 0.0V
--none--
--none--
Socket 0 Device 0:	[-- no driver --]	(bus ID: 0.0)
	Configuration:	state: on
	Product Name:   Digigram VX-POCKET440 V1.0 R1.0 
	Identification:	manf_id: 0x01f1	card_id: 0x0100
			function: 254 (unknown)
			prod_id(1): "Digigram" (0x8c4bdb78)
			prod_id(2): "VX-POCKET440" (0x53e68e4a)
			prod_id(3): "V1.0" (0xe611e659)
			prod_id(4): "R1.0" (0x6973710e)
~$ 

```

Also, from dmesg, there are some warnings about IRQ that seem pertinent.  Specifically the lines

[18.753868] snd-vxpocket 0.0: pcmcia: request for exclusive IRQ could not be fulfilled.
[18.753870] snd-vxpocket 0.0: pcmcia: the driver needs updating to supported shared IRQ lines.

```
[   17.450555] pcmcia 0.0: pcmcia: registering new device pcmcia0.0
[   17.680832] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x100-0x3af: clean.
[   17.682651] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3e0-0x4ff: clean.
[   17.683428] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x820-0x8ff: clean.
[   17.684074] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xc00-0xcf7: clean.
[   17.684770] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xa00-0xaff: clean.
[   18.753860] pcmcia: Driver needs updating to support IRQ sharing.
[   18.753868] snd-vxpocket 0.0: pcmcia: request for exclusive IRQ could not be fulfilled.
[   18.753870] snd-vxpocket 0.0: pcmcia: the driver needs updating to supported shared IRQ lines.
[   18.793669] snd-vxpocket 0.0: firmware: requesting vx/bx_1_vp4.b56
[   18.804909] HDA Intel 0000:00:14.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   19.147962] vx: can't load firmware vx/bx_1_vp4.b56
[   19.272809] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:14.2/input/input8
[   19.437451] pcmcia: Driver needs updating to support IRQ sharing.
[   19.437459] snd-vxpocket 0.0: pcmcia: request for exclusive IRQ could not be fulfilled.
[   19.437462] snd-vxpocket 0.0: pcmcia: the driver needs updating to supported shared IRQ lines.
[   19.477251] snd-vxpocket 0.0: firmware: requesting vx/bx_1_vp4.b56
[   19.479666] vx: can't load firmware vx/bx_1_vp4.b56

```

I wonder which driver its referring to as "needing to be upgraded".  Is it

a) pcmcia->pci adapter driver?
b) the driver for the soundcard?
c) the driver for pcmcia in general?

Thanks in advance for any suggestions you can provide.

Cheers,

Matt

---

### Post by weematt on 2010-04-13
I have made some progress..

I found 

[http://www.math.tu-clausthal.de/~matsa/linux/vxpocket/](http://www.math.tu-clausthal.de/~matsa/linux/vxpocket/)

which pointed out that ubuntu does not come with alsa-firmware installed.  It comes with alsa-firmware-loaders, but not alsa-firmware.

I downloaded from [http://www.alsa-project.org/main/index.php/Download](http://www.alsa-project.org/main/index.php/Download) the latest version of alsa-firmware, uncompressed it and in the dir:

./configure
make
sudo make install

...which seems to have helped as now I get

```

/proc/asound$ ls
card0  cards    hwdep    oss  SB   timers   VXPocket440
card1  devices  modules  pcm  seq  version

```

and unlike before, the card seems to be recognized in pccardctl ls
```

~$ pccardctl -vv ls
Socket 0 Bridge:   	[yenta_cardbus] 	(bus ID: 0000:03:06.0)
	Configuration:	state: on	ready: unknown
			Voltage: 5.0V Vcc: 5.0V Vpp: 0.0V
--none--
--none--
Socket 0 Device 0:	[snd-vxpocket]		(bus ID: 0.0)
	Configuration:	state: on
	Product Name:   Digigram VX-POCKET440 V1.0 R1.0 
	Identification:	manf_id: 0x01f1	card_id: 0x0100
			function: 254 (unknown)
			prod_id(1): "Digigram" (0x8c4bdb78)
			prod_id(2): "VX-POCKET440" (0x53e68e4a)
			prod_id(3): "V1.0" (0xe611e659)
			prod_id(4): "R1.0" (0x6973710e)

```

I can also see a new card now in system->preferences->sound->hardware, but I'm not sure it's correctly id'd the card. as it says 'CB1410 Cardbus Controller', not 'VXpocket440'.  

Unfortunately, though this is not yet resolved, because my whole system will lock up sometimes and the card is not playing audio (instead blasting loud static).  

So one step forward, but still not there.

[B]Question:
[/B]
Does anyone know what the meaning of the card being listed in system->preferences->sound->hardware as 'CB1410 Cardbus Controller' means?  Is this possibly the problem?  Or is it just saying that it's using the pcmcia cardbus to control the card?  It would be great if someone with a working VXpocket card could tell me what their system has there.

---

### Post by weematt on 2010-04-14
I've moved my queries to a group that is a bit more specific to my problems, to follow my ongoing efforts go to

[http://www.mail-archive.com/alsa-user@lists.sourceforge.net/msg26462.html](http://www.mail-archive.com/alsa-user@lists.sourceforge.net/msg26462.html)

cheers,

Matt

---

