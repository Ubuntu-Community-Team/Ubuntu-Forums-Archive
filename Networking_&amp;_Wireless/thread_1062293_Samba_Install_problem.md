---
title: "Samba Install problem?"
date: 2009-02-06
forum: Networking &amp; Wireless
---

### Post by ductiletoaster on 2009-02-06
I have installed Samba and i was installing these updates with this 

repository:
```
http://ppa.launchpad.net/tcarrez/ubuntu
```

when i run command:
```

sudo apt-get update

```

This is what is outputed
```

Hit http://security.ubuntu.com hardy-security Release.gpg
Ign http://security.ubuntu.com hardy-security/main Translation-en_US
Ign http://security.ubuntu.com hardy-security/restricted Translation-en_US
Hit http://us.archive.ubuntu.com hardy Release.gpg                   
Ign http://us.archive.ubuntu.com hardy/main Translation-en_US        
Ign http://ppa.launchpad.net intrepid Release.gpg                    
Ign http://ppa.launchpad.net intrepid/main Translation-en_US         
Ign http://security.ubuntu.com hardy-security/universe Translation-en_US
Ign http://security.ubuntu.com hardy-security/multiverse Translation-en_US
Hit http://security.ubuntu.com hardy-security Release                
Ign http://us.archive.ubuntu.com hardy/restricted Translation-en_US  
Ign http://us.archive.ubuntu.com hardy/universe Translation-en_US
Ign http://us.archive.ubuntu.com hardy/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com hardy-updates Release.gpg
Ign http://us.archive.ubuntu.com hardy-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com hardy-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com hardy-updates/universe Translation-en_US
Ign http://us.archive.ubuntu.com hardy-updates/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com hardy Release 
Get:1 http://ppa.launchpad.net intrepid Release [27.6kB]
Hit http://us.archive.ubuntu.com hardy-updates Release
Ign http://ppa.launchpad.net intrepid/main Packages
Hit http://ppa.launchpad.net intrepid/main Packages                            
Hit http://security.ubuntu.com hardy-security/main Packages                    
Hit http://us.archive.ubuntu.com hardy/main Packages
Hit http://security.ubuntu.com hardy-security/restricted Packages
Hit http://security.ubuntu.com hardy-security/main Sources
Hit http://security.ubuntu.com hardy-security/restricted Sources
Hit http://security.ubuntu.com hardy-security/universe Packages
Hit http://us.archive.ubuntu.com hardy/restricted Packages
Hit http://us.archive.ubuntu.com hardy/main Sources
Hit http://us.archive.ubuntu.com hardy/restricted Sources
Hit http://us.archive.ubuntu.com hardy/universe Packages
Hit http://security.ubuntu.com hardy-security/universe Sources
Hit http://security.ubuntu.com hardy-security/multiverse Packages
Hit http://security.ubuntu.com hardy-security/multiverse Sources
Hit http://us.archive.ubuntu.com hardy/universe Sources
Hit http://us.archive.ubuntu.com hardy/multiverse Packages
Hit http://us.archive.ubuntu.com hardy/multiverse Sources
Hit http://us.archive.ubuntu.com hardy-updates/main Packages
Hit http://us.archive.ubuntu.com hardy-updates/restricted Packages
Hit http://us.archive.ubuntu.com hardy-updates/main Sources
Hit http://us.archive.ubuntu.com hardy-updates/restricted Sources
Hit http://us.archive.ubuntu.com hardy-updates/universe Packages
Hit http://us.archive.ubuntu.com hardy-updates/universe Sources
Hit http://us.archive.ubuntu.com hardy-updates/multiverse Packages
Hit http://us.archive.ubuntu.com hardy-updates/multiverse Sources
Fetched 1B in 1s (1B/s)  
Reading package lists... Done

```

And when i run command:
```

sudo apt-get upgrade

```

I get this **"this is where the problem is"**
```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  libsmbclient samba samba-common smbclient
0 upgraded, 0 newly installed, 0 to remove and 4 not upgraded.

```

Now the thing is i ran this exact same thing on my other machine and it worked fine. but as u can see for somereason the packages are being **kept back**

Thanks ahead of time for your suggestions.

---

### Post by ductiletoaster on 2009-02-06
May have figured out but still would like some input...... I believe that these updates are for 8.10 only and that whould explain why they worked fine on one machine and not the other. 

I have two compters as i mentioned before one is running Ubuntu 8.10 and the other is running Ubuntu 8.04 lts. 

Agian if you dont think this is why please let me know but for now im goin to disable that repo.

---

