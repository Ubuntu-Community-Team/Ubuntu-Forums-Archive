---
title: "wavesurfer + libsnack-alsa"
date: 2011-03-14
forum: Multimedia Software
---

### Post by ben61 on 2011-03-14
The wavesurfer (audio/speech research) application is broken in 10.10 (both 32-bit & 64-bit) because it depends on the libsnack (Tcl audio) OSS-based library and OSS support has been removed from 10.10. wavesurfer fails looking for /dev/mixer

There's a new libsnack-alsa package in the repositories, but wavesurfer still depends on the OSS libsnack, so it's of no use.

A google search for "wavesurfer libsnack-alsa" shows someone talking about fixing the package dependencies (i.e have wavesurfer depend on libsnack-alsa, not libsnack), but as of today it's still broken.

Does anyone know the status of this fix, or if there's any workaround to get wavesurfer working in Ubuntu 10.10 ?

Thanks,
Ben

---

