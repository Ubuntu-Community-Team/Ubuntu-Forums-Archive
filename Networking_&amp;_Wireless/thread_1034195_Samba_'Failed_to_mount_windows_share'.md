---
title: "Samba: 'Failed to mount windows share'"
date: 2009-01-08
forum: Networking &amp; Wireless
---

### Post by HeinzVoerbakje on 2009-01-08
Hi all,

This is a copy of my post in this thread [http://ubuntuforums.org/showthread.php?t=964564&goto=newpost](http://ubuntuforums.org/showthread.php?t=964564&goto=newpost) , but since that thread is marked as solved I'm starting a new one, as the solutions in that tread do not seem to help in my case.

I'm having a problem with Samba, which started after a certain upgrade on the fifth of january. I cannot access any Samba shares, neither from the server itself when browsing the network, neither from an other (windows) client. It's strange as it did work until that fateful update.

The error I get is 'Failed to mount windows share'.

Samba's log (var/log/samba/log.heinzvoerbakje) says:

[2009/01/07 23:39:00, 0] smbd/service.c:make_connection_snum(1156)
'/home/myname/share' does not exist or permission denied when connecting to [share] Error was Permission denied

The usershares in /var/lib/samba/usershares says for this folder:

#VERSION 2
path=/home/myname/share
comment=
usershare_acl=S-1-1-0:R
guest_ok=y

Who has any clue?

Thanks, HeinzVoerbakje

---

### Post by untappedpilot2 on 2009-01-08
Maybe try reconfiguring your firewall settings or just completely turning it off while you try to access your samba shares. I think I know which update your talking about.. maybe you chose to use the default "smb.conf" file (I think the path is /etc/samba/smb.conf.) After the update I think you had to select whether to keep your current smb.conf file or replace it with the default installation file. I remember it being a hassle to get my samba configured at first and whenever I access my Linux computer from another Windows one on my network I have to hit the stop button in Firestarter because I haven't configured it to play with the Windows computer. 

Anyway there's two things to try. Repost on how it goes, if it still doesn't work repost the log file if there is any change.

=Derek

---

### Post by dmizer on 2009-01-08
The error is telling you that the directory /home/myname/share does not exist. What is the output of this command:
```
ls /home
```

---

### Post by HeinzVoerbakje on 2009-01-08
> **untappedpilot2 said:**
> Maybe try reconfiguring your firewall settings or just completely turning it off while you try to access your samba shares. I think I know which update your talking about.. maybe you chose to use the default "smb.conf" file (I think the path is /etc/samba/smb.conf.) After the update I think you had to select whether to keep your current smb.conf file or replace it with the default installation file. 

No, I don't have a firewall turned on on this computer, I've got a hardware firewall protecting my home network. Besides, I can actually see the folder that is shared, I just cannot access it.

Also, my smb.conf appears to be the way it was before the update, it looks ok, I'l post it here when I get home.

> **dmizer said:**
> The error is telling you that the directory /home/myname/share does not exist. What is the output of this command:
```
ls /home
```

No, the folders are there, I can access that folder just fine locally. Only when I'll access it through smb:// or by browsing the network it will not work. Also, when I create any other new share they are not accessible, bu they do appear in the list of shared folders on the network.

I think the error has more to do with the secong part of the error-message: 

/home/myname/share' does not exist or **permission denied when connecting to [share] Error was Permission denied**

---

### Post by dmizer on 2009-01-08
No, in this case, I don't think the second part of the error is the problem.

In a mount command, there are two sections:
1) the section which tells your computer where the remote share is located (smb://servername/directory)
2) the section which tells your computer where to place the contents of that share locally (/home/myname/share)

Part 1 must exist on the server, part 2 must exist on the client. The error is telling you that /home/myname/share does not exist on your client. I can see that this is the case because "/home/myname/share" is a mount path, not a share path.

---

### Post by HeinzVoerbakje on 2009-01-08
> **dmizer said:**
> No, in this case, I don't think the second part of the error is the problem.

In a mount command, there are two sections:
1) the section which tells your computer where the remote share is located (smb://servername/directory)
2) the section which tells your computer where to place the contents of that share locally (/home/myname/share)

Part 1 must exist on the server, part 2 must exist on the client. The error is telling you that /home/myname/share does not exist on your client. I can see that this is the case because "/home/myname/share" is a mount path, not a share path.

Ok, when I get home I'll post the output of 'ls /home', but I'm pretty sure the folder will be there, although you never know what might have happened ;)

---

### Post by dmizer on 2009-01-08
It would also be very helpful if you posted your actual mount command. There is no reason to obscure your local network paths in the name of security. The only way someone could exploit this information is if they had access to your local network, and if they had access to your local network, it wouldn't matter if you obscured that information or not.

---

### Post by HeinzVoerbakje on 2009-01-08
> **dmizer said:**
> It would also be very helpful if you posted your actual mount command. There is no reason to obscure your local network paths in the name of security. The only way someone could exploit this information is if they had access to your local network, and if they had access to your local network, it wouldn't matter if you obscured that information or not.

Yes, I know, but my home folder is mounted automatically, I don't mount it by hand. I navigate to the samba shared folder using nautilus, so I don't use any commands there either.... is there a log-file made by nautilus you would like to see?

---

### Post by albinootje on 2009-01-08
> **HeinzVoerbakje said:**
> Ok, when I get home I'll post the output of 'ls /home', but I'm pretty sure the folder will be there, although you never know what might have happened ;)

I recommend testing with smbclient on your Ubuntu machine locally first.
```

smbclient //localhost/your_share-name_here -U your_samba_username

```
And please provide the output of :
```

testparm
ls -la /home/your_name|grep your_sharename

```

---

### Post by HeinzVoerbakje on 2009-01-08
Doh, I've solved it!

Somehow the permissions of the folder were set wrong..... I was the owner of the folder, but others (even those who were in the same group) were not able to read it....

Sorry for wasting your time, but I'm glad it's working now again!

HeinzVoerbakje

---

