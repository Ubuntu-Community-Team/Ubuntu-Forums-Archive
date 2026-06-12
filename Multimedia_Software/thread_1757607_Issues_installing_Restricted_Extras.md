---
title: "Issues installing Restricted Extras"
date: 2011-05-13
forum: Multimedia Software
---

### Post by Onoku on 2011-05-13
I just installed 10.10 and am trying to install restricted extras. First I tried it in the terminal, and got this
```
onoku@onoku-MacBook:~$ sudo apt-get install ubuntu-restricted-extras
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package ubuntu-restricted-extras

```

Then I tried to get it via the software center. I found it in the software center and it said "Available from 'multiverse' source" I clicked "use this source", and on the left side a little green arrow with "In Progress (1)" popped up for a few seconds then went away. I have no idea what to do after that. Any advice would be much appreciated. I am quite new to Linux, so this is all taking me a bit to get used to. Thanks.

---

### Post by walt.smith1960 on 2011-05-13
I used synaptic rather than the Software Center.  It installed and works perfectly.

---

### Post by SecretCode on 2011-05-13
Have you run 
```
sudo apt-get update
```
?

---

### Post by Onoku on 2011-05-13
Yes, I ran the update, however I did get some errors when I did it.

```
onoku@onoku-MacBook:~$ sudo apt-get update
Hit http://ppa.launchpad.net maverick Release.gpg                              
Get:1 http://extras.ubuntu.com maverick Release.gpg [72B]                      
Get:2 http://security.ubuntu.com maverick-security Release.gpg [198B]          
Ign http://extras.ubuntu.com/ubuntu/ maverick/main Translation-en              
Ign http://security.ubuntu.com/ubuntu/ maverick-security/main Translation-en   
Ign http://extras.ubuntu.com/ubuntu/ maverick/main Translation-en_US           
Ign http://ppa.launchpad.net/mactel-support/ppa/ubuntu/ maverick/main Translation-en
Get:3 http://extras.ubuntu.com maverick Release [9,762B]                       
Err http://extras.ubuntu.com maverick Release                                  
  
Ign http://security.ubuntu.com/ubuntu/ maverick-security/main Translation-en_US
Ign http://ppa.launchpad.net/mactel-support/ppa/ubuntu/ maverick/main Translation-en_US
Get:4 http://iq.archive.ubuntu.com maverick Release.gpg [198B]       
Ign http://iq.archive.ubuntu.com/ubuntu/ maverick/main Translation-en         
Hit http://ppa.launchpad.net maverick Release  
Ign http://security.ubuntu.com/ubuntu/ maverick-security/multiverse Translation-en
Ign http://iq.archive.ubuntu.com/ubuntu/ maverick/main Translation-en_US
Hit http://ppa.launchpad.net maverick/main Sources
Ign http://security.ubuntu.com/ubuntu/ maverick-security/multiverse Translation-en_US
Ign http://iq.archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-en
Hit http://ppa.launchpad.net maverick/main i386 Packages
Ign http://iq.archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en
Ign http://iq.archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en
Ign http://security.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en_US
Ign http://iq.archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ maverick-security/universe Translation-en
Ign http://iq.archive.ubuntu.com/ubuntu/ maverick/universe Translation-en
Ign http://iq.archive.ubuntu.com/ubuntu/ maverick/universe Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ maverick-security/universe Translation-en_US
Get:5 http://iq.archive.ubuntu.com maverick-updates Release.gpg [198B]
Get:6 http://security.ubuntu.com maverick-security Release [31.4kB]
Err http://security.ubuntu.com maverick-security Release
  
Ign http://iq.archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en
Ign http://iq.archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en_US
Ign http://iq.archive.ubuntu.com/ubuntu/ maverick-updates/multiverse Translation-en
Ign http://iq.archive.ubuntu.com/ubuntu/ maverick-updates/multiverse Translation-en_US
Ign http://iq.archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en
Ign http://iq.archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en_US
Ign http://iq.archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en
Ign http://iq.archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en_US
Get:7 http://iq.archive.ubuntu.com maverick Release [39.8kB]
Err http://iq.archive.ubuntu.com maverick Release
  
Get:8 http://iq.archive.ubuntu.com maverick-updates Release [31.4kB]
Err http://iq.archive.ubuntu.com maverick-updates Release
  
Fetched 670B in 4s (154B/s)
Reading package lists... Done
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: http://extras.ubuntu.com maverick Release: The following signatures were invalid: BADSIG 16126D3A3E5C1192 Ubuntu Extras Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: http://security.ubuntu.com maverick-security Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: http://iq.archive.ubuntu.com maverick Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: http://iq.archive.ubuntu.com maverick-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/maverick/Release  

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/maverick-security/Release  

W: Failed to fetch http://iq.archive.ubuntu.com/ubuntu/dists/maverick/Release  

W: Failed to fetch http://iq.archive.ubuntu.com/ubuntu/dists/maverick-updates/Release  

W: Some index files failed to download, they have been ignored, or old ones used instead.

```

