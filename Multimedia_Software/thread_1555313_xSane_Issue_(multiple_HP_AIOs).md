---
title: "xSane Issue (multiple HP AIOs)"
date: 2010-08-17
forum: Multimedia Software
---

### Post by orethrius on 2010-08-17
Okay, so here's the issue I'm having.  My current location has both OfficeJet 8500 and a PhotoSmart C6100 series AIOs.  Both of these systems work just fine for printing purposes.  However, when I wish to *scan* something, xSane defaults to the OfficeJet 8500.  It's not an issue of detection as such; I can directly access the PhotoSmart via **xsane hpaio:/net/Photosmart_C6100_series?ip=MYIPHERE**.

I suppose my question is whether there's some sort of dialog or setting that I'm missing here, or if I'm relegated to the CLI for inherently graphical scanning tasks (which seems a bit daft, despite my love of the CLI).

Please help (or point me to a thread with suggestions that work with the C6100 on Lucid).

UPDATE 1: Could be an installation issue.  The help docs (F2, F3) don't work at all.
UPDATE 2: This appears to be an issue with how /etc/sane.d/hp.conf is handled, perhaps **hpaio** only accepts the first device found? :(
UPDATE 3: Well now, this is confusing.  Experimenting with the **hplip** snippet in /etc/sane.d/dll.d and dll.conf in /etc/sane.d did nothing.  The OfficeJet is still the default scanner.
WORKAROUND: Re-linked the Main Menu xSane item to the command-line parameter above.  Still looking for an actual, elegant fix.
UPDATE 4: "Error during CMS conversion: Could not open scanner ICM profile:"  Now I've lost Contrast/Brightness/Gamma settings.  Reinstalling xsane did nothing; not even purging and reinstalling worked. (fixed by unchecking "Enable color management" under the Preferences menu)

---

