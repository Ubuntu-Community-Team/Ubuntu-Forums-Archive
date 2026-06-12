---
title: "Share refuses to work"
date: 2009-02-05
forum: Networking &amp; Wireless
---

### Post by oldcelt on 2009-02-05
I've installed Ubuntu dual boot with XP.  The network (ethernet) seems to work ok and I can see other machines on the LAN.  Internet connection works fine.

However, when I try to set up a share on a folder created within the /home partition it doesn't work.  Every time I try to create a share it says "Sharing service is not installed".  I click on "install service" and it then says "restart session".  

I do that but when it's restarted and I try to share a folder it goes through the same routine again!

I tried making a folder on the desktop and the same thing happens.

What is happening here - I'm just going around in circles! :(

Ken

---

### Post by Iowan on 2009-02-05
I presume the service it wants/needs to install is Samba. [Here]("https://help.ubuntu.com/community/SettingUpSamba") is a help page for setting up Samba - hope it helps.

---

### Post by oldcelt on 2009-02-06
Bingo!  Many thanks.

I've moved the Ubuntu machine from the default 'Workgroup' to my LAN workgroup.  'Workgroup' is now empty - how can I remove it please?

Ken

---

### Post by Another Monkey on 2009-02-06
"Workgroup" should disappear on its own.  It is just Windows/Samba-service remembering that something used to be in that.

After a while they should realise that nothing is there any more and drop it.  That's been my experience anyway.

I am sure someone who knows a lot more would be able to tell you how to specifically remove it.

---

### Post by oldcelt on 2009-02-06
You're absolutely right.  'Workgroup' has now disappeared.

TVM

---

