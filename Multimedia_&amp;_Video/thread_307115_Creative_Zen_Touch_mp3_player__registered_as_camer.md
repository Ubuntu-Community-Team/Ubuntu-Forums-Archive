---
title: "Creative Zen Touch mp3 player  registered as camera"
date: 2006-11-26
forum: Multimedia &amp; Video
---

### Post by items on 2006-11-26
Hi,
after updating my Creative mp3 player with a new firmware 2.11.01 the camera isn't longer detected by Ubuntu. Just a window comes up that a new digitalcamera has been detected and that no photo has been found. Afterwards nothing more happens. Kzenexplorer as well as Gnomad2 do not find the player on the USB port but no error or anything else is shown.

Has anybody got an idea, how to solve the problem?

TIA
items

---

### Post by viciouslime on 2006-11-26
You need to look into a thing called libmtp, try this post [http://ubuntuforums.org/showthread.php?t=199250&highlight=zen+touch](http://ubuntuforums.org/showthread.php?t=199250&highlight=zen+touch)

It worked for me. Ideally you shouldn't have updated the firmware, your device is now a playsforsure device which in linux speak means doesn'tplayforsure

---

### Post by msak007 on 2006-11-26
Your firmware upgrade most likely made the Zen Touch an MTP MP3 player, which is why it can't be seen by apps such as Gnomad and KZenExplorer (which is severely outdated). I wrote a how-to on getting Creative MTP devices working using Gnomad, which is the thread that viciouslime linked to. Please try it, and if you run into any problems post in that thread for help. Good luck!

---

### Post by items on 2006-11-26
Hi all,
thanks a lot for your fast help!
I will look for the tutorial and I hope it works. I've made the upgrade, in order to make amarok work with the player but I havn't thought about that afterwards maybe nothing will go on :o|

bye
items

---

### Post by items on 2006-11-26
Hi again,
the Tutorial works great for me. Thank you.
Does anybody know if it is also possible to copy a folder with music to the player with gnomad?

bye
items

---

### Post by msak007 on 2006-11-26
Great! I'm glad you got it working without any issues. Which Method did you try, 1 or 2? Regarding your question about folders, unfortunately Gnomad does not support folders or folder transfer with MTP devices (yet). It is a known limitation (I believe with libmtp, not Gnomad itself) that I hope will eventually be resolved. I was going to try getting Amarok to working with MTP support, but haven't had the time to actually try to compile it. I believe there are a few guides already on compiling Amarok, I'll take a look at one of them and see what I can find.

---

### Post by items on 2006-11-26
Hi,
I choose the first method only compiling gnomad. Like I said: It works great and out of the box :o)
Do you know whether there is any opportunity to make it also working with kzenexploerer? That would be nice, because, IIRC, copying folders is possible here.

bye
items

---

### Post by msak007 on 2006-11-26
> **items said:**
> Hi,
I choose the first method only compiling gnomad. Like I said: It works great and out of the box :o)
Do you know whether there is any opportunity to make it also working with kzenexploerer? That would be nice, because, IIRC, copying folders is possible here.

bye
items
As far as I know, Gnomad also supports folder transfer. However, the limitation is with libmtp as it is fairly new. KZenExplorer is severely outdated (last updated was 1 1/2 years ago), and there is no way to enable MTP support using it. Even if you did get it to work with libmtp, as I already said it's a limitation with libmtp and MTP devices. I too would rather use that as it is a KDE app, but Gnomad does the job. I'm sure it'll eventually get resolved, but for now you have to transfer individual songs instead of folders. At least it's working and you don't have to dual boot for it, right :)?

---

