---
title: "Leadtek DTV 1800H"
date: 2009-02-09
forum: Multimedia Software
---

### Post by haxeman on 2009-02-09
Hi!

I have read the following description ([http://ubuntuforums.org/showthread.php?t=648028](http://ubuntuforums.org/showthread.php?t=648028)) about installation of DTV 1800H on Ubuntu. 

[COLOR="Red"]1) hg clone -r 55d60e988b89 [http://mcentral.de/hg/~mrec/v4l-dvb-kernel/](http://mcentral.de/hg/~mrec/v4l-dvb-kernel/)

2) Download patch here.

3) Copy the patch file to the v4l-dvb-kernel directory.

5) Apply the patch file:
Code:

patch -p1 < leadtek_dtv1800h.patch

6) Compile and install modules
Code:

make
sudo make install
[/COLOR]

I visited [http://mcentral.de/hg/~mrec/v4l-dvb-kernel/](http://mcentral.de/hg/~mrec/v4l-dvb-kernel/) because the revision number "55d60e988b89" was wrong. I found a new number "80a3bec444d3" there, and I modified the hg command. After this it could download the v4l-dvb-kernel.

I copied the patch file into the directory, and tried to run patch command, but I got an error message again: "can't find file for patch in line 4"

Can somebody guide me on correct installation method step-by-step?

Thank you!

---

### Post by haxeman on 2009-02-10
I tried to locate the files which are listed in the patch, but I could not find them.

I visited the mcentral.de again. There are no these files in **v4l-dvb-kernel** directory (and in the cloned directory on my computer of course). I found files started with "cx88.." only in **[COLOR="SeaGreen"]v4l-dvb[/COLOR]** directory. Now, the modified "hg clone http://mcentral.de/hg/~mrec/v4l-dvb/" command works and the patch command does not stop now with previous "can't find file for patch" error.

The first four changes during patching are succesfull, but after this all failed, so I think, the patch and v4l files are incompatible.

Do you have any idea?

---

