---
title: "mplayer from svn"
date: 2010-10-31
forum: Multimedia Software
---

### Post by pickarooney on 2010-10-31
I checked out mplayer from svn and farn configure with no errors. 
Then I ran make and I just got a couple of lines back:

help/help_create.sh help/help_mp-en.h utf-8 ./version.sh `cc -dumpversion` awk -f vidix/pci_db2c.awk vidix/pci.db 1

I tried make install but just got returned to the prompt with no error or success message. Likewise when I run make again. 

What's going wrong?

---

### Post by FakeOutdoorsman on 2010-10-31
I'm not sure what is wrong with your make, but did you see this?
[url=http://ubuntuforums.org/showthread.php?t=1542240]
Howto: Build the svn MPlayer under the latest release version of Ubuntu[/url]

---

