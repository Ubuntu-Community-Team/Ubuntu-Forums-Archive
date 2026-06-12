---
title: "Sharing files between Vista(Desktop) and Ubuntu(Laptop)"
date: 2009-05-08
forum: Networking &amp; Wireless
---

### Post by Plasma_Snake on 2009-05-08
I want to share the files between the 2 but here's the problem:

[[IMG]http://img23.imageshack.us/img23/4620/nw1.th.png[/IMG]](http://img23.imageshack.us/my.php?image=nw1.png)

[[IMG]http://img80.imageshack.us/img80/2025/nw2.th.png[/IMG]](http://img80.imageshack.us/my.php?image=nw2.png)
What username and password do I have to give?
If I give my root password, its rejected, if I give my Window's User name and password, it too is rejected? What to do?
Scrape it all and go by [this]("http://ubuntuforums.org/showthread.php?t=1151752") method?

---

### Post by Plasma_Snake on 2009-05-08
Bumping for Reply!

---

### Post by albinootje on 2009-05-08
> **Plasma_Snake said:**
> I want to share the files between the 2 
What did you do to enable sharing in Ubuntu ? Did you do that through Nautilus file manager ?

Easier imho is to install ssh on your Ubuntu machine :
```

sudo apt-get install ssh

```
Install WinSCP in MS-Windows : [http://winscp.sf.net/](http://winscp.sf.net/) and use that to copy files over.
You can also install a ssh-server with cygwin in MS-Windows, but that's much harder to install.

By the way, using a root account in Ubuntu is not recommended at all, see here, please read it carefully :
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by superprash2003 on 2009-05-08
disable simple file sharing in windows..

---

### Post by Plasma_Snake on 2009-05-08
> **albinootje said:**
> What did you do to enable sharing in Ubuntu ? Did you do that through Nautilus file manager ?

Easier imho is to install ssh on your Ubuntu machine :
```

sudo apt-get install ssh

```Install WinSCP in MS-Windows : [http://winscp.sf.net/](http://winscp.sf.net/) and use that to copy files over.
You can also install a ssh-server with cygwin in MS-Windows, but that's much harder to install.

By the way, using a root account in Ubuntu is not recommended at all, see here, please read it carefully :
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

> **superprash2003 said:**
> disable simple file sharing in windows..
Why wud I need a Secure Shell utility for File Transfer, wouldn't SAMBA b up for this? The screens I showed are through Nautilius. AS for disabling simple file sharing, if I do so then How would I share the files? I share them between various laptops like of my friends and mine too through Vista as my laptop is in Dual-Boot mode with Ubuntu and Vista.

---

### Post by jawana on 2009-05-08
ok, what you need to do is on the windows machine you must have username and password, if you have not set up the password do that first by going in to control panel/users.

then normally you will need set up a share folder which you can do by browsing to the folder using windows explorer and then right clicking and selecting properties.

in the properties window look for sharing tab and enable, under permission tab give full read and write access to the username you are using for windows box.

also make sure booth windows box and ubunttu are in the same domain/workgroup, defauilt is 'workgroup' in windows.

please refer to [this post]("http://ubuntuforums.org/showthread.php?t=392088") on how to change the  workgroup in ubuntu .

once all the above is done browse your networkk again from ubuntu and when prompted for username and password type your windows username and password , make sure you also type the right workgroup.

hope this help :-)

regards

kash

---

### Post by albinootje on 2009-05-08
> **Plasma_Snake said:**
> Why wud I need a Secure Shell utility for File Transfer, wouldn't SAMBA b up for this?

Samba is, despite various GUI ways of handling it, not so easy to set up as ssh is imho.
For Samba you will normally also need Samba users, while ssh can work with system accounts right away.

---

### Post by mattgyver83 on 2009-05-08
Have you created a samba username and password yet?

sudo smbpasswd -a <USERNAME>
then enter a password

You will use this usn/pass to connect to that specific machine.
 maybe?

sorry, looks like i misunderstood the trouble.  This would be correct if it was the Ubuntu machine that you cant connect to however i guess its the windows machine thats giving you the headache.

Would have deleted the post, but looks like i cant ;l

---

### Post by superprash2003 on 2009-05-09
i meant disable simple file sharing and enable advanced file sharing.. you dont need samba as you are trying to access shares not trying to share folders [http://support.microsoft.com/kb/307874](http://support.microsoft.com/kb/307874)

---

### Post by dandnsmith on 2009-05-09
Expanding that last, you don't need the full SAMBA thing, but you do need smbclient to read the Windows shares.

---

### Post by Plasma_Snake on 2009-05-09
I manually changed my workgroup from Window's default to a custom one. All the drive partitions are open for sharing thus including all files and folders. Here's the screenshot of it.
OK, now when I click on the Network, it goes like this: Network>Windows Share>PANJETA(Workgroup name)>RUDRAPRATAP-PC
Here when I click, it asks for username and password so I give my Window's Username, change the workgroup to PANJETA and type the password too but on clicking "Connect" nothing happens. In Windows too I'm the Administrator and here too I work as Root.

---

### Post by Peter09 on 2009-05-09
If you can see the shares then sambaclient is already installed.

---

### Post by Plasma_Snake on 2009-05-09
This screenshot is from my Windows machine. The /etc/samba directory does exist but nothing like /etc/init.d/samba for service to start or stop. This now how it looks after me changing the workgroup from Inside the Windows but one thing bugging me is that in the login dialog box it asks for Domain and WORKGROUP is written there whilst in Windows there is no Domain, just workgroup.

---

### Post by Plasma_Snake on 2009-05-09
Bumping for Response!

---

### Post by Peter09 on 2009-05-09
Just leave the domain blank

---

### Post by Plasma_Snake on 2009-05-10
Tried that, still nothing. What is wrong here, can anybody tell me???

---

### Post by Peter09 on 2009-05-10
Looking at mine, I put the workgroup name into the domain.

---

### Post by Peter09 on 2009-05-10
Looking at you screenshot, I think root is the wrong username, it may be blocked for other security reasons. The user name should be your username.

---

### Post by Plasma_Snake on 2009-05-10
By Default it too shows my Workgroup name in the Domain field and as for username, wouldn't it b the Window's account's username and password? I tried giving that and logging in as Root too but everything was futile.

---

### Post by Peter09 on 2009-05-10
The issue is  as follows:

If you have opened you windows shares up to no password then windows does not expect a password for access.

On the other hand Samba, by default, expects shares to be password protected, so between windows and Samba confusion rules.

If you have password protected your windows shares then you should gain access through the windows user name password combination.

---

### Post by jonandrews on 2009-05-10
Have a look at my step-by-step illustrated guides to networking between Ubuntu & windows pcs: [www.europe.eclipse.co.uk/Ubuntu](www.europe.eclipse.co.uk/Ubuntu) 

There is also a section on the workgroup issue.

---

### Post by Plasma_Snake on 2009-05-10
The guide is about accessing Ubuntu machine from Windows, whilst here I'm not able to access even the Windows share from Ubuntu machine. 
This is my second post and this time I figured it out and now its working. Earlier whether a root or non-root account of Ubuntu, I was trying to access my windows account as it is, giving my windows password and stuff but since it wasn't happening, I created a standard user account in Windows, gave it all the necessary permissions and settings and then tried to login from that account and it worked! :) :D
Thanks for help u all one word to the wise, please do respond to our mortal n00b prayers and requests a bit more quickly. I know Linux is all learning and doing and learn-by-doing thing but please don't leave us at our own plight, we need u FOSS GODS and dearly in Piracy hit nation like ours where every 2nd Homosapien is a Microsoft Monkey. This time I'm really trying to go the Ubuntu as the Vista on my new laptop keeps giving me BSOD while Ubuntu is rocksteady. Check my other post too where I need help regarding my laptop's GPU drivers for Ubuntu.
Thank you once again for helping me y'all.

---

### Post by Plasma_Snake on 2010-01-08
After a long time, a new but similar problem has cropped up. My laptop is running Windows 7 and 100GB NTFS partition is shared. Its a NTFS share.  Regardless of that earlier when I used click on "Windows Network" icon in Nautilus, all my laptop's drives were visible and accessible but now for past few days the windows network window is blank. It shows no drive or share. I think it was caused by an update but which or what I don't know. The Ubuntu version is 9.10 and I have installed both Samba and smbfs on it but not configured them yet. What iz ze problem now? :(

---

