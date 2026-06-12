---
title: "dvd-video hfs hybrid"
date: 2007-08-10
forum: Multimedia Production
---

### Post by cdenley on 2007-08-10
I'm trying to burn a DVD video which also has a computer application. The computer application has a Mac binary and a Windows binary. Mac binaries will not run unless they are on an HFS filesystem, so I want to create a hybrid disc which can also be read as an HFS filesystem. I used mkisofs (now called genisoimage?) to create my disc image, then burned it. It seems like it works, except it doesn't play right in DVD players. It will hang or freeze. Is what I'm attempting to do possible?

The disc can be mounted in Ubuntu as udf, hfs, or iso9660, so the hybrid filesystem is correct. Do DVD players only work with UDF or UDF+ISO9660? Does adding HFS interfere with the ordering or padding that must be done with DVD video discs? Is this a bug in mkisofs?

This isn't really an Ubuntu question, because mkisofs must be run from a Mac in order for the Mac binary to be recognized as an executable file. However, I was hoping somebody who is an expert on filesystems or DVD authoring would be able to answer my question. My mkisofs command was something like:

```

mkisofs -dvd-video -hfs --osx-hfs --macbin -V MYTITLE -o image.iso ./mydata

```

---

