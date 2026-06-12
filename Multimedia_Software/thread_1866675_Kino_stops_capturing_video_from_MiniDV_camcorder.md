---
title: "Kino stops capturing video from MiniDV camcorder"
date: 2011-10-21
forum: Multimedia Software
---

### Post by tomdkat on 2011-10-21
I'm running Ubuntu 11.10 (64-bit) and I'm using Kino to capture video from my JVC GR-D850U camcorder.  I can use Kino to control the camera just fine and I can capture some video ok.  For some reason, at random points, the video preview in kino stops updating and the imported frame count stops incrementing.  I can click the stop button and the camera stops playing back the video but I have to exit and restart Kino to get it to start capturing again.

I've got about 2 hours of video I need to transfer to my computer from my camcorder and I can't seem to get through 5 mins of importing. :(

I'm having Kino write the video to a SATA hard drive with 50GB or so of free space.

Any ideas?

Thanks!

Peace...

---

### Post by FakeOutdoorsman on 2011-10-22
I'm not sure what the issue is. I generally use dvgrab, which I think is also used by Kino, but using it directly might give better results. Example:
```
dvgrab -rewind -s 0 output.dv
```

---

### Post by tomdkat on 2011-10-22
I'll give that a try.  Thanks!

Peace...

---

### Post by tomdkat on 2011-10-22
> **FakeOutdoorsman said:**
> I'm not sure what the issue is. I generally use dvgrab, which I think is also used by Kino, but using it directly might give better results. Example:
```
dvgrab -rewind -s 0 output.dv
```

This appears to be working well!  Thanks!

Peace...

---

