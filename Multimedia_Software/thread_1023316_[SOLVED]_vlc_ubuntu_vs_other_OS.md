---
title: "[SOLVED] vlc ubuntu vs other OS"
date: 2008-12-27
forum: Multimedia Software
---

### Post by flyingsolo on 2008-12-27
I have a Flip Mino HD which records video in mpeg4 but I can't play the videos with vlc under ubuntu but I _can_ play the same video with vlc on an iMac.
When I try playing it with vlc/ubuntu, I hear the audio fine and see one still frame which then will occasionally change to a new fixed frame somewhere later in the video which might be OK or blurred.
What would be the difference between the two versions of vlc?  Is it related to something else perhaps?
(vlc for ubuntu is version 0.8.6e and for leopard is 0.8.6d if that helps)
Thanks.

---

### Post by SuperSonic4 on 2008-12-27
Probably a codec. What was the video codec you tried (find out by Tools -> Codec Information or ctrl+J, both when playing the video in VLC)

---

### Post by sirjoebob on 2008-12-27
I would recommend installing the Medibuntu repository. See my signature for a link.

---

### Post by flyingsolo on 2008-12-27
Thanks for the replies--looking further into this, I've found the vlc will play the video on a full dell laptop (ubuntu hardy) but the problem laptop was an asus eee 1000 with netbook remix.  They both have identical vlc versions and (as far as I can see), identical video codecs.  So maybe it just reflects the low end processor of the asus 1000?  I'll try to find an mp4 file from another source to try on the asus.

By the way, why did you suggest using medibuntu?  Doesn't it use the same version of vlc anyway?  This laptop is a general purpose machine after all so I've got plain-old-vanilla ubuntu hardy on both of them.

---

### Post by mb_webguy on 2008-12-28
He wasn't suggesting Medibuntu because of the Medibuntu version of VLC -- or at least not *only* because of it -- but rather for the codecs that aren't available in the regular Ubuntu repositories.  If you follow the link in SirJoeBob's signature, you'll find a walkthrough for installing all of the codecs and software required to play just about any media you want.

That said, the mp4 could contain h.264 video, which is rather processor intensive to decode.  While it's likely a codec issue if the file won't play *at all*, if it plays *badly*, it could indeed be that the hardware isn't sufficient to play it.

---

### Post by sirjoebob on 2008-12-28
> **mb_webguy said:**
> He wasn't suggesting Medibuntu because of the Medibuntu version of VLC -- or at least not *only* because of it -- but rather for the codecs that aren't available in the regular Ubuntu repositories.  If you follow the link in SirJoeBob's signature, you'll find a walkthrough for installing all of the codecs and software required to play just about any media you want.

Thanks for beating me to this response. That is EXACTLY my point. It is much easier to get all codecs working right using Medibuntu.

---

### Post by flyingsolo on 2008-12-28
Great!  Thanks sirjoebob & mb_webguy--though it was playing on the better dell laptop, it was a little herky-jerky but better now with new repositories.  One point of interest--I typically have used the Canadian server for any software installs/updates but had to use the Main server for getting the Medibuntu resources; I guess I always thought the Canada server was just a mirror of the Main server so used it to reduce traffic to the main server but apparently, that's not so.  I was getting error: "Could not connect to ca.archive.ubuntu.com:80 (129.97.134.71). - connect (113 No route to host)"

Anyway, all seems good now with playback of these videos.

---

### Post by sirjoebob on 2008-12-28
Fantastic. Glad we could help. remember to mark thread as closed.

---

