---
title: "Channels disappeared from mixer after Lucid update"
date: 2010-05-04
forum: Multimedia Software
---

### Post by edd07 on 2010-05-04
Hello, I'm having some trouble with my audio setup.

I used to run Kubuntu 9.10 (Jaunty) and KMixer and alsamixer showed me a "Line" channel that let me control the line-in volume. After I upgraded to 10.04 (Lucid) the "Line" channel disappeared. I can still record through the line-in jack, but I can't hear what I record until I play it back. Could you help me get it back?

My card is listed as:
```
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)

```

Thanks in advance

---

### Post by edd07 on 2010-05-06
Bump

---

### Post by edd07 on 2010-05-09
Re-bump!

---

### Post by Zorael on 2010-05-09
I think that if it's gone from alsamixer, then it's been disabled in the driver. KMix allows for hiding channels, but as far as I know alsamixer should show them all.

Perhaps the driver maintainer figured the extra volume slider confused users. (Which can be a valid concern but I detest the argument.) Alternatively, perhaps Ubuntu packages it with a patch disabling it for the same reason.

You may have better luck with the Ubuntu (or kernel!) mailing lists.

---

### Post by edd07 on 2010-05-10
Thanks for your reply

> **Zorael said:**
> I think that if it's gone from alsamixer, then it's been disabled in the driver. KMix allows for hiding channels, but as far as I know alsamixer should show them all.

Yes, that's what I guessed, but wasn't sure. Do you know how I can downgrade my driver to the Jaunty version (Would that even work :-P?). I can't find the package that contains the driver by searching synaptic.

Thanks

---

