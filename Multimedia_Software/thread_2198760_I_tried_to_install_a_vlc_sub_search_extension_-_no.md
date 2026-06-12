---
title: "I tried to install a vlc sub search extension - now the player doesn't function."
date: 2014-01-10
forum: Multimedia Software
---

### Post by still_learning_to_ on 2014-01-10
According to these instructions:

[http://www.webupd8.org/2012/02/vlsub-vlc-extension-to-search-and.html](http://www.webupd8.org/2012/02/vlsub-vlc-extension-to-search-and.html)

What might have happened, any idea? Is it possible to get this feature work or what to do, re-install vlc player?

Thank you!

---

### Post by oldos2er on 2014-01-10
Assuming you ran the necessary commands and they completed without any errors, starting vlc from a terminal might offer some clues. Ctrl-Alt-t, then ```
vlc
```

---

### Post by mc4man on 2014-01-10
As per above post if vlc fails to start due to trying to open on an improper or an supported interface then  try starting as such
```
vlc -Iqt4
```
Generally speaking removing, re-installing vlc would have no effect as your issue(s) are likely from local changes. In those cases you could locate & remove vlcrc file, usually found in ~/.config/vlc 
(or just remove ~/.config/vlc folder itself

---

### Post by still_learning_to_ on 2014-01-10
Thank you, yes I thought I did. Now the program started and plays well again. :) And I see **VLSub 0.9.10 under the VLC View menu**, but it doesn't open up any search window.

This is what showed up in terminal:

VLC media player 2.1.1 Rincewind (revision 2.1.0-207-g89c9520)
[0x1174058] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
Fontconfig warning: FcPattern object size does not accept value "0"
Fontconfig warning: FcPattern object size does not accept value "0"
[0x7feb90001248] xcb_xv vout display error: no available XVideo adaptor
Fontconfig warning: FcPattern object size does not accept value "0"
Fontconfig warning: FcPattern object size does not accept value "0"
[0x7feb90001248] main vout display error: Failed to resize display
[0x7febdc2db968] lua generic error: Could not activate extension!

What could I do to activate the extension, anyone?

---

### Post by still_learning_to_ on 2014-01-10
I used the* vlc -Iqt4 *command, the program started well and played the video but again, no search window opened.

and this is what showed in terminal:

VLC media player 2.1.1 Rincewind (revision 2.1.0-207-g89c9520)
Fontconfig warning: FcPattern object size does not accept value "0"
Fontconfig warning: FcPattern object size does not accept value "0"
[0x7f4a1c001248] xcb_xv vout display error: no available XVideo adaptor
Fontconfig warning: FcPattern object size does not accept value "0"
Fontconfig warning: FcPattern object size does not accept value "0"
[0x7f4a1c001248] main vout display error: Failed to resize display
[0x7f4a682db5f8] lua generic error: Could not activate extension!
[h264 @ 0x7f4a328d4a60] mmco: unref short failure
[h264 @ 0x7f4a3292a680] mmco: unref short failure
[0x7f4a32864668] avcodec decoder error: more than 5 seconds of late video -> dropping frame (computer too slow ?)
[0x7f4a682db5f8] lua generic error: Could not activate extension!
[0x7f4a1c001248] main vout display error: Failed to resize display

Is it possible to fix this problem with the extension? 
Thank you!

---

### Post by oldos2er on 2014-01-11
Apparently vlsub needs to be updated to work with vlc 2.1.1, see [https://github.com/exebetche/vlsub/issues/28](https://github.com/exebetche/vlsub/issues/28)

---

### Post by still_learning_to_ on 2014-01-13
Thank you, I understood from the link you provided that I should maybe uninstall the vlc player (which wasn't working but kept freezing) and install the 2.0.8 version which still supports the vlsub extension. I found this page:
[http://www.oldapps.com/linux/vlc_player.php?system=ubuntu](http://www.oldapps.com/linux/vlc_player.php?system=ubuntu) 
and downloaded the file, extracted it from the tar.xz file into a file named vlc-2.0.8 but now I don't know what to do with it. How to install it? And should I somehow uninstall the vlsub extension before installing it again after getting this other version of vlc player installed?

---

### Post by still_learning_to_ on 2014-01-13
Okay, I gave up on the idea of the vlsub extension. I just had a looong session with a more experienced friend, trying to install the older vlc version but 

now I just want to find out how to uninstall the vlsub extension 

because it's still haunting me in the "View" dropdown list of the newly installed newest version of vlc player. Which still doesn't function, pausing before it even started to play anything. 

So if anyone can help me with how to just remove the extension installed following these instructions: [http://www.webupd8.org/2012/02/vlsub...earch-and.html]("http://www.webupd8.org/2012/02/vlsub-vlc-extension-to-search-and.html") I'll fully appreciate!!
Thank you!

---

