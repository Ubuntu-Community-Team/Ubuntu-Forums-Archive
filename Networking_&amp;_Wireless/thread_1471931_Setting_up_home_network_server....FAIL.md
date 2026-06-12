---
title: "Setting up home network server....FAIL"
date: 2010-05-03
forum: Networking &amp; Wireless
---

### Post by catnip_X07 on 2010-05-03
ok.  Off and on trying new things with Ubuntu.  Using 9.10 for several months and enjoy it.  Have WIN7 in the basement hooked up to large screen TV and barely use.  My new thing I want to do is to set up a home network...trouble is, I don't see any other computers. What I want to do is share files/stream videos and music from ubuntu computer to other computer.

Setup:  internet to cable modem - cable modem to router
router - wire connection to Ubuntu - connect to internet
router -wire connection to WIN7 - connect to internet
router broadcasts wireless.  can use laptop to connect to wireless.  thus, I can have three computers using internet simultaneously...just can't get any one computer to see the other (laptop is VISTA and will only use laptop for internet-do not want on network)

On WIN7, there no other computers found - same with Ubuntu.  

Ubuntu, loaded SAMBA and other files, but no luck.  Read many postings, but I think there is something wrong in a trivial step that I'm overlooking.  

WIN7 - no active directory running....what am I doing wrong?

---

### Post by pytheas22 on 2010-05-04
Can all of the computers ping one another?

---

### Post by catnip_X07 on 2010-05-04
Yes.  Ubuntu can ping WIN7 and vice versa.

---

### Post by pytheas22 on 2010-05-05
Please try opening a file browser in Ubuntu.  Press control-L to edit the location manually, and enter:
```

smb://win7-IP-address
```

(obviously, replace "win7-IP-address" with the actual IP address).  Does this show you your share on the Windows 7 computer?

---

### Post by catnip_X07 on 2010-05-05
Yes!  I got something with that.  Unfortunately, I was not able to get the same with WIN7.  I can access everything on WIN7 computer.  How about the reserve?  How do I access UBUNTU from WIN7?

---

### Post by paulisdead on 2010-05-05
Try the reverse from the win7 machine, type this into the run box
\\ubuntu-IP-address\sharename

remember it's windows, they had to use backslashes instead of forward slashes like every other OS.  You might've tried it this way, just wanted to be sure you didn't try to type it in the same way you did to access the win7 machine from the ubuntu box with the smb://.

What about if you run this from the command line on the windows 7 machine
telnet ubuntu-ip-address 139

You should see a message that it's connected if the server's actually listening on those ports and accepting connections.  It'll say refused if it's not.

---

### Post by catnip_X07 on 2010-05-05
ok....didn't get anything with WIN7.  "telnet" does not seem to be a good command.  Tried using the correct \\IP address and didn't get anything either.

---

### Post by pytheas22 on 2010-05-05
Since you can see the Windows share from Ubuntu, you know it's at least partially working.  Failure to do the reverse could be due to several issues, and not being able to telnet on port 139 to the Ubuntu machine from the Windows machine suggests that either there's a firewall issue somewhere, or samba is not properly configured on Ubuntu.

Do you get a "connection refused" message if you type on your Ubuntu computer:
```

telnet localhost 139
```

---

### Post by CharlesA on 2010-05-05
Did running ```
testparm
``` return any errors?

---

### Post by catnip_X07 on 2010-05-06
I was confused.  I thought I was to do the telnet localhost 139 from my WIN7 machine.  doing telnet localhost 139 from Ubuntu using terminal said I was connected to host
No issues with testparm using UBUNTU, other than shares being longer than 12 characters.

STill nothing from accessing UBUNTU from WIN7

---

### Post by paulisdead on 2010-05-06
Do you have network discovery turned on in win7?

---

### Post by catnip_X07 on 2010-05-06
Yes.  Everything is turned on in WIN7.
That I am aware of....

---

### Post by CharlesA on 2010-05-07
Are you able to connect via IP address from the win7 or Ubuntu machine?

I had to start nmbd for it to show up, even tho I already had a DNS server running.

Check here: [http://ubuntuforums.org/showthread.php?t=1466127](http://ubuntuforums.org/showthread.php?t=1466127)

---

### Post by catnip_X07 on 2010-05-08
NO.  I can't even connect via IP.  Errors on connecting stating the machine could be offline, etc.  It's not.  

On the WIN7, I do have ZoneAlarm firewall running.  I eased all security on it for a brief period, but nothing worked.

---

### Post by paulisdead on 2010-05-08
> **catnip_X07 said:**
> NO.  I can't even connect via IP.  Errors on connecting stating the machine could be offline, etc.  It's not.  

On the WIN7, I do have ZoneAlarm firewall running.  I eased all security on it for a brief period, but nothing worked.

Turn it off completely just for a few minutes to test.  If it works without it, at least you'll know where the problem is.

---

### Post by CharlesA on 2010-05-08
> **catnip_X07 said:**
> NO.  I can't even connect via IP.  Errors on connecting stating the machine could be offline, etc.  It's not.  

On the WIN7, I do have ZoneAlarm firewall running.  I eased all security on it for a brief period, but nothing worked.

Hrm. Are you able to ping the machine using the ip address or SSH into it (if you've got that installed)?

---

### Post by catnip_X07 on 2010-05-08
Yes, I can ping Ubuntu from WIN7 just fine.   Turned off ZoneAlarm...no luck

---

### Post by catnip_X07 on 2010-05-10
wow.  Now everything is going to ****.  Can't access WIN7 anymore from Ubuntu.  typing in the IP address within file manager worked perfect.  Now getting an error.  Didn't change anything either, other than turning off ZoneAlarm.

---

