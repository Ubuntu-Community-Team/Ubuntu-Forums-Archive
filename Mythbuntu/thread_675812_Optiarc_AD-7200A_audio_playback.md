---
title: "Optiarc AD-7200A audio playback"
date: 2008-01-23
forum: Mythbuntu
---

### Post by kloosdijk on 2008-01-23
Hi,

I've installed MythBuntu 7.10 on my newly built HTPC and installed all available updates.
Unfortunately my system does not recognise audio CD's inserted in the Sony/NEC Optiarc AD-7200A (i.e. ATA).

- Drive is accessed via /dev/hda and is recognised by the CDROM driver (checked the kernel's boot messages).
- Playing DVD's works.
- Mounting (automatically upon insertion) of CD-ROMs works.
- Recognition of audio CD's fails.

I checked /var/log/messages and /var/log/syslog. Messages from the CDROM driver include seek errors on /dev/hda and messages like "This disc doesn't contain tracks that I recognise". I checked the kernel sources and the latter indeed comes from the CDROM driver (module cdrom.o).

Strange enough the drive capabilities listed in /proc/sys/dev/cdrom/info show that the drive is not capable of playing audio CD's. Two indications that this observation must be wrong:
- the specs of the drive tell me that it is capable of playing audio;
- once connected to my WinXP box it does play audio CD's.

I upgraded the drive's firmware from 1.01 to 1.04 (latest version), but no change in behaviour.

Anyone having a clue what can be wrong here? Every help is highly appreciated!

---

### Post by chicos on 2008-03-02
have you tried disabling 'audio stream' in your cd properties? (see: 'device manager' -> cdrom properties)

it appears that latest optiarc recorders don't support plain ("analog") cdaudio playback (only streaming / digital playback thru your soundcard)

---

### Post by kloosdijk on 2008-03-11
Hi Chicos,

Thanks for the suggestion. However, I might be overlooking something, but I can not find the option you mention in de CD-ROM properties in the device manager.

But the problem seems to be in de kernel's ide_cd driver (imho). When I manually remove the ide_cd module and insert the scsi emulation modules for ATAPI devices, the device info reports that the device is capable of playing audio, but then it isn't recognised of being capable to burn CD's and DVD's any more.

So for now it seems I have two options left: either being able to play audio CD's or to be able to burn CD's and DVD's ;-)

Might be that I have to post my question on some kernel forum or try to debug the kernel drivers myself...

---

### Post by Linicks on 2008-10-04
I had this issue too, and gave up looking for the problem, so posted to LKML.

The thread is here, including a patch from Bodo to fix this buggy drive up :-)

[http://marc.info/?t=122311292800002&r=1&w=2](http://marc.info/?t=122311292800002&r=1&w=2)

Nick

---

### Post by kloosdijk on 2008-10-06
Hi Nick,

Thanks a lot for your reply/support.
I will apply the patch and try again...

Thanks again!

Erwin

---

### Post by Linicks on 2008-10-06
The patch is included in the latest changeset, so kernel 2.6.27 will have it when released - I guess Distro's will backport a lot of these buggy firmware type fixes.

[http://marc.info/?l=linux-kernel&m=122322600831664&w=2](http://marc.info/?l=linux-kernel&m=122322600831664&w=2)

Nick

---

