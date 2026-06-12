---
title: "nVidia drivers 280 hide my built-in sound card?"
date: 2011-09-07
forum: Multimedia Software
---

### Post by linsnos on 2011-09-07
Hi! 
(This is not really an Ubuntu issue, but since many people use Ubuntu and nVidia drivers, it might be relevant to post here anyway.)

After a fresh install of Ubuntu 11.04 I follow the (non-standard) procedures to make a manual installation of the nVidia drivers, and run NVIDIA-Linux-x86-280.13.run.
After reboot, the graphics works as expected, but my built-in sound card is no longer used. 
Instead, an nVidia sound device is used, but my GT240 does not have any sound capabilities (what I am aware of anyway).

It is not listed with aplay -l, but it is listed when I run lspci | grep Audio.
lshw reports my device as "UNCLAIMED".

I have submitted some information below, which might be of relevance. I suspect it could be some kernel module conflict, but I have no clue how to fix it.

If you could help me with this I would be very happy! I want my sound back, and I want it to come from my motherboard!
(Below is selected output from: lspci, aplay, lsmod, lshw, dmesg)

Edit: 
more /lib/modules/`uname -r`/modules.alias | grep 'snd' | grep 'nv'
give the line
alias snd-hda-codec-nvhdmi snd_hda_codec_hdmi
Can that give a clue to what to do?

$lspci | grep Audio =>
02:00.1 Audio device: nVidia Corporation High Definition Audio Controller (rev a1)
**80:01.0 Audio device: VIA Technologies, Inc. VT1708/A [Azalia HDAC] (VIA High Definition Audio Controller) (rev 10)**

I want to use the bold one, but ALSA does not find it, so that's why I suspect some trouble with module loading.
------------------------------------------------------------------

$aplay -l => 
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 7: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 8: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 9: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

------------------------------------------------------------------

$lsmod | grep snd =>
Module                  Size  Used by
snd_hda_codec_hdmi     27479  4 
snd_hda_intel          24140  0 
snd_hda_codec          90901  2 snd_hda_codec_hdmi,snd_hda_intel
snd_hwdep              13274  1 snd_hda_codec
snd_pcm                80244  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25269  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28659  2 snd_pcm,snd_seq
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    55295  9 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              12600  1 snd
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm

------------------------------------------------------------------

$lshw -c sound =>

  *-multimedia            
       description: Audio device
       product: High Definition Audio Controller
       vendor: nVidia Corporation
       physical id: 0.1
       bus info: pci@0000:02:00.1
       version: a1
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=HDA Intel latency=0
       resources: irq:25 memory:deffc000-deffffff
  *-multimedia UNCLAIMED
       description: Audio device
       product: VT1708/A [Azalia HDAC] (VIA High Definition Audio Controller)
       vendor: VIA Technologies, Inc.
       physical id: 1
       bus info: pci@0000:80:01.0
       version: 10
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress cap_list
       configuration: latency=0

------------------------------------------------------------------

$dmesg (some of the output) =>

12.013240] WARNING: at /build/buildd/linux-2.6.38/drivers/pci/pci.c:118 pci_ioremap_bar+0x57/0x60()
[   12.013243] Hardware name: MS-7253
[   12.013244] Modules linked in: snd_hda_codec_hdmi ppdev snd_hda_intel(+) snd_hda_codec snd_hwdep snd_pcm parport_pc snd_seq_midi snd_rawmidi snd_seq_midi_e
vent snd_seq snd_timer snd_seq_device snd k8temp i2c_viapro soundcore snd_page_alloc lp shpchp parport usbhid hid usb_storage uas pata_via via_rhine floppy sa
ta_via
[   12.013269] Pid: 469, comm: modprobe Tainted: P            2.6.38-8-generic #42-Ubuntu
[   12.013272] Call Trace:
[   12.013279]  [<c104f912>] ? warn_slowpath_common+0x72/0xa0
[   12.013282]  [<c128fa07>] ? pci_ioremap_bar+0x57/0x60
[   12.013285]  [<c128fa07>] ? pci_ioremap_bar+0x57/0x60
[   12.013289]  [<c104f962>] ? warn_slowpath_null+0x22/0x30
[   12.013292]  [<c128fa07>] ? pci_ioremap_bar+0x57/0x60
[   12.013299]  [<f8d417cc>] ? azx_create+0x330/0x71a [snd_hda_intel]
[   12.013305]  [<f8d41ded>] ? azx_probe+0xa4/0x20f [snd_hda_intel]
[   12.013309]  [<c1291f77>] ? local_pci_probe+0x47/0xb0
[   12.013313]  [<c12933f8>] ? pci_device_probe+0x68/0x90
[   12.013317]  [<c1333d8d>] ? really_probe+0x4d/0x150
[   12.013321]  [<c133bffb>] ? pm_runtime_barrier+0x4b/0xb0
[   12.013325]  [<c133402c>] ? driver_probe_device+0x3c/0x60
[   12.013328]  [<c13340d1>] ? __driver_attach+0x81/0x90
[   12.013331]  [<c1334050>] ? __driver_attach+0x0/0x90
[   12.013334]  [<c1333188>] ? bus_for_each_dev+0x48/0x70
[   12.013337]  [<c1292e00>] ? pci_device_remove+0x0/0xf0
[   12.013340]  [<c1333c3e>] ? driver_attach+0x1e/0x20
[   12.013343]  [<c1334050>] ? __driver_attach+0x0/0x90
[   12.013346]  [<c1333858>] ? bus_add_driver+0xb8/0x250
[   12.013349]  [<c1292e00>] ? pci_device_remove+0x0/0xf0
[   12.013352]  [<c1334316>] ? driver_register+0x66/0x110
[   12.013355]  [<c1292515>] ? __pci_register_driver+0x45/0xb0
[   12.013361]  [<f8d47017>] ? alsa_card_azx_init+0x17/0x1000 [snd_hda_intel]
[   12.013364]  [<c1001255>] ? do_one_initcall+0x35/0x170
[   12.013369]  [<f8d47000>] ? alsa_card_azx_init+0x0/0x1000 [snd_hda_intel]
[   12.013374]  [<c108899b>] ? sys_init_module+0xdb/0x230
[   12.013380]  [<c1509bf4>] ? syscall_call+0x7/0xb
[   12.013382] ---[ end trace 77ab60665e12c426 ]---
[   12.013384] hda-intel: ioremap error
[   12.013394] HDA Intel 0000:80:01.0: PCI INT A disabled
[   12.744651] nvidia 0000:02:00.0: PCI INT A -> GSI 24 (level, low) -> IRQ 24
[   12.744662] nvidia 0000:02:00.0: setting latency timer to 64
[   12.744668] vgaarb: device changed decodes: PCI:0000:02:00.0,olddecodes=io+mem,decodes=none:owns=io+mem
[   12.744960] NVRM: loading NVIDIA UNIX x86 Kernel Module  280.13  Wed Jul 27 16:55:43 PDT 2011

---

### Post by linsnos on 2011-09-08
It turns out there is a bug for VIA VT1708/A, [see link]("http://hardc0l2e.wordpress.com/2011/04/25/vt1708a-workaround-for-ubuntu-10-10/") for the solution I found.
Summarized, the solution was to
sudo nano /etc/default/grub
by adding pci=use_crs to the boot options, e.g
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash pci=use_crs"
then make a
sudo update-grub
and reboot.

You might also have to select the preferred sound card in e.g System Settings -> Sound.

---

