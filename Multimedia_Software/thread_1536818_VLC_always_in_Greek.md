---
title: "VLC always in Greek"
date: 2010-07-22
forum: Multimedia Software
---

### Post by matty_muso on 2010-07-22
Hi there, just upgraded to ubuntu 10.04 on a Dell Latitude D810 and VLC is displaying all characters in Greek. Lucky for me I can read Greek phonetically however it's frustrating because I can read English much quicker. It's not actually in Greek, just using Greek characters to represent all the English sounds. I don't have Greek installed in System-Admin-Language Support. I also have tried uninstalling VLC completely and reinstalling via Synaptic Package Manager. I even tried editing the command to launch VLC to the following:
env LANGUAGE=en vlc %U
All to no avail. Someone please help me! I love VLC and don't want to change.

---

### Post by gizmobay on 2010-07-23
Maybe try renaming /home/username/.vlc to /home/username/.backup_vlc and then restart vlc. If that doesn't work, you could rename it back. Probably a setting in /home/username/.vlc/vlcrc is causing your issue.

---

### Post by bigd73 on 2010-07-23
Hi, I too have this same problem. VLC displays all text in English in Ubuntu 9.10 Its only when I upgraded to 10.04  that the problem appeared.  When you suggest renaming /home/username/.vlc this path does not exist in 10.04. Did you mean the directory /home/username/.configure/vlc?
Also in ~/.vlc/vlcrc most lines are hashed out and I can find no reference to any language settings.
Got any other ideas :-)
Thanks and regards
bigd73

---

### Post by bigd73 on 2010-07-27
Hello everyone, I found from another forum that if I change the fonts in System->preference->appearance->fonts from standard to (say) comic sans all is well.
This worked and VCL is now displayed in English.
Thanks to all for your time and replies.

---

### Post by matty_muso on 2010-07-29
This worked for me thanks! I had the font set to Symbol. In preview, it uses the roman alphabet but greek characters in symbol. This is why it was English words using greek letter representation instead of actually being in Greek. Cool...

---

