---
title: "Sound card not detected"
date: 2007-10-20
forum: Multimedia &amp; Video
---

### Post by gj15987 on 2007-10-20
I have a Toshiba laptop and was experiencing the problem of a very very low audio output so I followed the instructions under "Update to the latest version of ALSA" in the following link and now my sound card is not detected at all, [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

On system startup I get the following error message:

> The volume control did not find any elements and/or devices to control. This means either that you don't have the right GStreamer plug-ins installed, or that you don't have a sound card configured.

You can remove the volume control from the panel by right-clicking the speaker icon on the panel and selecting "Remove From Panel" from the menu.

Is there a way for me to just go back to how my system was BEFORE I carried out the steps on that site or a way to get it to detect my card again?

If i run lspci my card shows up as:

> 00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)


Thanks in advance.

Oh...also, I've run alsaconf and it said it configured my sound card ok...obviously not though.

---

### Post by gdudeman on 2007-10-20
I'm having the same problem with the same card:

Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)

It worked before I upgraded from Feisty to Gutsy yesterday. n00b here - any help appreciated.

---

