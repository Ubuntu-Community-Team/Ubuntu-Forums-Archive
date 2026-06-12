---
title: "Networking issues"
date: 2009-09-30
forum: Networking &amp; Wireless
---

### Post by Smeags on 2009-09-30
I'm new to Ubuntu and Linux so please bear with me.

I'm having a few networking-related issues.  My setup is like this: I have 2 PC's running Vista x64 and one PC running Ubuntu 8.10 connected to a router.  My printer, Brother HL-2140 laser printer, is connected to the Ubuntu PC via USB.  The printer works fine on the Ubuntu PC...haven't run into any issues yet.

I've got the Vista PC's setup to be able to use the printer connected to the Ubuntu PC over the network.  Here's the first problem: the Vista PC's can print MS Office documents without any problem, however they cannot print .txt or pdf files.

Problem 2: I thought as a work-around I'd setup a shared folder on the Ubuntu PC so that I could drag a .txt or pdf file to it and print it from the Ubuntu PC.  However when I try to access the shared folder from Vista, it prompts for a username and password.  I've tried all username and password combination that I could think of and it would not let me access it.

I tried looking at some properties on the Ubuntu PC to see why the Windows PC's wouldn't be able to access the folder but I haven't found any reason why it they shouldn't be able to.  One thing I did notice is that from the Ubuntu PC, I cannot access 'WORKGROUP' on the Windows Network.  When I try to I get the message, "Unable to mount location.  Failed to retrieve share list from server".  So essentially I can see all PC's on the network from the Windows PC's, but not from the Ubuntu PC.

I did some searching on the net and haven't run into anything very helpful, so I'm hoping someone here can point me in the right direction.

Any help is appreciated.

---

### Post by Littleweseth on 2009-10-01
I can't help you with your printer not printing .txt or .pdf, but your file share not working is fairly easy to fix.

The problem is that your Linux logins and your Samba (filesharing) logins are two separate animals. You need to create a Samba username and password; right now, you have none.

Here's how : from a terminal, type 'smbpasswd -a username'. This is the command to **a**dd a new Samba login (hence the -a.) Type a suitable password twice, and you should be set.

If the error is now 'access denied' instead of 'no such login', you may need to add yourself to the 'valid users' list for the share you created. See one of my posts from earlier today : [http://ubuntuforums.org/showthread.php?t=1279028](http://ubuntuforums.org/showthread.php?t=1279028)

HTH.
 - L.

---

### Post by Smeags on 2009-10-01
Littleweseth,

Thanks for the suggestion.  I ran 'smbpasswd -a "username"' from the terminal and created a password as you said.  However I don't see that it has changed anything.  I get the same thing when trying to access the "shared" Ubuntu folder from a Windows PC.  It prompts me for a username and password and no username/password combination I try works.

First of all I should ask what is the correct thing I should be using for the username and password?  The same thing I just created by running the above command in terminal?  The Windows account name and ? for the password?

Also, you mentioned adding myself to the 'valid users' list for the share that was created.  From the post you linked to, it looks like that is done in smb.conf.  If this is true, reading through smb.conf, I came upon this right above the 'valid users' statement: 'By default, \\server\username shares can be connected to by anyone with access to the samba server.'  How can I ensure that the Windows PC's have access to the samba server?

Finally, from the Windows PC's, I can see all PC's on the network.  However I cannot access 'WORKGROUP' from 'Windows Network' from the Linux PC.  Shouldn't I be able to see the Windows PC's from Ubuntu?

Again, any help is appreciated.

---

### Post by Smeags on 2009-10-01
One more thing I've tried.  When I run 'findsmb' from a terminal the only thing that shows up is the Ubuntu machine.  None of the Windows PC's show up.

---

### Post by Littleweseth on 2009-10-02
The username and password to access the samba share will be the one you just created using smbpasswd -a.

I'll look at this in an Ubuntu virtual machine later. I'd do it now, but I broke it while I was hacking at it and I'll need a reboot before it comes good again. ;)

- L.

---

### Post by Littleweseth on 2009-10-03
On further reading of your post, I'm not exactly sure what steps you've gone through. In fact, I'm not even sure that you've installed the 'samba' package, which contains the samba filesharing server (and isn't installed by default.)

See this for reference: [https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

Anyway, the steps I used to set up filesharing on Ubuntu 9.04 were :
1) Install samba manually: 'sudo aptitude install samba'.
2) Right click folder I wanted to share : select the 'Sharing Options' option.
3) The 'Folder sharing' dialog appears. Check all the boxes : 'Share this folder', 'Allow other people to write in this folder', and 'Guest Access'. (Note : guest write access is insecure!)

I'm not sure where this GUI method puts the configuration; it's not in smb.conf, but seems to work fine.

This method may vary for 8.10. Any particular reason you haven't upgraded to 9.04 yet?

- L.

---

### Post by maestrobwh1 on 2009-10-03
What might be causing this issue:

A shared folder on my host machine that is in /home/user willingly gives write permissions

A shared folder on my host machine that is on a partition/other disk on my host machine refuses writing from client machines and remains read only.  I can't even use sudo cp "filename" to the share.

I am thinking it has something to do with mount permissions for that disk in fstab on the host but I am uncertain how to fix that.  The samba permissions for the host folder in my home directory are set the same as they are for the one sharing from this external disk (refuses write).

UUID=092C-326C	/media/30GB_SSD	vfat   defaults,auto,gid=1000,uid=1000,shortname=mixed	0	0

If I unmount it, comment it out in fstab, rename the mount directory, and mount it with the automounter, I can write to it as a share, so I know it is an fstab permission issue for the disk on the host, I just don't know how to fix it.

---

