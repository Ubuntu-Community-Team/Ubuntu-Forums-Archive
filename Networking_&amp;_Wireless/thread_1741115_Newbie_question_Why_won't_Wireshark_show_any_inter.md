---
title: "Newbie question: Why won't Wireshark show any interfaces in"
date: 2011-04-27
forum: Networking &amp; Wireless
---

### Post by rocksockdoc on 2011-04-27
I installed Wireshark 1.2.7 on my Lenovo X61 tablet PC running Ubuntu 10.04 lucid during the quest for a decent signal strength meter for available wifi access points. 
- [**What is a good software or hardware method to TEST WiFi strength & power?**]("http://ubuntuforums.org/showthread.php?t=1739093")

But I can't get Wireshark to do the simplest thing, which is to "Capture Interfaces".

The Wireshark "Capture -> Interfaces" command always comes up empty.

What am I doing wrong?

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=190194&stc=1&d=1303944991[/IMG]

---

### Post by bab1 on 2011-04-27
> **rocksockdoc said:**
> I installed Wireshark 1.2.7 on my Lenovo X61 tablet PC running Ubuntu 10.04 lucid during the quest for a decent signal strength meter for available wifi access points. 
- [**What is a good software or hardware method to TEST WiFi strength & power?**]("http://ubuntuforums.org/showthread.php?t=1739093")

But I can't get Wireshark to do the simplest thing, which is to "Capture Interfaces".

The Wireshark "Capture -> Interfaces" command always comes up empty.

What am I doing wrong?

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=190194&stc=1&d=1303944991[/IMG]

Run Wireshark as root:```
alt+f2>> gksudo wireshark
```

---

