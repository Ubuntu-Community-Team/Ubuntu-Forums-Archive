---
title: "Errors with gnome-sound-recorder"
date: 2010-10-11
forum: Multimedia Software
---

### Post by jmblock2 on 2010-10-11
Hey everyone,

Just upgraded to 10.10 and enjoyed the improved visuals the first day. I didn't think I had any issues until this morning. When I try and launch Sound Recorder I get the message:
"Your audio capture settings are invalid. Please correct them with the "Sound Preferences" under the System Preferences menu."

I go there, everything looks great. Next I try launching it from the terminal and I get the error message:
"(gnome-sound-recorder:2473): Gtk-WARNING **: Attempting to read the recently used resources file at `/home/jacob/.recently-used.xbel', but the parser failed: Error reading file '/home/jacob/.recently-used.xbel': Is a directory."

.recently-used.xbel is empty, so I try it with sudo and get the error:
"(gnome-sound-recorder:2755): GStreamer-CRITICAL **: gst_implements_interface_cast: assertion `gst_element_implements_interface (GST_ELEMENT (from), iface_type)' failed"

Except now the app shows up and seems to function correctly. I can record and playback just fine. Next I went onto Skype and ran some of their tests and it seems like all the hardware and drivers are working fine. I could record/playback with no problems.

So any thoughts on  why gnome-sound-recorder is giving the errors? I don't know many commands to trace errors past just terminal messages. Thanks,

Jacob

P.S. I was also getting an error message on bootup of: "modprobe: FATAL: could not load /lib/modules/2.6.35-22-generic/modules.dep: no such file or directory" But after following the steps on [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/642421]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/642421") it went away. Fixing it doesn't seem to have changed any of the error messages.

---

### Post by Yellow Pasque on 2010-10-11
Try deleting .recently-used.xbel

---

### Post by jmblock2 on 2010-10-11
Thanks for the suggestion, but that didn't work. I deleted the folder and a few files with similar names and rebooted.

---

