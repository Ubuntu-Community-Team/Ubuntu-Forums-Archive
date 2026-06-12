---
title: "can't record from line-in"
date: 2011-06-02
forum: Multimedia Software
---

### Post by DarthFennec on 2011-06-02
I run Kubuntu 11.04 and I have a C-Media CM8738 sound card. My problem is, my card won't record from the line-in jack, even when I set it to capture in alsamixer. Furthermore, the mic jack only records when both the line-in and the mic are set to capture in alsamixer. I'm using the same settings I used in 10.04, and the line-in captured fine then. I have no idea what the problem is, I've been searching around and I can't find anything about it. Thanks in advance.

---

### Post by Zorael on 2011-06-02
Hm. Kubuntu uses the PulseAudio sound server nowadays; I think it's simply not routing the sound input to your recording application. 

Start by installing the PulseAudio volume control tool **[pavucontrol](apt://pavucontrol)** unless already installed, and start it.

[list=1][*]Go to the Input Devices tab and pick Line-in in the Ports dropdown menu at your soundcard's device entry. Make sure it's not muted and that it's set to be the Fallback device.
[*]Now go to the Recording tab and find the program you're trying to record with in that list. It may need to be trying to record to show up, depending on how good its pulse integration is. Make sure its dropdown menu has your soundcard selected and is not muted.
[*]Now try again.[/list]

In parallel to this, make sure to try toggling which device is recording in alsamixer. I think setting an input to "not recording" in alsamixer stops PulseAudio from being able to tap into its stream.

---

### Post by DarthFennec on 2011-06-03
I followed those steps, and now it's not recording from line-in or mic, although I can get it recording mic again through alsamixer.

---

### Post by DarthFennec on 2011-06-22
Bump. Still can't find anything about this at all ... have tried a bunch of things and none of them have helped. Hopefully somebody knows how to fix this.

---

### Post by BuntuNooob on 2011-06-22
This might be a silly question, but can you record through usb? Is the software recording at all?

---

### Post by DarthFennec on 2011-06-26
I don't have any USB recording hardware, so no I can't. But I can record from my mic port so the recording software is working, I just can't do it from my Line-In port.

---

### Post by DarthFennec on 2011-07-02
Well ... I fixed it by switching to OpenSUSE :-|
Ciao, Ubuntu forum. It's been fun.

---

