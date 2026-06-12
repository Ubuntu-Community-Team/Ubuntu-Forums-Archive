---
title: "What's involved in making power *ON* work over LIRC"
date: 2012-02-29
forum: Mythbuntu
---

### Post by 1script on 2012-02-29
Hi all, I'm trying to wrap my head around this issue: I have a multi-device Logitech remote that sets up its working modes (Watch TV, Watch DVD etc.) by sending "ON" signals to all devices that would be involved in the chosen activity. They then have all to be powered of by the remote as well else the remote confuses itself and thinks that you're still watching tv a week later and would not control, say, a bluray player.

Anyhow, long story short - one of those devices is an XBMC machine with a USB LIRC receiver. It obviously does not work when the PC is off (and I'm very much sure it's the exact same way it would be in Mythbuntu, which I'm also interested in trying).

So, how can a problem of turning the PC with a LIRC receiver on be solved? What extra hardware would I need?    

Thanks for all your input!

---

### Post by nickrout on 2012-03-01
> **1script said:**
> Hi all, I'm trying to wrap my head around this issue: I have a multi-device Logitech remote that sets up its working modes (Watch TV, Watch DVD etc.) by sending "ON" signals to all devices that would be involved in the chosen activity. They then have all to be powered of by the remote as well else the remote confuses itself and thinks that you're still watching tv a week later and would not control, say, a bluray player.

Anyhow, long story short - one of those devices is an XBMC machine with a USB LIRC receiver. It obviously does not work when the PC is off (and I'm very much sure it's the exact same way it would be in Mythbuntu, which I'm also interested in trying).

So, how can a problem of turning the PC with a LIRC receiver on be solved? What extra hardware would I need?    

Thanks for all your input!

I think you need to be googling "wake on usb" - ie if your system supports wake on usb, and you put the computer to sleep (rather than off) then a remote keypress should be able to wake it. (I assume it is a USB receiver!)

---

