---
title: "MTP Devices Data Transfer Fix"
date: 2010-08-01
forum: Multimedia Software
---

### Post by HeadHunter00 on 2010-08-01
For the past few days, i have been trying to fix a common error related to mtp devices such as creative zen. Because of the new updated libmtp8 library, it is impossible to transfer files into any mtp devices. However there is a fix that will remove this issue. Here's how:
1. Get the older karmic version of libmtp8 from here: [http://packages.ubuntu.com/karmic/libmtp8](http://packages.ubuntu.com/karmic/libmtp8)
2. Install this package from terminal using: sudo dpkg -i libmtp8*.deb
3. Lock libmtp8 from the synaptic package manager, so it doesn't get updated.
4. Uninstall and then downgrade any mtp packages (through packages.ubuntu.com) that become broken after step 2 to the karmic version.
5. Enjoy.

---

### Post by colnizster on 2010-10-15
HALLELUJAH!!!!

Thank you, thank you, thank you! I want to smack myself for not thinking of this :mad: I can finally upgrade all my *buntus and still be able to use my zen, instead of always needing a 9,10 in my multi-boot.

Cannot thank you enough.

---

### Post by spadewarrior on 2011-01-28
I tried this as I've got a Zen MX 16Gb, but it didn't help. Turns out it auto mounted to /media/usb, but no audio apps recognise this. I have tried gmpt, rhythmbox and qlix. 

The only way I currently have of adding / removing tracks with any ease is by sudo-ing a pcmanfm instance (I run lxde) so I can drag and drop files into its Music folder from Rhythmbox. 

I'm unsure what permissions I have to set to remove the need for the sudo. Any advice here?

Warnings for the curious:

- the Zen apparently has no mp3v1 tags, only v2. You'll see you mp3s listed as 'unknown artists' if you use v1 tags (or if you use no tags at all).

- although the player eventually moves the tracks into the
Music/ImportedMusic, I found that putting them straight in there means they aren't found on the next library re-build. So just put them in Music.

edit: second thoughts, no idea what the ImportedMusic folder is for as it's still empty. Ah well.

---

