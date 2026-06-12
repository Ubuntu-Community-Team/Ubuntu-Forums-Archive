---
title: "Why Can I Not Access Samba Share from Windows XP?"
date: 2009-09-30
forum: Networking &amp; Wireless
---

### Post by fourtyseven on 2009-09-30
I have searched high and low for the solution and have come up short. I even found a few threads on here but none of them solved my problem.

I have two machines; one running Ubuntu 8.10 Desktop and the other running Windows XP. 

I created a share on the XP machine which I can access from the Ubuntu machine. No problems there.
However when I create a share on Ubuntu and try to access it from Windows XP, I get the following error:

[B][I]"\\Testlinux\Documents is not accessible. You might not have permission to use this network resource. Contact the administrator of this server to find out if you have access permissions.
The network path was not found."[/B][/I]

The steps I went through to setup Samba are:

I installed smbfs using ***sudo apt-get install smbfs.*** Once that was done I typed ***shares-admin*** in the terminal and got the Shared Folders dialog box. I chose a folder to share, shared it through SMB, gave it a name and unchecked the read-only box.
Next I opened up the smb.conf file and made sure that the following entry exists:

[B][I][Documents]
path = /home/%username%/Documents
available = yes
browseable = yes
public = yes
writable = yes[/B][/I]

I saved and exited, restarted Samba and added a Samba username and password using ***sudo smbpasswd -a %username%.*** Then when I go into My Network Places in XP, I can see the Ubuntu machine and I can even access it but when I click on the shared folder, I get the above error.

I really dont know what to do. I managed to get it working in Red Hat and Fedora but it simply wont work in Ubuntu. Is there something Im missing here?

---

### Post by Littleweseth on 2009-09-30
You may need an 'allowed users' line, specifying who is allowed to access the share (even though you've marked it public.) I believe 'public' may only mean 'let everyone know this share exists' as opposed to 'let everyone read/write here'.

Here's a snippet from my smb.conf :

[shared]
comment=Shared folder.
path=/home/shared/
valid users = lws, root
public = yes;
writable=yes
printable=no
create mask=0775

Try adding a 'valid users' line, with the usernames being the ones you added using smbpasswd.

---

### Post by Iowan on 2009-09-30
My Samba book is getting a little old - it doesn't list **public=** as an option. The **valid users=** option is there, and *should* work.

---

### Post by fourtyseven on 2009-10-01
Nope. F-all. I tried editing smb.conf as suggested but I still get the same error.
Any other ideas?

---

### Post by fourtyseven on 2009-10-01
> **fourtyseven said:**
> Nope. F-all. I tried editing smb.conf as suggested but I still get the same error.
Any other ideas?

OK. After much hair pulling and teeth gnashing, I eventually removed 8.10 and installed 8.04.2 instead. Configured SAMBA and now it works!
Although it is working, Im still unsure as to why it did not work previously. I did nothing different except use a different ubuntu version. Could it be an 8.10 bug?

---

### Post by fourtyseven on 2009-10-02
... and posts go un-noticed as usual.

---

### Post by kpiascik on 2009-11-11
Hey,

I'm having the exact same issue, also on 8.10. I set up samba using the GUI application "Samba Server Configuration".  I have not been able to connect to it from XP.  Its XP SP3 MCE 2005.  I'm not sure if this makes any difference?

I made my share public, and read only.  There are no allowed users specified but I set it to allow anybody access.

I've been reading on the net about changing the security policy in XP, would this have any effect on samba connectivity?

I'm not willing to change to 8.04, can anyone tell me if this is a bug on 8.10 and if it has been fixed in 9.04 or 9.10?

Thanks

---

### Post by dmizer on 2009-11-11
> **fourtyseven said:**
> ... and posts go un-noticed as usual.

Posts go unanswered because the people who know how to answer them simply haven't seen it.

In your case, all you need to do is look for this option:
```
#   security = user
```
Change it to this:
```
   security = share
```
Restart samba or reboot.

---

