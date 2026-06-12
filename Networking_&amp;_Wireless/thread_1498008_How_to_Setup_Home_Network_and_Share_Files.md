---
title: "How to Setup Home Network and Share Files?"
date: 2010-05-31
forum: Networking &amp; Wireless
---

### Post by dsky97 on 2010-05-31
Hi All, I just switched over to ubuntu 10.04 LTS Netbook Edition from Windows XP and I am wondering how to setup a home network and share files with other computers in my house? I tried going to Preferences -> Personal File Sharing.  But the options for 'Share Files over the Network' is grayed out.  The message is "This feature cannot be enabled because the required packages are not installed on your system."  Can someone please help?  Thanks.

-danny

---

### Post by cusinndzl on 2010-05-31
Try installing Samba by typing in "sudo apt-get install samba".

---

### Post by dsky97 on 2010-05-31
I did that. Then what do I do?  I am new to Linux so I am not familiar with working with the Terminal. Is there a GUI with Samba?

---

### Post by cusinndzl on 2010-05-31
You can get Webmin and use that as a GUI. 

Open up the terminal and type in what is below. 

```
wget http://prdownloads.sourceforge.net/webadmin/webmin_1.510-2_all.deb 
```

That gets the Debian package. Now you will need to install it. 

```
dpkg --install webmin_1.510-2_all.deb
```

You might get an error message about dependencies, if so type in what is below. 

```
apt-get install -f
```

