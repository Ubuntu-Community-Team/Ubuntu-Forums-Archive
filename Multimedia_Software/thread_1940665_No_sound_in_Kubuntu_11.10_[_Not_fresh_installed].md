---
title: "No sound in Kubuntu 11.10 [ Not fresh installed]"
date: 2012-03-14
forum: Multimedia Software
---

### Post by carot on 2012-03-14
Hi,


As title, my environment is Kubuntu 11.10, 64 bit cpu, 
and I try this web page to enable sound, 
[https://help.ubuntu.com/community/OpenSound](https://help.ubuntu.com/community/OpenSound)

and still does not work.

any help to me, please.

and do i need to provide other information about my environment to here?

[IMG]https://docs.google.com/open?id=0Bw_anl4aGs8UMFVVVUpEb29TQVdDOTJha1h1dVU3dw[/IMG]

---

### Post by carot on 2012-03-16
Following is my pc information:(or need i provide other information?)

sudo lshw -class multimedia
  *-multimedia UNCLAIMED  
       description: Audio device
       product: RV710/730
       vendor: ATI Technologies Inc
       physical id: 0.1
       bus info: pci@0000:01:00.1
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi bus_master cap_list
       configuration: latency=0
       resources: memory:f7dfc000-f7dfffff
  *-multimedia
       description: Audio device
       product: 5 Series/3400 Series Chipset High Definition Audio
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@0000:00:1b.0
       version: 06
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=oss_hdaudio latency=0
       resources: irq:22 memory:f7cf8000-f7cfbfff

---

### Post by SeijiSensei on 2012-03-18
Check that you have the right input and output settings in System Settings > Multimedia > Phonon.  If you have multiple inputs, as it appears you do, KDE may be using the wrong one.

---

### Post by carot on 2012-03-19
> **SeijiSensei said:**
> Check that you have the right input and output settings in System Settings > Multimedia > Phonon.  If you have multiple inputs, as it appears you do, KDE may be using the wrong one.

I pasted my Phonon page at this link
[https://docs.google.com/file/d/0Bw_anl4aGs8UMFVVVUpEb29TQVdDOTJha1h1dVU3dw/edit](https://docs.google.com/file/d/0Bw_anl4aGs8UMFVVVUpEb29TQVdDOTJha1h1dVU3dw/edit)

---

