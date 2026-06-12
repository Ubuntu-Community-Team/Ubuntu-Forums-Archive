---
title: "Unable to open JPEG files imported from Android"
date: 2012-08-25
forum: Multimedia Software
---

### Post by Lxplot on 2012-08-25
Hello all.  I apologize if this is posted in the wrong place or if somehow this has been previously solved and I missed it in my searches.  If either of these are true, pass along the link or move it.

All that said, I am having the following issue.  I have connected a Motorola Droid 2 to a Dell Inspiron 1520 laptop running the latest version of Ubuntu.  The phone was connected in USB storage mode, and when I navigated to DCIM/Camera none of the files within would open.  The error message was something along the lines of "Error interpreting JPEG image file (Not a JPEG file: starts with 0x00 0x00)."  I have opened several of the images in a hex editor and FF d8 is buried deep within the file while the start of them appears to be a string of zeroes, some random characters, than over a hundred lines worth of zeroes, followed by more random characters, and then the actual file start.

Does anyone know what my issue seems to be or how I could rectify it?

Thank you for all of your help!

---

### Post by brainschrat on 2012-09-30
I'm on Gentoo and have the same problem. After a bit of research I found this:

[http://www.linuxquestions.org/questions/linux-general-1/jpegs-show-as-not-jpeg-files-on-hybrid-iso9660-hfs-cdrom-and-dvds-729140/](http://www.linuxquestions.org/questions/linux-general-1/jpegs-show-as-not-jpeg-files-on-hybrid-iso9660-hfs-cdrom-and-dvds-729140/)

The setting is different, but the symptoms are the same. The bottom line is that this may be a filesystem problem. I noticed that my jpgs were all right if I sent them to other people via email.

So the key is to get the the files from the phone without mounting it as mass storage device. I achieved this by using scp via DroidSCP, but this could not copy to my computer on the same local network, but running an SSH server (like SSHDroid) on the phone and then copying from the other computer worked.

---

