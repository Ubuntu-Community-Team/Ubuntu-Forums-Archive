---
title: "Setting up a network - file and printer sharing 2 Ubuntu machines"
date: 2013-05-19
forum: Networking &amp; Wireless
---

### Post by jukingeo on 2013-05-19
Hello All,

I am having a bit of an issue in regards to setting up two computers on a small network, both on Ubuntu 12.04.   One is Gnome Ubuntu, and the other machine is Ubuntu Studio which uses Xfce.

Now in the past the first computer, which is the Gnome Ubuntu one, was strictly a Windows XP machine and I was able to connect to a network.  The Ubuntu Studio machine was always a dual boot that could go to Windows XP or Ubuntu Studio.

I noticed that when BOTH machines are running Ubuntu that in the network places, I only see one icon that says 'windows network'.  I figured that isn't right.  The printer is set up on the Gnome Ubuntu machine and I am trying to network that printer to the Ubuntu Studio machine.    I would also like to set up a shared folder as well.

I would appreciate any assistance in regards to this issue.

**Edit**:  Ok, I managed to find a solution in regards to the printer sharing issue with this document here:

[https://help.ubuntu.com/community/NetworkPrintingWithUbuntu](https://help.ubuntu.com/community/NetworkPrintingWithUbuntu)

However, I am still having difficultly in setting up a shared folder for the network.   I tried my wife's computer which uses Nautlius for the file manager, and naturally I opened that with sudo in the terminal.   I CAN set the folder for sharing, but once set and I exit from nautilus and go to the folder through the taskbar, the folder shows as not shared.

Next I tried the reverse and tried to set up a shared folder on my computer.  Now I am using Ubuntu Studio, and for version 12.04 I have Xfce as the desktop.   So I tried it's file manager which is Trunar and setting up the shared folder through that, however, the option doesn't even show up on the drop down.

I am surprised that setting up a shared folder seems to be this difficult.   However, in the past I usually set up a shared folder that was on a Windows machine.  I never tried to do it vice versa.

Once again, any assistance would be appreciated.

Geo

Thank You,
Geo

---

### Post by Morbius1 on 2013-05-20
> I noticed that when BOTH machines are running Ubuntu that in the network  places, I only see one icon that says 'windows network'. I figured that isn't right.
You are using Samba which is the UNIX / Linux / Every-other-OS-except-Windows version of SMB which is a Windows file sharing protocol. That's why you see "Windows Network" and your Samba servers should show up under that folder. The people who put these kind of things together for Linux think Samba is just for Windows.
> However, I am still having difficultly in setting up a shared folder for  the network.   I tried my wife's computer which uses Nautlius for the  file manager, and naturally I opened that with sudo in the terminal.   I  CAN set the folder for sharing, but once set and I exit from nautilus  and go to the folder through the taskbar, the folder shows as not  shared.
There's nothing "natural" about invoking Nautilus with a sudo - it should be gksu. There's a couple of issues here. If you are using Nautilus to create a samba share then you are using nautilus-share which in turn creates the share using the Samba Usershare process. If you create the share in Nautilus as gksu then the share emblem on the folder changes. If you then open Nautilus as a regular user the share emblem is gone - that's the "user" part of ***[COLOR=#0000cd]user[/COLOR]**share*. The other issue is a 4 or 5 year old bug where the share emblem disappears even for the user that created the share based on humidity levels and sun spot changes. Doesn't seem to be any way to fix it so my recommendation is to use the following command:
```
net usershare info --long
```
The output will tell you if you created any shares through Nautilus and how they are configured. Any folder missing the share emblem does not necessarily mean it's not shared.
> Next I tried the reverse and tried to set up a shared folder on my  computer.  Now I am using Ubuntu Studio, and for version 12.04 I have  Xfce as the desktop.   So I tried it's file manager which is Trunar and  setting up the shared folder through that, however, the option doesn't  even show up on the drop down.
You are correct. There is no way to create a Samba Usershare through Thunar. This was not always the case. Back in the Golden Age of Linux there was a package called thunar-shares-plugin that gave Thunar the same ability as Nautilus in regards to Samba shares but that's gone now. Your only recourse is to set up the share using the smb.conf way. One GUI that allows you to do this can be installed:
```
sudo apt-get install system-config-samba
```
It should show up in XFCE's menu if not then invoke it this way:
```
gksu system-config-samba
```

---