---

### Post by SecretCode on 2011-05-13
That's a lot of errors ... do you have a bad network connection?

Maybe try a different repository - go to Software Sources e.g. System > Admin > Synaptic > Settings > Repositories and choose something else under "Download from:"

---

### Post by wilee-nilee on 2011-05-13
> **Onoku said:**
> Yes, I ran the update, however I did get some errors when I did it.

```
onoku@onoku-MacBook:~$ sudo apt-get update
Hit http://ppa.launchpad.net maverick Release.gpg                              
Get:1 http://extras.ubuntu.com maverick Release.gpg [72B]                      
Get:2 http://security.ubuntu.com maverick-security Release.gpg [198B]          
Ign http://extras.ubuntu.com/ubuntu/ maverick/main Translation-en              
Ign http://security.ubuntu.com/ubuntu/ maverick-security/main Translation-en   
Ign http://extras.ubuntu.com/ubuntu/ maverick/main Translation-en_US           
Ign http://ppa.launchpad.net/mactel-support/ppa/ubuntu/ maverick/main Translation-en
Get:3 http://extras.ubuntu.com maverick Release [9,762B]                       
Err http://extras.ubuntu.com maverick Release                                  
  
Ign http://security.ubuntu.com/ubuntu/ maverick-security/main Translation-en_US
Ign http://ppa.launchpad.net/mactel-support/ppa/ubuntu/ maverick/main Translation-en_US
Get:4 http://iq.archive.ubuntu.com maverick Release.gpg [198B]       
Ign http://iq.archive.ubuntu.com/ubuntu/ maverick/main Translation-en         
Hit http://ppa.launchpad.net maverick Release  
Ign http://security.ubuntu.com/ubuntu/ maverick-security/multiverse Translation-en
Ign http://iq.archive.ubuntu.com/ubuntu/ maverick/main Translation-en_US
Hit http://ppa.launchpad.net maverick/main Sources
Ign http://security.ubuntu.com/ubuntu/ maverick-security/multiverse Translation-en_US
Ign http://iq.archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-en
Hit http://ppa.launchpad.net maverick/main i386 Packages
Ign http://iq.archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en
Ign http://iq.archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en
Ign http://security.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en_US
Ign http://iq.archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ maverick-security/universe Translation-en
Ign http://iq.archive.ubuntu.com/ubuntu/ maverick/universe Translation-en
Ign http://iq.archive.ubuntu.com/ubuntu/ maverick/universe Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ maverick-security/universe Translation-en_US
Get:5 http://iq.archive.ubuntu.com maverick-updates Release.gpg [198B]
Get:6 http://security.ubuntu.com maverick-security Release [31.4kB]
Err http://security.ubuntu.com maverick-security Release
  
Ign http://iq.archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en
Ign http://iq.archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en_US
Ign http://iq.archive.ubuntu.com/ubuntu/ maverick-updates/multiverse Translation-en
Ign http://iq.archive.ubuntu.com/ubuntu/ maverick-updates/multiverse Translation-en_US
Ign http://iq.archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en
Ign http://iq.archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en_US
Ign http://iq.archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en
Ign http://iq.archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en_US
Get:7 http://iq.archive.ubuntu.com maverick Release [39.8kB]
Err http://iq.archive.ubuntu.com maverick Release
  
Get:8 http://iq.archive.ubuntu.com maverick-updates Release [31.4kB]
Err http://iq.archive.ubuntu.com maverick-updates Release
  
Fetched 670B in 4s (154B/s)
Reading package lists... Done
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: http://extras.ubuntu.com maverick Release: The following signatures were invalid: BADSIG 16126D3A3E5C1192 Ubuntu Extras Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: http://security.ubuntu.com maverick-security Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: http://iq.archive.ubuntu.com maverick Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: http://iq.archive.ubuntu.com maverick-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/maverick/Release  

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/maverick-security/Release  

W: Failed to fetch http://iq.archive.ubuntu.com/ubuntu/dists/maverick/Release  

W: Failed to fetch http://iq.archive.ubuntu.com/ubuntu/dists/maverick-updates/Release  

W: Some index files failed to download, they have been ignored, or old ones used instead.

```

