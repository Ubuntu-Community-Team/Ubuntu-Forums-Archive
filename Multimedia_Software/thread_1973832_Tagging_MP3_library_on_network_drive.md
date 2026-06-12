---
title: "Tagging MP3 library on network drive"
date: 2012-05-05
forum: Multimedia Software
---

### Post by graabein on 2012-05-05
Hi, any tips on how to tag my music library over LAN?

I have a headless Ubuntu settop computer in the living room that I can access over ssh or ftp, but some of the albums are not tagged. I've tried **EasyTAG** and **Ex Falso** but they can only read local files. What are my options? I don't really want to detach the drive and mount it locally...

The computer is running **XMBC Live** so maybe there is an add-on for tagging on XBMC?

:popcorn::guitar:

---

### Post by graabein on 2012-05-05
I'm seriously considering [SettingUpNFSHowTo]("https://help.ubuntu.com/community/SettingUpNFSHowTo")

---

### Post by gordintoronto on 2012-05-05
You can make the files look local. I assume you have samba installed and you have shared the folder containing the MP3s.

You just need to do this once: make sure your file manager is set to display hidden files. In your Home folder, scroll down to .gvfs and right-click on it. Select "Make Link." The Link will not be hidden, drag it onto your desktop.

After making sure the folder is mounted, from your application's Open dialogue navigate to Desktop, select "Link to .gvfs" and the network drive will appear in it. One more double-click and you are looking at the shared folder as if it were local.

---

### Post by graabein on 2012-05-05
Oh that's clever. Works like a charm. Thanks!

---

