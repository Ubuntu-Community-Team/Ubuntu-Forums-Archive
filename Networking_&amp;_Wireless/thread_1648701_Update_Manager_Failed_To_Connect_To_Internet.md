---
title: "Update Manager Failed To Connect To Internet"
date: 2010-12-19
forum: Networking &amp; Wireless
---

### Post by RichieB07 on 2010-12-19
I clicked on Update Manger and this is what popped up:
[IMG]http://i55.tinypic.com/2ntio9k.png[/IMG]

The text in the box says "W:Failed to fetch [http://archive.canonical.com/ubuntu/dists/maverick/partner/binary-i386/Packages.lzma](http://archive.canonical.com/ubuntu/dists/maverick/partner/binary-i386/Packages.lzma)  Sub-process /usr/bin/lzma returned an error code (1)
, W:Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/maverick/main/binary-i386/Packages.lzma](http://extras.ubuntu.com/ubuntu/dists/maverick/main/binary-i386/Packages.lzma)  Sub-process /usr/bin/lzma returned an error code (1)
, W:Failed to fetch [http://ppa.launchpad.net/tiheum/equinox/ubuntu/dists/maverick/main/source/Sources.lzma](http://ppa.launchpad.net/tiheum/equinox/ubuntu/dists/maverick/main/source/Sources.lzma)  Sub-process /usr/bin/lzma returned an error code (1)
, E:Some index files failed to download, they have been ignored, or old ones used instead."

This just randomly happened today, as 10.10 has been working fine for me lately.  I didn't change any settings, restarted, and it still can't connect.  Any help would be greatly appreciated.  Also, I'm kinda new to Ubuntu, so as much detail as possible when giving responses is also greatly appreciated!

---

### Post by grahammechanical on 2010-12-19
The message says: "Check your Internet connection." It is a standard message. Let us assume that your Internet connection is fine. You can surf the web. You can access the Ubuntu forums. You can download programs using the Software Centre.

Did you only have those four error messages? I am no expert but I think that you tried to update a program called lzma. I do not know if lzma is part of the Operating System or some other kind of program. It is possible that this program is no longer supported in the repositories. Or the links to the place where this program is stored are broken.

I have just run Synaptic Package Manager and lzma is described as a "Compression method 7z format in the 7-zip program." It is installed on my system even though I do not use it for compressing files. I think it is there in case I need to uncompress a file compressed by 7-Zip. May be it will update later.

I have had this happen to me. Update manager says that there are update but not all of them get updated when I let Update Manager run. I do not think that this is a system critical file.

Regards.

---

### Post by RichieB07 on 2010-12-19
> **grahammechanical said:**
> The message says: "Check your Internet connection." It is a standard message. Let us assume that your Internet connection is fine. You can surf the web. You can access the Ubuntu forums. You can download programs using the Software Centre.

Did you only have those four error messages? I am no expert but I think that you tried to update a program called lzma. I do not know if lzma is part of the Operating System or some other kind of program. It is possible that this program is no longer supported in the repositories. Or the links to the place where this program is stored are broken.

I have just run Synaptic Package Manager and lzma is described as a "Compression method 7z format in the 7-zip program." It is installed on my system even though I do not use it for compressing files. I think it is there in case I need to uncompress a file compressed by 7-Zip. May be it will update later.

I have had this happen to me. Update manager says that there are update but not all of them get updated when I let Update Manager run. I do not think that this is a system critical file.

Regards.

I do have p7Zip, or whatever the name of the Ubuntu version of 7zip is, installed on my computer.  Maybe this is what's causing the problem then?  I don't know why I didn't think to check Synaptic, but thanks for the help.  I'll check it out when I get on my Ubuntu partition again later tonight.

---

### Post by RichieB07 on 2010-12-22
I found LMZA in Synaptic, deleted it, and now everything works fine.  I still have no idea why the repository didn't download if it was in Synaptic, but since deleting it, I have had no problems.

---

