---
title: "How do I set up dual screen with custom resolution using Nvidia X Server?"
date: 2010-02-14
forum: Multimedia Software
---

### Post by Giltrap on 2010-02-14
Hello,

I am dual booting Ubuntu and Windows XP, and on XP I have it set up to be a dual screen with a HDTV at 1200x700 (I think) and a normal monitor set at 1024x768 and I wish to have the same setup when I am using Ubuntu.

On the NVIDIA X Server driver that I installed it can give me dual screen but I cannot get the HDTV to go at 1200x700, only 1280x720, which means that some of the screen is not visible.

I have had a look here [https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution) which looks like it might be useful for adding in a custom resolution, but I haven't got a clue how to use it so I'd like some guidance as to what I should do. I don't want to cause any more problems :)

Thanks!

---

### Post by hxcobd on 2010-02-14
720p, or basic "HD," IS 1280x720... So I'm not exactly sure what the problem is.

If your TV is an LCD/PLASMA/LED HDTV, 1280x720 should be standard 720p, and should look fine.

---

### Post by Giltrap on 2010-02-14
I've never understood why sending proper HD to my TV doesn't work properly. It doesn't overscan from my PS3, so I don't know why it would from my computer.

I am using a DVI to HDMI converter cable though. That might affect it, but I doubt it. I really have no idea why it doesn't display correctly, but I know it does if I have it on this slightly smaller resolution. I've tried looking through all sorts of settings on my TV, but nothing other than the resolution does the trick.

However, I still don't know how to get said resolution on Ubuntu. Can anyone tell me how to get it?

Thanks

---

### Post by hxcobd on 2010-02-14
You haven't really explained exactly what the issue is with what the TV's displaying, so I'm really not sure how to help you.

Are you saying that in standard 720p mode, 1280 x 720, the picture is too large for the screen itself? Too small? Does it protrude off one or more sides of the screen? Is the image just off-center?

One thing I'd try is to set it on the 1280 x 720 setting and use your TV's "auto" setting a few times. Sometimes this can set things straight really quickly.

---

### Post by Giltrap on 2010-02-15
My problem, to use an analogy, is that it looks like I'm trying to fit a 15x15 photo into a 10x10 photo frame. That is, there's a significant amount of my screen missing around the edges when I am in 720p. The top and bottom panels are completely gone off the edges of the screen, and so are both the left and right sides.

On Windows it does the same if I have it in proper 720p, but the drivers on there allow me to change it to a custom resolution which does fit and allows me to see the entire screen.

I'm pretty sure it's something to do with how the graphics card is handling the output, as when I put the TV into 4:3 mode I still don't get any of the screen back even though the image is displayed as a square in the centre of the TV.

Here's a similar explanation of what is happening. It's more or less what my desktop looked like on Windows before I fixed it on there. I simply need to do the same on Ubuntu. [http://jakebillo.com/11-pixel-mapping-and-full-720p-on-the-sony-kf42e200a-tv/](http://jakebillo.com/11-pixel-mapping-and-full-720p-on-the-sony-kf42e200a-tv/) (I've not got the same TV as they do, but the same thing is happening)

---

### Post by hxcobd on 2010-02-15
Ahh, that makes more sense.

I actually believe I had a similar issue back when I owned a 27" iLo (Walmart brand) HDTV.

I don't recall ever finding a proper solution, to be honest. I was simply using VGA though, no DVI or DVI adapters of any sort.

Either the "Auto" option in the TV's menus solved my problem, or I ended up going one resolution "notch" DOWN, and then using the TV's "Auto" to get it to stretch it to fill the screen properly.

Obviously neither solution is prime, and it'd be nice if it just worked out of the box, but... Technology.

I strongly recommend getting crazy with the "Auto" option, and possibly the TV's configuration (vertical and horizontal offsets, etc.) before messing with any xorg.conf editing, as it's almost entirely the TV's issue, not your video card.

---

### Post by Giltrap on 2010-02-27
I tried to solve the problem using the TV when I first tried to fix it on Windows, and even after going into all the secret menus the only thing that improved was the likelihood I'd be involuntarily committed to a Psychiatric hospital. Changing the resolution was the only thing that fixed the problem, so doing the same will fix it on Linux too.

However, I haven't got any idea how to do that. I've had a go at changing the xorg.conf but after following several different guides on how to do it, none of them added a new resolution for me to use.

How do I add a new resolution to select in the Nvidia XServer thing, or do I have to configure my resolution by other means to get it to use the one I want specifically? (and if so, how do I do that?)

---

