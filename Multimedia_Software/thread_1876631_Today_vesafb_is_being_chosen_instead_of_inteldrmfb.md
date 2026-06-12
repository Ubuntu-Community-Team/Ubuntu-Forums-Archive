---
title: "Today vesafb is being chosen instead of inteldrmfb"
date: 2011-11-06
forum: Multimedia Software
---

### Post by psycotica0 on 2011-11-06
I have a media-centre I set up for my family that they're using to watch movies and TV shows.

It's running 11.10 and has been since that was released.

Yesterday it worked fine and I didn't change anything (honest) but today when it turned on I got Unity 2D instead of normal Unity, and XBMC (which makes heavy use of GL) was unusably slow.

So, eventually I tracked it down to a difference in dmesg between yesterday and today where yesterday (and before that) it used inteldrmfb as the framebuffer, and today it decided vesafb was a more suitable choice.
I didn't change any settings between today and yesterday, and I didn't upgrade anything.
I upgraded today after it wasn't working to see if any updates would fix it but they didn't.

I've restarted multiple times today and it's still picking vesa.

Now, this might not have anything to do with it, but it seems somewhat fishy that last night (while the computer was off) my region changed from Daylights Savings Time to Standard Time.
Maybe it has nothing to do with it, but I'll mention it.

I'm intending to attach /var/log/dmesg.3.gz and dmesg.4.gz where 4 has inteldrmfb and 3 has vesa.
I'm almost positive there's nothing risky to post in the dmesg logs... but if I'm wrong if someone could let me know rather than exploit me, that'd be awesome.

Any help would be appreciated.

PS: I tried uploading the log files unzipped but it complained about invalid file type, so I added a .txt on to them and it complained about my logs being too big, so I've uploaded them zipped.
Sorry for any inconvenience. I tried.

---

