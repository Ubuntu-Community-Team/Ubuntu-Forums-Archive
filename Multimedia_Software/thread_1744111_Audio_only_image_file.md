---
title: "Audio only image file"
date: 2011-04-30
forum: Multimedia Software
---

### Post by Lordestabia on 2011-04-30
I need to mount an audio only image file. The only program I'm aware of is cdEmu, unfortunately, since my upgrade to 11.04 x86_64, It was removed during the process. Any other programs/commands capable of mounting an image file? And no, I do not want to burn,extract, or convert. Just mount.

Thanks in advance.

---

### Post by fdrake on 2011-04-30
> **Lordestabia said:**
> I need to mount an audio only image file. The only program I'm aware of is cdEmu, unfortunately, since my upgrade to 11.04 x86_64, It was removed during the process. Any other programs/commands capable of mounting an image file? And no, I do not want to burn,extract, or convert. Just mount.

Thanks in advance.

what kind of image is? iso?
mount -o loop /path/file.iso /mnt

---

### Post by Lordestabia on 2011-04-30
As I indicated, it is an audio only[COLOR=Red][COLOR=Black] image file. The command you gave has no effect.[/COLOR][/COLOR] Also, it's a Nero image file. The command I use to open nrg files are [COLOR=Blue]mount -t iso9660 -o loop,offset=307200 test\ data.nrg /mnt/fsloop/[/COLOR], and it works without problems. Audio files on the other hand, [COLOR=Blue]mount -t iso9660 -o loop,offset=307200 test\ audio.nrg /mnt/fsloop/[/COLOR] gives me this error.[INDENT][COLOR=DimGray]mount: wrong fs type, bad option, bad superblock on /dev/loop0,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so[/COLOR]
[/INDENT]Your command gives the same error message.

---

