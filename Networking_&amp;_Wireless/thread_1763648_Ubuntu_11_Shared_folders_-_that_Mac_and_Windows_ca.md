---
title: "Ubuntu 11 Shared folders - that Mac and Windows can see?"
date: 2011-05-20
forum: Networking &amp; Wireless
---

### Post by maxe on 2011-05-20
Hello,

I have set up a shared folder on my Ubuntu computer and I want everyone on the network to be able to see and use those folders, whether they have Ubuntu, Mac OSX or Windows XP.

So far, I am able to view some Mac computers on the network and see the Windows network too - from Ubuntu. However, I am not able to see the Ubuntu computer on Mac or Windows yet.

I think I should be trying to use Samba, but I am not sure how. I used
```
sudo smbpasswd -a [user]
```
to set up a password but I am not sure where to go in Windows or in Mac. Can anyone who is good in those systems tell me how I can see and hook up to my Ubuntu computer on the same network?

On this helpful page ([https://help.ubuntu.com/8.04/internet/C/networking-shares.html](https://help.ubuntu.com/8.04/internet/C/networking-shares.html)) I got as far as the last step and realized here:

> If you are still unable to access the shared folder, check that the folder sharing service is running on the Ubuntu computer:

Press System &#8594; Administration &#8594; Services

Find the Folder sharing service (samba) and ensure that the checkbox next to it is checked

Press Close

I don't *have* a "Services" icon in my Administration drop down menu!

---

### Post by maxe on 2011-05-24
Just wanted to update that I found out how to get this to work.

It was a matter of installing Apache, then turning on individual share folders. As far as accessing them from PCs and Macs, this is what I found out. So you may as well call this one "SOLVED" if you'd like:

Macintosh/OSX:
-=-=-=-=-=-=-=-=-=-=-=-=-=-=-
Click on your desktop and from the top menu bar, select GO > Network
Alternatively, open your hard drive and select "Network" from the side bar
Find "[server]" and open it
Usually, you will see a small almost unnoticeable bar at the top saying "You are logged in as Guest"
If it requires a password, select the button on the right of that bar which says "Login as..."
Enter username and password
Save it in your keychain if you don't want to have to do this every time
Now you should be able to open the folders 
 
 
Windows 7/Vista:
~~~~~~~~~~~~~~~~~~~~~~~~~~~~
Click "Start" and select "Network" from the Start Menu
If you are not allowing file sharing, click on the small bar that appears and choose to "ALLOW" network file sharing.
Select "Yes" when prompted for allowance
Find "[server]" and open it
Open a folder and when prompted for username and password enter user and password
 
 
Windows XP:
+++++++++++++++++++++++++++
Go to "My Network Places" from the Start menu or by opening it from the common locations sidebar of the My Computer window
Select "Microsoft Windows Network" and then "Entire Network" and then "Workgroup" and then "[Server]"
When prompted for a password, enter username and password 
If you cannot see any computers in your Workgroup, your firewall may be on too strong. Windows XP can be finicky (not in an entirely useless way but a frustrating way)

---

