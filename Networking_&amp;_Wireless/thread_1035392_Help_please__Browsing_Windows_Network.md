---
title: "Help please:  Browsing Windows Network"
date: 2009-01-09
forum: Networking &amp; Wireless
---

### Post by Jackie_Treehorn on 2009-01-09
I had this problem with my last version of Ubuntu.  I'm on 8.10 now.

I have a few machines on my LAN.  One Ubuntu laptop and the others are Windows boxes.

I can not browse the shares on those machines within Ubuntu.

My steps thus far:
Clicking Places>Network>Windows Network brings up my Lan WORKGROUP.
Clicking Workgroup shows me my windows boxes.  One of them is MEDIA-CENTER.
Clicking MEDIA-CENTER does nothing.  It does not show me the shares that are on that box.

If I further type smb://media-center/music/, I can now browse my shared music folder on media-center.

My question is why will Ubuntu not bring up a list of all shares on media-center?  Why must I know what the share folders are and have to type them?

Am I doing something wrong?

Thanks,

Jackie

---

### Post by frankelr on 2009-01-09
Hi, its not you its some bug between nautilus...samba...gnome.  Read about bug # 207072.  Don't give up reading until nearly the end since there are some workarounds... one of which you already found


Bob

---

