---
title: "How To Authenticate Wifi Network For System?"
date: 2013-04-07
forum: Networking &amp; Wireless
---

### Post by Ashfaqur Rahman on 2013-04-07
Currently i am using a wifi network.
To access wifi authentication required. So when i open firefox it give me field for id and password.I have my id and pass. I access firefox using that and i can browse or download any thing.
But when I tried to download using terminal code:
```

sudo apt-get install

```

It says "Proxy authentication required" for every server.

Also I cant download the updates using wifi it gives following errors "Installation from unauthenticated source"

How can i authenticate with my id and password for terminal or system downloads?

---

### Post by praseodym on 2013-04-07
You need to set the proxy setting of the current network in "proxy-settings"

---

### Post by Ashfaqur Rahman on 2013-04-07
I have set proxy settings from network option.I think there is no problem with proxy settings.The problem is Authentication.
if i give this code in the terminal
```

sudo apt-get update

```
It gives following error:

W: Failed to fetch [http://download.opensuse.org/repositories/home:/sarimkhan/xUbuntu_12.10/./Sources](http://download.opensuse.org/repositories/home:/sarimkhan/xUbuntu_12.10/./Sources)  407  Proxy Authentication Required

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/quantal/main/source/Sources](http://extras.ubuntu.com/ubuntu/dists/quantal/main/source/Sources)  407  Proxy Authentication Required

W: Failed to fetch [http://ppa.launchpad.net/rvm/smplayer/ubuntu/dists/quantal/main/source/Sources](http://ppa.launchpad.net/rvm/smplayer/ubuntu/dists/quantal/main/source/Sources)  407  Proxy Authentication Required

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/quantal-security/restricted/source/Sources](http://security.ubuntu.com/ubuntu/dists/quantal-security/restricted/source/Sources)  407  Proxy Authentication Required

W: Failed to fetch [http://download.opensuse.org/repositories/home:/sarimkhan/xUbuntu_12.10/./Packages](http://download.opensuse.org/repositories/home:/sarimkhan/xUbuntu_12.10/./Packages)  407  Proxy Authentication Required

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/quantal/main/binary-i386/Packages](http://extras.ubuntu.com/ubuntu/dists/quantal/main/binary-i386/Packages)  407  Proxy Authentication Required

E: Some index files failed to download. They have been ignored, or old ones used instead.

Problem Is I dont know how to authenticate with my id and pass!!!

---

### Post by praseodym on 2013-04-07
Check:

```
echo 'Acquire::http::proxy "false";' | sudo tee -a /etc/apt/apt.conf
```
Reboot and try again.

---

### Post by Ashfaqur Rahman on 2013-04-17
I have tried that but now its giving following error:

```

Ign http://download.opensuse.org ./ InRelease                                  
Ign http://dl.google.com stable InRelease                                      
Ign http://extras.ubuntu.com quantal InRelease                                                                                                 
Ign http://bd.archive.ubuntu.com quantal InRelease                                                                                             
Ign http://security.ubuntu.com quantal-security InRelease                                                                                      
Err http://extras.ubuntu.com quantal Release.gpg                                                                                               
  Something wicked happened resolving 'extras.ubuntu.com:http' (-5 - No address associated with hostname)
Ign http://bd.archive.ubuntu.com quantal-updates InRelease                                                                                     
Err http://security.ubuntu.com quantal-security Release.gpg                                                                                    
  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)

```

---

### Post by praseodym on 2013-04-17
Check:
```

cat /etc/apt/apt.conf
cat /etc/apt/sources.list
```

---

### Post by Ashfaqur Rahman on 2013-04-20
I have tried all your ideas.I am telling u in details:

After connecting to wifi. From network settings I have set network proxy manual from automatic and gave my proxy settings there(IP = 172.16.180.251 and Port = 3128).
I also click the option "Apply system wide" too.
After that When I open a browser it asks me for my wifi username and pass.After giving my username and pass I can browse from browser also can download anything from browser.
[IMG]http://www.mediafire.com/view/?myfiles#xez1kiirh22581j[/IMG]
But the problem is when I tried to download software through apt-get or try to update ubuntu, [B]I CAN'T!

[/B]When I try to install through apt-get it gives following errors:
```

sajib@MULTIVAC:~$ sudo apt-get install  uget
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  uget
0 upgraded, 1 newly installed, 0 to remove and 333 not upgraded.
Need to get 206 kB of archives.
After this operation, 705 kB of additional disk space will be used.
WARNING: The following packages cannot be authenticated!
  uget
Install these packages without verification [y/N]? y
Err http://bd.archive.ubuntu.com/ubuntu/ quantal/universe uget i386 1.8.2-1
  407  Proxy Authentication Required
Failed to fetch http://bd.archive.ubuntu.com/ubuntu/pool/universe/u/uget/uget_1.8.2-1_i386.deb  407  Proxy Authentication Required
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

```

Then I gave this code **[COLOR=#000000][FONT=Ubuntu Mono]echo 'Acquire::http::proxy "false";' | sudo tee -a /etc/apt/apt.conf [/FONT][/COLOR]**[COLOR=#000000][FONT=Ubuntu Mono]as you told before. And after that i found:
[/FONT][/COLOR]```
sajib@MULTIVAC:~$ echo 'Acquire::http::proxy "false";' | sudo tee -a /etc/apt/apt.conf
Acquire::http::proxy "false";
sajib@MULTIVAC:~$ sudo apt-get install  ugetReading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  uget
0 upgraded, 1 newly installed, 0 to remove and 333 not upgraded.
Need to get 206 kB of archives.
After this operation, 705 kB of additional disk space will be used.
WARNING: The following packages cannot be authenticated!
  uget
Install these packages without verification [y/N]? y
Err http://bd.archive.ubuntu.com/ubuntu/ quantal/universe uget i386 1.8.2-1
  Something wicked happened resolving 'bd.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Failed to fetch http://bd.archive.ubuntu.com/ubuntu/pool/universe/u/uget/uget_1.8.2-1_i386.deb  Something wicked happened resolving 'bd.archive.ubuntu.com:http' (-5 - No address associated with hostname)
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

```[COLOR=#000000][FONT=Ubuntu Mono]

After that I examined [/FONT][/COLOR]**[COLOR=#000000][FONT=Ubuntu Mono]cat /etc/apt/apt.conf [/FONT][/COLOR]**[COLOR=#000000][FONT=Ubuntu Mono]which gives this:
[/FONT][/COLOR]```
sajib@MULTIVAC:~$ cat /etc/apt/apt.conf
Acquire::http::proxy "http://172.16.180.251:3128/";
Acquire::https::proxy "https://172.16.180.251:3128/";
Acquire::ftp::proxy "ftp://172.16.180.251:3128/";
Acquire::socks::proxy "socks://172.16.180.251:3128/";
Acquire::http::proxy "false";

```[COLOR=#000000][FONT=Ubuntu Mono]
And [/FONT][/COLOR]**[COLOR=#000000][FONT=Ubuntu Mono]cat /etc/apt/sources.list [/FONT][/COLOR]**[COLOR=#000000][FONT=Ubuntu Mono]which gives:
[/FONT][/COLOR]```
sajib@MULTIVAC:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 12.10 _Quantal Quetzal_ - Release i386 (20121017.2)]/ quantal main restricted


# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://bd.archive.ubuntu.com/ubuntu/ quantal main restricted
deb-src http://bd.archive.ubuntu.com/ubuntu/ quantal main restricted


## Major bug fix updates produced after the final release of the
## distribution.
deb http://bd.archive.ubuntu.com/ubuntu/ quantal-updates main restricted
deb-src http://bd.archive.ubuntu.com/ubuntu/ quantal-updates main restricted


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://bd.archive.ubuntu.com/ubuntu/ quantal universe
deb-src http://bd.archive.ubuntu.com/ubuntu/ quantal universe
deb http://bd.archive.ubuntu.com/ubuntu/ quantal-updates universe
deb-src http://bd.archive.ubuntu.com/ubuntu/ quantal-updates universe


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://bd.archive.ubuntu.com/ubuntu/ quantal multiverse
deb-src http://bd.archive.ubuntu.com/ubuntu/ quantal multiverse
deb http://bd.archive.ubuntu.com/ubuntu/ quantal-updates multiverse
deb-src http://bd.archive.ubuntu.com/ubuntu/ quantal-updates multiverse


## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://bd.archive.ubuntu.com/ubuntu/ quantal-backports main restricted universe multiverse
deb-src http://bd.archive.ubuntu.com/ubuntu/ quantal-backports main restricted universe multiverse


deb http://security.ubuntu.com/ubuntu quantal-security main restricted
deb-src http://security.ubuntu.com/ubuntu quantal-security main restricted
deb http://security.ubuntu.com/ubuntu quantal-security universe
deb-src http://security.ubuntu.com/ubuntu quantal-security universe
deb http://security.ubuntu.com/ubuntu quantal-security multiverse
deb-src http://security.ubuntu.com/ubuntu quantal-security multiverse


## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu quantal partner
# deb-src http://archive.canonical.com/ubuntu quantal partner


## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu quantal main
deb-src http://extras.ubuntu.com/ubuntu quantal main
deb http://download.opensuse.org/repositories/home:/sarimkhan/xUbuntu_12.10/ ./
deb-src http://download.opensuse.org/repositories/home:/sarimkhan/xUbuntu_12.10/ ./

```[COLOR=#000000][FONT=Ubuntu Mono]
**AFTER THAT SAME PROBLEM STILL EXIST!!!! :(**
[/FONT][/COLOR]

---

### Post by praseodym on 2013-04-20
Did you run:

sudo apt-get update

---

### Post by Ashfaqur Rahman on 2013-04-21
I have run:
```

sudo apt-get update

```

It gives following errors:
```

Err http://extras.ubuntu.com quantal/main Sources                              
  407  Proxy Authentication Required
Err http://download.opensuse.org ./ Sources                                    
  407  Proxy Authentication Required

```

Its clearly seen that it cant authenticate.Thats what I am looking for.
How can I authenticate?

---

