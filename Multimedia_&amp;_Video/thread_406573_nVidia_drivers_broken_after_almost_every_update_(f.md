---
title: "nVidia drivers broken after almost every update (feisty)"
date: 2007-04-11
forum: Multimedia &amp; Video
---

### Post by DaVinciXL on 2007-04-11
Hi everyone.

After almost every update (I'm only doing updates when the adept manager / notification tool tells me to) I can't use the nvidia drivers anymore.

It's so annoying!

I always have to manually edit the xorg.conf file and change the driver part from "nvidia" back to "nv" to get things working (sort of) again.
From there on nothing helps - but waiting for the next update. Even a downgrade of the nvidia packages doesn't change anything.
And of course I tried dpkg-reconfigure...

My guess so far is that the nvidia packages and the restricted-modules packages aren't compatible. This would also explain why my problem sorts itself out with the next update (at least that's what happend the last couple of times).
I know, I shouldn't complain all too loud since I'm using Feisty - but somehow I think that's not the way it should be...

For further debugging I attached my xorg.conf and the latest Xorg.0.log.

Maybe someone of you finds out that I'm just plain stupid and overlooked some important thing... :)

Thanks in advance!

---

### Post by gaten on 2007-04-11
Im not using Feisty, but I find that after every X-server update my nvidia drivers break; so every time I see Xorg in the update list, I make sure I download the binary drivers from nvidia's website and am prepared to install them. It's REALLY annoying, I agree, especially  if you have auto updates on (which I suggest turning off).

---

### Post by kvonb on 2007-04-11
What happens is that one part of the chain is updated, and another part is not done till later, hence the "breakage".

I'll have to say it: Feisty is BETA, you'll have to put up with it :).

I got around it by installing the Nvidia driver from the Nvidia web-site, rather than using the Ubuntu repo version, that way I know that all I have to do is re-run the driver install each time it breaks, it makes it easier.

And yes Compiz AND Beryl still work :).

Maybe give that a go, or just ignore the updates until the final release.

---

