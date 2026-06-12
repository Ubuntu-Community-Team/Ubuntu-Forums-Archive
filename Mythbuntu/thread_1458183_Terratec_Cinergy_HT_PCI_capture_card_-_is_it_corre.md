---
title: "Terratec Cinergy HT PCI capture card - is it correctly installed?"
date: 2010-04-19
forum: Mythbuntu
---

### Post by Lightsider on 2010-04-19
I'm a Linux newbie who has decided to take the plunge and build a HTPC running Mythbuntu. Mythbuntu installed correctly and I got as far as scanning for channels in the Mythbuntu backend setup - but no TV channels were found. 

Hardware:
- Terratec Cinergy HT PCI TV capture card (PCI subsystem 153b:1177)
- MSI p965 Neo motherboard

I'm running Mythbuntu 9.10 (linux 2.6.31-20-generic, mythtv 0.22.0+fixes22594-0ubuntu1). According to [http://www.linuxtv.org/wiki/index.php/DVB-T_PCI_Cards#TerraTec](http://www.linuxtv.org/wiki/index.php/DVB-T_PCI_Cards#TerraTec) my capture card was not supported in October 2007, so I was hoping things had changed since then! 

dmesg output: [http://pastebin.com/5x0LhYza](http://pastebin.com/5x0LhYza) (sorry, I wasn't sure which lines were relevant)
lspci output: 
```

03:01.0 Multimedia video controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder (rev 05)
    Subsystem: TERRATEC Electronic GmbH Device 1177
    Flags: bus master, medium devsel, latency 20, IRQ 19
    Memory at fa000000 (32-bit, non-prefetchable) [size=16M]
    Capabilities: <access denied>
    Kernel driver in use: cx8800
    Kernel modules: cx8800

03:01.1 Multimedia controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder [Audio Port] (rev 05)
    Subsystem: TERRATEC Electronic GmbH Device 1177
    Flags: bus master, medium devsel, latency 64, IRQ 19
    Memory at f9000000 (32-bit, non-prefetchable) [size=16M]
    Capabilities: <access denied>
    Kernel driver in use: cx88_audio
    Kernel modules: cx88-alsa

03:01.2 Multimedia controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder [MPEG Port] (rev 05)
    Subsystem: TERRATEC Electronic GmbH Device 1177
    Flags: bus master, medium devsel, latency 64, IRQ 19
    Memory at fb000000 (32-bit, non-prefetchable) [size=16M]
    Capabilities: <access denied>
    Kernel driver in use: cx88-mpeg driver manager
    Kernel modules: cx8802

```I tried following the instructions on [how to test a DVB card]("http://parker1.co.uk/mythtv_dvb.php") , and got as far as scanning for channels, but got error messages like:
```

>>> tune to: 490000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_2_3:FEC_AUTO:QAM_16:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_4:HIERARCHY_NONE
WARNING: >>> tuning failed!!!
>>> tune to: 490000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_2_3:FEC_AUTO:QAM_16:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_4:HIERARCHY_NONE (tuning failed)
WARNING: >>> tuning failed!!!

```I tried testing the card under Windows XP, and it works fine. Hence my questions:

- Did my card install (and was recognised) correctly? Mythtv and the channel scan failing say no, but lspci lists associated kernel modules... (or have I misunderstood something?)
- Do I need additional firmware? I looked at [http://www.linuxtv.org/wiki/index.php/How_to_Obtain,_Build_and_Install_V4L-DVB_Device_Drivers](http://www.linuxtv.org/wiki/index.php/How_to_Obtain,_Build_and_Install_V4L-DVB_Device_Drivers) , but I have to admit I was fairly daunted.
- In general, any advice on what I should look at to get my card working would be grand! I'm happy to dig in deeper, but I'm a little lost on where to look next...

Thanks a lot in advance!

---

