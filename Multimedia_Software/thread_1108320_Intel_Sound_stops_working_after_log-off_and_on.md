---
title: "Intel Sound stops working after log-off and on"
date: 2009-03-27
forum: Multimedia Software
---

### Post by solidsnake204 on 2009-03-27
I have this strange problem where normally my sound works fine.

But if I log-off then log back in without restarting the PC, I lose sound.

>         *-multimedia
             description: Audio device
             product: 82801G (ICH7 Family) High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 01
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=HDA Intel latency=0 module=snd_hda_intel


When I click the test button in the Sound settings, I get this error:
> audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Failed to connect stream: Invalid argument
Then the window stops responding and I have to kill it with xkill.

If you need more info then please just ask.

Thanks in advance.
Dan

---

