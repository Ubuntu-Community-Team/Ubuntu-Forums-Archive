---
title: "Sharing Files and Folders with Windows 7"
date: 2009-09-23
forum: Networking &amp; Wireless
---

### Post by Gordonbp531 on 2009-09-23
I have a Tosh Netbook running Ubuntu Remix 9.04, a desktop running Win XP and a Tosh Satelite running Windows 7 RC.
Both the XP machine and the Win7 machine have shared directories, and both can see each others shares over the network.
The Ubuntu Netbook can see and access shares on the XP machine, but NOT on the Win 7 machine.
When I try to connect to the Win 7 machine, all I get is a continuous log-on dialog box loop.
Has anyone had any success in coneccting Ubuntu to Windows 7 shares?

---

### Post by badger_fruit on 2009-09-23
> **gendibal said:**
> Has anyone had any success in coneccting Ubuntu to Windows 7 shares?

Never tried but at this logon box, are you entering anything or just clicking "OK"?

---

### Post by Gordonbp531 on 2009-09-23
> **badger_fruit said:**
> Never tried but at this logon box, are you entering anything or just clicking "OK"?

Entering the User password. Each machine has the same Username and password....

---

### Post by petersaints on 2009-09-29
I think I have the same problem with Windows 7 RTM. I just insert my Windows username, I put the Workgroup on the domain box, type in the password and it just asks it all over again.

What can I do? Is this the same problem you have gendibal?

---

### Post by thoriumchameleon on 2009-09-29
hmmm i just accessed it fine... i'm using 64-bit RC and Ubuntu 9.04 and NTFS file system... what about you?
EDIT: are these separate machines? i don't think i fully understood what you said

---

### Post by petersaints on 2009-09-29
Yeah. This are seperated machines. One Desktop and one laptop. One is running Ubuntu the other Windows 7.

I also tried to debug it out on the console using: "smbclient -L localhost" it shows me that I have something shared on my local computer (I'm also running Samba on Ubuntu and I can access the shared folders on Windows 7 without any problem).

But when I do "smbclient -L 192.168.1.100 -U PEDRO" (where 192.168.1.10 is the IP address of my other computer and PEDRO is my Windows 7 username) I get this error after inserting my password:

session setup failed: SUCCESS - 0

Any ideas? This is really frustrating!!

---

### Post by thoriumchameleon on 2009-09-29
sorry I haven't quite gotten into SAMBA... after i got apache to work i felt special enough to revert back to regular pc usage lol...

---

### Post by petersaints on 2009-09-29
Tomorrow I'll try with a Vista laptop to know if this is a problem between 7 and Samba.

By the way does anyone know if that's the case? I mean, if Samba SMB implementation is somewhat incompatible with Windows 7? At least without some tweaking I mean?

---

### Post by cariboo on 2009-09-29
I have Windows 7 in a vm and connects to my file server with no problem. I have the shares on the server setup to allow guest access, and Win 7 found the shares automagically. THis is what the share setup in /etc/samba/smb.conf looks like:

```
[stuff]
	path = /media/stuff
	comment = whatever fits
	guest ok = yes
	browseable = yes
	writeable = yes
```

---

### Post by petersaints on 2009-09-30
But my problem is the opposite. I can access Ubuntu's shares from Windows 7. I can't access Windows 7's shares from Ubuntu.

And I have tested with another computer running Windows Vista SP2 and it works fine. The problem must be with Windows 7.

---

### Post by NoFearDJB on 2009-10-04
> **petersaints said:**
> 

But when I do "smbclient -L 192.168.1.100 -U PEDRO" (where 192.168.1.10 is the IP address of my other computer and PEDRO is my Windows 7 username) I get this error after inserting my password:

session setup failed: SUCCESS - 0

Any ideas? This is really frustrating!!

I'm having this same problem connecting to my Windows 7 shares from Ubuntu.

---

### Post by jpt266 on 2009-10-07
I have same problem. Ubuntu system does not connect to the win7 box but will connect to a XP box.
If you find a fix please share.

Thanks,

---

### Post by MaLaCoiD on 2009-10-09
There's [another thread]("http://ubuntuforums.org/showthread.php?t=1043933") with the same issue: XP and another Win 7 can access the Win 7 share, but not Jaunty. In Win 7 server, I changed the setting that requires a local account for access to make the XP box work. Tried to set Local Security Policy to Send LM & NTLM v2 if negotiated- no change.

---

### Post by jpt266 on 2009-12-25
I think the fix as been found. Read some of these;


It seems caused by windows live sign-in assistant. I had exact same problem. [https://bugs.launchpad.net/ubuntu/+s...ba/+bug/458637](https://bugs.launchpad.net/ubuntu/+s...ba/+bug/458637)

[http://social.technet.microsoft.com/...a-0d79a5597527](http://social.technet.microsoft.com/...a-0d79a5597527)



Thanks to Yejun above.

Removing windows live sign-in assistant program has "fixed" it for me too - I can use my WIndows 7 printer and access shared folders using my windows user/password, whereas before Win 7 appeared to be refusing to accept the credentials.

Fixed it for me too. Could always go ubuntu to xp but not ubuntu to vista or windows7. Tried the system services tweak, no fix. So what is this windows live sign-in assistant doing that stops the share request?

Again, I removed windows live sign-in assistant on the windows7 box and that fixed it for me too.

---

### Post by castalla on 2010-01-22
This is driving me nuts!

I have smbnetfs to connect to windows shares - this works 100% with Vista.  With Win 7 I see the PC but no shares.  The Vista box does see the Win 7 shares.  Using Everyone to connect.

Is there a solution - I've googled and read just about every 'fix' - nothing works!

There must be a simple solution!  Is it Win 7 share setup?  Or a smbnetfs.conf issue?

Help please - for a newbie.

---

### Post by petersaints on 2010-09-12
And this is still not fixed in 10.10. It's really frustrating and a real problem to people who have a home network consisting of both Ubuntu and Windows 7 machines (lik I do).

---

### Post by castalla on 2010-09-12
The solution is here: [http://ubuntuforums.org/showthread.php?t=288534](http://ubuntuforums.org/showthread.php?t=288534)

---

### Post by petersaints on 2010-09-12
That's more something like a work around. It works but not the way it should.

---

### Post by castalla on 2010-09-12
Well, you can't have everything ... I find it 100% acceptable.

---

### Post by xeno0904 on 2010-11-07
The problem is actually because of Windows Live Sign-in Assistant.

To solve it:
1. go to the folder "\Program Files\Common Files\Microsoft Shared\Windows Live" (or 'Program Files (x64)' on x64 OS)
2. unreg all of dlls here using regsvr32 (command like this: 'for %i in (*.dll) do regsvr32 /s /u %i')

:) That's all!

---

### Post by castalla on 2010-11-07
I don't have Live Assistant installed ... so what now?

---

### Post by Moko-Moko Seijin on 2010-11-08
I also didn't have Live Sign-In Assistant installed. Of the Windows Live Essentials, I only had Messenger installed. After removing it, I was able to access my Win7 share.

---

### Post by castalla on 2010-11-09
Don't have any Live Essentials installed - that folder you mentioed doesn't exist on my installation.

---