Post the output of
cat /etc/apt/sources.list

Look in the software sources, you have to turn the SS menu icon with a right click on the menu-edit-admin-software sources, click it on. Open software sources 2nd tab other software and tick on the repos and edit them to maverick if needed then run the above command.

---

### Post by Onoku on 2011-05-13
> **SecretCode said:**
> That's a lot of errors ... do you have a bad network connection?

Maybe try a different repository - go to Software Sources e.g. System > Admin > Synaptic > Settings > Repositories and choose something else under "Download from:"

Yeah, my connection is crap here. I am in Iraq, and while I am fortunate to have an internet connection, it isn't ideal.

@wilee-nilee, here is what I got.

```
onoku@onoku-MacBook:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007)]/ maverick main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://iq.archive.ubuntu.com/ubuntu/ maverick main restricted
deb-src http://iq.archive.ubuntu.com/ubuntu/ maverick main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://iq.archive.ubuntu.com/ubuntu/ maverick-updates main restricted
deb-src http://iq.archive.ubuntu.com/ubuntu/ maverick-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://iq.archive.ubuntu.com/ubuntu/ maverick universe
deb-src http://iq.archive.ubuntu.com/ubuntu/ maverick universe
deb http://iq.archive.ubuntu.com/ubuntu/ maverick-updates universe
deb-src http://iq.archive.ubuntu.com/ubuntu/ maverick-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://iq.archive.ubuntu.com/ubuntu/ maverick multiverse
deb-src http://iq.archive.ubuntu.com/ubuntu/ maverick multiverse
deb http://iq.archive.ubuntu.com/ubuntu/ maverick-updates multiverse
deb-src http://iq.archive.ubuntu.com/ubuntu/ maverick-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://iq.archive.ubuntu.com/ubuntu/ maverick-backports main restricted universe multiverse
# deb-src http://iq.archive.ubuntu.com/ubuntu/ maverick-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu maverick partner
# deb-src http://archive.canonical.com/ubuntu maverick partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu maverick main
deb-src http://extras.ubuntu.com/ubuntu maverick main

deb http://security.ubuntu.com/ubuntu maverick-security main restricted
deb-src http://security.ubuntu.com/ubuntu maverick-security main restricted
deb http://security.ubuntu.com/ubuntu maverick-security universe
deb-src http://security.ubuntu.com/ubuntu maverick-security universe
deb http://security.ubuntu.com/ubuntu maverick-security multiverse
deb-src http://security.ubuntu.com/ubuntu maverick-security multiverse

```

---

### Post by wilee-nilee on 2011-05-13
Remove the # here.
```
# deb http://archive.canonical.com/ubuntu maverick partner
```

open the file again with this command to edit.
```
gksudo gedit /etc/apt/sources.list
```

Open the software sources as I described, edit them to maverick, and click them on, we will presume that they are all maverick compatible.

Run in the terminal.
```
sudo apt-get update && sudo apt-get upgrade
```

These lines can be run independently without the &&.

Then run the restricted extras again and enloy the new set up.;)

---

### Post by Onoku on 2011-05-13
If I understood you correctly, you wanted me to just remove the pound sign from that one line, then save it and run update and upgrade? I did so, and I am still receiving errors.

