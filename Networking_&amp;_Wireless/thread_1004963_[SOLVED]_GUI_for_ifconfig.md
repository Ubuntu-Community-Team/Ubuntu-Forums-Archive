---
title: "[SOLVED] GUI for ifconfig?"
date: 2008-12-07
forum: Networking &amp; Wireless
---

### Post by Rytron on 2008-12-07
Hi,
Is there a GUI for ifconfig such a [Winipcfg]("http://www.practicallynetworked.com/images/winipcfg.gif") equivalent?

---

### Post by Iowan on 2008-12-08
Well, there's Network Manager... but you knew that. ;)

---

### Post by tecknomage on 2009-08-07
I don't think [Rytron]("http://ubuntuforums.org/member.php?u=505033")'s question was FULLY answered.

I use **WICD** not Network Manager, **so is there GUI for ifconfig** :confused:

---

### Post by Rytron on 2009-08-08
> **tecknomage said:**
> I don't think [Rytron]("http://ubuntuforums.org/member.php?u=505033")'s question was FULLY answered.

I use **WICD** not Network Manager, **so is there GUI for ifconfig** :confused:

Thank you tecknomage.

---

### Post by tecknomage on 2009-08-18
It looks like there is no GUI for ifconfig.  But another solution came up.

If you use "gedit" (*Text Editor*) install "**gedit-plugins**"

From "gedit" **Tools** menu, **External Tools**, and add a **[New]** tool:

Name = **Run Ifconfig** (*on left sidebar*) and Description

In the **Commands** box enter (*or copy/paste*) the _following lines_:

#!/bin/sh

#TODO: use "gconftool-2 -g /desktop/gnome/applications/terminal/exec"
exec ifconfig

----- ***command lines end above***

I set [B]Output: Create new document
[/B]
Now, in the **Tools** menu, **Run Ifconfig** should be listed.

If you select your new tool, the output of ifconfig appears. With my setting, in a new document. Now you can save it if you wish.

Note; I could not get any Hot-Keys to actually work, so I assigned none to **Run Ifconfig**.

---

