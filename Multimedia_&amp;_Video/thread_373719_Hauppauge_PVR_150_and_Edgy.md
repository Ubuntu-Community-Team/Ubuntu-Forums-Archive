---
title: "Hauppauge PVR 150 and Edgy"
date: 2007-03-01
forum: Multimedia &amp; Video
---

### Post by klohmann on 2007-03-01
I have a question about capturing video.  I have installed the PVR 150 on Edgy, and after much tweaking, I have output from the cat /dev/video0 > /tmp/test_capture.mpg, but there is no audio (probably by design).

I've tried several other packages to try and capture analog source, and although they can see the card, nothing will run (kino only does firewire, cinerella gives an error, dxtv will not run (although it doesn't give any errors) and DVR-qtgui recognizes the card, but when I choose it, the program exits.

I'm guessing that this is a hardware issue.  I'd be happy to capture from the command line (as above) if someone would just tell me how I would be able to capture audio as well as video.

Thanks very much for any assistance.  Keith.

---

### Post by rsambuca on 2007-03-01
Try just viewing the output in VLC.

Once you have VLC installed (it is in the add/remove programs), just click on File -> open Capture Device -> PVR

Mine seemed to work from the get-go using the IVTV firmware and drivers.  If you want to, VLC can also be used to capture the audio/video and transcode it into many different formats.

You can change the channel with this code:```
ivtv-tune -c#
```
Where the # is the channel you want.

Edit:  I am sure you will be happy to hear that in the upcoming Feisty version 7.04, the IVTV will be integrated into the new kernel, so we won't have to do all of this fiddling around!

---