```
onoku@onoku-MacBook:~$ sudo apt-get update && sudo apt-get upgrade
Hit http://archive.canonical.com maverick Release.gpg
Get:1 http://security.ubuntu.com maverick-security Release.gpg [198B]          
Hit http://ppa.launchpad.net maverick Release.gpg                              
Get:2 http://extras.ubuntu.com maverick Release.gpg [72B]                      
Get:3 http://iq.archive.ubuntu.com maverick Release.gpg [198B]                 
Ign http://extras.ubuntu.com/ubuntu/ maverick/main Translation-en              
Ign http://security.ubuntu.com/ubuntu/ maverick-security/main Translation-en   
Ign http://iq.archive.ubuntu.com/ubuntu/ maverick/main Translation-en          
Ign http://extras.ubuntu.com/ubuntu/ maverick/main Translation-en_US           
Ign http://archive.canonical.com/ubuntu/ maverick/partner Translation-en       
Ign http://iq.archive.ubuntu.com/ubuntu/ maverick/main Translation-en_US       
Ign http://security.ubuntu.com/ubuntu/ maverick-security/main Translation-en_US
Ign http://ppa.launchpad.net/mactel-support/ppa/ubuntu/ maverick/main Translation-en
Get:4 http://extras.ubuntu.com maverick Release [9,762B]                       
Ign http://archive.canonical.com/ubuntu/ maverick/partner Translation-en_US    
Ign http://iq.archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-en    
Err http://extras.ubuntu.com maverick Release                                  
  
Ign http://ppa.launchpad.net/mactel-support/ppa/ubuntu/ maverick/main Translation-en_US
Hit http://archive.canonical.com maverick Release.gpg                          
Ign http://iq.archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ maverick-security/multiverse Translation-en
Hit http://ppa.launchpad.net maverick Release                                  
Ign http://iq.archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en    
Ign http://security.ubuntu.com/ubuntu/ maverick-security/multiverse Translation-en_US
Ign http://iq.archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en_US 
Ign http://archive.canonical.com/ maverick/partner Translation-en    
Hit http://ppa.launchpad.net maverick/main Sources                   
Ign http://archive.canonical.com/ maverick/partner Translation-en_US 
Ign http://iq.archive.ubuntu.com/ubuntu/ maverick/universe Translation-en
Ign http://security.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en
Hit http://ppa.launchpad.net maverick/main i386 Packages             
Hit http://archive.canonical.com maverick Release                    
Ign http://iq.archive.ubuntu.com/ubuntu/ maverick/universe Translation-en_US   
Ign http://security.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en_US
Hit http://archive.canonical.com maverick Release                    
Get:5 http://iq.archive.ubuntu.com maverick-updates Release.gpg [198B]
Ign http://iq.archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en 
Hit http://archive.canonical.com maverick/partner i386 Packages
Ign http://security.ubuntu.com/ubuntu/ maverick-security/universe Translation-en
Ign http://iq.archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en_US
Hit http://archive.canonical.com maverick/partner i386 Packages
Ign http://security.ubuntu.com/ubuntu/ maverick-security/universe Translation-en_US
Ign http://iq.archive.ubuntu.com/ubuntu/ maverick-updates/multiverse Translation-en
Ign http://iq.archive.ubuntu.com/ubuntu/ maverick-updates/multiverse Translation-en_US
Get:6 http://security.ubuntu.com maverick-security Release [31.4kB]
Err http://security.ubuntu.com maverick-security Release
  
Ign http://iq.archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en
Ign http://iq.archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en_US
Ign http://iq.archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en
Ign http://iq.archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en_US
Get:7 http://iq.archive.ubuntu.com maverick Release [39.8kB]
Err http://iq.archive.ubuntu.com maverick Release
  
Get:8 http://iq.archive.ubuntu.com maverick-updates Release [31.4kB]
Err http://iq.archive.ubuntu.com maverick-updates Release
  
Fetched 670B in 3s (200B/s)
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: http://extras.ubuntu.com maverick Release: The following signatures were invalid: BADSIG 16126D3A3E5C1192 Ubuntu Extras Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: http://security.ubuntu.com maverick-security Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: http://iq.archive.ubuntu.com maverick Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: http://iq.archive.ubuntu.com maverick-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/maverick-security/Release  

W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/maverick/Release  

W: Failed to fetch http://iq.archive.ubuntu.com/ubuntu/dists/maverick/Release  

W: Failed to fetch http://iq.archive.ubuntu.com/ubuntu/dists/maverick-updates/Release  

W: Some index files failed to download, they have been ignored, or old ones used instead.
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

```edit: maybe I didn't understand this > Open the software sources as I described, edit them to maverick, and  click them on, we will presume that they are all maverick compatible. I opened the file, deleted the pound sign, saved it, closed it then ran the update and upgrade.

---

