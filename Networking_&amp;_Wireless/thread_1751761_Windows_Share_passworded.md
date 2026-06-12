---
title: "Windows Share passworded"
date: 2011-05-07
forum: Networking &amp; Wireless
---

### Post by ChrisRatahi on 2011-05-07
Sorry if this has been answered before but I haven't been able to find a fix from searching. I've got a windows share on one of my computers. I can access it from my Win7 laptop by logging in with \\Server\ServerUser and Password. I tried to do the same in Ubuntu but it keeps asking me for the username and password again. I don't know how to get this working and everyone else seems to have trouble with connecting the opposite way.

Thanks in advance.

---

### Post by Paddy Landau on 2011-05-07
Accessing Windows is easy -- in theory. In practice, it can be a bugbear.

Have you installed Samba? If not, install [system-config-samba]("apt:system-config-samba"). Reboot. Go to System > Administration > Samba (or search for Samba in your Dash if you have Unity). Set it up there.

Post back here if you struggle.

---

### Post by ChrisRatahi on 2011-05-07
Hi Paddy,

Thanks for the reply. I have been playing around with the frontend you linked to, it doesn't seem to configure outgoing connections though. Just my local ubuntu shares. I'm trying to connect from Ubuntu to my Windows7 host on a local network. I can access some folders (such as music and movies) because they are open to guest access on the local network. The problem is when I try to access the folders I share to authorised users only such as my documents.

Am I missing something in the settings? I hope this makes sense. I'm happy to clarify anything if need be.

Thanks again. :)

--EDIT--
Update:
I've found some information on command line use of smbclient. I can access movies and music folders. The ones I need to access are C$ E$ and Admin$ which are default shares on Windows according to SMBClient. I login with the windows account details and get access denied. I'm using the following commands:

```

chris@CJPC:~$ smbclient -L agnes -U "agnes\htpc"
Enter agnes\htpc's password: 
Domain=[AGNES] OS=[Windows 7 Professional 7600] Server=[Windows 7 Professional 6.1]
	Sharename       Type      Comment
	---------       ----      -------
	ADMIN$          Disk      Remote Admin
	C$              Disk      Default share
	E$              Disk      Default share
	IPC$            IPC       Remote IPC
	Movies          Disk      
	Music2          Disk      
	Users           Disk      
Domain=[AGNES] OS=[Windows 7 Professional 7600] Server=[Windows 7 Professional 6.1]

	Server               Comment
	---------            -------

	Workgroup            Master
	---------            -------
chris@CJPC:~$ smbclient //agnes/Admin$ -U "anges\htpc"
Enter anges\htpc's password: 
Domain=[AGNES] OS=[Windows 7 Professional 7600] Server=[Windows 7 Professional 6.1]
tree connect failed: NT_STATUS_ACCESS_DENIED
chris@CJPC:~$ 

```
I was using the same password both times. With those credentials I can access movies and music2. The account is system administrator account.

---

### Post by doas777 on 2011-05-07
may be a long shot, but have the windows authentication protocol defaults changed?
I used to set all my xp clients to us NTLMv2 excelusively, and had to add this to the smb.conf:
```
client NTLMv2 auth = yes
```

---

### Post by bobwyajnr on 2011-05-08
> **ChrisRatahi said:**
> 
```

chris@CJPC:~$ smbclient //agnes/Admin$ -U "anges\htpc"
Enter anges\htpc's password: 
Domain=[AGNES] OS=[Windows 7 Professional 7600] Server=[Windows 7 Professional 6.1]
tree connect failed: NT_STATUS_ACCESS_DENIED
chris@CJPC:~$ 

```
I was using the same password both times. With those credentials I can access movies and music2. The account is system administrator account.

I presume you've done all the Windows 7 basics 101 (*Homegroup* sharing disabled, etc., etc. - been there, done that!) to allow it to actually work at all...  I have spent quite a bit of time on this issue myself. Since your using Windows 7 *Professional* (which isn't [COLOR="Red"]crippled[/COLOR] like *Home Premium* - which only works with a single CPU socket MB and has the security policy editors disabled) - just check in the *local security policy editor* that your network access rights are set to sensible values. :-k

