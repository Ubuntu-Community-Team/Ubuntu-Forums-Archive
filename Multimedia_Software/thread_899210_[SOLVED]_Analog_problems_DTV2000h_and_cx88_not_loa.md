---
title: "[SOLVED] Analog problems DTV2000h and cx88 not loading"
date: 2008-08-24
forum: Multimedia Software
---

### Post by tedkel on 2008-08-24
I can not get analog sound on my DTV 2000h card and it appears not to be loading at startup. I have been searching the posts and trying different things for about 6 weeks now and any help would be appreciated.

I run  *$ cat /proc/asound/cards* and get

 0 [SB             ]: HDA-Intel - HDA ATI SB
                      HDA ATI SB at 0xfe024000 irq 18
 1 [HDMI           ]: HDA-Intel - HDA ATI HDMI
                      HDA ATI HDMI at 0xfdffc000 irq 20

no sign of the cx88 card

the cx88 card also does not show up in alsamixer?


when I run *$ lspci -v | grep -i audio* then I see the card

00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia
01:05.1 Audio device: ATI Technologies Inc RS780 Azalia controller
03:06.0 Multimedia video controller: Conexant CX23880/1/2/3 PCI Video and Audio Decoder (rev 05)
03:06.1 Multimedia controller: Conexant CX23880/1/2/3 PCI Video and Audio Decoder [Audio Port] (rev 05)
03:06.2 Multimedia controller: Conexant CX23880/1/2/3 PCI Video and Audio Decoder [MPEG Port] (rev 05)


the relevant bit of my dmesg file is;

[   38.301818] tuner' 1-0061: chip found @ 0xc2 (cx88[0])
[   38.302583] tuner' 1-0063: chip found @ 0xc6 (cx88[0])
[   38.358985] tuner-simple 1-0061: creating new instance
[   38.358990] tuner-simple 1-0061: type set to 63 (Philips FMD1216ME MK3 Hybrid Tuner)
[   38.361684] input: cx88 IR (WinFast DTV2000 H) as /devices/pci0000:00/0000:00:14.4/0000:03:06.2/input/input6
[   38.396675] cx88[0]/2: cx2388x 8802 Driver Manager
[   38.396703] ACPI: PCI Interrupt 0000:03:06.2[A] -> GSI 20 (level, low) -> IRQ 22
[   38.396713] cx88[0]/2: found at 0000:03:06.2, rev: 5, irq: 22, latency: 32, mmio: 0xf9000000
[   38.396760] ACPI: PCI Interrupt 0000:03:06.0[A] -> GSI 20 (level, low) -> IRQ 22
[   38.396768] cx88[0]/0: found at 0000:03:06.0, rev: 5, irq: 22, latency: 32, mmio: 0xfb000000
[   38.396799] cx88[0]/0: registered device video0 [v4l2]
[   38.396817] cx88[0]/0: registered device vbi0
[   38.451924] cx88/2: cx2388x dvb driver version 0.0.6 loaded
[   38.451928] cx88/2: registering cx8802 driver, type: dvb access: shared
[   38.451930] cx88[0]/2: subsystem: 107d:6f2b, board: WinFast DTV2000 H [card=51]
[   38.451933] cx88[0]/2: cx2388x based DVB/ATSC card
[   38.483318] tuner-simple 1-0061: attaching existing instance
[   38.483322] tuner-simple 1-0061: type set to 63 (Philips FMD1216ME MK3 Hybrid Tuner)
[   38.486424] DVB: registering new adapter (cx88[0])
[   38.486426] DVB: registering frontend 0 (Conexant CX22702 DVB-T)...
[   38.633635] lp0: using parport0 (interrupt-driven).
[   38.743123] cx88_alsa: disagrees about version of symbol videobuf_dma_free
[   38.743127] cx88_alsa: Unknown symbol videobuf_dma_free
[   38.743163] cx88_alsa: disagrees about version of symbol cx88_core_put
[   38.743165] cx88_alsa: Unknown symbol cx88_core_put
[   38.743234] cx88_alsa: Unknown symbol videobuf_pci_alloc
[   38.743257] cx88_alsa: disagrees about version of symbol cx88_core_irq
[   38.743259] cx88_alsa: Unknown symbol cx88_core_irq
[   38.743291] cx88_alsa: disagrees about version of symbol cx88_core_get
[   38.743293] cx88_alsa: Unknown symbol cx88_core_get
[   38.743439] cx88_alsa: disagrees about version of symbol btcx_riscmem_free
[   38.743441] cx88_alsa: Unknown symbol btcx_riscmem_free
[   38.743528] cx88_alsa: disagrees about version of symbol videobuf_dma_init
[   38.743529] cx88_alsa: Unknown symbol videobuf_dma_init
[   38.743583] cx88_alsa: disagrees about version of symbol cx88_sram_channel_dump
[   38.743585] cx88_alsa: Unknown symbol cx88_sram_channel_dump
[   38.743618] cx88_alsa: disagrees about version of symbol cx88_sram_channel_setup
[   38.743619] cx88_alsa: Unknown symbol cx88_sram_channel_setup
[   38.743647] cx88_alsa: disagrees about version of symbol videobuf_dma_init_kernel
[   38.743649] cx88_alsa: Unknown symbol videobuf_dma_init_kernel
[   38.743696] cx88_alsa: Unknown symbol videobuf_pci_dma_unmap
[   38.743760] cx88_alsa: Unknown symbol videobuf_pci_dma_map
[   38.743792] cx88_alsa: disagrees about version of symbol cx88_risc_databuffer
[   38.743794] cx88_alsa: Unknown symbol cx88_risc_databuffer
[   38.743818] cx88_alsa: disagrees about version of symbol videobuf_to_dma
[   38.743820] cx88_alsa: Unknown symbol videobuf_to_dma


Definitely something wrong with cx88-alsa. I have seen a bug report on something like this but not sure that it is m y problem.

Do I need to add some scritpt to get the cx88 card in my asound.conf?

Any ideas very much appreciated.

Thanks.

---

### Post by tedkel on 2008-08-26
New Kernel & Headers downloaded today solved my problem. (2.6.24-19.41)

CX88 now shows in alsa mixer

dmesg now says

[   35.343424] cx88[0]/1: CX88x/0: ALSA support for cx2388x boards

---

