---
title: "Unable to mount location; failed to retrieve share list from server"
date: 2010-10-18
forum: Networking &amp; Wireless
---

### Post by finsyourfriend on 2010-10-18
Greetings all.

THE HISTORY:

My network was running happily with no problems. After clicking "Places," then "Network," I double-clicked "Windows Network." My wife's laptop appeared merrily ready to be clicked. I browsed through and accessed the "Public" folder. Ubuntu auto-mounted the "Public" folder on the Windows Vista machine to the desktop. All was well.

THE REASON:

I wanted to change the icon to a disk so it would mimic a "mapped" drive like in Windows. I right-clicked the shared folder mounted on the desktop, clicked "Properties," and then clicked the picture of the folder. I then clicked through to "/usr/share/icons/Human/scalable/devices" and selected the "drive-harddisk.svg" icon. The icon changed and I could still browse. I unmounted and re-mounted the folder with no problems, then changed back the disk to the regular folder icon.

THE PROBLEM:

After restarting the computer, if I click "Places," then "Network," then double-click "Windows Network," I'm greeted with the following error message:

Unable to mount location. Failed to retrieve share list from server.

WORKAROUND:

Opening Firefox and typing smb://IP-of-wife's-laptop shows the share list. I can open and access the "Public" folder no problem.

Thoughts?

---

### Post by johnnytm on 2010-10-18
by chance is ufw enabled? check it and see
```
sudo ufw status
```

---

### Post by finsyourfriend on 2010-10-18
```
Firewall not loaded
```

That's the result that's returned.

The good news is is that the problem is gone. After navigating to the share I noticed that the hard drive icon was still being used for the Public folder in the navigation pane to the left. There was a "Revert" button sitting at the bottom of the window. I clicked it, and "Boom!" the folder icon returned. It also appeared that a "drive" was unmounted when I clicked the button. After that, I rebooted. Everything works. 

Guess even a little icon is not what it seems in Ubuntu... :)

Thanks for the reply.

---

### Post by johnnytm on 2010-10-18
well at least its working, matters not how as long as it works......lol

---

