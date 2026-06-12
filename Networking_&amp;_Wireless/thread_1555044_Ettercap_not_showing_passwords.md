---
title: "Ettercap not showing passwords"
date: 2010-08-17
forum: Networking &amp; Wireless
---

### Post by monty47 on 2010-08-17
Hi everyone
I used to have ettercap on backtrack 4 and everything was ok...
But on ubuntu 10.04 I'm having this issue; it is not showing passwords (if i log in for example in a forum with a http link ) and not sending false certificate (if i try to log in in https links, after uncommenting the redir ip tables in etter.conf).
Other features seems to work alright (such as dns spoofing) and the arp poisonning is succesful.
Besides, Wireshark gets the passwords.
Any ideas?
thanks for your replies

---

### Post by monty47 on 2010-08-17
after some research I used "iptables -t nat -A PREROUTING -p tcp --destination-port 80 -j REDIRECT --to-port 10000" while ettercap was on, and its behaviour is a bit weird ; I successfully got the facebook user and password that I've input in the machine I was sniffing (https link, this time the certificate process went on) but still no password on http links.
Sometimes I get this message "SEND L3 ERROR: 93 byte packet (0800:11) destined to 172.16.1.1 was not forwarded (libnet_write_raw_ipv4(): -1 bytes written (Operation not permitted)
)"

I tried to uninstall firewall and reinstall iptables but no improvements.
And another thing I noticed is that I can't sniff passwords input by the attacker (when the target is set on the router and no second target), while it is possible on backtrack.

Don't see what I'm doing wrong, I've done it millions of times back then but somehow it's not working...

---

