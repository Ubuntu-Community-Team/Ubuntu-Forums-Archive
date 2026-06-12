---
title: "Failed to mount Windows share"
date: 2013-07-14
forum: Networking &amp; Wireless
---

### Post by raedmohammadi on 2013-07-14
hello guys 

 i want to access windows shared folder in ubuntu , i installed "samba system-config-samba python-glade" then restart the computer now when i open the Nautilus - network i can see all the folders sharing on the network

[IMG]http://i.imagebanana.com/img/bgsge40w/Selection_001.png[/IMG]

 but some of them i can't access to it ! every time i open a folder there is an error message Unable to mount location , Failed to mount Windows share

[IMG]http://i.imagebanana.com/img/98lv9ldc/Untitledwindow_002.png[/IMG]

in windows 7 i do all the steps here exactlly 
[http://www.7tutorials.com/how-customize-network-sharing-settings-windows-7](http://www.7tutorials.com/how-customize-network-sharing-settings-windows-7)

BTW , what is the difference between these two icons ! 
the icon on the right i can access to this folder , the other one i can't 

[IMG]http://i.imagebanana.com/img/q7mifnoi/Selection_003.png[/IMG]

---

### Post by raedmohammadi on 2013-07-14
any idea guys ?

---

### Post by PaulW2U on 2013-07-14
I've used [Howto: Fix Windows share browsing issues](http://ubuntuforums.org/showthread.php?t=1169149) on these very forums dozens of times and never needed to look elsewhere.

I'm not sure the guide that you linked to actually deals with the Linux side of things.

---

### Post by Morbius1 on 2013-07-14
** Everthing with a "$" at the end is a hidden share ( sometimes called an administrative share ) and is Windows way of hiding a share from network clients. The reason it's listed in Linux is because the samba client isn't Windows. It's not meant to be accessed by mortals and it should not be visible on a Windows client.

** THe FFOutput appears to be a share that has not been mounted.

** THe kekkita smith share appears to be a share that you have mounted.

** "Unable to mount location" is usually a permissions error. You may have permissions to access the share but you do not have permissions to access the underlying folder that is shared.

---

### Post by Morbius1 on 2013-07-14
[COLOR=#0000cd]*EDIT: That last statement may need some  explanation since it sounds like gibberish.  You can reproduce that  exact same error message on your own Linux system by:*[/COLOR]

[1] Creating a Samba share of a folder and allowing guest access.
[2] Then changing the Linux permissions on the folder itself restricting  access only to you ( i.e., chmod 700 /path/to/shared/folder ).

When you go to Browse Network you will pass the Samba test since you are  a guest but you will get the exact same error message: "Unable to mount  location. Failed to mount Windows share".

The client can see the share - Samba lets the client pass - but Linux  prevents the client access. Windows does the same exact thing only it's  more intuative in Linux.

---

