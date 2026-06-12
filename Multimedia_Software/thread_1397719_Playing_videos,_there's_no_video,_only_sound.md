---
title: "Playing videos, there's no video, only sound"
date: 2010-02-03
forum: Multimedia Software
---

### Post by Eoghanalbar on 2010-02-03
This is true for .flv, .avi, .mov, and .mp4, at least.
This is true in both vlc and movie player.
Thumbnails generated from frames in the videos appear correctly in nautilus.
Videos play fine in firefox, on youtube, but I downloaded one as an .flv and then it had the same problem.
I have restricted extras freshly installed. My "Ubuntu 9.10 - *the Karmic Koala*" system is fully updated.
I've found several other forum posts about the same kind of problem, but I couldn't find anything helpful in them (like that the contrast setting might be WAY out of whack, which it wasn't, or that nvidia drivers needed to be updated or reinstalled, which I don't have anyway, etc).
So, if anyone has any ideas what I should try next, I'd be much obliged!

Thanks!
Owen

---

### Post by ajgreeny on 2010-02-03
Are you sure you have all the codecs needed for all those different file types?  I suggest you enable the [medibuntu]("http://www.medibuntu.org/") repos, if you have not already done so and install the w32codecs (or w64... if that is your system) plus libdvdcss2, and also make sure you have all the gstreamer plugins, good, bad and ugly.

---

### Post by Eoghanalbar on 2010-02-03
Oh! I thought the restricted extras thing took care of ALL the codecs and things that can't come preinstalled for legal headache reasons. Thanks for demisinformizing me. ^^

Well anyway, I followed all the instructions on that site you so helpfully linked me to. That is, used the bash commands they gave to add the repository, and then installed the w32codecs (yeah that's my system) and libdvdcss2.

Problem was still there. Checked in synaptic and yes, the codecs WERE marked as installed, as were all the gstreamer plugins. I restarted (because that's one thing I do when I have no idea what else to try), but the problem's still there.

So... anything else I could I try next?

PS At least those .wma files I've got kicking around work now! And I hadn't even gotten around to thinking about fixing THAT problem yet. :P

---

