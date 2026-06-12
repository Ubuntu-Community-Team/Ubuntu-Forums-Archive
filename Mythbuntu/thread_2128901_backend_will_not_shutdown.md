---
title: "backend will not shutdown"
date: 2013-03-24
forum: Mythbuntu
---

### Post by Neon612 on 2013-03-24
I installed ubuntu 12.04 server on the computer and then installed mythbuntu and all the required packages. It works fine.
I tried setting up something that would allow me to auto mount the hard drive where the media files are stored. I've tried py(something, I forget what it was called), ntfs-config, and finally a edit to the fstab file, which I am currently using and as far as I know it is working correctly.

The other two programs are uninstalled (hopefully purged), but on boot I still get this message box pop up saying something about an error and gives me the option to report it. The messagebox is dealing with ntfs-config, which is no longer installed.

The shutdown problem happens with the poweroff, shutdown -P or -h commands, as well as going through the menu on the desktop. No matter which way is used, the xfce desktop closes and the text scrolls by telling me what processes are stopping (The right hand side all show up as [OK]). Then there is the line "Will now halt" followed by "([numbers]) System halted". I hear a click from the computer case, and it just sits there. The text screen is still displayed, the fans and everything are still running, and having left it for 12+ hours running in this state, I know that giving it time doesn't help.

I googled and searched and found out that it is probably some process waiting for another one to quit, which probably already has, the first process just doesn't know it yet.

How can this be fixed?
Thanks

---

