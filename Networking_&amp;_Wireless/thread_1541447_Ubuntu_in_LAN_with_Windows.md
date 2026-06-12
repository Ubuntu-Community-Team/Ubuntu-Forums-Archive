---
title: "Ubuntu in LAN with Windows"
date: 2010-07-29
forum: Networking &amp; Wireless
---

### Post by Jedit Ojanen on 2010-07-29
Hi, I'm using Ubuntu and I'm in LAN with my friends who are using Windows Vista.

My problem is that I don't know how to reach the friends' shared folders. *Places ->  Network -> Windows Network* throws the following error: **"Unable to mount location. Failed to retrieve the shared list from server"**. I've tried to solve the problem by googling the error code with no help.

LAN works great between the Windows computers and my Internet is working just fine. Think this is some basic stuff I've missed somehow. I'm not familiar with Ubuntu network.

---

### Post by Unterseeboot_234 on 2010-07-29
Sounds like the Vista box doesn't have group ownership permissions to the folder, the chown. That is, the folder was not created by an administrator account. That can prevent failed to return share list. But so can the wrong partition format, example: exFAT.

First, make sure you have Samba
sudo apt-get install samba

The other thing you should know is that sharing was easier in XP --  because XP is WinNT with an interface, then a little harder in Vista and Win7 is most fun of all. Google: share vista with ubuntu, here is one 'hit'

**[share vista with ubuntu]("http://ubuntuforums.org/showthread.php?t=373917")**

The thing that MUST happen is your Linux box is a member of the same Workgroup of the Vista box(es). Much info on the web about how to gedit the samba.conf file.

Your friends folder should reside on a hard drive partition that has been formatted NTFS or FAT32 and they mark the folder to 'share' with guests. exFAT will not work, NTFS will allow larger file sizes and larger partitions.

It is easier if you make a partition on the Win boxes with gparted and format that to NTFS. Clicking on a new folder while in Linux and tell it to share will cause Ubuntu to request to download winbind. Let it do so.

Once you have the Workgroup, and the folder's permission to share you can use Nautilas from [menu] Places -> Network and that will bring up a window with icons. You want the folder with the wires. Open that, navigate to your shared folder.

Seek googles like I outline above. Otherwise there are a variety of troubleshooting techniques, which do work, but you have to keep it all straight in your head about what is happening as you begin to edit some files on Ubuntu.

File sharing started working for me after I did sudo gedit /etc/samba/smb.conf and changed the workgroup name to match the Win box. Later, I got two dual-boot boxes to configure shares in both directions after spending about a week on the problem with Win7.

---

### Post by noobunto on 2010-07-29
Is there any easy GUI-driven interface to allow easy Ubuntu/Windows co-existence on a home LAN ?

I'm using a notebook so 'sometimes' it's not on the LAN and shouldn't hang-up/fail if the network drives I want to access aren't 'there.'  Also, I don't want to have to click through so many levels in Nautilus to get to the drives.  I want them mounted and on the file system at start-up, available for use.

---

### Post by Morbius1 on 2010-07-29
Unterseeboot_234,

Wow, I feel compelled beyond good sense to point out a few problems:
> The thing that [COLOR=Blue]MUST[/COLOR] happen is your Linux box is a member of the same Workgroup of the Vista box(es) Had you said "it's best to" or "it's easier if you had" or " because of how I set up my network I " but you used the word "MUST". I have 4 workgroups in my network and everybody can see everyone else. 
> It is easier if you make a partition on the Win boxes with gparted and format that to NTFS I'll admit this is more prejudice on my part than anything else but I prefer windows tools on windows systems and linux tools on linux systems. And why are we asking his / her friend to create an NTFS partition?
> Clicking on a new folder while in Linux and tell it to share will cause Ubuntu to request to download winbind. No it will not. What it will do is ask you if you want to install Samba ( "Windows Networking" I think is what the dialog box calls it ).
> File sharing started working for me after I did [COLOR=Blue]sudo gedit [/COLOR]/etc/samba/smb.conf  You really should be using "gksu gedit". sudo for command line and gksu for GUI applications.

Jedit Ojanen,

Can you access the friends share by ip address:

In a Terminal:
```
nautilus smb://192.168.0.100
```[COLOR=Blue]*Change 192.168.0.100 to the ip address of the friends machine.*[/COLOR]

---

### Post by Morbius1 on 2010-07-29
> **noobunto said:**
> Is there any easy GUI-driven interface to allow easy Ubuntu/Windows co-existence on a home LAN ?

I'm using a notebook so 'sometimes' it's not on the LAN and shouldn't hang-up/fail if the network drives I want to access aren't 'there.'  Also, I don't want to have to click through so many levels in Nautilus to get to the drives.  I want them mounted and on the file system at start-up, available for use.
You really should start your own thread as this is very much off topic. 

