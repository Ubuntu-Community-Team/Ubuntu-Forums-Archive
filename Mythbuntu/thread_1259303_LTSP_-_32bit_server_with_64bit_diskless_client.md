---
title: "LTSP - 32bit server with 64bit diskless client"
date: 2009-09-06
forum: Mythbuntu
---

### Post by amauk on 2009-09-06
Hey all,

Currently got LTSP working great, with a Pentium 4 Mythbuntu server serving a core2duo diskless client

everything's 32bit at the moment, and I was wondering if it's possible to setup the client to be 64bit?
(no particular reason, but seems a waste to have a 64bit system with a 32bit OS)

I've done a bit of reading around, and the LTSP project help says it should be possible.
*edit* See here [http://wiki.ltsp.org/twiki/bin/view/Ltsp/CpuArchitectures](http://wiki.ltsp.org/twiki/bin/view/Ltsp/CpuArchitectures) *edit*

When I force 64bit by passing --arch=amd64 to ltsp-build-client, it starts to build, but fails during the later stages (server unable to chroot into client environment)

Am I being silly, or is this just not possible at the moment?

Thanks
- Tony

---

### Post by williammanda on 2009-09-06
My opinion on mixing architectures is to keep the same architecture across the board. If it is working now why fix it?
Thanks

---

