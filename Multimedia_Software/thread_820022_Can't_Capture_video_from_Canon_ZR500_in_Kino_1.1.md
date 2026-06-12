---
title: "Can't Capture video from Canon ZR500 in Kino 1.1"
date: 2008-06-05
forum: Multimedia Software
---

### Post by SgtPepper91179 on 2008-06-05
I have a Canon Mini DV camcorder and I'm trying to capture the video for editing in Kino.  When I have the camcorder on in standby Kino begins not responding.  If I hit play on the camcorder, Kino resumes and recognizes my camcorder.  If I try to use the AV/C controls or I stop the camcorder, Kino freezes up again.  If I turn off the camcorder or disconnect it Kino resumes.  If I leave it play and try to capture the video, Kino just counts down looking for DV and then says Capture Failed.

I have the raw1394 module loaded and permissions look fine.  I'm running Ubuntu 8.04 with a Rosewill RC-502 PCI Firewire card.

Any insight anyone can give would be greatly appreciated.

---

### Post by xc3RnbFO8P on 2008-06-06
Look at this:
[http://ubuntuforums.org/showpost.php?p=4649034&postcount=4]("http://ubuntuforums.org/showpost.php?p=4649034&postcount=4")

---

### Post by SgtPepper91179 on 2008-06-06
ok I tried that, and it's still acting the same.  What I am seeing is when I go to change the permissions the only one that changes is raw1394.  dv1394 and video1394 both show as crw-rw----  ohci1394 isn't even listed in the dev folder eventhough I gave it the modprobe command.

Another thing which I'm not sure if it matters, but when I'm looking at the details for the modules raw1394 has /dev/raw1394 at the end of its line while dv1394 and video1394 show a 0 at the end.

Thanks for the help Ringi.  I feel like I'm getting closer, but I'm not quite there yet.

---

### Post by DuncanNZ on 2009-02-23
Hi there, since you're having trouble with capture over Firewire to Kino you might want to look at my recent update of the [https://help.ubuntu.com/community/Firewire](https://help.ubuntu.com/community/Firewire) page. Please let me know if there are any problems with that guide.

---

