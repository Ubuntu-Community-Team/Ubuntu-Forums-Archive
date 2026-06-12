---
title: "File server???"
date: 2009-06-02
forum: Networking &amp; Wireless
---

### Post by moebob24 on 2009-06-02
So I want to turn my Linux box into a file server for my whole house to use. Should I install the sever edition of Ubuntu? Also, I would like to have it either hardline or wireless accessible with a WEP key for wireless. Is there anyway to do this or something similar to the PC. I would also still like to have usability of the computer, meaning still use it as if I didn't make a file server. 

If anyone has a link to a site that talks about this it would greatly be appreciated.   

Thanks in advance. I'll be back in a bit to respond...

---

### Post by Iowan on 2009-06-02
You can add the server packages to a desktop install. If you're gonna put a standard desktop back on it anyway, it seems (in my opinion) unnecessary to re-install the server version, then re-install a desktop over it... although you didn't specifically say that the "Linux box" is an "Ubuntu box".
[Here]("https://help.ubuntu.com/community/Internet/ConnectionSharing") is a help page for connection sharing.  Near the end is a [link]("https://help.ubuntu.com/community/WifiDocs/ShareEthernetConnectionThroughWireless") for sharing through wireless.

---

### Post by StooJ on 2009-06-02
> **moebob24 said:**
> So I want to turn my Linux box into a file server for my whole house to use. Should I install the sever edition of Ubuntu?

Not necessarily. A desktop install can be a file server quite happily, so there would be no need to reinstall to get a fileserver up and running. Only possible point would be that because want your fileserver to be accessible all the time, and a desktop install will be driving a GUI, it will probably draw more electricity. Even if the screen is switched off, I would imagine the graphics card would be doing more work.

> **moebob24 said:**
> Also, I would like to have it either hardline or wireless accessible with a WEP key for wireless. Is there anyway to do this or something similar to the PC.
Not sure if I understand this. Obviously, you want the fileserver networked, and you can have it physically connected (more reliable, faster, less power drain) or wirelessly. If you must have it wireless, I'd recommend upping the security to WPA if possible. Far more secure.

> **moebob24 said:**
> I would also still like to have usability of the computer, meaning still use it as if I didn't make a file server. 

Then you'll want to keep the desktop installation with Gnome. Don't bother reinstalling the server edition.

> **moebob24 said:**
> If anyone has a link to a site that talks about this it would greatly be appreciated.

For a simple file server, all you really need is samba.

Have a look at [https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba) to start with.

> **moebob24 said:**
> Thanks in advance. I'll be back in a bit to respond...
No problem

---

### Post by moebob24 on 2009-06-02
> **Iowan said:**
> You can add the server packages to a desktop install. If you're gonna put a standard desktop back on it anyway, it seems (in my opinion) unnecessary to re-install the server version, then re-install a desktop over it... although you didn't specifically say that the "Linux box" is an "Ubuntu box".
[Here]("https://help.ubuntu.com/community/Internet/ConnectionSharing") is a help page for connection sharing.  Near the end is a [link]("https://help.ubuntu.com/community/WifiDocs/ShareEthernetConnectionThroughWireless") for sharing through wireless.

The thread was tagged as Ubuntu so I thought it would be redundant to state what it is. Thanks for the links.

---

### Post by Iowan on 2009-06-02
Yeah... sorry, I missed that.  I tend to pay more attention to the title.  Once I've opened the thread, I can't see the tag list. Just didn't want to assume Ubuntu - as you might have been considering changing from Redhat, Suse, or another distro.

---

