---
title: "apt-get through proxy"
date: 2006-04-17
forum: Networking &amp; Wireless
---

### Post by djgenesis on 2006-04-17
Hi all, i am running my hoary behind a windows XP NAT machine and it is using WINPROXY (a software for windows anyway) to connect my windows clients into the network . 
The problem i am facing is that although firefox is working properly after i put the correct proxy settings in the connection settings, i can't seem to run apt-get correctly . 
Here is the output when i am trying to download and install something:
```

genesis@ubuntuj:~$ sudo apt-get update
Err http://archive.ubuntu.com hoary Release.gpg
  Temporary failure resolving ‘archive.ubuntu.com’
Err http://wine.sourceforge.net binary/ Release.gpg
  Temporary failure resolving ‘wine.sourceforge.net’
Err http://us.archive.ubuntu.com hoary Release.gpg
  Temporary failure resolving ‘us.archive.ubuntu.com’
Err http://security.ubuntu.com hoary-security Release.gpg
  Temporary failure resolving ‘security.ubuntu.com’
Ign http://archive.ubuntu.com hoary Release
Err http://us.archive.ubuntu.com hoary-updates Release.gpg
  Temporary failure resolving ‘us.archive.ubuntu.com’
Ign http://wine.sourceforge.net binary/ Release
Ign http://security.ubuntu.com hoary-security Release
Ign http://archive.ubuntu.com hoary/multiverse Packages
Ign http://us.archive.ubuntu.com hoary Release
Ign http://security.ubuntu.com hoary-security/main Packages
Ign http://wine.sourceforge.net binary/ Packages
Ign http://archive.ubuntu.com hoary/multiverse Sources
Ign http://us.archive.ubuntu.com hoary-updates Release
Ign http://security.ubuntu.com hoary-security/restricted Packages
Err http://wine.sourceforge.net binary/ Packages
  Temporary failure resolving ‘wine.sourceforge.net’
14% [Connecting to us.archive.ubuntu.com] [Connecting to security.ubuntu.com] [Connecting to archive.ubuntu.com]


```


On the other hand, synaptic has no problem connecting whatsoever. 
I can go to google through firefox but if i ping or dig it off the command line, i don't get anything. 

In the /etc/resolv.conf i have as registered DNS 192.168.0.1 


P.S. the windows machine is running SOCKS 4 proxy with 192.168.0.1


Do i need to set any proxy options from my command line ?

I tried to play around and i inserted in the command

```

genesis@ubuntuj:~$ http_proxy=192.168.0.1:80

and 

genesis@ubuntuj:~$ proxy=192.168.0.1:80

```
but this obviously didn't help. Have i done/put something on my system that i shouldn't have with the above commands?

How can i fix this problem ?


Thanks a lot 
GenXX

---

### Post by JonnyRo on 2006-04-17
Is the windows box also providing DNS proxy services?  If it isnt, you are going to have strange name resolution errors.

Try this if you can get your resolv.conf stuff figured out.
```

export http_proxy="http://192.168.0.1:80"
apt-get upgrade

```

---

### Post by djgenesis on 2006-04-17
It worked!!! Thanks a lot!
Ummmmmmmmmm... kinda stupid question to ask but.... umm... what did i just do ? :) And is the change permanent? And how do i make it permanent/change it/remove it?

---

### Post by JonnyRo on 2006-04-18
The change is not permenant.  It only lasts in the shell window that you opened.  If you want to make it happen every time you open a terminal, you will have to modify your .bashrc file.  Just do some searching for bashrc on google:

[http://www.tldp.org/LDP/abs/html/sample-bashrc.html](http://www.tldp.org/LDP/abs/html/sample-bashrc.html)

For example, if in your bashrc file you put the above mentioned command
```

export http_proxy="http://myproxy:myport"

```
Then every time you open a terminal, that would be set up.

---

### Post by djgenesis on 2006-04-18
Seems to be working swell !! Thanks again :D

---

### Post by vinfred on 2006-04-20
set the http_proxy environment variable or set the http value in /etc/apt/apt.conf

see section 6 in [http://www.us.debian.org/doc/manuals/reference/reference.en.html](http://www.us.debian.org/doc/manuals/reference/reference.en.html)

vinfred

---