### Post by monty47 on 2010-08-21
I did a clean install of ubuntu (10.04.1) and tested ettercap another time and the problem is still there.
I forgot to mention that I'm using Thimoty Redaelli's fixed version ([https://launchpad.net/~timothy-redaelli/+archive/drizzt/+packages](https://launchpad.net/~timothy-redaelli/+archive/drizzt/+packages)) since the version on the backtrack repo crashes when scanning for hosts on ubuntu.
Maybe the problem is comming from this version...(all other plugins seems to work well though).
Has anyone managed to make ettercap work on ubuntu 10.04 ?

---

### Post by bastienvans on 2010-09-14
hey man, I am in the same boat as you. Have you figured out anything? It works fine in BT4, but not ubuntu 10.0.4

Thanks!

---

### Post by monty47 on 2010-09-24
I gave up on ubuntu 10.04 but it seems to work on the Ubuntu 10.10 (beta) version, though updating some packets (python I think ,but not sure) made ettercap crash once again after scanning hosts.
I'm waiting for the final version of 10.10 to see if it will still be working.

---

### Post by kapiljhajhria on 2010-10-22
same with me dude...i have upgraded to latest version of Ubuntu but still same problem...after scanning for host it just crashes

---

### Post by monty47 on 2010-10-23
try to use the ettercap version from the link i posted in my 3rd message.
It won't crash after scanning for hosts but http sniffing doesn't seem to work, can you confirm this?

---

### Post by monty47 on 2010-10-23
Good and bad news guys. I managed to partially solve the problem on 10.10 ; as I said before, ettercap needed python2.5 to work correctly (dunno why though), since I noticed that as soon as I upgraded python on the beta version, ettercap started to crash while scanning for hosts.That's why I wanted to install python2.5.
The problem was (dunno if you'll have the same problem)  that every time I wanted to install the python2.5 minimal package (python2.5 depends on that package) synaptic wanted to delete many other essential packages.
So I used this technique to install it ;

[http://welcometoubuntu.blogspot.com/2010/05/howto-install-python-255-on-ubuntu-1004.html](http://welcometoubuntu.blogspot.com/2010/05/howto-install-python-255-on-ubuntu-1004.html)

Now ettercap seems to be unstable, it sometime crashes after scanning hosts and sometimes it's ok...(I'm using the version from the backtrack repo, [http://moon.backtrack-linux.org/README.txt](http://moon.backtrack-linux.org/README.txt) )

---

### Post by FutureNeo on 2010-11-20
i found a solution here: [http://codenull.net/?p=153](http://codenull.net/?p=153)

---

### Post by monty47 on 2010-12-30
Hey thanks a lot FutureNeo! I've succesfully followed all the steps and it is true that ettercap sniffs passwords after this (the other computers no longer loose their connection), but I still have the crashing issue; ettercap crash 3 times over 4 after scanning hosts...

---

### Post by FutureNeo on 2011-01-24
@monty47 try to use terminal mode...


because the guy who have codenull.net change his site.. i put his post here.. the ettercap_ubuntu_fix.patch is below

> 
&#65279;&#65279;Many people told me that ettercap in Ubuntu, Debian or in other Debian-based distributions doesn't show the sniffed passwords, but the MITM attack was successful. So I decide to check what was the problem and I came accross this bug report: [Debian bug #521857]("http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=521857")

The bug acctually is in *src/protocols/ec_tcp.c* at line *119*:

```
opt_end = (u_char *)((int)tcp + tcp->off * 4);
```

***tcp*** variable is a pointer and they cast it to ***int*** data type, so in 64bit systems this actually cuts the 32 high bits of the address, so sometimes ettercap will crashes with Segmentation fault.

A guy replied with a patch that change the line *119* to:

```
opt_end = (u_char *)(tcp + tcp->off * 4);
```

which is a way too wrong and that patch cause the problem that I mention at the beginning. Fews months after another guy post another patch that change the line *119* to:

```
opt_end = (u_char *)((long)tcp + tcp->off * 4);
```

and that fixed the bug, because ***long*** data type in Linux is always the size of the registers, so in 32bit it is 4 bytes and in 64bit 8 bytes.

Because developers didn't compile it with the new patch, I created a new patch for the faulty patch and below I wrote the steps to install (or reinstall) ettercap that will work fine in 32bit and 64bit Debian/Debian-based systems.

First you must remove the old ettercap (if it's installed) and install the build dependencies that you will need for the compilation.

```
$ sudo apt-get remove ettercap ettercap-common ettercap-gtk
$ sudo apt-get build-dep ettercap
```

next you have to compile ettercap

```
$ mkdir ettercap
$ cd ettercap
$ apt-get source ettercap
$ cd ettercap-0.73
$ wget http://codenull.net/uploads/ettercap_ubuntu_fix.patch
$ patch -p1 -i ettercap_ubuntu_fix.patch
$ dpkg-buildpackage -rfakeroot -uc -b
```

now you must have three .deb files in the previous directory:

The **ettercap-common_0.7.3-1.4ubuntu1_i386.deb** which you must install it, **ettercap-gtk_0.7.3-1.4ubuntu1_i386.deb** which is ettercap with GUI support **and ettercap_0.7.3-1.4ubuntu1_i386.deb** which is ettercap without GUI support.
Of course if you are on a 64bit system filenames will end with amd64 instead of i386.

You must choose one of the last two .deb, in my example I will install the one with GUI support.

```
$ cd ..
$ sudo dpkg -i ettercap-common_0.7.3-1.4ubuntu1_i386.deb
$ sudo dpkg -i ettercap-gtk_0.7.3-1.4ubuntu1_i386.deb
```

and cleanup

```
$ cd ..
$ rm -rf ettercap
```

Thats all.. now ettercap will work fine..


**ettercap_ubuntu_fix.patch**
```

--- ettercap-0.7.3.orig/debian/patches/01_pointers_and_ints_dont_mix.diff
+++ ettercap-0.7.3/debian/patches/01_pointers_and_ints_dont_mix.diff
@@ -7,6 +5,6 @@
     
     opt_start = (u_char *)(tcp + 1);
 -   opt_end = (u_char *)((int)tcp + tcp->off * 4);
-+   opt_end = (u_char *)(tcp + tcp->off * 4);
++   opt_end = (u_char *)((long)tcp + tcp->off * 4);
  
     DECODED_LEN = (u_int32)(tcp->off * 4);
```

---

### Post by udaychaitanya on 2011-03-28
hi
it seems the web address of codenull is not working and i got 404 error when i used the terminal wget command.though ubuntu fix patch for ettercap is given im unable to go into the opt directory itself.im very new to ubuntu.help me

Thank you

---

### Post by FutureNeo on 2011-03-28
i gave codenull's patch file in my previous post..

---

### Post by udaychaitanya on 2011-03-31
> **FutureNeo said:**
> i gave codenull's patch file in my previous post..
1.should i copy and paste the code into terminal? When i actually did that its giving me some errors.
2.so i have searched for src.It was in usr directory but there was no protocols in that.so i could not manually edit line 119.

please understand that i am very new to ubuntu.Your help is greatly appreciated.
Thank you

---

### Post by nova47 on 2011-04-17
None of that worked for me but here's a work around I found to work for Ubuntu 10.10 amd64

cd ~/
mkdir ettercap
cd ettercap

Go to [https://launchpad.net/~timothy-redaelli/+archive/drizzt/+buildjob/1758138](https://launchpad.net/~timothy-redaelli/+archive/drizzt/+buildjob/1758138) and download into the folder you have created

ettercap-common_0.7.3-1.4ubuntu1drizzt1_amd64.deb (312.9 KiB)
ettercap-gtk_0.7.3-1.4ubuntu1drizzt1_amd64.deb (246.1 KiB)

Now type

sudo dpkg -i *.deb

Everything should install and you should be able to run ettercap with sudo ettercap -G

---

### Post by udaychaitanya on 2011-04-18
> **nova47 said:**
> None of that worked for me but here's a work around I found to work for Ubuntu 10.10 amd64

cd ~/
mkdir ettercap
cd ettercap

Go to [https://launchpad.net/~timothy-redaelli/+archive/drizzt/+buildjob/1758138](https://launchpad.net/~timothy-redaelli/+archive/drizzt/+buildjob/1758138) and download into the folder you have created

ettercap-common_0.7.3-1.4ubuntu1drizzt1_amd64.deb (312.9 KiB)
ettercap-gtk_0.7.3-1.4ubuntu1drizzt1_amd64.deb (246.1 KiB)

Now type

sudo dpkg -i *.deb

Everything should install and you should be able to run ettercap with sudo ettercap -G

Thank you verymuch for the help.Infact i got it working following the post of FutureNeo.Since i am a noob i couldnt understand what i should i do with the ubuntu fix patch provided by codenull.After hours of working with the terminal i entered into ettercap directory and edited according to the fix.Everything was fine.You know ,though i got it working a lot of days back i was  successful only yesterday.I got the user and pass of a open wifi network victim.

It would be awesome if you tell me why after scanning 255 hosts in my subnet ettercap is showing only my router? I tried with connecting the cable .Then it scanned almost 16000 hosts and gave around 8 hosts.But i suspect they are from another subnet because ettercap shows there is no poison between me and the hosts i tested.

your help is greatly appreciated.:D

---

### Post by jl303 on 2011-05-10
I tried to patch and compile ettercap by following the post above, but I get this error. E: Could not open file /var/lib/apt/lists/ppa.launchpad.net_mangler_mangler_ubun tu_dists_maverick_main_source_Sources - open (2: No such file or directory) Can someone upload *_i386.deb ones? Thanks,  JL

---

### Post by jl303 on 2011-05-12
Anyone please?

---

### Post by alcapony007 on 2011-08-14
Hi, I really needs Your Help.  I removed ettercap and I cant get though Your tutorial. Can U write what I have to do step by step with links please? I've tried everything and it goes real bad ... thank You for help [email]alcaponymc@gmail.com[/email]

---

### Post by bpill on 2011-09-07
udaychaitanya:
Any chance of getting the (i386) ?

Thanks !

---

