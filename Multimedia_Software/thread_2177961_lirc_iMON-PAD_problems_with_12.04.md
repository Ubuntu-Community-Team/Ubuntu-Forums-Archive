---
title: "lirc iMON-PAD problems with 12.04"
date: 2013-10-01
forum: Multimedia Software
---

### Post by lindend on 2013-10-01
Running 12.04 LTS and my system uses the iMON-PAD.  When running XBMC, the cursor keys (up, down, left, right, select etc) trick keys (play, pause, stop) work, but none of the other keys are working.

After enabling XBMC debug, XBMC reports that these keys are coming from the keyboard and not the remote.

As far as I can tell, lirc is correctly configured and completely functional.  The lircd.conf points to the imon device
```

#Configuration for the Soundgraph iMON PAD IR/VFD remote:
include "/usr/share/lirc/remotes/imon/lircd.conf.imon-pad"
```

I have a properly configured Lircmap.xml in my userdata directory and even tried a keymap file in the userdata/keymaps.  The keymap file revealed that all remote keys that xbmc is processing are coming from the keyboard not the remote.

Finally, tried gedit and the cursor keys on the remote manipulate the cursor in the editor.

Seems like something is mapping the remote to the keyboard prior to lirc getting involved.  Any ideas where I can start looking?

---

### Post by lindend on 2013-10-01
Was able to get the remote working via the linux-input-layer described in this HOW-TO guide in the XBMC forums.  Turns out this is expected behavior with newer kernels.

[http://forum.xbmc.org/showthread.php?tid=145488](http://forum.xbmc.org/showthread.php?tid=145488)

---

