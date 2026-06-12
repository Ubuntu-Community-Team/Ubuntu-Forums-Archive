---
title: "USB Sound Card is not recognized"
date: 2009-05-02
forum: Multimedia Software
---

### Post by Aren on 2009-05-02
Hi there.

I have a Native Instruments Audio Kontrol 1 USB sound card that I've never been able to really make it work in (K)Ubuntu.

Problem is that since one of the latest upgrades on Kubuntu Jaunty, whenever I try to log in to my account with the sound card pluged in, my computer freezes completely and I have to switch it off and on and unplug the sound card before entering my username and password.

If I plug it in once I've logged in I can keep working without a problem.

Today I connected the sound card and, when checking the output of dmesg, I got this:

```
[13164.733017] usb 3-1: new high speed USB device using ehci_hcd and address 9
[13165.052475] hub 3-0:1.0: unable to enumerate USB device on port 1
[13166.764020] usb 3-1: new high speed USB device using ehci_hcd and address 10
[13166.897441] usb 3-1: string descriptor 0 read error: -61
[13166.898439] usb 3-1: string descriptor 0 read error: -61
[13166.899194] usb 3-1: string descriptor 0 read error: -61
[13166.899572] usb 3-1: configuration #1 chosen from 1 choice
[13166.901430] usb 3-1: string descriptor 0 read error: -61
[13166.907705] usb 3-1: string descriptor 0 read error: -61
[13166.908450] usb 3-1: string descriptor 0 read error: -61
[13166.909185] usb 3-1: string descriptor 0 read error: -61
[13166.910263] input:  as /devices/pci0000:00/0000:00:1e.0/0000:05:02.2/usb3/3-1/input/input10

```

The strange thing is that this wasn't happening before. I was able to plug my sound card and when executing asoundconf -list, I could see the sound card in the output.

Is it a bug in the kernel module (snd-usb-caiaq) that controls this sound card? Any hint on what can I do at least to gather some additional information?

The sound card and the USB hub are both working fine as I have no problem at all using them with Vista.

Thanks a lot in advance.

---

