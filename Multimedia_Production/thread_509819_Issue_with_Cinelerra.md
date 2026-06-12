---
title: "Issue with Cinelerra"
date: 2007-07-25
forum: Multimedia Production
---

### Post by dustcloud97 on 2007-07-25
Okay here's my issue, I've been trying to get Cinelerra installed and if somebody could post a step by step or a link to one that makes sure it works I'd appreciate it because I'm getting frustrated trying to get it to install. I've gone around in circles with the libmjpegtools0 dependency and it's really getting on my last nerve. I've reinstalled it through a download of the package from a site, then tried to remove it and reinstall it so it would come out right and I got nothing. Here's where I'm at right now in terminal

ryan@ryan-laptop:~$ sudo apt-get install cinelerra
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  cinelerra: Depends: libmjpegtools0 (>= 1:1.8.0) but it is not installable
             Depends: libquicktimehv (>= 1:2.1.0) but it is not going to be installed
             Depends: libquicktimehv (= 1:2.1.0-2svn20070520) but it is not going to be installed
E: Broken packages

Thanks in advance to whoever gives me an answer.

---

### Post by Cryophallion on 2007-07-27
Take a quick look for cinelerra under search - there have been a ton of posts on this topic:

[http://ubuntuforums.org/showthread.php?t=463275&highlight=cinelerra](http://ubuntuforums.org/showthread.php?t=463275&highlight=cinelerra)

[http://ubuntuforums.org/showthread.php?t=464223](http://ubuntuforums.org/showthread.php?t=464223)

[http://ubuntuforums.org/showthread.php?t=193086&highlight=cinelerra](http://ubuntuforums.org/showthread.php?t=193086&highlight=cinelerra)

---

### Post by dad311 on 2007-08-14
I had success by downloading the Fedora rpm (version2.0) and converting it to a deb file using Alien.  I tried the 2.1 version, but had several issues with dependencies.

---

### Post by dad311 on 2007-08-14
Here are the detailed steps to install cinelerra on AMD64:

1) Install alien  "apt-get install alien"

2)Download cinelerra from [HERE]("http://ftp.freshrpms.net/pub/freshrpms/fedora/linux/4/cinelerra/").

3) sudo alien cinelerra-2.0-0.4.20051210.2.fc4.x86_64.rpm 

4) right click on new cincelerra deb file and install.

This worked for me on cinelerra 2.0, but not 2.1.
I dont know if it makes a difference, but I have all the extra codecs install from the automatix program also.

Im also attaching a screen shot recording of the install.

---

### Post by fsman on 2007-08-15
Or just use the cinelerra repos for ubuntu!
they are listed here

[http://cvs.cinelerra.org/getting_cinelerra.php](http://cvs.cinelerra.org/getting_cinelerra.php)

Note. some people have problems with the fiesty repo.So like me just use the edgy - they work fine.

---

### Post by dad311 on 2007-08-17
Yeah, your correct.  I had issues with the Feisty sources, tried the Edgy sources, install correctly.

thx

---

