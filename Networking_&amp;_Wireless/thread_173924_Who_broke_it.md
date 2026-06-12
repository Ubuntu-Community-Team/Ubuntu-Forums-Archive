---
title: "Who broke it?"
date: 2006-05-11
forum: Networking &amp; Wireless
---

### Post by RichardTyson on 2006-05-11
I am running an internet cafe. I am a user not a geek.
Up until yesterday it was great, I work on Breezy and could see all computers and shared folders on all the other machines and easily transfer files back and forth. Most of them unfortunately run Windows (customers used to it). Then I did an update. Now if someone brings their laptop in and hooks up, my networks wants me to log onto that machine, which I am unable to do. As long as anyone has their laptop on our network I cannot see anything or get into the Windows network.

Please reverse whatever caused this. I did not need Samba before, but I thought I would give it a try. What happens? It sees the other computers, but tells me that I have to change the names of the files to something that Samba wants.

I am angry and frustrated. I do not know how to change these things, and really have no intention of trying to learn or understand yet something else. This is all far to complicated for me. I want to USE Ubuntu, not program it.

Why do you guys insist on breaking something that worked perfectly before?

---

### Post by WakkiTabakki on 2006-05-11
This isn't really going to help, but I just want to clear a few points...

Your problem is probably due to something with the configuration of SAMBA. That piece of software is ment to be able to work in a multitude of situations, and is also required to be safe and secure of course.
So, there will be a need for it to be configured correctly (it's already "programmed", otherwise it wouldn't exist...).

Configuring a network _is_ a task that requires skill, regardless of whether it's a windows, *nix or mixed network...

If your angry and frustrated, I'd suggest you hire someone that knows what he/she's doing. 
Otherwise, please, provide better information on what happened, such as:
- what was the update you did
- what samba-version do you use
- posting the actual error message
- provide info on your network, i.e routerconfig etc.
- what is your Ubuntu-version
- what windows-versions are used (incl what sp, etc)
- you say that you never needed samba to connect before, then how did you connect to the windows network before?


And, btw, I seriously doubt that anyone is insisting on breaking anything... I mean, really, man...


Cheers
/N

---

### Post by RichardTyson on 2006-05-11
I installed 1 5.10 version on one of Windows Network (XP Pro) computers. Told the setup program the name of the workgroup. Brilliant. All I had to do after setup was look in Places, Networking and there they were. I could see them although they couldn't see me.
Updates done whenever the prompt tells me to update.
Yesterday someone connects his Acer Ferrari laptop (he connects everday) and all of a sudden I need his permission. The network insisted on trying to log me onto his machine. I needed my password although I am already working as administrator. This has never happened before, so must have been in the last update.
Networking done by ethernet, cabling and wizard. One router for all the computers to connect directly to the internet.

---

### Post by nocturn on 2006-05-11
As far as I can see, there hasn't been a samba update recently, not even in the last month.

So, I suspect the breakage is caused by something else.  Possibly even by one of the recent XP updates (there was one this week).
Without more information, I cannot be sure either way.

---

### Post by nocturn on 2006-05-11
You say that you cannot connect to laptops people bring in.  That should be normal though.  Unless you are in the same workgroup and/or they have full anonymous access set up (not recommended, certainly not in a public place).

If it is about seeing shares, it might be that the SMB browse master is hijacked by one of the laptops, this is not a samba issue, it is a bug in the design of the SMB protocol and can be corrected by forcing the Samba server to win browser elections.

---

### Post by RichardTyson on 2006-05-11
If he is not connected to the workgroup, why would Samba all of a sudden insist on trying to connect to him?

---

### Post by RichardTyson on 2006-05-11
[QUOTE=RichardTyson]If he is not connected to the workgroup, why would Samba all of a sudden insist on trying to connect to him?[/QUOTE]

If he is connected, why is this happening all of a sudden?

And I haven't the foggiest idea of how to force win elections. I want to play like normal, not enter american politics

---

### Post by nocturn on 2006-05-11
[QUOTE=RichardTyson]If he is not connected to the workgroup, why would Samba all of a sudden insist on trying to connect to him?[/QUOTE]

Can you post a little more details on your problem?

The guy with the Ferrari laptop connects to your network and you try to access his shares from Breezy, is this correct?

If so, is het on the same workgroup as you are, are his shares set up to allow anonymous connects?  

Does this happen to all machines on your network, or only some of them?

As far as I can see there was no update to samba recently, so if that is correct, it cannot be the cause of your problem.

---

### Post by WakkiTabakki on 2006-05-12
[QUOTE=RichardTyson]
And I haven't the foggiest idea of how to force win elections. I want to play like normal, not enter american politics[/QUOTE]

