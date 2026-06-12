---
title: "File sharing problem with direct ethernet cable."
date: 2009-12-03
forum: Networking &amp; Wireless
---

### Post by Mr.Whippy on 2009-12-03
Hi - 

First time posting and I'm a newbie to Ubuntu & Linux so please go easy on me !

I have a new PC that I have installed Ubuntu KK on. My old PC has Windows XP on it and all my documents / mp3's etc.

I have made up a crossover ethernet cable, connected the two together and have been trying to get file sharing working between the two but although both computers can see the ethernet connection going active, and I can access the internet through the cable from one machine to the other (the PC running Ubuntu has a wireless link to my home hub), I still cannot browse any folders on either machine from the other one, so I cannot transfer any files.

The network locations on both machines do not show the other PC, only themselves.

I have tried all the suggestions on the Ubuntu help screens to no avail. I have (or at least I am pretty sure I have) enabled file sharing on both machines.

I'm not bothered which way it works, only that I can transfer files from one machine to the other. I have a lot of data and it would take ages burning it all onto DVD's to transfer it that way.

Any ideas ? 

Dave.

---

### Post by cgb on 2009-12-03
Could be a dns issue.  Have you tried browsing from one machine to the other via IP address?  from ubuntu you could try putting in Nautilus in the address field smb://"IPADDRESSOFXPMACHINE" and see what the response is.

---

### Post by JBAlaska on 2009-12-03
Do you have Samba installed and configured? Are the workgroups set the same on both computers?

Opened the filesharing port in iptables via ufw, and windoze firewall?

