---
title: "Samba to Windows 7 Home Premium"
date: 2012-01-07
forum: Networking &amp; Wireless
---

### Post by jeffreylees on 2012-01-07
Let me preface this by saying that I understand that it's almost certainly an issue with my Windows PC - yet it's to do with sharing with the ubuntu machine, so, I'm posting here as well in the hopes of finding an answer.

I apologize if this has already been answered somewhere else, but I've spent a lot of time tinkering and a lot of time on Google and I've given up and decided to come here and ask for help!

I'm attempting to set up a Linux file/media server at home. Right now, I have Xubuntu installed on the server, along with Samba.
So, two questions.
1) When I share a file, without requiring authentication (to everyone on LAN) the server and its shares are visible and accessible from my wife's Mac Mini and from my work laptop (Which is also running Windows 7 Home Premium). However, this PC (Windows 7 Home Premium, as well) requests username/password to connect to the server computer - before even seeing what share(s) are available on it - and is satisfied with neither logins for the PC or the Ubuntu machine, even when I set up identical ones. So, I know the sharing works on some level but am at a loss to figure out what this PC has set up different than the laptop.

2) I might at some point want to restrict file access to those with logins, and am wondering how this works if the computers are not on a domain (since home premium cannot be) - can Win 7 HP edition even do this successfully?

Thanks in advance. When replying let me know if you need any further information, I'm just not sure what you might consider relevant.

Oh, and the server is running Ubuntu 11.10, with an XFCE interface, although I believe if memory serves I had the same trouble on another version of ubuntu, and gnome.

Oh - at some point during this process I ended up doing a wipe/reinstall of Windows for some other reasons - and the clean install has the same issues. FYI.

Edit: I've also tried adding a registry file LmCompatibility something or another, at value 1, and at value 2, respectively depending on different sources. Neither worked or made any difference at all.

---

### Post by Morbius1 on 2012-01-07
> 1) When I share a file, without requiring authentication (to everyone on LAN) the server and its shares are visible and accessible from my wife's Mac Mini and from my work laptop (Which is also running Windows 7 Home Premium). However, this PC (Windows 7 Home Premium, as well) requests username/password to connect to the server computer - before even seeing what share(s) are available on it - and is satisfied with neither logins for the PC or the Ubuntu machine, even when I set up identical ones. So, I know the sharing works on some level but am at a loss to figure out what this PC has set up different than the laptop.This may or not be relevant but it's the only thing I can think of that fits all those symptoms. It has to do with the way a Windows machine browses the network.

Windows actually passes the current user's Windows login user name and password when it browses. If you happen to have a Linux user by the same name and you have given him a Samba password that is different from the Windows password then you are in an infinite loop of credentials prompts. And that will happen at the host level before it even gets to the share.

If you truly have only guest shares then remove the samba password entirely, something like this:
```
sudo smbpasswd -x morbius
```Or tell the Windows user to use the new samba password.

Or make sure the samba password matches the Windows user's login password exactly.

---

### Post by jeffreylees on 2012-01-07
I will try removing the Samba user password as suggested and let you know. Here is my other dilemma regarding this.

The laptop has the same operating system as the desktop. The user account which I am currently using on all three machines (Win7 Laptop, Win7 PC, and Ubuntu desktop "server") is named identically. The laptop sees the public unsecured shares and can access them even though I know for a fact that its password has never even been typed on the linux box - the linux and/or samba user does not have a matching password - yet it works, and the Windows PC does not, whether its passwords match or not.

Sorry to be a difficult person to troubleshoot!

---

### Post by Morbius1 on 2012-01-07
It's very late in the day for me so I'm not sure I followed that but: All three machines have identical user names?

Remember to Linux user Morbius is not the same as user morbius.

---

### Post by jeffreylees on 2012-01-07
Indeed. All three machines have the same username. The two 'clients' - the laptop and the desktop - have the same Win 7 Home Premium OS. However, the laptop has a password that is different from the others, and it CAN access the share. The desktop and the Ubuntu machine CURRENTLY have the same password (in addition to the same username) although that has been changed back and forth during this process.

The laptop does not even prompt for login info to access the shares, it just accesses them. If I secure the shares, THEN I have authentication annoyances with the laptop - but as long as the share is public, the laptop does not ask for authentication, whereas the PC insists on it. I hope I'm making sense.

And remember, we also have an additional input in the Mac Mini, which has accessed the shares fine from the beginning. It has different login info altogether, and has never prompted for info.

---

### Post by Morbius1 on 2012-01-07
Run the following command and see how many samba accounts you have:
```
sudo pdbedit -w -L
```The actual password will be encrypted so you wont be able to read it but it should list "nobody", your-name unless you already deleted it with the smbpasswd -x, plus any others.

---

### Post by jeffreylees on 2012-01-07
just nobody, and my own. I didn't delete mine yet, should I do that?

---

### Post by Morbius1 on 2012-01-07
Yes. It's easy enough to add it back. Then test all of your Win Boxes. Your mac is acting just like a good UNIX based samba client should act :wink:

---

### Post by Morbius1 on 2012-01-07
Sorry but I've got to pack it in for the day. Any future posts of mine at this point would be more incoherent than what I've already posted anyway.

---

### Post by jeffreylees on 2012-01-07
No problem, it wasn't an urgent problem anyway, and, as it turns out, you fixed the urgent part.

When I removed the samba user with the same name as my user accounts, as you suggested, my PC is now able to access the free shares.

Next question, and of considerably less importance, will be how to secure these shares or any others I'd like to share. It's the LAN at my house, I'm not really worried about security... but paranoia is king in this business, and I do have most of my work material in the same network.

Thoughts on how to fix the authentication problems, anyone? Should I set up SAMBA user to match both windows users? Like, set them all up identically, and try that?

For now, I'll be content with exactly how it is, though, I'm just wondering for the future.

Thanks again Morbius

---

### Post by Morbius1 on 2012-01-08
[1] Create a new user on the Linux machine

Create a local user account on the Linux machine in such a way that it does not create a home directory or local login capability to the physical server itself:
```
sudo useradd -s /bin/true jeffreys
```[COLOR=Blue]*I've added an "s" at the end of your name to specify "server" or "samba" user.*[/COLOR]

[2] Then add that user to the samba database:
```
sudo smbpasswd -a jeffreys
```[3] Now set your share to not allow guest access or allow access only to "jeffreys".

When the client is prompted for credentials he/she will have to use the username "jeffreys" and the samba password that you set up in step [2].

[COLOR=Blue]NOTE:[/COLOR] There's a second peculiarity about how Windows accesses shares. When the Windows client successfully connects to a share with the right credentials it saves that information in perpetuity. So if the Windows machine is rebooted for example, the next time it tries to access the share it will automatically send those credentials without being prompted. You will think that security has been compromised but that is not the case. You can always prove it to yourself by changing the samba password for "jeffreys" by re-running the command:
```
sudo smbpasswd -a jeffreys
```Depending on how you set up your share that may not be the end of the story however since "jeffereys" may not have access to the shared directory itself. This isn't a Samba issue it's a Linux permissions issue and one that can be fixed. For that we need to know how your shares are set up so please post the output of the following commands:
```
testparm -s
``````
net usershare info --long
```

---

### Post by jeffreylees on 2012-01-09
Thanks. Between your help and my fresh look at what I messed up, I think I've got this fixed. I now have both secure and unsecure shares working on every machine on my LAN. It did have to do with the Linux user accounts, I think.

Anyway, I've idly asked questions about this on other forums for the last month or so and you're the first person to give me enough input to push to a solution, so thanks for taking the time!

---

