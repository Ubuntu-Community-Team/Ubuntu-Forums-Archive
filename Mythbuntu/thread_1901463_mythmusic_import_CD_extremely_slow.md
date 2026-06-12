---
title: "mythmusic import CD extremely slow"
date: 2011-12-28
forum: Mythbuntu
---

### Post by Galen Seitz on 2011-12-28
I have mythbuntu 11.10 installed on a Sandy Bridge i3 system, as well as a Zotac ION Atom system.  The Atom system is a remote FE, and the i3 is the master BE.  Sometimes I run a FE on the i3.  The problem I'm having relates to ripping CDs on the combined BE/FE of the i3.  When I use the mythmusic Import CD feature on the i3 FE, the import is very, very slow.  Here are some numbers.  Note that these are all done with the same CD, with Paranoia set to Full, and quality set to Perfect(aka Flac).

Atom Remote FE.  Writes to disk on i3 BE via NFS mount.
      Complete mythmusic Import CD takes ~10 minutes.

i3 BE/FE.  Writes to local disk.
   CLI rip with 'cdparanoia -B' takes ~7 minutes.
   CLI encode with 'flac *.wav' takes ~45 seconds.
   **mythmusic Import CD is only 25% complete after 50 minutes.**

Any ideas what might be wrong?

As a side note, neither the Atom FE nor the i3 FE ejects the CD after the import completes, despite eject being set in the ripper settings.

thanks,
galen

---

