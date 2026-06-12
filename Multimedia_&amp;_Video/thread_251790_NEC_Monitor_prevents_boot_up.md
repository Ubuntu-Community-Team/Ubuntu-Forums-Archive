---
title: "NEC Monitor prevents boot up"
date: 2006-09-05
forum: Multimedia &amp; Video
---

### Post by hoosemon61 on 2006-09-05
I have an IBM NetVista that I picked up for about $50 with a 17" HP monitor.   I'm pretty sure it's a Celeron with 128MB ram.  I've run hoary, breezy, and now Dapper on it (at reasonable speed) without a hitch.

I just tried swapping monitors and connecting a 19" NEC Multisync monitor to this computer, and it won't boot successfully.  It gives me some message about the xserver not initiating successfully (or something close to that), then it goes into terminal mode.

Putting the 17" monitor back fixed the problem.

Any ideas on what I should do if I want to use the 19" monitor?

Thanks,

Hoosemon

---

### Post by meng on 2006-09-06
You could try
sudo dpkg-reconfigure xserver-xorg
which would allow you to reselect resolutions/refresh rates which may be your problem.

---

### Post by hoosemon61 on 2006-09-14
Thanks Meng

It worked great.

I checked out the specs for my larger monitor and chose those during config, and it booted fine.

You rock!

---

