---
title: "how do I access sound card settings inside linux?"
date: 2009-06-21
forum: Mythbuntu
---

### Post by Arminius on 2009-06-21
hey, I'm running mythbuntu, I'm trying to run skype but I can't get it to hear my microphone, I think I need to access my soundcard settings but I see no way to do that in the menu's

I'm using the creative sound blaster X-Fi Fatal1ty
the driver file is XFiDrv_Linux_Public_US_1.00.tar.gz

don't know how to access any further details until I find the control panel

---

### Post by gradinaruvasile on 2009-06-21
Click on the sound icon in your upper taskbar. And click volume control.

---

### Post by Arminius on 2009-06-21
thanks, found it, but it's no where near as extensive as the windows config, how do I switch from PC speakers to headphone speakers, I got the headphone speakers plugged in right. how do u tell linux to switch?

---

### Post by itlarson on 2009-06-21
alsamixer   (in a terminal)

---

### Post by Arminius on 2009-06-22
ok, that shows me the mixer settings? but not seeing how I can use that to change from PC speakers to Headset speaker

---

### Post by gradinaruvasile on 2009-06-22
> **Arminius said:**
> thanks, found it, but it's no where near as extensive as the windows config, how do I switch from PC speakers to headphone speakers, I got the headphone speakers plugged in right. how do u tell linux to switch?

Alsamixer helps, but has a bit strange interface. A workaround would be opening volume control, click preferences and tick everything. You will have more options to play with. Unfortunately the options differ too much from card to card.

Anyways some help about Alsamixer:

Top to bottom u have 4 lines : Card, Chip, View, Item. Card and chip is only informs u about your hardware.
View: 3 tabs - Playback - It has the items related to playback
- Here you should mute mic, cd, line because those settings may cause interference
- Capture - Items for sound capture (mic volumes, capture volumes)
- All - All items in a disorganised manner. Never used it for anything useful.

Navigation: TAB for changing the tabs, left/right changing items, up/down changing volumes/devices (such as in input source tabs changing mic1, mic2, front mic, etc), "m" mutes/unmutes items (only those that have a box right under the volume bar). Space is used to set capture devices - this works only if the item has "-----" between the volume level and the volume bar. Set only 1 source.

---

### Post by Arminius on 2009-06-22
other then microphone capture and master capture under the capture tab
and master and microphone under the playback tab, which other setting effect the microphone?
cause my comp can't hear my mic now and I've tried shutting some down in a 100 different combinations

so if your comp can't hear your mic? the most likely problem is with?

---

