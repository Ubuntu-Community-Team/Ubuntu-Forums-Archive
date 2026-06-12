---
title: "libfaad! How have other people solved this silly library naming problem?"
date: 2007-12-01
forum: Multimedia Production
---

### Post by hoppipolla on 2007-12-01
Hi everyone, first post for ages I think so it's good to cover something that's quite a big issue!

I found that when I tried to install any video/audio encoding or editing program, it failed, as it couldn't satisfy it's libfaad dependency (or rather, it couldn't satisfy the dependencies that relied on libfaad).  EDIT -- libfaad is an audio decoding library i think

The only problem is that the packages seem to want libfaad0, and the one installed has a different name which is libfaad2.  and it doesn't seem to understand that it's the same library!

So, firstly shouldn't they have given it say two names in the package to stop this from happening? and also, it never mentions in the package tool what the reason for the problem is, I had to manually in the prompt work out it was a dependency issue, and what the problem was, so fingers crossed for later versions of ubuntu it will be a bit more friendly.

Does anyone know the best way to install the packages above libfaad? Is there a way to create a link or whatever to give libfaad two names so the dependencies are all satisfied?

Thanks, as this is really annoying me, I can't install transcode, kdenlive, manencoder or any of those cool programs!

Thanks,

Mike

---

