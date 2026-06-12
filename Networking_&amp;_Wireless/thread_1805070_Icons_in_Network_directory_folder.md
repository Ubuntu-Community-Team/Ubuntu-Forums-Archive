---
title: "Icons in Network directory/ folder?"
date: 2011-07-15
forum: Networking &amp; Wireless
---

### Post by j*tech on 2011-07-15
I am sharing my wireless connection (thru router) with a friend, and recently I checked the Network folder and his PC showed up as an icon, along with a Windows Network.  Does this mean he has access to my Ubuntu system and files?  I have ufw set to deny incoming, remote access turned off, and file sharing turned off.  What is the purpose of the Network folder?  Is it showing possible connections?  Or established ones?  Thanx.

---

### Post by jmoorse on 2011-07-16
He will not have access unless you:

1. Install samba
2. enable sharing on a folder and 
3. give them a username/password or set up the share to allow guest access

This folder is showing possible connections, much like legacy windows 'Network Neighborhood'

---

### Post by j*tech on 2011-07-20
Kool, thanx man...

---

### Post by capscrew on 2011-07-20
> **j*tech said:**
> I am sharing my wireless connection (thru router) with a friend, and recently I checked the Network folder and his PC showed up as an icon, along with a Windows Network.  Does this mean he has access to my Ubuntu system and files?  I have ufw set to deny incoming, remote access turned off, and file sharing turned off.  What is the purpose of the Network folder?  Is it showing possible connections?  Or established ones?  Thanx.

To be a little more specific: what you are seeing is your friends machine because by default, Ubuntu installs Samba *Client* software.  His machine has a SMB/CIFS server running (either Windows File sharing or Samba).  He is at risk not you.

---

