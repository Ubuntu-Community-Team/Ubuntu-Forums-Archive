---
title: "(Solved) Share files and folders with other computers"
date: 2009-01-20
forum: Networking &amp; Wireless
---

### Post by stSpringer2003 on 2009-01-20
This worked for me Ubuntu 8.04
[https://help.ubuntu.com/7.10/internet/C/networking-shares.html](https://help.ubuntu.com/7.10/internet/C/networking-shares.html)

You can share files and folders with other people on your network.

 Press System &#8594; Administration &#8594; Shared Folders

You may receive a message which says Sharing services are not installed. If this is the case, ensure that the two checkboxes in the message box are checked and press Install services. Sharing service support will then be downloaded and installed; this may take a while.

Select the Shared Folders tab and press Add

Select the location of the folder you wish to share by changing the Path option

Choose Windows networks (SMB) from the Share through option

Enter a name and comment for the shared folder

If you would like people accessing the shared folder to be able to add, change and remove files in the folder, uncheck Read only. If you leave Read only checked, people will only be able to view files in the folder

Press OK to make the shared folder available. Other people on the same network (LAN) as you should now be able to access the folder

See the Shared Folders Administration Tool manual for more information on managing network shares.

Accessing shared folders on Windows
If you would like to access a shared folder hosted on an Ubuntu computer by using computers running Windows, you may have to perform some additional steps:

Press Applications &#8594; Accessories &#8594; Terminal to open a Terminal

Type sudo smbpasswd -a username, replacing “username” with your own username. Press Return to run the command.

   
![https://help.ubuntu.com/7.10/images/admon/note.png](https://help.ubuntu.com/7.10/images/admon/note.png)! You can find out what your username is by typing *whoami* into the Terminal and then pressing Return
 

Enter your password when prompted with “[sudo] password for username:” and press Return again.

When prompted with “New SMB password:”, enter the password that you would like to use to access the shared folder and then press Return. You can leave the password blank if you like, which will allow anyone to access the shared folder.

When prompted with “Retype new SMB password:”, enter the password that you just entered and then press Return

You should now be able to connect to the shared folders on the Ubuntu computer

Problems connecting to shared folders in Windows
If you are unable to connect to a shared folder using Windows, try using the IP address of the Ubuntu computer rather than its host name to access the share:


 Press System &#8594; Administration &#8594; Network Tools 

and select the Devices tab

Select the name of your network connection from the Network device option list (for example, “eth0”). If you have several network connections, you may have to try this several times.

Make a note of the number in the IP address column. It should consist of four numbers separated by dots (for example, “192.168.2.10”)

On the Windows computer, select Start &#8594; Run and type \\ipaddress in the text box, replacing “ipaddress” with the IP address of the Ubuntu computer

Press OK to connect to the shared folder

If you are still unable to access the shared folder, check that the folder sharing service is running on the Ubuntu computer:

Press System &#8594; Administration &#8594; Services

Find the Folder sharing service (samba) and ensure that the checkbox next to it is checked

Press Close

---

### Post by LinuxRocks713 on 2009-01-24
In 8.04 and above (System->Administration->Network Shares has been removed), use this guide to create network shares:

[http://www.compdigitec.com/labs/2008/11/30/setting-up-a-samba-share-in-ubuntu/](http://www.compdigitec.com/labs/2008/11/30/setting-up-a-samba-share-in-ubuntu/)

---

