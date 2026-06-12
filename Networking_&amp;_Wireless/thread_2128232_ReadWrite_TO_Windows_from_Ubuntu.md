---
title: "Read/Write TO Windows from Ubuntu"
date: 2013-03-22
forum: Networking &amp; Wireless
---

### Post by Ubu_Fester on 2013-03-22
My linux box is running Mythbuntu 12.04 which uses the xfce desktop environment. My goal is to create a connection/shared drive from linux to Windows.  

What have I done so far?  I have samba installed and I can connect from my Win7 PC _**TO**_ my linux  box.  IOW, I can read/write from Windows to a share on my mythbuntu box.  But  for some reason, my linux box can't see my Win7 PC -- so I can't create a connection/shared drive from linux to Windows.  From a  linux terminal I can ping to Win7 box successfully.  

I think I'm stuck on either:

1) My login names are different on the two boxes and I'm probably not  creating my Windows share correctly.  My Win7 login is "John" and my  linux box is "JSmith".  Windows will not let me create a share for  "JSmith"

2) Because I'm running mythbuntu, I do not have a default Network icon  setup by default. As some of you are aware Mythbuntu uses xfce/thunar,  not nautilus.  I believe nautilus is used in the general Ubuntu installation and has some additional tools/network settings  that makes it easier than what the Mythbuntu install has. 

3)  Do I need samba client  installed? I installed Samba (server?) about 6 months ago, so I forgot if that installation included the samba client.  When I navigated to the terminal to install the client, I received an install error.  After this happened I decided I better post this message before I screw anything up.

Thanks in advance

---

### Post by Ubu_Fester on 2013-03-24
bump

---

### Post by ahallubuntu on 2013-03-24
~

---

### Post by Ubu_Fester on 2013-03-27
I've got two Win7 PCs (desktop/wired and laptop/wireless) and have no problem creating shares and moving files across the two Win7 boxes.  I am using the homegroup networking capability within Win7 to do this.

I don't think I have a firewall or router (block) problem, since I can do the following:
  - I can use my main Win7 desktop PC to navigate and read/write files to a volume that is on the Ubuntu (mythbuntu) box
  - Using my main Win7 desktop, I can stream mythtv recordings that are saved on my Ubuntu box
  - I can use my Android phone to stream mythtv recordings saved on my Ubuntu box
  - On my Ubuntu box, I can ping my Win7 desktop and/or my Win7 laptop.

However with my Ubuntu box, I can't "see" any of my Win7 PCs, nor can I open up a shared Win7 folder.  I see a lot of threads across the internet with users having similar issues and believe this is a common use case -- I'd like to get this to work.

---