### Post by wilee-nilee on 2011-05-13
```
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: http://extras.ubuntu.com maverick Release: The following signatures were invalid: BADSIG **16126D3A3E5C1192** Ubuntu Extras Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: http://security.ubuntu.com maverick-security Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: http://iq.archive.ubuntu.com maverick Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: http://iq.archive.ubuntu.com maverick-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/maverick-security/Release  

W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/maverick/Release  

W: Failed to fetch http://iq.archive.ubuntu.com/ubuntu/dists/maverick/Release  

W: Failed to fetch http://iq.archive.ubuntu.com/ubuntu/dists/maverick-updates/Release  

W: Some index files failed to download, they have been ignored, or old ones used instead.
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
```

First I'm using the key number as a example as how to get it first line top of reply; insert each additional one like the highlighted one, in individual command, here is the example using that first key.
```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 16126D3A3E5C1192
```

Run each number like the one missing like this but inserting the number, does this make sense?

Add the repositories like I suggested.

Do this all before the restricted extras, and lets see what is up then.

```
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
```
 
These errors relate to this. 

Do not have any thing open except the terminal, or synaptic or software center no installs occur with any open together.

This may happen as well if you have an update in the update manager and it is auto opened in the background. 

This can also happen if the system is doing a software update call out which is in the backgound, but may block using the one of all these normal manual install methods.

Last of all you can change the server in software sources.

I don't mind questions but I hope for complete follow through of all instructions before showing errors.

---

### Post by Onoku on 2011-05-13
I'm going to call it a night. I will have to pick this back up tomorrow after work. Thanks for your help so far, Wilee-Nilee.

edit: since you got back to me so quickly, I gave it a try. I still have some errors. It seems like it only was able to retrieve one key.

```
onoku@onoku-MacBook:~$ sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 16126D3A3E5C1192
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv-keys 16126D3A3E5C1192
gpg: requesting key 3E5C1192 from hkp server keyserver.ubuntu.com
gpg: key 3E5C1192: "Ubuntu Extras Archive Automatic Signing Key <ftpmaster@ubuntu.com>" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1
onoku@onoku-MacBook:~$ sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 40976EAF437D05B5
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv-keys 40976EAF437D05B5
gpg: requesting key 437D05B5 from hkp server keyserver.ubuntu.com
gpg: key 437D05B5: "Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>" 21 new signatures
gpg: no ultimately trusted keys found
gpg: Total number processed: 1
gpg:         new signatures: 21
onoku@onoku-MacBook:~$ sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 40976EAF437D05B5
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv-keys 40976EAF437D05B5
gpg: requesting key 437D05B5 from hkp server keyserver.ubuntu.com
gpg: key 437D05B5: "Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1
onoku@onoku-MacBook:~$ sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 40976EAF437D05B5
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv-keys 40976EAF437D05B5
gpg: requesting key 437D05B5 from hkp server keyserver.ubuntu.com
gpg: key 437D05B5: "Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1

```

So I put in all four, though I now see that the last 3 were the same key >.< 

Anyways I did that then I ran the next part, and it got a bit further than last time, but I still have errors

