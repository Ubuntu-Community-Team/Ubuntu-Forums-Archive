---
title: "Cannot network some Win 7 drives with Ubuntu 10.10"
date: 2010-11-02
forum: Networking &amp; Wireless
---

### Post by joy83 on 2010-11-02
My desktop is Win 7 and my laptop is Ubuntu 10.10. As usual I want to share files between the two. They are using the same internet connection, the desktop connected using an ethernet and the laptop wirelessly. 
I have enabled sharing on my E: and F: on the desktop so while they do show up on the Windows network list on my Ubuntu laptop, if I click them it asks me for my Homegroup password which I have no idea what it is(I don't think I ever set a password). I also have "Turn off password protected sharing" checked on windows. Ubuntu has created two icons E and E$ for the E: and F and F$ for the F:. When I click E it says "Unable to mount location Failed to mount Windows share" and if click E$ then it is asking me for my HOMEGROUP password. 

On the other hand the folder "Users" in windows is also shared and I can access it from Ubuntu without it asking me for any password. This is where I don't understand as to why I can share one folder but having problems viewing my other drives.

Just for information sharing a ubuntu folder in windows is working fine, I have enabled sharing on one of my folders in ubuntu and it is visible in windows and I can access all the files.

Any help would be appreciated.

---

### Post by andysom25 on 2010-11-04
I am having a very similar problem as well, plus I am a noob I will admit. 
At the moment I can access all my ubuntu shared files from my windows 7 laptop but whenever I try to access windows shares from my ubuntu desktop I am prompted for a user name and password and once I fill that out it does not do anything it just sits there and ask for the password again.
Any help would be wonderful either for what I have to do on the windows side or ubuntu

---

### Post by dforthman on 2010-11-04
Disable password protected sharing

Start->Control Panel->Network and Internet->Network and Sharing Center

Select **Change advanced sharing settings** in the left column of the Network and Sharing Center

Expand the network you want to disable password protected sharing on by clicking the down arrow on the right of the profile (Labeled current profile).
Select **Turn off password protected sharing** and then click **Save changes**.

Steps taken from [http://maximumpcguides.com/windows-7/disable-password-protected-sharing/](http://maximumpcguides.com/windows-7/disable-password-protected-sharing/) since I am not currently on Win7 and don't remember the exact steps

---

### Post by andysom25 on 2010-11-04
just tryed that, although for some reason it still ask me for a password, am I doing something wrong? I can access another computer on the network but not my windows 7 laptop ? should I restart ubuntu after changing these settings, or reconnect?

---

### Post by dforthman on 2010-11-05
Is the folder you want to share set up correctly? Correct permissions set?

Go to the folder's properties and click the Sharing tab.
In Group or user names, hit Advanced Sharing.
Be sure it is set to "Share" and choose "Permissions"
If "Everyone" is not listed, click "Add" type "Everyone" and hit "OK". 
Assign Everyone full control. Hit OK. and close the sharing window.
Move to the Security tab (if listed) and click Edit.
Click 'Add' and add Everyone to the list of users.

If you want to be quick and dirty, assign "Full Control" to the Everyone  user. If you want to limit what "Everyone" can do, choose the lowest  permissions needed.

Hit "Ok" and try accessing the windows share again.

---

