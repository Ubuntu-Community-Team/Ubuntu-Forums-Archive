---
title: "windows can't resolve ubuntu lucid hostname (not sending it?)"
date: 2010-08-22
forum: Networking &amp; Wireless
---

### Post by darthwissen on 2010-08-22
Hello everybody,

I am currently facing one issue with my network. I have several computers and this is what happens, everything works fine when I use the ip address, but when it comes to hostname:

Computer 1 - Windows 7 x64
Computer 2 - Mac OS X / Windows 7
Computer 3 - Ubuntu 8.10 / Windows XP x64 / Windows 7 x64
Computer 4 - Windows Vista
[COLOR="Red"]Computer 5 - Ubuntu Lucid Lynx 10.04 / Windows XP[/COLOR] (This is the one with the problem)

-Windows computers can't ping/see the computer 5 (while it is running linux), but they can see computer 3 while running ubuntu 8.10 and computer 2 while on Mac OS X.

-computers 2 and 3 can see/ping everybody while on Mac/Linux. 

-computer 5 can ping everybody.

-computers 1, 2, 3 and 4 (on every OS) can see/ping computer 5 while on windows xp.

Basically, the problem is with computer 5, it can see, but it is not seen by other computers (just when running ubuntu lucid)

Computer 5 is supposed to be a printer server, so it must be seen by the others regardless of OS.


**Other Thoughts:**

When I ping computers 5 the TTL is 64, when I ping other computers, TTL is 128. I don't think this means anything, but I am not sure.
Initially I thought this was a printer issue, but then I realized is something related to network when I tried to use ping/explore the computer 5 by ip/hostname (it works by ip, but not by hostname).

Thanks in advance spending your time helping me solve this,

Igor Campos

**Edit:**

Computer 5 is sending the hostname to the router properly, it appears in the dhcp client list.

---

### Post by darthwissen on 2010-08-25
Please, I need help!!! Any suggestion is usefull!

---

### Post by darthwissen on 2010-08-27
New info:

Just installed Ubuntu 10.04 on another computer of the network and the same thing happens with it, It can ping everyone, but it's hostname is not resolved by windows computers.

Any Ideas? Please reply!!! At least to say no!!!

Thanks

---

### Post by redmk2 on 2010-08-27
> **darthwissen said:**
> New info:

Just installed Ubuntu 10.04 on another computer of the network and the same thing happens with it, It can ping everyone, but it's hostname is not resolved by windows computers.

Any Ideas? Please reply!!! At least to say no!!!

Thanks
What name services are you running in your network?

---

### Post by Morbius1 on 2010-08-27
You might want to check some preliminary things:

What is the name of Computer5? 
It cannot be more that 15 characters long.

Ubuntu introduced a few bugs because of how it starts services these days so you need to make sure the nmbd service is running:
```
sudo service nmbd status
```If it's not running start it:
```
sudo service nmbd start
```The other obvious thing is any firewall or apparmor you have on Computer5. If you haven't done anything with those then that shouldn't be the issue.

Finally, you might want to issue the following command on Computer5:
```
smbtree
```It should show you a list of all the shared resources on your network including it's own. Post the output if there are errors.

---

### Post by bpsanborn on 2010-08-31
Hi guys,

I am new to Linux and Ubuntu but an advanced user on Windows.  I am running Ubuntu 10.04.1 on a spare PC and Windows 7 on a hot new 4 core PC.  The windows 7 system is fully updated with maintenance.  So is the Ubuntu system.  The windows 7 system sees and shares files and printers with an XP SP3 laptop and Win 7 Netbook.  No known problems anywhere in Windows world.

I can't browse the windows 7 system from ubuntu.  I tried the smblist command an this is what I get:

brian@linux:~$ smbtree
Enter brian's password: 
Server requested plaintext password but 'client plaintext auth' is disabled
failed tcon_X with NT_STATUS_ACCESS_DENIED
Server requested plaintext password but 'client plaintext auth' is disabled
failed tcon_X with NT_STATUS_ACCESS_DENIED

There is obviously some mismatch with security between the systems.  Any help would be appreciated. 

Brian

---

### Post by Morbius1 on 2010-08-31
Go into etc/samba/smb.conf and see if you have the following line:
> encrypt passwords = No
If you do then place a # sign in front of it so that it looks like this:
> #encrypt passwords = No
Then restart samba

---

### Post by bpsanborn on 2010-09-01
Thanks,

That did it.  I have been poking at this system for two days trying everything suggested on the forums.  At times not knowing what I was doing.  The first success came from turning off "password protected shares" in Win7.  That allowed the connection but I did not like running with the shares unprotected.  Then with turning back on password encryption in Samba I was able turn the password protection back on in Win7 and all is well.

I am still getting a random (BSOD(00007F) in Win7 when I click on the network icon in the Nautilus File Manager.  I got and error message the last time and I can see that Ubuntu/Samba/Nautilius is sent out a NETWORK\\\ query.  I'll try chasing it on the Windows side.

Brian

---