Now Webmin should be installed, so go to [https://localhost:10000](https://localhost:10000) in your browser and login with your username and password. Click refresh modules. Then Samba should be under servers.

---

### Post by Morbius1 on 2010-05-31
It depends on how complicated your requirements are. The easiest way is through Nautilus ( called Nautilus-share ):

Open Nautilus
Right click on a folder in your home directory that you want to share
Select "Sharing Options"
Select "Share this Folder", "Allow others to create and delete files", and "Guest Access"
Select "Create Share"

It will ask you if you want it to add permissions - you do.

You've just created a public share.

[COLOR=Blue]NOTE:[/COLOR] "Personal File Sharing" is not Samba - it's something completely different. It will allow you to share only one folder: /home/your_user_name/Public. If that's all you want let us know.

---

### Post by dsky97 on 2010-05-31
Thanks guys for all your input.  

What I want to do is be able to access the files on my desktop or laptop, both of which are running Ubuntus 10.04, from other computers and the media player in my network.  I installed Samba through the Ubuntu Software Center in both machines.  Then I added the directories that I wanted to share and allow everyone to access.  I was able to share the folders that way. Is Nautilus more appropriate for this purpose?

---

### Post by cusinndzl on 2010-05-31
> **dsky97 said:**
> Thanks guys for all your input.  

What I want to do is be able to access the files on my desktop or laptop, both of which are running Ubuntus 10.04, from other computers and the media player in my network.  I installed Samba through the Ubuntu Software Center in both machines.  Then I added the directories that I wanted to share and allow everyone to access.  I was able to share the folders that way. Is Nautilus more appropriate for this purpose?

I don't know, I've always used Samba and I've had no problems with it.

---

### Post by Morbius1 on 2010-05-31
> I installed Samba through the Ubuntu Software Center in both machines.   Then I added the directories that I wanted to share and allow everyone  to access.  I was able to share the folders that way. Is Nautilus more  appropriate for this purpose?Now you've got me confused.

First: Nautilus-share is Samba. Been part of Samba for years. It's just a different way to create shares and a different location for the share definitions.

Second: If you already created shares what is the purpose of your post. It sounds like you've accomplished what you seek using what is now called  Classic-shares.

Are you experiencing problems with your setup? If you are then post the output of the following command and let's se if there is a problem with smb.conf itself:

```
testparm -s
```

---

### Post by dsky97 on 2010-05-31
no no no, when I posted my question, i wasn't able to create share at all. but after getting some inputs from you all, I tried using samba and it worked. so i was wondering whether it would have been easier or more appropriate using nautilus-share. but now you are saying nautilus-share is samba. i am confused. what do you mean by that?

---

### Post by Morbius1 on 2010-05-31
There are three ways ( excluding NFS, ssh and such ) to share folders in Ubuntu:
 
**1st: Personal File Sharing**: [http://ubuntuforums.org/showthread.php?t=1473760](http://ubuntuforums.org/showthread.php?t=1473760)
This is not samba and from my experience with it there is a reason  Ubuntu ships this thing disabled :wink: You need to install Apache2.2.bin and libapache2-mod-dnssd to get it to work. You can only share one folder and you can if you want make the share password protected.
[B]
2nd: Samba Classic-shares[/B]:
This is the way it has always been done and  is still the most flexible and configurable of the two samba methods  available. There's a lot of documentation about this method on the web  and some of it is actually accurate. [COLOR=Blue]It's shares are defined in smb.conf.[/COLOR]

**3rd: Samba Nautilus-shares**. 
This is the newest form of samba sharing ( I think it's been there since Gutsy but it's been part of Samba - where it's called usershares - for years ). It's purpose is to allow a user to share any folder he owns only by using Nautilus itself and without becoming root. It has it's limitations but I would argue that for the average user who wants to create a simple guest or authenticated share it's the easiest to use. [COLOR=Blue]It's shares are defined in /var/lib/samba/usershares.[/COLOR]

You can use both Classic and Nautilus shares at the same time but they may conflict with one another so unless you keep careful track of what method is being used on what folder, it's best to use one samba method or the other -  at least in the beginning. It's not that that one samba method is better than the other or that one is prefereed over the other, they're just different ways to accomplish the same thing.

I apologize if my previous posts were incoherent - this subject is complicated enough without me adding to the confusion :)

---

### Post by Morbius1 on 2010-05-31
Duplicate - sorry

---

### Post by dsky97 on 2010-05-31
Morbius,

Thanks for getting me started on my ubuntu journey.  I don't understand everything you said perfectly properly due to my own lack of technical experience.  After years of getting used to using Windows, one sort of take GUI (point and click) for granted.  So I have to try using the terminal.  But I will experiment with both method and see if I can figure out the differences.  Thanks again.

---

### Post by Morbius1 on 2010-06-01
For a long time Windows user the Samba Nautilus-share method is the equivalent to Windows "Simple Sharing" - where you can just right click a folder and tell Windows to share it.

---

### Post by rg_stephens on 2010-06-01
> **Morbius1 said:**
> There are three ways ( excluding NFS, ssh and such ) to share folders in Ubuntu: ....

I don't mean to hijack your thread, but does anyone know of a tutorial or explanation of how to get networking to work in 10.4? Samba or otherwise. I've read the forums, installed the packages, and it only halfway works, sometimes. When it works, I get a *general i/o error* when opening with OpenOffice

---

### Post by Morbius1 on 2010-06-01
> **rg_stephens said:**
> I don't mean to hijack your thread, but does anyone know of a tutorial or explanation of how to get networking to work in 10.4? Samba or otherwise. I've read the forums, installed the packages, and it only halfway works, sometimes. When it works, I get a *general i/o error* when opening with OpenOffice
From your other post on this subject you're getting the General I/O error when using "Personal File Sharing".

Why not try samba instead. Want a HowTo on Samba Nautilus-share? See post #5 above.

---

### Post by rg_stephens on 2010-06-01
Ok, trying with Samba:

Tells me "Unable to Mount Location"

Installed Samba on both computers. Same thing.

---

### Post by Morbius1 on 2010-06-01
Open a terminal and type:
```
 nautilus smb://192.168.0.100
```*[COLOR=Blue]Change 192.168.0.100 to the ip address of the machine you're trying to access.[/COLOR]*

---

### Post by v1ad on 2010-06-01
i do that and it says wrong password, even though it is right.

---

### Post by rg_stephens on 2010-06-01
Error: Failed to receive share list from server

---

### Post by rg_stephens on 2010-06-01
But using the other computer to mine, it shows me the print service, but not the folder I just shared.

---

### Post by Morbius1 on 2010-06-01
vlad and rg_stephens, you guys really need to start your own threads.  The original poster has no problems accessing his shares, his is more a methods question.

When you start your threads you might want to provide the output of the following commands to save time:

```
net usershare info
testparm -s
smbtree
findsmb
nmap -sT 192.168.0.100/22
```[COLOR=Blue]Change 192.168.0.100 to the ip address of the machine you're using.[/COLOR]

And vlad you might want to tell in your post if you did an "smbpasswd -a username" to prove that you created a password for samba.

Just a suggestion

---

### Post by rg_stephens on 2010-06-01
Thanks. I found that Skype works amazingly well for file transfer, and it configures itself, so I'm happy.

---

### Post by Dragmah on 2010-11-13
> **cusinndzl said:**
> You can get Webmin and use that as a GUI. 

Open up the terminal and type in what is below. 

```
wget http://prdownloads.sourceforge.net/webadmin/webmin_1.510-2_all.deb 
```That gets the Debian package. Now you will need to install it. 

```
dpkg --install webmin_1.510-2_all.deb
```You might get an error message about dependencies, if so type in what is below. 

```
apt-get install -f
```Now Webmin should be installed, so go to [https://localhost:10000](https://localhost:10000) in your browser and login with your username and password. Click refresh modules. Then Samba should be under servers.

I am trying the second part 2 - install file - but it comes up with error

dpkg: requested operation requires superuser privilege

I have only just installed Ubuntu on this computer and it only has th  one login?? I tried the third prompt you had - get install- but it came  up with

E: could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

Please help... Just to let you know, i am trying to set up file sharing  so that this can have all my files and i can access them from my HTPC in  the living room. Connections are all good, just need the file sharing  setup.

Thanks in advance..

---

### Post by Dragmah on 2010-11-13
Sorry, fidured this out myself, was having one of my wifes blonde pregnant moments, to top it off i had my son on my lap, great influence i am to technology :D

---

### Post by p_motch on 2010-11-13
> **dsky97 said:**
> I did that. Then what do I do?  I am new to Linux so I am not familiar with working with the Terminal. Is there a GUI with Samba?

Then go to "System" --> "Administration" --> "Samba". The "Samba Server Configuration" GUI will open and you can create Samba shares in there. I'm assuming that's what you want to do, share a folder on your netbook with the rest of the Windows network. If you want to browse other Windows computer in your network, go to "Places" --> "Network". Hope this helps.

---

