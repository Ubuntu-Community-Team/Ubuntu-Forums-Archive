---
title: "Mediocre performance of VmWare video driver for Edgy"
date: 2006-11-23
forum: Multimedia &amp; Video
---

### Post by obi1kenobi on 2006-11-23
Hello folks,


This is probably a shot in the dark but I'll give it a try anyway ...

I have kubuntu edgy running as guest in wmware 5.5.2. Video performance is "so and so". On the same machine, I am running opensuse 10.1 also as a guest. VmWare tools installed on both. Now my grief is that the video performnace and the font rendering in opensuse is **significantly** better when compared to kubuntu.

I know that opensuse uses xorg 6.8 whilst kubuntu is on 7.1. And vmware offers support up to version 7.0 - so maybe that's the problem (e.g., when installing vmware tools on opensuse, I get the option of setting the resolution to 1280x960 - that option is missing when installing on kubuntu, however ...).

I would like to switch from opensuse to kubuntu but this performnace difference is really a showstopper for me.

Any ideas ?

Thanks in advance.

Regards.

---

### Post by GarlicFish on 2006-11-23
I don't think Edgy is officially supported by VMWare tools yet, I've had a few issues with Edgy as a guest.

Dapper is supported and works well, perhaps you could try comparing the video performance of Dapper to OpenSuse as guests.

When you say you want to switch, do you just mean under VMWare or on real hardware?

---

### Post by obi1kenobi on 2006-11-24
Hi GarlicFish,

Thanks for comming back to me on this and apologize for the delayed response. You're right, Edgy is not officially supported in vmware :( yet. I'll give Dapper a try but would have loved to have Firefox 2 and especially Evolution 2.8. Now I know I can install Firefox 2 in Dapper (although I believe you'll be on your own to provide security updates for it then). Installing Evolution 2.8 in Dapper, however, I'm afraid is a whole new game altogether since it depends on quite a few "new/updated" system libraries (glibc, dbus, etc ...) which might wreck Dapper if I forcedly squeeze them in.

When I said I wanted to "switch" I was referring to moving from opensuse to edgy :). I am using Linux at work and I have to run WinXP as well (required for Outlook, Visio, and a customized database application, among others). So I've set up a dual-head workstation, in one display I'm running WinXP while on the other is Linux inside vmware. Last time I've tried to do the other way around (WinXP as a guest on vmware running on Linux), the performance of Outlook and Visio inside WinXP was poor (I should say annoyingly slow). But that was an year ago. Not sure whether or not that has been improved by now :-k.

Regards.

---