I'm also getting a **tree connect failed: NT_STATUS_ACCESS_DENIED** error - if I try and access one of my shares with a guest account - when that shares access is restricted to my 'normal' user account only.

So in your case it's probably an issue of that the Windows CIFS service **thinks** it is not getting an **Administrative** account (which it requires) when you try to login to an **Administrative** share. Or an authentication fail due mismatch in the agreed encryption and signing requirements of the client and server (Windows 7 defaults - I think - to 128bit encryption and NTLM v2 signing)... As I stated (previously) you can confirm the latter with a look in the *local security policy editor* on your Windows 7 box.

I presume that (since you are logging into a Windows 7 machine from a Linux-based OS) you will need to ensure that **smbclient** is passed an exact match of Windows 7 username (case sensitive, with spaces or other, non-standard on UNIX, Windows allowed stuff) and a matching password on both machines (also case sensitive, etc.) The username goes through *name mangling* in the reverse case (as Linux is a much more friendly OS :-) )

Sorry for rambling on - but getting Windows 7 just to talk to Windows XP (let alone Ubuntu) was an uphill battle in my experience!
 
Bob

---

### Post by Paddy Landau on 2011-05-08
Hmm, Samba is a problematic creature.

Have you installed [winbind]("apt:winbind")?

Can you access your shares through Nautilus (menu item Go > Network)?

---

### Post by Morbius1 on 2011-05-08
Let's recap what we've got here:

You can access the shares you've actually created on Win7 from Ubuntu.
You can't access any of the shares ending with "$".

So there doesn't seem to be anything wrong with the samba client on Ubuntu and the error message is "NT_STATUS_ACCESS_DENIED" is not a Samba issue it's a permissions / authentication issue.

These "$" shares - sometimes called "Administrative" shares are in fact "hidden" shares. Another Windows box can't see them normally but Linux isn't Windows so it can see them. Back in the good old days Linux could access these shares if it knew the administrators password but Win7 "fixed" that - security is job 1 at Microsoft you know. You need to do one extra step. Give this a shot ( note: I only did this once and it was for someone else's machine so I found a link that is from a Windows user and not a Linux user talking about Windows ):
***Enable Access to Windows 7 Administrative Shares:***
[http://chall32.blogspot.com/2010/02/how-to-enable-access-windows-7.html](http://chall32.blogspot.com/2010/02/how-to-enable-access-windows-7.html)

**[COLOR=Blue]EDIT:[/COLOR]** In other cases where this has come up I have successfully convinced the user that sharing C and especially ADMIN$ was not advisable since it's the functional equivalent of sharing "/" on Linux.

---

### Post by ChrisRatahi on 2011-05-09
Thanks for all of your VERY informative replies. I've tested these solutions and am still struggling to get it working. I'm going to settle with the fact that Windows is just a bother for now, and have decided to run a virtual Ubuntu box on my other machine because I can link through to the Windows drive from there. I'll probably make the full switch to Ubuntu on that machine in the coming weeks as it was a whole lot easier for me to use and it plays nicer with the Windows clients than Windows does with Ubuntu clients. +1 for Ubuntu! :)

---

### Post by bobwyajnr on 2011-05-09
> **ChrisRatahi said:**
> ... I'll probably make the full switch to Ubuntu on that machine in the coming weeks as it was a whole lot easier for me to use and it plays nicer with the Windows clients than Windows does with Ubuntu clients. +1 for Ubuntu! :)

One of the problems with the whole SMB/CIFS protocol being run as a Workgroup (i.e. not a domain) is that any one wrongly configured or incompatible machine entering the network can cause things to go south... In my experience Ubuntu (Linux) machines see everything on the network, Windows XP machines can never seem to access SMB networked devices and Windows 7 boxes only want to see other Windows 7 boxes! SSH ftw IMHO! :popcorn:

Don't mark the thread as solved. Just go back to working on the problem every so often - I am sure you will eventually get some kind of fix or kludge solution :P

Bob

PS I have to say I was struggling to convert to Ubuntu full-time but I found Lucid to be an awesome release. The addition of WINE and VirtualBox (w/ Windows XP Professional 32-bit) eases the transition even more!

---

