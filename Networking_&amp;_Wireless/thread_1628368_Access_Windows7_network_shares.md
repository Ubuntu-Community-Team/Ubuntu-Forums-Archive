---
title: "Access Windows7 network shares"
date: 2010-11-22
forum: Networking &amp; Wireless
---

### Post by næl on 2010-11-22
I am trying to access my win7 networks shares with pcmanfm. (I have done sudo apt-get install gvfs-backends). I dont have any pw on my win7 and i dont want one. So every time i try to connect, pcman ask me for pw. How to configure pcman to dont ask me for pw? I have tried linux mint live usb and ubuntu live usb with same result.

---

### Post by cavalier911 on 2010-11-22
Add group **Everyone **to the _**Windows 7** computer_ for Network Share
with no prompt for username or password,

Right Click the drive or folder you want to share in Windows Explorer
Choose properties,Security tab,Group or Usernames,Add button,type **Everyone**
in the Enter the object names to select box,click OK button,
With **Everyone** highlighted,click the checkbox by the permissions you desire in the Permissions for **Everyone** box,click apply button,click ok,Ok to close drive/folder name properties of your share.

You should now be able to mount the Windows 7 share on the Lubuntu computer without being prompted for a username or password.

---

### Post by næl on 2010-11-23
> **cavalier911 said:**
> Add group **Everyone **to the _**Windows 7** computer_ for Network Share
with no prompt for username or password,

Right Click the drive or folder you want to share in Windows Explorer
Choose properties,Security tab,Group or Usernames,Add button,type **Everyone**
in the Enter the object names to select box,click OK button,
With **Everyone** highlighted,click the checkbox by the permissions you desire in the Permissions for **Everyone** box,click apply button,click ok,Ok to close drive/folder name properties of your share.

You should now be able to mount the Windows 7 share on the Lubuntu computer without being prompted for a username or password.

 I have done that of curse. I can access my win7 shares from xp, win 7 and even my nexus one phone. So the problem is not there.

---

### Post by næl on 2010-11-23
no?

---

### Post by gharika on 2010-11-29
Same issue here, but a more complex one. Since, it was working fine a few days back, and I was able to share my folders on Win 7 to my Ubuntu machine, then I don't know what changed and I am getting username/password prompts now. Providing the username and password for one of the accounts that I have does not help either. This happens when I try to browse the Win7 pc from Nautilus without any specific folder being accessed.

---

### Post by ndefontenay on 2010-11-29
This proves that windows got much more secure than before. So much so that it doesn't even let you connect AT ALL!

I'm having the same problem here. I've heard disabling the guest username can work too.

I've tried that without success but haven't tried the everyone group yet.

try disabling the guest acccount. It could work for you!

---