Hehe, good one :D!

Check the file ```
/etc/samba/smb.conf
```
It contains all the configurations for your samba setup.

The settings below may be a good starting point... But hey! Start by making a backup of the file!!!
```
# Domain Master specifies Samba to be the Domain Master Browser. This
# allows Samba to collate browse lists between subnets. Don't use this
# if you already have a Windows NT domain controller doing this job
; domain master = yes

# Preferred Master causes Samba to force a local browser election on startup
# and gives it a slightly higher chance of winning the election
; preferred master = yes

# Enable this if you want Samba to be a domain logon server for
# Windows95 workstations.
; domain logons = yes

```
(lines starting with a ; and # are comments)

Well, this is providing your problem has to do with the domain controller etc..

Good luck
/N

---

### Post by nocturn on 2006-05-12
[QUOTE=RichardTyson]If he is connected, why is this happening all of a sudden?

And I haven't the foggiest idea of how to force win elections. I want to play like normal, not enter american politics[/QUOTE]

That is why I asked the question if this happens on all computers.
Maybe the configuration on his laptop changed, maybe a windows update (there were several recently) changed some default insecure behavior.

As far as I can see, there was no Samba update, so unless you changed your Ubuntu config, there was no change on that side.

The browser election is pretty funny, but it exists because of the insane manner that the SMB protocol behaves (not something that Samba invented).

Browse master problems (elections) are very common causes of Windows networking errors, regardless whether Samba is used (Samba is actually the only one offering a partial solution by allowing you to trick the election process).

---

### Post by nocturn on 2006-05-12
I still do not exactly understand your problem.

Can you post the exact error you got?  Why did you need to install samba (you should only need the samba client to browse the network.

---

### Post by RichardTyson on 2006-05-12
Guys, thanks for your assistance. I don't know the jargon or what does what, (not yet), so I am leaving well enough alone. As you assure me this strange behaviour was not caused by Ubuntu that is good enough for me.

A thought occured to me that Networking should not be an art any longer. I think that the process is probably a bit more complicated than it should. With the hardware available now, isn't it time someone went back and started over?

Here is a computer, here is another one, and here is a third. They share these cables and these are their names. Now talk to each other.

---

### Post by nocturn on 2006-05-12
[QUOTE=RichardTyson]Guys, thanks for your assistance. I don't know the jargon or what does what, (not yet), so I am leaving well enough alone. As you assure me this strange behaviour was not caused by Ubuntu that is good enough for me.[/quote]

No problem, if you do need help again though, just post/ask.

> 
A thought occured to me that Networking should not be an art any longer. I think that the process is probably a bit more complicated than it should. With the hardware available now, isn't it time someone went back and started over?

Here is a computer, here is another one, and here is a third. They share these cables and these are their names. Now talk to each other.

That's a good point, and there is some very good work being done on this by Apple amongst others.  The Windows filesharing protocol however is a complete and utter mess.  It is very fragile, even when sticking to a windows only environment.

---

### Post by RichardTyson on 2006-05-12
[QUOTE=nocturn]I still do not exactly understand your problem.

Can you post the exact error you got?  Why did you need to install samba (you should only need the samba client to browse the network.[/QUOTE]

Sorry, I did not write down the error messages and I don't think I can repeat them. I installed Samba because of a suggestion during the process.

I'm afraid that if you want to find out the cause you are looking at the wrong person. Perhaps there is someone out there who can set up the same scenario.

1. Windows LAN 
2. All computers except one running WinXP and all linked to a wireless internet connection router.
3. The Ubuntu computer can see all the other computers which all share the same domain name. 
4. Plug in a new computer and the Ubuntu computer wants to connect to it but can't.
5. A login prompt will appear but will not let you in, and will also not allow you into your LAN.
6. Press various options and a message appears telling you that perhaps samba should be installed.
7. Install it and now the Ubuntu computer sees the other computers but still won't let you in as it wants you to change the names of the files/folders

That is about all I can give. Again sorry. Again thanks for your time.

---

### Post by Slim Odds on 2006-05-12
[QUOTE=RichardTyson]
3. The Ubuntu computer can see all the other computers which all share the same domain name. [/QUOTE]

In your 1st post, you mentioned workgroups. Here you mention domain names. These two are mutually exclusive. Domains require a domain controller and are much more rigid. Workgroups are looser and somewhat adhoc.

As nocturn mentioned earlier, it sounds like to you need some help from someone who understands these things more completely.

Some details from you would also go a long way, especially the exact configuration of the "Windows" machines.

---