### Post by josephmills on 2011-04-27
please take a look at 
[https://www.youtube.com/watch?v=GH8QDoI7rkU](https://www.youtube.com/watch?v=GH8QDoI7rkU)
[https://www.youtube.com/watch?v=U6ZveV0nDpk&feature=fvwrel](https://www.youtube.com/watch?v=U6ZveV0nDpk&feature=fvwrel)
[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=wireshark&as_qdr=m6&sa=Google+Search&lang=en](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=wireshark&as_qdr=m6&sa=Google+Search&lang=en)

---

### Post by rocksockdoc on 2011-04-29
> **bab1 said:**
> Run Wireshark as root

That did the trick!
```
$ sudo wireshark &
```

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=190329&stc=1&d=1304056692[/IMG]

---

### Post by rocksockdoc on 2011-04-29
> **josephmills said:**
> please take a look at 

Ooops. Now I see that I should have used "gksudo" (as originally explained).

I had never heard of "gksudo" before. 

```
$gksudo wireshark &
```

Now it's time to start learning what each of these lines means in the wireshark output as I'm trying to find a signal-strength meter for my Ubuntu 10.04 laptop:
- [**What is a good software or hardware method to TEST WiFi strength & power?**]("http://ubuntuforums.org/showthread.php?p=10735996#post10735996")

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=190400&stc=1&d=1304094773[/IMG]

---

### Post by 1000_isles on 2011-05-05
Hey all, a question here. I have a similar issue with Xlink kai, I can only run this app as root. Is there a secutiry risk? How can you make a user/add permissions, to use the network, I would rather not leave the app in root.
Thanks

---

### Post by josephmills on 2011-05-05
> **1000_isles said:**
> Hey all, a question here. I have a similar issue with Xlink kai, I can only run this app as root. Is there a secutiry risk? How can you make a user/add permissions, to use the network, I would rather not leave the app in root.
Thanks

please open your terminal and type in ```
man sudo 
```
is there a risk yes there is you have to weigh your options. some programs need to run at root because they need total control. I am not a great pentester or anything like that so I dont go to root (that much) but I am tring to learn. bodi wrote a thing about going into root here it is [http://ubuntuforums.org/showthread.php?t=1486138](http://ubuntuforums.org/showthread.php?t=1486138)

---

### Post by rocksockdoc on 2011-05-06
One problem, I found, using sudo as root to run a graphical program, is that it screws up your later login by changing the ownership to root of certain user dot files.
- [What is the function of the ICEauthority file /home/username/.ICEauthority]("http://ubuntuforums.org/showthread.php?t=1743473")

Based on my research of this common problem, the file-permission switch to root only seems to occur using sudo with 'some' graphical programs. However, it's hard to remember 'which' graphical programs cause the file-ownersihp-and-permission problem so the net advice is (from my research trying to solve this myself) to never use sudo with a graphical program.

Use gksudo instead. 

Having said that, I do wish we could run wireshark without having to be root. :(

---

### Post by Slave2Metal on 2011-05-06
Interfaces will load at every run, as non root.
```
sudo apt-get install libcap2-bin wireshark
sudo chgrp admin /usr/bin/dumpcap
sudo chmod 750 /usr/bin/dumpcap
sudo setcap cap_net_raw,cap_net_admin+eip /usr/bin/dumpcap
```

---

### Post by rocksockdoc on 2011-05-06
> **Slave2Metal said:**
> Interfaces will load at every run, as non root.
```
sudo apt-get install libcap2-bin wireshark
sudo chgrp admin /usr/bin/dumpcap
sudo chmod 750 /usr/bin/dumpcap
sudo setcap cap_net_raw,cap_net_admin+eip /usr/bin/dumpcap
```

Wow. I had never heard of the '/sbin/setcap" command before but those steps worked to allow wireshark to see the interfaces sans being root.

However, even after reading the manpage, I'm still not sure what 'setcap' actually does.
> ```
 NAME
       setcap - set file capabilities

SYNOPSIS
       setcap [-q] [-v] (capabilities|-|-r) filename [ ... capabilitiesN fileN ]

DESCRIPTION
       In the absence of the -v (verify) option setcap sets the capabilities of each specified filename to the capa&#8208;
       bilities specified.  The -v option is used to verify that the specified capabilities are currently associated
       with the file.

       The capabilities are specified in the form described in cap_from_text(3).

       The  special  capability  string,  '-',  can be used to indicate that capabilities are read from the standard
       input. In such cases, the capability set is terminated with a blank line.

       The special capability string, '-r', is used to remove a capability set from a file.

       The -q flag is used to make the program less verbose in its output.

```There are no ubuntuforums threads 'tagged' with "setcap"; and, surprisingly, none in the title. However there are plenty of posts with setcap in them, most about getting Wireshark to display interfaces without being root!

[LIST]
[*][Wireshark - how to see capture interface as non-root?]("http://ubuntuforums.org/#%20http://ubuntuforums.org/showthread.php?t=1086288&highlight=setcap")
[*]                                  [**Wireshark Security Root Privileges**]("http://ubuntuforums.org/showthread.php?t=1438538&highlight=setcap")
[*]                                  [**Wireshark group and user question**]("http://ubuntuforums.org/showthread.php?t=1558456&highlight=setcap")
[/LIST]
etc.

So I'll have to dig elsewhere to find out what setcap actually does. (this is work in progress):

[LIST]
[*][Sniffing with Wireshark as a Non-Root User]("http://packetlife.net/blog/2010/mar/19/sniffing-wireshark-non-root-user/")
[*][Platform-Specific information about capture privileges]("http://wiki.wireshark.org/CaptureSetup/CapturePrivileges")
[*][Wireshark Security]("http://wiki.wireshark.org/Security")
[*][Linux capabilities ]("http://ftp.kernel.org/pub/linux/libs/security/linux-privs/kernel-2.4/capfaq-0.2.txt")
[/LIST]
etc.

Notable quotes ... 

> Setting network privileges for dumpcap
1. Ensure your linux kernel and filesystem supports File Capabilities and also you have installed necessary tools.
2. "setcap 'CAP_NET_RAW+eip CAP_NET_ADMIN+eip' /usr/bin/dumpcap"
3. Start Wireshark as non-root and ensure you see the list of interfaces and can do live capture.
Limiting capture permission to only one group
1. Create user "wireshark" in group "wireshark".
2. "chgrp wireshark /usr/bin/dumpcap"
3. chmod 754 /usr/bin/dumpcap
4. "setcap 'CAP_NET_RAW+eip CAP_NET_ADMIN+eip' /usr/bin/dumpcap"
5. Ensure Wireshak works only from root and from "wireshark" user. 			 		

> ```

http://www.wensley.org.uk/info

If you want to use wireshark from a non-root account, do setcap 
cap_net_raw=+ep /usr/bin/dumpcap. Now you can run wireshark from a normal account and choose to capture from the network.

For superuser ports, try setcap cap_net_bind_service=+ep /path/to/program

If linux is older than about 2.6.18&#8230;

You'll need to enable capabilities in Linux by editing
/usr/src/linux/include/linux/capability.h to make
CAP_INIT_EFF_SET equal to CAP_FULL_SET. Like this.

Re-compile and install linux with capabilites and commoncap modules and then
modprobe commoncap

Now you can give any program access to ports less than 1024 by executing something like
sudo setpcaps cap_net_bind_service+eip `pidof program`. The program itself
never has or gets root privieges by this way.

The realtime priority of jackd could be checked with
chrt -p `ps -C jackd -o pid=`. chrt can be found in
the schedutils package. You now see jackd bear a priority of RT within the top program.

Of course you need to allow users to do this by letting setpcaps run as root
to do its work in /etc/sudoers file.

You might co-erce Adobe Flash to try jackplug with FLASH_ALSA_DEVICE=plug:SLAVE=jack set in the 
environment variables.

Modifying your servers to use setpcaps

It may also be useful to insert a slight delay with sleep(1) in
the main() function of some programs so that setpcaps has time to do its
work before the background program attempts to bind ports under 1024.

That works in C programs, in python can put something like this near the beginning

import select
select.select([],[],[],1)

 
```

---

