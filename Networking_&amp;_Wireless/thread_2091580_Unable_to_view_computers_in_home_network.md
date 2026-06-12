---
title: "Unable to view computers in home network"
date: 2012-12-05
forum: Networking &amp; Wireless
---

### Post by Fluttershutter on 2012-12-05
I got ubuntu a short while ago, 12.04, on my laptop. I was hoping to be able to, among other things, view & use files on my Windows 7 desktop. However, so far, I'm not even able to view the ubuntu PC on my windows, and vice versa.

I have done/tried doing the following: 

Make sure sharing is enabled on Win7.
Making sure it's the same workgroup on both computers.
Made sure both computers have shared files.
Made an account on my Win7 with the same username & password as I use on ubuntu.
Installed Samba.

I have tried connecting to the Win7 PC directly through IP. No luck.
Tried following [this]("http://www.7tutorials.com/how-access-windows-7-shared-folders-ubuntu"), but step 3 doesn't work; there is no "places" button, and I can't find "connect to server" anywhere.

Again, when I view the network in either my Win7 or Ubuntu, I can't see the other computer (IE, my win7 sees my win7, my ubuntu sees my ubuntu).

Any help would be appreciated. Any way in which I can share files between my two computers without downloading/requiring a 3rd party. :)

If you're awesome enough to decide to help me, assume the following things:

I don't know anything about ubuntu, windows, or sharing in general.
I've not done anything at all except turn on the computers.

---

### Post by drdos2006 on 2012-12-05
The Samba configuration should be modified to show the Windows 7 workgroup or homegroup.
From a terminal onthe Ubuntu machine, type :
sudo gedit /etc/samba/smb.conf

Enter your password and change this section in Global.
# Change this to the workgroup/NT-domain name your Samba server will part of
      workgroup = MyWorkGroup
Change MyWorkGroup to your Windows7 workgroup name.


There are a couple of ways to get to the section to allow Windows7 sharing.

From the Control Panel -> Network and Internet -> Network and Sharing Center -> Advanced sharing settings -> Choose Homegroup and sharing options-> Change Advanced sharing settings

From the Control Panel -> Network and Internet -> HomeGroup -> Choose Homegroup and sharing options -> Change Advanced sharing settings

Turn on network discovery
Turn on file and printer sharing
Turn on sharing so that anyone with network access can read and write files in the Public folders
Use 128-bit encryption to help protect file sharing connections
Turn on password protected sharing
Use user accounts and passwords to connect to other computers.
Save and close


Right click the folder you wish to share.
Share with -> HomeGroup(Read/Write) or 
Share with -> Specific people
Choose Read/Write plus the Share button.

Once the folder is shared an information dialogue should show at the bottom of the page when the shared folder is highlighted.
It should show State: Shared and Shared With: Your sharing selection(s)

From the Ubuntu machine, Places, Network should now show the Windows machine
Selct the Windows machine and the Windows shared folders should be seen.

Select the folder, enter the user name of the Windows machine, password, remember the password or not and you should be connected.

regards

---

