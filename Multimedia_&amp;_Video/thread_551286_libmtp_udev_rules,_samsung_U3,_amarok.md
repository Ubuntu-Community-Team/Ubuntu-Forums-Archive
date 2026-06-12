---
title: "libmtp udev rules, samsung U3, amarok"
date: 2007-09-15
forum: Multimedia &amp; Video
---

### Post by Hagbard on 2007-09-15
I just bought a Samsung U3 portable music player because of the native OGG support -- only to discover that its an MTP only device that doesn't support UMS at all and doesn't even (supposedly) allow the firmware change for UMS support. I was able to get the device working in Amarok by adding a custom line to /etc/udev/rules.d/65-libmtp.rules as described in this bug report: [http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg420632.html](http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg420632.html)

However, the functionality seemed to "break" suddenly during a file transfer, and I haven't been able to get it working again in Ubuntu Feisty. It had been displaying correct information in response to mtp-detect previously, but no longer does -- the error message makes me wonder if the udev rule is no longer being correctly applied. I did verify the device is still functioning properly when accessed via the included software on a windows install.

Any advice for how to restore functionality under libmtp in Amarok is appreciated, I would prefer to avoid booting my windows partition to load this player -- seems that if it was working before, there has to be a way to get it working again.

---

### Post by trippinnik on 2007-09-15
check with the libmtp development team [http://libmtp.sourceforge.net/](http://libmtp.sourceforge.net/)
There's a table for compatibility.  There are also much more up to date versions of the libmtp.  
Also libmtp has some command line tools.  What is the output of mtp-detect?  If you send that and the USB Id to the mailing list it'll help get mtp working in linux for others as well.

---

### Post by Hagbard on 2007-09-15
Thanks for the info on the libmtp developers. I appreciate the hard work they do in letting me use my device despite Samsung's foolishness in making it MTP only. I suspect the U3 might be at fault, because my ability to transfer files to it suddenly started working again. The U3 is a new device and might have flaky firmware. Of course, since I'm posting this, it will probably start glitching again immediately! I'm planning on testing Gutsy soon, which supposedly supports the U3 in the version of libmtp it will ship with.

---

### Post by trippinnik on 2007-09-16
I recommend grabbing the new one yourself.  It's a simple install:
./configure, make, sudo make install 
in the directory where you download the archive.  The one in the repos is pretty old.

---