But to answer your question: As a matter of fact there is and it's called Gigolo. It's a very misunderstood and under appreciated little application that can do some marvelous things. One thing in particular is Auto-connect. It will find and mount a bookmarked remote share whenever it becomes available and at no extra cost  it will actually remount it if the connection is interrupted.

---

### Post by pricetech on 2010-07-29
For a new user;  System - Administration - Synaptic Package Manager.
Search for "system-config-samba" (without the quotes of course) and install it.  It will also install Samba.  The main difference is, it lets you configure Samba using a GUI tool instead of trying to figure out what all that stuff means in smb.conf.

You can set your workgroup with the tools as well as share folders from your own computer.

Also, try Places - Connect to Server and choose Windows Share as the service type, then see if you can connect by IP address, then by machine name.

---

### Post by Morbius1 on 2010-07-29
> **pricetech said:**
> For a new user;  System - Administration - Synaptic Package Manager.
Search for "system-config-samba" (without the quotes of course) and install it.  It will also install Samba.  The main difference is, it lets you configure Samba using a GUI tool instead of trying to figure out what all that stuff means in smb.conf.
And for an even easier gui for samba you can use Nautilus:

Right click a folder > Select "Sharing Options"

Everyone does realize that this particular user is trying to access someone else's share right? Not create one for someone else to access.

---

### Post by pricetech on 2010-07-29
> **Morbius1 said:**
> Everyone does realize that this particular user is trying to access someone else's share right? Not create one for someone else to access.

Well, this portion of everyone does.  That's why I mentioned setting the workgroup in the GUI and using Places - Connect to Server.

Besides, he'll probably want to "share back" at some point and this will help him prepare for that.

---

### Post by nirvblakr on 2010-07-29
Hi!  I have a Synology home server at home.  I have a laptop with Linux Mint 8 (Helena) installed.  I can access my server's shared files using LAN through Places>Network>Windows Network>Workgroup>*Server*>*Shared files*.  I can also access the files through a web browser.  Samba is installed.  The problem is when I use the wireless lan of my laptop, I cannot access the server and the files anymore even through a web browser. 

I tried Connect to Server through Windows Share but what I get is "Could not display "smb://server/".".  

Any help would be appreciated.  Thanks!

---

### Post by bab1 on 2010-07-29
> **nirvblakr said:**
> Hi!  I have a Synology home server at home.  I have a laptop with Linux Mint 8 (Helena) installed.  I can access my server's shared files using LAN through Places>Network>Windows Network>Workgroup>*Server*>*Shared files*.  I can also access the files through a web browser.  Samba is installed.  The problem is when I use the wireless lan of my laptop, I cannot access the server and the files anymore even through a web browser. 

I tried Connect to Server through Windows Share but what I get is "Could not display "smb://server/".".  

Any help would be appreciated.  Thanks!
Your question is off topic to the OP's original question.  Why would you hijack this thread rather than start your own?

---

### Post by pricetech on 2010-07-29
noobunto and nirvblakr:

Please start your own threads rather than hijacking someone else's

---

### Post by nirvblakr on 2010-07-30
> **bab1 said:**
> Your question is off topic to the OP's original question.  Why would you hijack this thread rather than start your own?

Sorry if I "hijacked" this thread.  I'm just new here.  Forgive my ignorance.

---

### Post by noobunto on 2010-07-30
thanks much, Morbius1, I'll try Gigolo> **pricetech said:**
> noobunto and nirvblakr:

Please start your own threads rather than hijacking someone else'sit didn't seem so off-topic to me, sorry for messing up the whole forum.

---

### Post by Jedit Ojanen on 2010-08-04
Sorry guys, I a bit forgot I started this thread. Anyway, I still would like to get this one fixed as I'm still having this problem. Thanks for the answers. I'm trying those things you asked me to do and tell how it turns out.

---

### Post by Jedit Ojanen on 2010-08-05
> Can you access the friends share by ip address:

In a Terminal:
Code:

nautilus smb://192.168.0.100

I tried this one and I got the same error message: *"Could not access share list..."*.

> For a new user; System - Administration - Synaptic Package Manager.
Search for "system-config-samba" (without the quotes of course) and install it. It will also install Samba. The main difference is, it lets you configure Samba using a GUI tool instead of trying to figure out what all that stuff means in smb.conf.

I did that and it installed fine.

> Also, try Places - Connect to Server and choose Windows Share as the service type, then see if you can connect by IP address, then by machine name.

Same error as above.

My friend's shared folder is shared to everyone and I can now access *Windows network* folder in my *places*, after installing samba, but I can't see the shared folder or anything else than my own shares.

---

