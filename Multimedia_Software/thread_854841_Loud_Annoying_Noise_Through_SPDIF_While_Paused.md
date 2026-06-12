---
title: "Loud Annoying Noise Through S/PDIF While Paused"
date: 2008-07-09
forum: Multimedia Software
---

### Post by tammer on 2008-07-09
I'd like to begin by thanking the Ubuntu community for being so knowledgeable and for supporting the open source initiative. I've found a *lot* of answers using this forum!

So this problem is the last thing standing between me and a perfect DVD server... I greatly appreciate any help!

I'm running Ubuntu Hardy, with kernel 2.6.24. My hardware is i686 based, and my sound card  is a Turtle Beach Santa Cruz, which uses the Cirrus Logic CS4624 chip. I'm playing DVD disc images in .iso format from the local hard drive with XBMC's internal DVD player, and I've tested ac3 files with mplayer and the exact same bug occurs.

I configured ALSA to unmute my iec958 device (a headphone jack converted to RCA, connected to coax port on my receiver), and it passes 5.1 audio perfectly. I was rather enthused, until I pressed the pause button.

Immediately upon pausing playback, my system starts sending a 48khz PCM stream (at least, according to my receiver). Instead of silence, it's an extremely loud, fast clicking.

Has anyone ever had an audio bug that only occurs when something is paused? Once I press play on whatever software I'm testing, the sound resumes with perfect clarity. If I close the software, my system stops sending a signal to the receiver and there's silence.

Thanks again for your help!

---

### Post by tammer on 2008-07-10
So I've been doing some research, and apparently other people have had this problem, just with different sound cards. On this forum ([http://www.nabble.com/looping-S-PDIF-data-td17573493.html](http://www.nabble.com/looping-S-PDIF-data-td17573493.html)), someone posted a patch to stop output during pause. This is precisely my problem, however I don't know exactly how to apply this patch, or if it's only specific to a particular sound card. 

Apparently ALSA is looping the cache over and over during pause, rather than stopping the output. Any help is greatly appreciated!

---

### Post by cariboo on 2008-07-10
The patch you looked at is only for the Trident sound card. Have you had a look here:

[http://www.alsa-project.org/main/index.php/Matrix:Module-cs46xx](http://www.alsa-project.org/main/index.php/Matrix:Module-cs46xx)

Jim

---

### Post by tammer on 2008-07-10
Thanks for the link, it's got some very detailed information about setting up the card. The only thing is, my card is set up and works perfectly except for this bug. (Which seems like a pretty rare bug, at least according to the number of valuable hits I've found on google.)

I'm aware that the patch is for Trident-based cards, however it remains that the patch does exactly what I need. I'll reproduce it below, and if anybody knows how to alter this patch so it will work with the cs46xx driver, I'll be eternally grateful!

```
diff --git a/sound/pci/trident/trident_main.c b/sound/pci/trident/trident_main.c
index bbcee2c..a69b420 100644
--- a/sound/pci/trident/trident_main.c
+++ b/sound/pci/trident/trident_main.c
@@ -1590,7 +1590,10 @@ static int snd_trident_trigger(struct snd_pcm_substream *substream,
        if (spdif_flag) {
                if (trident->device != TRIDENT_DEVICE_ID_SI7018) {
                        outl(trident->spdif_pcm_bits, TRID_REG(trident, NX_SPCSTATUS));
-                       outb(trident->spdif_pcm_ctrl, TRID_REG(trident, NX_SPCTRL_SPCSO + 3));
+                       val = trident->spdif_pcm_ctrl;
+                       if (!go)
+                               val &= ~(0x28);
+                       outb(val, TRID_REG(trident, NX_SPCTRL_SPCSO + 3));
                } else {
                        outl(trident->spdif_pcm_bits, TRID_REG(trident, SI_SPDIF_CS));
                        val = inl(TRID_REG(trident, SI_SERIAL_INTF_CTRL)) | SPDIF_EN;

```

---

### Post by tammer on 2008-07-14
I just tested the system using a LiveCD, and can confirm that the issue is reproduceable. Anyone have any ideas?

---

