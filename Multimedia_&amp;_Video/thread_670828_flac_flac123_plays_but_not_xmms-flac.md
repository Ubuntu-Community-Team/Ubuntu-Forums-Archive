---
title: "flac: flac123 plays but not xmms-flac"
date: 2008-01-17
forum: Multimedia &amp; Video
---

### Post by nc_jed on 2008-01-17
I play flac files at least once a day but recently I lost the ability to play flac files in XMMS.  Curiously, flac123 plays the files fine, but not xmms (via xmms-flac).  I have searched for 'flac' in Synaptic and reinstalled everything to no avail.

I am on Feisty.

Blake

---

### Post by nc_jed on 2008-01-20
bump.

---

### Post by JockVSJock on 2008-01-27
Having the same issue.  

Have used apt-get to install flac from XMMS and when trying to play flac files with XMMs, nothing.

---

### Post by JockVSJock on 2008-01-27
I found this in the forum: 

> 

Well guess downgrading was'nt that difficult after all... In synaptic, search for "flac" and locate libflac7, to downgrade from 2.1 to 2, click package in the to menu, and go to force version, now select the previous version... do the same for xmms-flac.... my xmms now plays flac files again



Did this and it fixed XMMS, will just have to manage these two when getting updates...

---

