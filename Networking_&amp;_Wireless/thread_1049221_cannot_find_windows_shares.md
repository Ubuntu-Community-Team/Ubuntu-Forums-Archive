---
title: "cannot find windows shares"
date: 2009-01-24
forum: Networking &amp; Wireless
---

### Post by mistrynitesh on 2009-01-24
I am using the Ubuntu 8.10 installed on live-usb. The pc on which I am using this is attached to a windows network. I want to access a shared folder on one of the other computers on this network. However, when I browse through the file manager to that particular computer and double click on the computer icon (on which that folder is shared), it shows no folder. I tried double clicking on the other computer icon and it showed the folders that are shared on that other computer. I am sure that the folder which I am trying to access is shared as I can access it when I work from Windows on this pc.
Any ideas about how can I access the desired folder? Also, if I can access the folder using command prompt (in that case, which command?)
Thanks in advance!
Nitesh

---

### Post by Iowan on 2009-01-24
[This]("http://www.prash-babu.com/2008/09/how-to-access-windows-shared-folders-in.html") How-To might help - at least to see if shares *can* be accessed.

---

### Post by mistrynitesh on 2009-01-25
Thanks! it worked...
The idea was not to just type the computer name (eg. smb://xxx.xxx.xxx.xxx) but also to include the name of shared folder (eg. smb://xxx.xxx.xxx.xxx/shared folder). On typing this into the location bar of file manager, it prompts for the user-name and password (same as the one while using Windows).Feed the same and you are good to go! I guess just typing the computer name in the location bar does not show the password protected folders.

I also liked the additional options provided while feeding in the username and password, viz., 1) to use the password only once; 2) remember the passowrd until log out; and 3) always remember. Cool!

---

