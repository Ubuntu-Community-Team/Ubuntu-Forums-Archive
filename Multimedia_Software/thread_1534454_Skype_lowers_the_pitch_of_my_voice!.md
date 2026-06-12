---
title: "Skype lowers the pitch of my voice!"
date: 2010-07-19
forum: Multimedia Software
---

### Post by tghe-retford on 2010-07-19
I have Skype installed within Kubuntu, which I downloaded from the official website. After some changes to the sound settings I have been able to use the Skype test call to verify that my headset is working, but the pitch is far lower when the test call is played back to me than it should be.

When I record my voice using Audacity, the pitch is normal on playback and works perfectly, so the headset is clearly fine, but the problem lies with Skype. Is there any way I can adjust settings or is there another reason why the sound on Skype is being played back to me in the test call in a far lower pitch?

I've tried other devices but only two work, both have the same problem with lower pitch in Skype but not Audacity and I also ticked and unticked the 'allow Skype to automatically adjust my mixer levels' option with no change to the pitch.

I am using Skype (Beta) 2.0.1.81 64-bit with Kubuntu and ALSA for the playback and capture of sound to/from my headset (which uses normal phono inputs for sound and mic) on the Realtek ALC883 chipset (using snd_hda_intel).

Thanks in advance.

---

### Post by tghe-retford on 2010-07-19
Managed to fix the problem by downgrading Skype. Had to search for a package though.

I think my problem could be related to this:

[https://jira.skype.com/browse/SCL-454](https://jira.skype.com/browse/SCL-454)

At least it is a known issue.

---

