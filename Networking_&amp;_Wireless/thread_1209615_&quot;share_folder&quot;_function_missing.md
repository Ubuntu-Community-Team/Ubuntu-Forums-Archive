---
title: "&quot;share folder&quot; function missing"
date: 2009-07-10
forum: Networking &amp; Wireless
---

### Post by d0dja on 2009-07-10
I'm trying to share folders on my new Ubuntu install (first Linux install in 10 years). Should be easy, no? Scratch around, find nothing. Go through all menus and Help, find 
You can start Shared Folders Administration Tool in the following ways:

System menu
        Choose Administration &#9656; Shared Folders.

Nautilus Context Menu
    Press the right mouse button on any local folder and choose Share folder to share or stop sharing the folder.
           
Command line
    Execute the following command: shares-admin.

Except none of these exist -- there is no "Shared folders" option in Admin, there is no option in right-click. See pics.

 I check out a very good video by PCMech on Youtube (pic 3) -- they're def there. But not on my machine.

Installed Samba, no diffs.

What's going on? Why is stuff that's meant to be there by default not?

---

### Post by sisco311 on 2009-07-10
I think, you have to install system-config-samba.

---

### Post by superprash2003 on 2009-07-10
here is a guide [https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

---

### Post by d0dja on 2009-07-10
Hmmm. I'm not sure that is right. According to the other documentation, the folder sharing should already be there. According to that Samba site, you don't need the whole Samba, just the plugin called smbfs.

I checked on add/remove programs and it's not listed, but it is listed in Synaptics. So I installed it. And Samba.

No change. Still no "share folders"...

---

### Post by d0dja on 2009-07-10
Ok, now with the smbfs installed I get "share options" if I right-click on a folder and I can see it from my OS X machine.

But still nothing in System/Administration/ and the share options right-click don't look like the example.

It's also behaving weirdly -  if it's not guest access it gives a weird error, if I set it to "guest access" it can see it,. When I change it back to non-guest access I can still read and write. Except if I write, it reserves permissions.

What a mess.

---

