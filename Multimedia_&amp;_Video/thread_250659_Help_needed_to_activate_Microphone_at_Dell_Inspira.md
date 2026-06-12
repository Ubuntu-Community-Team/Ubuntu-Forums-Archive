---
title: "Help needed to activate Microphone at Dell Inspiration 630"
date: 2006-09-04
forum: Multimedia &amp; Video
---

### Post by Najand on 2006-09-04
Hi,
I am trying to use sound recording facilities in Dapper, but it seems there is a bug does not allow ALSA to record the sound.
I searched for the bug in bugzilla and found the soulution but cannot understand any of it. Is there anyone who can help me to set my sound device up to use the Microphone? I appreciate any helps in advance.

> From eac90cd6fc5973a8f7c2a3041440993dd9dd260b Mon Sep 17 00:00:00 2001
From: Daniel T. Chen <crimsun@garnish.localdomain>
Date: Fri, 25 Aug 2006 20:21:36 -0400
Subject: [PATCH] [UBUNTU:sound/pci/hda/] #42600: Fix silent recording from microphone on Dell Inspiron 630m (and assorted models)

UpstreamStatus: Added in upstream alsa-kernel hg changeset:
		61bfe5b3a7ae [[http://hg-mirror.alsa-project.org/alsa-kernel?cmd=changeset;node=61bfe5b3a7aef3de2bab53677209dbc2ce827250;style=raw]](http://hg-mirror.alsa-project.org/alsa-kernel?cmd=changeset;node=61bfe5b3a7aef3de2bab53677209dbc2ce827250;style=raw])

References:	ALSA: #2038
		Ubuntu: #42600

Certain Dell laptops need to use the reference model due to a possible
BIOS bug, so make their subdevice IDs correspond to model=ref.

This commit closes Ubuntu: #42600.

Signed-off-by: Daniel T Chen <crimsun@ubuntu.com>
---
 sound/pci/hda/patch_sigmatel.c |    7 +++++++
 1 files changed, 7 insertions(+), 0 deletions(-)

diff --git a/sound/pci/hda/patch_sigmatel.c b/sound/pci/hda/patch_sigmatel.c
index d2a8333..5882d6d 100644
--- a/sound/pci/hda/patch_sigmatel.c
+++ b/sound/pci/hda/patch_sigmatel.c
@@ -465,6 +465,13 @@ static struct hda_board_config stac9205_
 	  .pci_subvendor = PCI_VENDOR_ID_INTEL,
 	  .pci_subdevice = 0x2668, /* DFI LanParty */
 	  .config = STAC_REF }, /* SigmaTel reference board */
+	/* Dell laptops have BIOS problem */
+	{ .pci_subvendor = PCI_VENDOR_ID_DELL, .pci_subdevice = 0x01b5,
+	  .config = STAC_REF }, /* Dell Inspiron 630m */
+	{ .pci_subvendor = PCI_VENDOR_ID_DELL, .pci_subdevice = 0x01c2,
+	  .config = STAC_REF }, /* Dell Latitude D620 */
+	{ .pci_subvendor = PCI_VENDOR_ID_DELL, .pci_subdevice = 0x01cb,
+	  .config = STAC_REF }, /* Dell Latitude 120L */
 	{} /* terminator */
 }; 
 
-- 
1.4.1

---

### Post by diggity on 2006-09-04
Just a shot in the dark, but on my Ubuntu install, the microphone input was muted. To unmute it, right-click on the speaker icon on the top panel and select "open volume control". Select the Capture tab. If you see an X over the speaker icon for the microphone, click it to un-mute. Also increase the slider for input level.

HTH

---

### Post by Najand on 2006-09-04
> **diggity said:**
> Just a shot in the dark, but on my Ubuntu install, the microphone input was muted. To unmute it, right-click on the speaker icon on the top panel and select "open volume control". Select the Capture tab. If you see an X over the speaker icon for the microphone, click it to un-mute. Also increase the slider for input level.

HTH

Thank you very much for you reply.... I checked it up... Unfortunately, although It sounds alright, when checking using "alsamixer" at capture section the mic is muted and cannot be changed at all... Still I don't have any sound captured!

---

### Post by alex.vice.grab on 2006-09-12
I also am having problems with getting the microphone to work at all. I have unmuted it and increased its volume on the 'master' and have installed the Alsa mixer, but none of the things that would work for other computers seems to work for this.
Please, if you know how to get the microphone fixed, let me know. Thank you greatly in advance!
Alejandro

---

