---
title: "Unity vs Gnome3 - Memory usage"
date: 2011-03-30
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by bluenova on 2011-03-30
Has anybody used both Unity and Gnome3 long enough to compare memory usage? I guess this is more of a Compiz vs Mutter thread but I think for me memory usage will probably be a major factor into which one I end up using come release day.

At the moment my desktop machine is running Unity and has 2 Chromium sessions open and Conky, that's it and it's using in total 1.07G of RAM, that seems quite a lot to me. I've yet to have a proper play with Gnome3 but if anyone who has want's to chime in...

---

### Post by macstevejb on 2011-03-30
Are you running an nVidia grahics card and have the proprietary driver installed?

If so, there is a problem with high Ram utilsisation when using Ubuntu 11.04,as highlighted in the following Bug #725434:

[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/725434](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/725434)

There should be a fix soon

regards,

---

### Post by bluenova on 2011-03-30
> **macstevejb said:**
> Are you running an nVidia grahics card and have the proprietary driver installed?

If so, there is a problem with high Ram utilsisation when using Ubuntu 11.04,as highlighted in the following Bug #725434:

[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/725434](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/725434)

There should be a fix soon

regards,

Yes and yes, thanks for pointing that out to me.

---

### Post by 3Miro on 2011-03-30
If you want small memory footprint, use XFCE. I don't think Gnome-shell and Unity would be anywhere near "low on resources". On the same note, I don't think comparison is fair at this point, both pieces of software will undergo more changes before release.

---

### Post by macstevejb on 2011-03-30
3Miro:

I had the same idea as you and installed Xubuntu 11.04 alpha 2.

However, the memøry problem occurs as soon as you install the nvidia proprietary driver no matter what window manager you use in 11.04.

So it's not specifically down to gnome or unity or xfce or whatever flavour window manager you choose.

regards,

---

### Post by bluenova on 2011-03-30
> **3Miro said:**
> If you want small memory footprint, use XFCE. I don't think Gnome-shell and Unity would be anywhere near "low on resources". On the same note, I don't think comparison is fair at this point, both pieces of software will undergo more changes before release.

No not after small, just a comparison between Unity and Gnome3. I don't think there is any harm in comparing now and as changes are made.

---

### Post by jerrylamos on 2011-03-30
Memory usage?

I'll bet Natty Unity 2D will roundly beat them both - I have no data, just the nice crisp feel.

Also Lubuntu will likely to be better yet.  They're preparing Natty Beta Lubuntu now.

Many people crave "eye candy" like Unity 3D which I'll bet will ALWAYS use lots of memory and processor cycles.  These people will have the latest fastest most memory anyway and are getting what they wanted.

By the way, this is a $248 Acer Aspire one netbook with 1 GB memory 250 GB hard drive running Unity 3D just fine...if that's what you prefer.

Jerry

---

### Post by macstevejb on 2011-03-30
> **jerrylamos said:**
> Memory usage?

I'll bet Natty Unity 2D will roundly beat them both - I have no data, just the nice crisp feel.

Also Lubuntu will likely to be better yet.  They're preparing Natty Beta Lubuntu now.

Many people crave "eye candy" like Unity 3D which I'll bet will ALWAYS use lots of memory and processor cycles.  These people will have the latest fastest most memory anyway and are getting what they wanted.

By the way, this is a $248 Acer Aspire one netbook with 1 GB memory 250 GB hard drive running Unity 3D just fine...if that's what you prefer.

Jerry


You miss my point in this thread.

It's all to do with anyone that uses nVidia graphics with the proprietary driver and NOT window manager...2D unity, 3D Unity, classic Gnome, XFCE...doesn't matter.

Until there is a fix, Ubuntu 11.04 will be a memory hog for those using nvidia graphics cards.

regards,

---