```
onoku@onoku-MacBook:~$ sudo apt-get update && sudo apt-get upgrade
Get:1 http://extras.ubuntu.com maverick Release.gpg [72B]
Hit http://ppa.launchpad.net maverick Release.gpg                              
Ign http://extras.ubuntu.com/ubuntu/ maverick/main Translation-en              
Get:2 http://iq.archive.ubuntu.com maverick Release.gpg [198B]                 
Ign http://extras.ubuntu.com/ubuntu/ maverick/main Translation-en_US           
Ign http://iq.archive.ubuntu.com/ubuntu/ maverick/main Translation-en          
Hit http://archive.canonical.com maverick Release.gpg                          
Get:3 http://extras.ubuntu.com maverick Release [9,762B]                       
Ign http://ppa.launchpad.net/mactel-support/ppa/ubuntu/ maverick/main Translation-en
Err http://extras.ubuntu.com maverick Release                                  
  
Get:4 http://security.ubuntu.com maverick-security Release.gpg [198B]          
Ign http://iq.archive.ubuntu.com/ubuntu/ maverick/main Translation-en_US       
Ign http://ppa.launchpad.net/mactel-support/ppa/ubuntu/ maverick/main Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ maverick-security/main Translation-en
Hit http://ppa.launchpad.net maverick Release                        
Ign http://iq.archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-en    
Hit http://ppa.launchpad.net maverick/main Sources                   
Ign http://security.ubuntu.com/ubuntu/ maverick-security/main Translation-en_US
Ign http://iq.archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-en_US 
Hit http://ppa.launchpad.net maverick/main i386 Packages                       
Ign http://security.ubuntu.com/ubuntu/ maverick-security/multiverse Translation-en
Ign http://archive.canonical.com/ubuntu/ maverick/partner Translation-en
Ign http://iq.archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en
Ign http://archive.canonical.com/ubuntu/ maverick/partner Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ maverick-security/multiverse Translation-en_US
Ign http://iq.archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en_US
Hit http://archive.canonical.com maverick Release.gpg
Ign http://security.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en
Ign http://iq.archive.ubuntu.com/ubuntu/ maverick/universe Translation-en
Ign http://archive.canonical.com/ maverick/partner Translation-en
Ign http://security.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en_US
Ign http://iq.archive.ubuntu.com/ubuntu/ maverick/universe Translation-en_US
Ign http://archive.canonical.com/ maverick/partner Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ maverick-security/universe Translation-en
Hit http://archive.canonical.com maverick Release
Get:5 http://iq.archive.ubuntu.com maverick-updates Release.gpg [198B]         
Hit http://archive.canonical.com maverick Release                             
Ign http://security.ubuntu.com/ubuntu/ maverick-security/universe Translation-en_US
Ign http://iq.archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en
Hit http://archive.canonical.com maverick/partner i386 Packages
Get:6 http://security.ubuntu.com maverick-security Release [31.4kB]
Err http://security.ubuntu.com maverick-security Release                      
  
Hit http://archive.canonical.com maverick/partner i386 Packages        
Ign http://iq.archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en_US
Ign http://iq.archive.ubuntu.com/ubuntu/ maverick-updates/multiverse Translation-en
Ign http://iq.archive.ubuntu.com/ubuntu/ maverick-updates/multiverse Translation-en_US
Ign http://iq.archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en
Ign http://iq.archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en_US
Ign http://iq.archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en
Ign http://iq.archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en_US
Get:7 http://iq.archive.ubuntu.com maverick Release [39.8kB]
Err http://iq.archive.ubuntu.com maverick Release
  
Get:8 http://iq.archive.ubuntu.com maverick-updates Release [31.4kB]
Err http://iq.archive.ubuntu.com maverick-updates Release
  
Fetched 670B in 4s (141B/s)
Reading package lists... Done
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: http://extras.ubuntu.com maverick Release: The following signatures were invalid: BADSIG 16126D3A3E5C1192 Ubuntu Extras Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: http://security.ubuntu.com maverick-security Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: http://iq.archive.ubuntu.com maverick Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: http://iq.archive.ubuntu.com maverick-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/maverick/Release  

W: Failed to fetch http://iq.archive.ubuntu.com/ubuntu/dists/maverick/Release  

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/maverick-security/Release  

W: Failed to fetch http://iq.archive.ubuntu.com/ubuntu/dists/maverick-updates/Release  

W: Some index files failed to download, they have been ignored, or old ones used instead.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  xserver-xorg-input-synaptics
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 156kB of archives.
After this operation, 8,192B of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://ppa.launchpad.net/mactel-support/ppa/ubuntu/ maverick/main xserver-xorg-input-synaptics i386 1.2.2-2ubuntu5-mactel1 [156kB]
Fetched 156kB in 31s (4,945B/s)                                                
(Reading database ... 118290 files and directories currently installed.)
Preparing to replace xserver-xorg-input-synaptics 1.2.2-2ubuntu5 (using .../xserver-xorg-input-synaptics_1.2.2-2ubuntu5-mactel1_i386.deb) ...
Unpacking replacement xserver-xorg-input-synaptics ...
Processing triggers for man-db ...
Setting up xserver-xorg-input-synaptics (1.2.2-2ubuntu5-mactel1) ...

```

Though I knew it wouldn't work, I went ahead and tried to install the restricted extras for good measure

```
onoku@onoku-MacBook:~$ sudo apt-get install ubuntu-restricted-extras
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package ubuntu-restricted-extras

```

Okay, now I really do need to go to bed. I'll give it another whirl tomorrow. Thanks so much.

---

### Post by Onoku on 2011-05-14
Still working to fix this if anyone has any more ideas it would be much appreciated.

---

### Post by Onoku on 2011-05-14
Should I just make another post in the general help forum since my problem is with the authentication keys rather than restricted extras?

edit: moved [here]("http://ubuntuforums.org/showthread.php?p=10814978#post10814978") since this is more than a media problem.

---