[Install Samba on Ubuntu 9.10](http://www.jonathanmoeller.com/screed/?p=1168)

---

### Post by Mr.Whippy on 2009-12-03
Thanks for the fast replies - 

Yes, I have Samba installed and set up to share root (not sure if that's a good thing or not but I reckoned I'd get everything that way)

Workgroups - Do you mean the same name ? - On Ubuntu it's WORKGROUP (all caps) and on XP it's Workgroup. I can't seem to change either of them to match the other but I'm not sure if it matters about being case sensitive.
 
Filesharing port ? Not come across that yet - is that like port forwarding on a router ?

Not come across UFW either - sorry. 

I'm pretty sure the XP end is OK with the firewall, I've got file and printer sharing enabled. I've done filesharing before between windows machines without too much fuss. 

I put smb://"IPADDRESSOFXPMACHINE" into Natuillus and got[I] 
Error: Failed to retrieve share list from server
Please select another viewer and try again.[/I]

Any more ideas ?

Thanks - Dave.

---

### Post by Mr.Whippy on 2009-12-03
Just discovered Gufw, Do I just allow NFS ? is that right ?

Dave.

---

### Post by doas777 on 2009-12-03
you should not need to configure the firewall to get samba going, as it opens the ports in iptables on install. 

have you confirmed that samba was able to load your settings?
open a terminal and enter:
```
sudo testparm /etc/samba/smb.conf
```

I don't think you can usually share /, because even though it is shared, no user would be able to access it.

---

### Post by doas777 on 2009-12-03
> **Mr.Whippy said:**
> Just discovered Gufw, Do I just allow NFS ? is that right ?

Dave.
samba is not the same as NFS. are you wanting to do an nfs network?

---

### Post by Mr.Whippy on 2009-12-03
OK, I got these results - 

[COLOR=Navy][I]Load smb config files from /etc/samba/smb.conf
Processing section "[printers]"
Processing section "[print$]"
Processing section "[dave]"
Loaded services file OK.
Server role: ROLE_STANDALONE
Press enter to see a dump of your service definitions

[global]
    server string = %h server (Samba, Ubuntu)
    map to guest = Bad User
    obey pam restrictions = Yes
    pam password change = Yes
    passwd program = /usr/bin/passwd %u
    passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
    username map = /etc/samba/smbusers
    unix password sync = Yes
    syslog = 0
    log file = /var/log/samba/log.%m
    max log size = 1000
    dns proxy = No
    usershare allow guests = Yes
    panic action = /usr/share/samba/panic-action %d

[printers]
    comment = All Printers
    path = /var/spool/samba
    create mask = 0700
    printable = Yes
    browseable = No
    browsable = No

[print$]
    comment = Printer Drivers
    path = /var/lib/samba/printers

[dave]
    comment = transfer from xpcomp
    path = /home/dave
    read only = No
    guest ok = Yes
dave@dave-linux-desktop:~$ 
[/I][/COLOR]
Since my last post I decided to unshare "root" and just share file system instead.

Sorry, I was just guessing with NFS. I'll just remove the exceptions in GUFW then.

Thanks so far.

Dave.

---

### Post by doas777 on 2009-12-03
well your smb.conf parsed without errors but i would add this line:
```

workgroup = WORKGROUP
security = user

```
(note: all names in SMB are converted to upper at evaluation, so WORKGROUP = Workgroup = workgroup). host and share names also follow that rule.

also have you run smbpasswd on both hosts?
```

sudo smbpasswd -add <username>

```

also, samba seems finicky about when it will enumerate a server root (\\servername). sometimes you have to specify the full path to the share (\\server\sharename).

have you don;t anything in XP that alters the ntlm/lm authentication security level? I specify NTLMv2 auth only, so I have to add:
```

client NTLMv2 auth = yes 

```
to my config as well.

---

### Post by Mr.Whippy on 2009-12-03
Not doing too well here - sorry if I'm being thick.

I tried to add those lines but got Workgroup - command not found and Security command not found.

I tried the password thing and got this - 
dave@dave-linux-desktop:~$ sudo smbpasswd -add dave
[sudo] password for dave: 
Disabled user dave.

I don't know what you mean about both hosts ? Surely the windows machine won't take linux commands ?

As for the NTLMv2 thing - sorry I don't have a clue. Never heard of it before.

Dave.

---

### Post by Mr.Whippy on 2009-12-03
Now when I try looking on the network, I get "Unable to mount location - failed to retrieve share list from server". I wasn't getting that before.

Dave.

---

### Post by doas777 on 2009-12-03
what do you get if you try to point nautilus directly to the share?

---

### Post by Mr.Whippy on 2009-12-03
I can no longer see the (ubuntu) shared files in nautilus. I just see windows workgroup and then I get that error message when I try to open it.

Dave.

---

### Post by doas777 on 2009-12-03
just to clarify, you are using the same username/password across all the boxes right? and the password matches the one you set with smbpasswd, right?

---

### Post by Mr.Whippy on 2009-12-03
Yes, I'm using the same username and password for everything on this machine.

I'm going to start transferring my files via an external USB hard drive, just to get the job done but I'd still like to get this connection working if possible. 

Dave.

---

### Post by cgb on 2009-12-03
Curious on what happens if you try browsing to yourself on the Ubuntu box.  So basically, like I mentioned before, try going into Nautilus and entering smb://"YourUbuntuIPAddress" and putting your Ubuntu IP address in the filed marked "YourUbuntuIPAddress" instead of your XP address I mentioned earlier.  You should see the shared folders listed if sharing is working correctly.  This will tell us if sharing is working at all and eliminate any other networking issues that may be going on.


so for me if I wanted to try this I would enter smb://10.5.60.51 since 10.5.60.51 is my IP address....

---

### Post by Mr.Whippy on 2009-12-03
OK, thanks, I'll give that a try but how do I find my IP address first ?

Dave.

---

### Post by doas777 on 2009-12-03
> **Mr.Whippy said:**
> OK, thanks, I'll give that a try but how do I find my IP address first ?

Dave.

ifconfig on ubuntu
'ipconfig /all' in windows

are you being prompted for uname/passwd prior to recieving the error mentioned above?

---

### Post by Mr.Whippy on 2009-12-03
No, not being prompted.

I'll go try what you suggest.

Dave.

---

### Post by Mr.Whippy on 2009-12-03
Whoa !

Didn't expect all that. !

[COLOR=Navy]dave@dave-linux-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:19:66:f2:69:2d  
          inet addr:10.42.43.1  Bcast:10.42.43.255  Mask:255.255.255.0
          inet6 addr: fe80::219:66ff:fef2:692d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:669 errors:0 dropped:0 overruns:0 frame:0
          TX packets:347 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:49236 (49.2 KB)  TX bytes:53142 (53.1 KB)
          Interrupt:27 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:116 errors:0 dropped:0 overruns:0 frame:0
          TX packets:116 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:9920 (9.9 KB)  TX bytes:9920 (9.9 KB)

wlan0     Link encap:Ethernet  HWaddr 00:17:3f:d4:49:c0  
          inet addr:192.168.1.65  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::217:3fff:fed4:49c0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:39753 errors:0 dropped:0 overruns:0 frame:0
          TX packets:21628 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:54253476 (54.2 MB)  TX bytes:2199661 (2.1 MB)

wmaster0  Link encap:UNSPEC  HWaddr 00-17-3F-D4-49-C0-64-34-00-00-00-00-00-00-00-00  
          UP RUNNING  MTU:0  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)[/COLOR]

Just a guess here, but as my link cable is Wlan0, am I correct in thinking my IP is 192.168.1.65 ?

Dave

---

### Post by Mr.Whippy on 2009-12-03
Well I tried that IP address in natillus and got to view my Documents and print$ folders (on the ubuntu machine).

Getting late now, off to bed, I'm out tomorrow night but will try again over the weekend.

Thanks everybody so far..

Dave.

---

### Post by doas777 on 2009-12-03
wlan is a wireless interface. you are using eth0 for wired, with an IP of [COLOR=Navy]10.42.43.1. I wonder if your samba daemon has bound to the wrong interface.
[/COLOR]

---

### Post by cgb on 2009-12-04
ya I would try with the wired IP address as doas777 suggested.  I dont think the samba daemon typically binds to a specific interface but I could be wrong in this case.  I would also try again connecting to the xp machine with the IP address just like we just did with the Ubuntu box, not sure if maybe you took my first suggestion in this thread to literally. :)  You can get the XP IP address by going to the command prompt and entering "ipconfig".

---

