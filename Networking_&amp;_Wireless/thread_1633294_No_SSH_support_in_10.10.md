---
title: "No SSH support in 10.10?"
date: 2010-11-29
forum: Networking &amp; Wireless
---

### Post by TheFr00n on 2010-11-29
I recently upgraded to 10.10 - did a clean install on my home serverbox. Attempts to SSH into this machine all fail, which is weird because SSH used to work by default on 10.04.

Unperturbed, I tried to install the openSSH server - but it's no longer in the Ubuntu Software Center, nor is it in the Package Manager. I tried to grab it via apt-get, and I get told that openssh is no longer available.

What gives? Educate me - I would have thought that SSH was a fairly standard security tool. Why would Ubuntu remove it?

---

### Post by prshah on 2010-11-29
> **TheFr00n said:**
> because SSH used to work by default on 10.04.

Unperturbed, I tried to install the openSSH server - but it's no longer in the Ubuntu Software Center, nor is it in the Package Manager. I tried to grab it via apt-get, and I get told that openssh is no longer available.

Why would Ubuntu remove it?

Someone's having you on, or you didn't look properly; ssh server is indeed available: ```
on Nov Mon 29 @15:58:45:~$ sudo apt-get install -s openssh-server 
[sudo] password for user: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  rssh molly-guard openssh-blacklist openssh-blacklist-extra
The following NEW packages will be installed:
  openssh-server
0 upgraded, 1 newly installed, 0 to remove and 7 not upgraded.
Inst openssh-server (1:5.5p1-4ubuntu4 Ubuntu:10.10/maverick [amd64])
Conf openssh-server (1:5.5p1-4ubuntu4 Ubuntu:10.10/maverick [amd64])
Mon Nov 29 @15:59:10:~$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 10.10
Release:	10.10
Codename:	maverick

```

As for software center, did you click the "Show xxx technical items" link along the bottom after searching for "ssh server"?

No Ubuntu (incl server edition) has come with ssh server pre-installed, it has to be installed manually. ssh (client) is available in most distros pre-installed.

---

### Post by TheFr00n on 2010-11-29
I would love nothing more than to find I'm wrong about this.

Revealing the technical items in Software Centre just shows the pre-installed client, not the server.

My attempt at apt-getting it looks more like this:

> :~$ sudo apt-get install openssh-server
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package openssh-server is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'openssh-server' has no installation candidate
:~$ 

---

### Post by prshah on 2010-11-29
> **TheFr00n said:**
> 
My attempt at apt-getting it looks more like this:

Did you run an apt-update after installation? ```
sudo apt-get update
``` (You will need an active Internet connection for this).

Please post your /etc/apt/sources.list file (maybe the repos are commented out) if the update does not work.

---

### Post by TheFr00n on 2010-11-29
Yes. There's an error, but it looks server related:

> Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) maverick Release.gpg                                                                        
Ign [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) maverick/main Translation-en                                                        
Ign [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) maverick/main Translation-en_ZA                                                     
Ign [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) maverick/multiverse Translation-en
Ign [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) maverick/multiverse Translation-en_ZA
Ign [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) maverick/restricted Translation-en
Ign [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) maverick/restricted Translation-en_ZA
Ign [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) maverick/universe Translation-en
Ign [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) maverick/universe Translation-en_ZA
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) maverick-updates Release.gpg
Ign [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) maverick-updates/main Translation-en
Get:1 [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick Release.gpg [316B]           
Ign [http://extras.ubuntu.com/ubuntu/](http://extras.ubuntu.com/ubuntu/) maverick/main Translation-en    
Ign [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) maverick-updates/main Translation-en_ZA
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security Release.gpg         
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/main Translation-en
Ign [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) maverick-updates/multiverse Translation-en
Ign [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) maverick-updates/multiverse Translation-en_ZA
Ign [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) maverick-updates/restricted Translation-en
Ign [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) maverick-updates/restricted Translation-en_ZA
Ign [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) maverick-updates/universe Translation-en
Ign [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) maverick-updates/universe Translation-en_ZA
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) maverick Release                    
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) maverick-updates Release                                  
Ign [http://extras.ubuntu.com/ubuntu/](http://extras.ubuntu.com/ubuntu/) maverick/main Translation-en_ZA                       
Get:2 [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick Release [57.3kB]             
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/main Translation-en_ZA
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/multiverse Translation-en
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/multiverse Translation-en_ZA
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) maverick/main Sources                 
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/restricted Translation-en
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/restricted Translation-en_ZA
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/universe Translation-en
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/universe Translation-en_ZA
Err [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick Release                          
  
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) maverick/restricted Sources           
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) maverick/universe Sources
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) maverick/multiverse Sources
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) maverick/main i386 Packages
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) maverick/restricted i386 Packages
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) maverick/universe i386 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security Release
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) maverick/multiverse i386 Packages
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) maverick-updates/main Sources
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) maverick-updates/restricted Sources
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) maverick-updates/universe Sources
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) maverick-updates/multiverse Sources
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) maverick-updates/main i386 Packages
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) maverick-updates/restricted i386 Packages
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) maverick-updates/universe i386 Packages
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) maverick-updates/multiverse i386 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/multiverse Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/main i386 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/restricted i386 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/universe i386 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/multiverse i386 Packages
Fetched 317B in 2s (149B/s)
Reading package lists... Done
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY DB141E2302FDF932

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/maverick/Release](http://extras.ubuntu.com/ubuntu/dists/maverick/Release)  

W: Some index files failed to download, they have been ignored, or old ones used instead.


---

### Post by wojox on 2010-11-29
Run :

```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 16126D3A3E5C1192
```

---

### Post by TheFr00n on 2010-11-29
That key didn't help because whatever key it is is already part of my system. However, over in the other thread I posted, a user called Surfer came up with one that did:

```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys DB141E2302FDF932
```

OpenSSH is now installing. I still don't really understand what happened here, but thank you very much for helping.

---

### Post by lombaardcj on 2011-04-12
I know this thread says SOLVED but the solution wasn't clear.

Had exactly the same dependancy problem Thefr00n had and the solution isn't obvious

So here is how to fix it:

Step 1: Go into Synaptic Package Manager > Settings > Repositories.
Step 2: Go to Updates tab and select everything option available (might be that only specific one is required after all. Not sure)
Step 3:Click Close button
Step 4:Click on Reload or in the terminal use sudo apt-get update.

For some reason the "newest" version op openssh isn't available until you also download the updates. :???:

Note: I didn't not have to upgrade at all to perform the install of openssh-server from the terminal.

:D

I think some users NEVER even see this happening cause they leave everything as default or love updating everything immediately.

Cheers!

---

