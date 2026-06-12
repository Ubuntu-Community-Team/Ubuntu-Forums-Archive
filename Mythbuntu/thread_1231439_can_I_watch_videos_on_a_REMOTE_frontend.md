---
title: "can I watch videos on a REMOTE frontend?"
date: 2009-08-04
forum: Mythbuntu
---

### Post by radnor on 2009-08-04
Hello all!

I have a BE & FE setup on my desktop.  As of now, I DO NOT have any tuners (looking to buy a HDHR tuner).  I imported a few DVD(s) and can watch them fine on the BE/FE desktop.  I can "see" (the titles listed) on the laptop (REMOTE) FE but CANNOT view them.  I get an error cannot open file.

On the BE/FE I have videos going to the /media/movies/videos and on the laptop made the same directory structure.

TIA,

Radnor

---

### Post by jensk on 2009-08-04
Hi radnor.
You cant se the videos unless your FE have access to the directory that the BE stored the videos in.

If you have recorded some shows (recordings) you can set the parameter "allways stream fromm the backend" on the FE. This lets the BE stream the recordings to the FE and thus the FE doesn't have to have direct access to the directory where the BE stores the recordings.

You can get the FE to play the videos by setting the BE to act as NFS host to the FE - se apropriate guides ie:
[http://www.mythtv.org/wiki/Mediashares]("http://www.mythtv.org/wiki/Mediashares")

Hopes this helps

On my wishlist for Mythtv 0.22 is that both recordings and videos could be streamed from the Backend

---

### Post by radnor on 2009-08-04
Thanks for the reply Jensk.

I do NOT have any recordings YET, no tuner.

Thank you for pointing me in the right direction to be able to play the DVD(s) {rips} on the RFE.

Thanks again!

Radnor

---

### Post by juancarlospaco on 2009-08-04
[B]ssh -X remote-user@remote-pc-ip frontend-executable

ssh -X chuck-norris@170.25.2.254 smplayer[/B]

:)

---

### Post by tgm4883 on 2009-08-05
> **juancarlospaco said:**
> [B]ssh -X remote-user@remote-pc-ip frontend-executable

ssh -X chuck-norris@170.25.2.254 smplayer[/B]

:)

Why not just mount the video shares via NFS or CIFS?

---

### Post by juancarlospaco on 2009-08-05
> **tgm4883 said:**
> Why not just mount the video shares via NFS or CIFS?

Im not saying its the*_ only _*way...
But SSH is **Compressed and Encrypted**

---

### Post by xinix on 2009-08-06
> **juancarlospaco said:**
> [B]ssh -X remote-user@remote-pc-ip frontend-executable

ssh -X chuck-norris@170.25.2.254 smplayer[/B]

:)

Have you gotten this method to work well?  I have tried it and it was not as good as installing a local frontend that connects to the remote BE.  Even then, with a reliable high speed wireless connection, it still gets flaky.  I get good results through the wired network I have available to me.  Live TV only works, at least for me, on the wired network.  It craps out after about 3 minutes over wireless.

---

