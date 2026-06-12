---
title: "Nvidia-glx-173 driver won't download, keeps asking for CD"
date: 2010-03-20
forum: Multimedia Software
---

### Post by madsporkmurderer on 2010-03-20
I've installed 9.10 and wish to use the nvidia-glx-173 driver as recommended by jockey. Using the jocky GUI just hangs at 100% cpu, a significant portion of which is the cdrom process; I've tried installing the package directly in aptitude and get the error:
```
Media Change: Please insert the disc labeled 'Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5)' in the drive '/cdrom/' and press [Enter].
```
The installation disc (standard x86 disk from shipit) doesn't satisfy it. How do I get aptitude to just download it from online repositories?

Thanks in advance,
Mike

---

### Post by drs305 on 2010-03-20
> **madsporkmurderer said:**
> I've installed 9.10 and wish to use the nvidia-glx-173 driver as recommended by jockey. Using the jocky GUI just hangs at 100% cpu, a significant portion of which is the cdrom process; I've tried installing the package directly in aptitude and get the error:
```
Media Change: Please insert the disc labeled 'Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5)' in the drive '/cdrom/' and press [Enter].
```
The installation disc (standard x86 disk from shipit) doesn't satisfy it. How do I get aptitude to just download it from online repositories?

Thanks in advance,
Mike

Most likely the CD-ROM is still referenced in sources.list. Open Synaptic (System, Administration, Synaptic Package Manager). Settings > Repositories > Ubuntu Software tab and untick the CD_ROM in the bottom pane.

If you are still getting the CD message, check the "Other Software" tab and make sure you don't have a CD referenced in that section.

Press the "Reload" option on the main menu to refresh your sources.

---

