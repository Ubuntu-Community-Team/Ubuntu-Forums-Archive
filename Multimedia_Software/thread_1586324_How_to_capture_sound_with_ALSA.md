---
title: "How to capture sound with ALSA??"
date: 2010-10-01
forum: Multimedia Software
---

### Post by Buffalo_Guy on 2010-10-01
I recently converted an amd 64 bit WINdows machine to Lucid 64 bit.  Everything has gone well.  I had numerous issues with Pulseaudio that I removed it.  Sound with Alsa has been great, including system theme sounds.  I can record via a mike as well.  What I cannot do is to capture sounds coming through the sound card.  When I record I am getting empty files.  The mixer indicates that there are two capture devices.   I am looking for some troubleshooting insight here.  What steps can I take to narrow this down?  Here is some data on my audio card.  Any insight or tips would be greatly appreciated,   Steve

**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC888 Analog
[ALC888 Analog]
Subdevices: 1/1
Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: ALC888 Digital
[ALC888 Digital]
Subdevices: 1/1
Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI
HDMI]
Subdevices: 1/1
Subdevice #0: subdevice #0
*
****************************************************

*-multimedia
                description: Audio device
                product: RV710/730
                vendor: ATI Technologies Inc
                physical id: 0.1
                bus info: pci@0000:01:00.1
                version: 00
                width: 64 bits
                clock: 33MHz
                capabilities: pm pciexpress msi bus_master cap_list
                configuration: driver=HDA Intel latency=0
                resources: irq:44 memory:fdffc000-fdffffff
        *-pci:1
             description: PCI bridge
             product: RD790 PCI to PCI bridge (PCI express gpp port F)
             vendor: ATI Technologies Inc
             physical id: a
             bus info: pci@0000:00:0a.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:41 ioport:d000(size=4096) memory:fde00000-fdefffff ioport:fdb00000(size=1048576)

---

### Post by Pablo_F on 2010-10-02
With the jack audio server, you can use jack_capture or timemachine to record whatever goes through the audio card.

Cheers! Pablo

---

### Post by Buffalo_Guy on 2010-10-04
THanks for the info on jack audio server.  Can you recommend a tutorial to walk me through the installation?  I am willing to give it a shot as I need audio capture for a number of projects.

---

