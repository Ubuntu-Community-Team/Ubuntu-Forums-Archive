---
title: "FGLRX not working, an Ubuntu specific problem?"
date: 2005-10-22
forum: Multimedia &amp; Video
---

### Post by Navyblue on 2005-10-22
Hi all,

I have not been following this issue lately. Not sure if there is a solution already. Anyway I have been monitoring the repository a few times a day hoping to get a working update. Anyone have a clue of when would it be fixed?

In the mean time, I can't wait to get my 3D working, so I am looking for a second Linux distribution to dual boot with (yes, I broke free from M$ just after Breezy is out). But I am wondering if it is:

- A Ubuntu specific problem? Meaning I can try Debian Sid or Knoppix 64 or Kanotix 64 for the moment.

- A Debian Sid problem? Meaning I'd need to go to Debian Etch or Gentoo or Suse to avoid this disaster?

- An X server problem? Meaning No matter what distribution I try I won't get away from this avalanche?

Thanks in advance. :)

---

### Post by garba on 2005-10-22
i got my ati 8500 to work ok on gentoo and debian a while back, but with the latest driver release my pc crashes as soon as i move a window across the screen, go figure... 3D is reported to work but 3d graphics are corrupted... tried these drivers on a lot of distros (even on my custom build CRUX) but i get the very same behaviour...  dunno what's wrong, besides ati being crap

---

### Post by archiesteel on 2005-10-22
Check out this thread:

[http://www.ubuntuforums.org/showthread.php?t=75585](http://www.ubuntuforums.org/showthread.php?t=75585)

---

### Post by mlomker on 2005-10-22
> - A Ubuntu specific problem? Meaning I can try Debian Sid or Knoppix 64 or Kanotix 64 for the moment.

The Xorg modularization broke the ATI drivers.  The Ubuntu ATI packager, Septor, found a temporary fix by downgrading the libdri.a file.  I don't know when a permanent fix will go out as an operating system update.  The how-to's stickied on this forum will walk you through the fix.

---

### Post by Navyblue on 2005-10-22
Thanks a lot. My 3D acceleration now worked, its not hard at all. :)

---

### Post by jecos on 2005-10-23
[QUOTE=garba]i got my ati 8500 to work ok on gentoo and debian a while back, but with the latest driver release my pc crashes as soon as i move a window across the screen, go figure... 3D is reported to work but 3d graphics are corrupted... tried these drivers on a lot of distros (even on my custom build CRUX) but i get the very same behaviour...  dunno what's wrong, besides ati being crap[/QUOTE]

8500 has open source drivers that have 3d support and every other feature, nvidia has NOT one open source driver that supports 3d!  therefore people developing Xgl(xserver using opengl to display 2d) are using 8500's so they can modify the driver.

---

