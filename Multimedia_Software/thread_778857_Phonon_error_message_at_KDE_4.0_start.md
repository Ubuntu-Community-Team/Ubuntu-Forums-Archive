---
title: "Phonon error message at KDE 4.0 start"
date: 2008-05-02
forum: Multimedia Software
---

### Post by vertago1 on 2008-05-02
The first image is the error I get every time KDE 4 starts.

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=68456&stc=1&d=1209740891[/IMG]

for the sake of searches I am going to type out the error:

**Phonon**
The audio playback device **VIA 8237 with ALC850 (VIA 8237)** does not work.
Falling back to **C-Media CMI8728 (model 55) (C-Media PCI DAC/ADC)**

This image is what my sound settings look like
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=68455&stc=1&d=1209740891[/IMG]

The strange thing to note is that the VIA sound device is listed twice. This doesn't always happen and after I restarted the 2nd listing went away. The one application I could find to test phonon was kopete. When I select notifications and do a test play of a sound sometimes it works, but sometimes it gives me the same error above and plays it over my 2nd sound card.

The reason I have two cards is that one is 6 channel for multimedia and normal applications. The second card is for recording and voice chat / skype.

When I set C-Media as the preferred device I never get the error, so I suspect the problem is with the VIA driver. If I figure out how to fix it I will post but any help would be appreciated.

Really this problem is not high priority but it would be nice not to be getting errors when I am trying to play sounds, and to have them play over the correct device.

Thanks

---

