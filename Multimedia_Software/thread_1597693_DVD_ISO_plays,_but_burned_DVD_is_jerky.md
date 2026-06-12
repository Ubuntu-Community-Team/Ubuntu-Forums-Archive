---
title: "DVD ISO plays, but burned DVD is jerky"
date: 2010-10-15
forum: Multimedia Software
---

### Post by qbee42 on 2010-10-15
OS: Ubuntu 10.4

I have an odd problem with a copied DVD. I started with a commercial DVD and created an ISO file. The ISO file plays perfectly with VLC. I take the ISO file and burn it to a DVD+RDL without error. The burned DVD will not properly play on my computer or DVD player. It loads, but the menu is jerky and full of video block artifacts. The menu does not function properly. I tried this more than once with different software, including going directly to the DVD. I am using a drive that worked before, with the same stack of DVD+Rs that I used before.

Here is where it gets interesting: I can take the non-working burned DVD and copy it to a new ISO file. The new ISO file works fine with VLC. Obviously the data is getting properly copied from the source DVD, and it must be good on the burned DVD, but it won't play properly.

Does any of this ring a bell with anyone?

Thanks,
Tom

---

### Post by endotherm on 2010-10-15
well, running an iso off a hdd is much faster and consistent than through an optical drive. also optical drive firmware has some DRM built in (region codes etc) so that may be a cause of problems. no good answers, just some things to think about.

---

### Post by hooby3dfx on 2010-11-26
I am having this same issue, but its not just a Linux/Ubuntu thing. I made an ISO of a DVD with the dd command in OS X. I am going to ask on the doom9 forums. Something tells me the dd command messes up the copy protection mechanism.

---

### Post by qbee42 on 2010-11-27
I now have a work-around to this problem. As best I can tell, some of the DVDs are deliberately mis-structured to cause slow-downs during playback. The HDD is fast enough to allow smooth playback, even with the slow-downs, but not from optical media. To fix this problem, I re-encode the DVD using k9copy, using 1:1 compression. The result of this is a perfect DVD at the original size. Here is my general approach:

1) Copy DVD to ISO image using any disk burning software.

2) If errors occur during the copy, use ddrescue instead:

ddrescue  -v  -n  -b2048  /dev/sr0 mymovie.iso

Obviously you need to specify your own source and destination.

ddrescue will remove breaks and other nasties that keep ordinary disk burning programs from making an ISO image.

At this point we have a good ISO image on the HD. Now we need to recode it to remove any funny stuff:

3) Run k9copy (not k9 assistant). Specify your ISO file for the input. Give the output ISO whatever name you want. Hit the load button. This will create a tree display of the DVD contents. Check the top checkbox on the tree to include all of the DVD components. Alternately, at this point you can remove previews and such if you wish. Click on an item or two in the tree view and make sure compression is at 1:1 unless you are trying to shrink the size. My copy of k9 defaults to 1:1. Hit the copy button.

4) Once the copy is complete, burn the converted ISO to a DVD using your favorite DVD burning software. I use k3b, but others work.

Hope this helps,
Tom

---

