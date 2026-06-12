---
title: "Problem restoring sound after installing modem driver"
date: 2008-06-29
forum: Multimedia Software
---

### Post by lesliek on 2008-06-29
I followed the steps mentioned here: [http://www.ubuntu1501.com/2008/06/getting-modem-to-work-in-hardy.html](http://www.ubuntu1501.com/2008/06/getting-modem-to-work-in-hardy.html)

The point was to get my dial-up modem working as a fallback if I couldn't get Ethernet or wireless Internet access. (That has happened to me in a few places.)

I got the error mentioned in the document but rebooting didn't fix the problem.

Since the document referred to the unloading of the snd-hda-intel module, I tried to reload that module, but got this result:

WARNING: Error inserting snd_hda_codec (/lib/modules/2.6.24-16-generic/updates/snd-hda-codec.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting snd_hda_intel (/lib/modules/2.6.24-16-generic/updates/snd-hda-intel.ko): Unknown symbol in module, or unknown parameter (see dmesg)

The relevant bit of the dmesg output says:

[ 2307.309883] snd_hda_codec: Unknown symbol snd_ctl_elem_read
[ 2307.310018] snd_hda_codec: Unknown symbol snd_ctl_elem_write
[ 2307.313681] snd_hda_intel: Unknown symbol snd_hda_bus_new
[ 2307.313954] snd_hda_intel: Unknown symbol snd_hda_build_pcms
[ 2307.314100] snd_hda_intel: Unknown symbol snd_hda_codec_new
[ 2307.314385] snd_hda_intel: Unknown symbol snd_hda_queue_unsol_event
[ 2307.314970] snd_hda_intel: Unknown symbol snd_hda_calc_stream_format
[ 2307.315225] snd_hda_intel: Unknown symbol snd_hda_suspend
[ 2307.315473] snd_hda_intel: Unknown symbol snd_hda_codec_remove_notify_all
[ 2307.315763] snd_hda_intel: Unknown symbol snd_hda_resume
[ 2307.315985] snd_hda_intel: Unknown symbol snd_hda_build_controls
[ 6703.225236] snd_hda_codec: Unknown symbol snd_ctl_elem_read
[ 6703.225371] snd_hda_codec: Unknown symbol snd_ctl_elem_write
[ 6703.231048] snd_hda_intel: Unknown symbol snd_hda_bus_new
[ 6703.231328] snd_hda_intel: Unknown symbol snd_hda_build_pcms
[ 6703.231475] snd_hda_intel: Unknown symbol snd_hda_codec_new
[ 6703.231759] snd_hda_intel: Unknown symbol snd_hda_queue_unsol_event
[ 6703.232375] snd_hda_intel: Unknown symbol snd_hda_calc_stream_format
[ 6703.232630] snd_hda_intel: Unknown symbol snd_hda_suspend
[ 6703.232878] snd_hda_intel: Unknown symbol snd_hda_codec_remove_notify_all
[ 6703.233169] snd_hda_intel: Unknown symbol snd_hda_resume
[ 6703.233390] snd_hda_intel: Unknown symbol snd_hda_build_controls

Can anyone tell me how to get the sound back?

Thanks for reading this,

Leslie

---

