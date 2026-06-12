---
title: "Connect to Server Error"
date: 2010-02-15
forum: Networking &amp; Wireless
---

### Post by Neezer on 2010-02-15
Hi,

I am trying to establish an ssh connection to my server. I have a regular ssh connection working through the command line, so I know my key works and I have the port forwarding on the router correct.

When I go to Places -> Connect to Server the window comes up properly. The only problem is that the drop down menu only has one option in it for Service Type. It is Custom Location. I have had this set up in the past and there were other options there. I chose the ssh connection and everything was fine. Now it doesn't work.

I have tried to completely uninstall nautilus and reinstall it, but that didn't work. When I did uninstall it, I uninstalled gnome-session as well, and I reinstalled that one too.

Any suggestions on how to fix this problem?

---

### Post by Neezer on 2010-02-15
Not sure what the protocol is for bumping a thread around here is, but bump...

---

### Post by lavinog on 2010-02-15
in the places bar in nautilus you can use:
ssh://address
where address is the server address

---

### Post by lavinog on 2010-02-15
> **Neezer said:**
> 
I have tried to completely uninstall nautilus and reinstall it, but that didn't work. When I did uninstall it, I uninstalled gnome-session as well, and I reinstalled that one too.


Try installing the ubuntu-desktop package. That should get things back to normal.

---

### Post by Neezer on 2010-02-15
> **lavinog said:**
> in the places bar in nautilus you can use:
ssh://address
where address is the server address

When I try ssh://192.168.1.105 from my home network I get an error from nautilus

Could not display ssh://192.168.1.105
Nautilus cannot handle "ssh" locations

When I try to look up ubuntu-desktop in synaptic I don't see anything.


**EDIT:**
Just noticed that search in synaptic is slow...or something. So I'm installing it now.

---

### Post by Neezer on 2010-02-15
Well, I was hoping that was it, but I still cannot change the option on the drop down menu from Custom Location.

could this be due to the kernel that I'm using? I did recently upgrade kernels. that is really the only thing that I can think of that I changed.

---

### Post by Iowan on 2010-02-15
Which version/kernel are you using? I just tried connecting to my server via this Hardy machine and a Karmic machine - both list the SSH option under Places>Connect to Server. Both were successful.(Doesn't help you, but I now know it can be done...)

---

### Post by Neezer on 2010-02-15
> **Iowan said:**
> Which version/kernel are you using? I just tried connecting to my server via this Hardy machine and a Karmic machine - both list the SSH option under Places>Connect to Server. Both were successful.(Doesn't help you, but I now know it can be done...)

I know it can be done too! I had it working 4 weeks ago. The two kernels that I have tried are 2.6.31-17 and 2.6.31-19.

Thanks

---

### Post by Neezer on 2010-02-15
A bump on this problem for the evening crew???

---

### Post by lavinog on 2010-02-15
test out this:
create a new user.
login with that user.
see if it works.
If it does, then it is a user configuration issue. (usually deleting the nautilus config folder will fix this)

---

### Post by Neezer on 2010-02-15
> **lavinog said:**
> test out this:
create a new user.
login with that user.
see if it works.
If it does, then it is a user configuration issue. (usually deleting the nautilus config folder will fix this)

How do I create a new user?

---

### Post by Neezer on 2010-02-15
Sorry about the double posts. 

I made a user named test with the users and groups application in System -> Administrator.

when I logged into the new user account I had the same problem. The drop down menu only had the Custom Location option on it.

---

### Post by lavinog on 2010-02-15
> **Neezer said:**
> Sorry about the double posts. 

I made a user named test with the users and groups application in System -> Administrator.

when I logged into the new user account I had the same problem. The drop down menu only had the Custom Location option on it.

Ok, well that narrows it down.

Is gvfs-backends installed?

[apt://gvfs-backends](apt://gvfs-backends)

---

### Post by Neezer on 2010-02-15
> **lavinog said:**
> Ok, well that narrows it down.

Is gvfs-backends installed?

[apt://gvfs-backends](apt://gvfs-backends)



I tried to install it with sudo apt-get and got an error.

```

nathan@lappy:~$ sudo apt-get install gvfs-backends
[sudo] password for nathan: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  gvfs-backends: Depends: gvfs (= 1.4.1-0ubuntu1) but 1.5.1-0ubuntu1~ppa2 is to be installed
E: Broken packages


```

I can't install it with synaptic either.

---

### Post by ant2ne on 2010-02-15
start with the basics. You never established that you can ping the server. So...
```
ping {servername}
```
then 
```
ping {serverIP}
```
Then at the server lets do a 
```
ps -A | grep ssh
```and lets hope there is a sshd

---

### Post by Neezer on 2010-02-15
> **ant2ne said:**
> start with the basics. You never established that you can ping the server. So...
```
ping {servername}
```
then 
```
ping {serverIP}
```
Then at the server lets do a 
```
ps -A | grep ssh
```and lets hope there is a sshd



Well, here we go...

```

nathan@lappy:~$ ping server
ping: unknown host server


nathan@lappy:~$ ping 192.168.1.105
PING 192.168.1.105 (192.168.1.105) 56(84) bytes of data.
64 bytes from 192.168.1.105: icmp_seq=1 ttl=64 time=10.4 ms
64 bytes from 192.168.1.105: icmp_seq=2 ttl=64 time=0.164 ms
64 bytes from 192.168.1.105: icmp_seq=3 ttl=64 time=2.33 ms
64 bytes from 192.168.1.105: icmp_seq=4 ttl=64 time=0.164 ms
64 bytes from 192.168.1.105: icmp_seq=5 ttl=64 time=0.156 ms
64 bytes from 192.168.1.105: icmp_seq=6 ttl=64 time=0.147 ms
64 bytes from 192.168.1.105: icmp_seq=7 ttl=64 time=2.28 ms
64 bytes from 192.168.1.105: icmp_seq=8 ttl=64 time=0.170 ms
64 bytes from 192.168.1.105: icmp_seq=9 ttl=64 time=0.160 ms
64 bytes from 192.168.1.105: icmp_seq=10 ttl=64 time=0.164 ms

nathan@server:~$ ps -A | grep ssh
 1201 ?        00:00:00 sshd
 6606 ?        00:00:00 sshd
 6664 ?        00:00:00 sshd


```

---

### Post by Neezer on 2010-02-15
I know that the ssh connection to the server is working...I can ssh all I want from the terminal. I can use scp for secure copy to the server. I just can't choose options when trying to connect to server through nautilus.

---

### Post by ant2ne on 2010-02-15
sorry, i just now read where you say, > I have a regular ssh connection working through the command line So this isn't a connection or network issue, but an issue with nautilis. 

I should comment that you are not pinging the server by name. So if you try to connect via ssh or nautilis by name, it will probably fail also.

Nautilis isn't my area of expertise. *anthropologically bows out*

---

### Post by lavinog on 2010-02-15
> **Neezer said:**
> 
```

  gvfs-backends: Depends: gvfs (= 1.4.1-0ubuntu1) but 1.5.1-0ubuntu1~ppa2 is to be installed

```

It looks like you are using a ppa that is conflicting with everything.

can you post /etc/apt/sources.list

---

### Post by Neezer on 2010-02-15
> **lavinog said:**
> It looks like you are using a ppa that is conflicting with everything.

can you post /etc/apt/sources.list

Here is my sources.list file

```

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ karmic main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ karmic-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ karmic universe
deb http://us.archive.ubuntu.com/ubuntu/ karmic-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ karmic multiverse
deb http://us.archive.ubuntu.com/ubuntu/ karmic-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu karmic partner
deb-src http://archive.canonical.com/ubuntu karmic partner

deb http://security.ubuntu.com/ubuntu karmic-security main restricted
deb http://security.ubuntu.com/ubuntu karmic-security universe
deb http://security.ubuntu.com/ubuntu karmic-security multiverse

```

---

### Post by lavinog on 2010-02-15
sorry you should post /etc/apt/sources.list.d/* also:
```

cat /etc/apt/sources.list.d/*

```

---

### Post by Neezer on 2010-02-15
> **lavinog said:**
> sorry you should post /etc/apt/sources.list.d/* also:
```

cat /etc/apt/sources.list.d/*

```


Here it is

```

nathan@lappy:~$ cat /etc/apt/sources.list.d/*
deb http://dl.google.com/linux/deb/ stable main
# channel for the jaunty partner channel
# 
#:description:This channel contains the partner software for jaunty 
deb http://archive.canonical.com/ubuntu karmic partner
# channel for the jaunty partner channel
# 
#:description:This channel contains the partner software for jaunty 
deb http://archive.canonical.com/ubuntu jaunty partner
# channel for the jaunty partner channel
# 
#:description:This channel contains the partner software for jaunty 
deb http://archive.canonical.com/ubuntu karmic partner
# kaivalagi's ppa
# sudo wget -q http://www.kaivalagi.com/m-buck-conky-jaunty.list -O /etc/apt/sources.list.d/m-buck-conky-jaunty.list
# wget -q http://www.kaivalagi.com/m-buck-conky-key.gpg -O- | sudo apt-key add -
# kaivalagi's ppa
# sudo wget -q http://www.kaivalagi.com/m-buck-conky-jaunty.list -O /etc/apt/sources.list.d/m-buck-conky-jaunty.list
# wget -q http://www.kaivalagi.com/m-buck-conky-key.gpg -O- | sudo apt-key add -
deb http://ppa.launchpad.net/m-buck/conky/ubuntu jaunty main
deb-src http://ppa.launchpad.net/m-buck/conky/ubuntu jaunty main
# kaivalagi's ppa
# sudo wget -q http://www.kaivalagi.com/m-buck-conky-jaunty.list -O /etc/apt/sources.list.d/m-buck-conky-jaunty.list
# wget -q http://www.kaivalagi.com/m-buck-conky-key.gpg -O- | sudo apt-key add -
## Please report any bug on https://bugs.launchpad.net/medibuntu/
deb http://packages.medibuntu.org/ karmic free non-free #Medibuntu - Ubuntu 9.10 "karmic koala"
# deb-src http://packages.medibuntu.org/ karmic free non-free #Medibuntu (source) - Ubuntu 9.10 "karmic koala"
## Please report any bug on https://bugs.launchpad.net/medibuntu/
deb http://packages.medibuntu.org/ jaunty free non-free #Medibuntu - Ubuntu 9.04 "jaunty jackalope"
deb-src http://packages.medibuntu.org/ jaunty free non-free #Medibuntu (source) - Ubuntu 9.04 "jaunty jackalope"
## Please report any bug on https://bugs.launchpad.net/medibuntu/
deb http://packages.medibuntu.org/ karmic free non-free #Medibuntu - Ubuntu 9.10 "karmic koala"
# deb-src http://packages.medibuntu.org/ karmic free non-free #Medibuntu (source) - Ubuntu 9.10 "karmic koala"
# This file makes sure that Opera Browser is kept up-to-date
# as part of regular system upgrades

deb http://deb.opera.com/opera/ stable non-free

# The line above will make sure you get all final public releases.
# Uncomment the following line if you want to get alpha and beta
# releases, too.

# deb http://deb.opera.com/opera-beta/ stable non-free


```

---

### Post by lavinog on 2010-02-15
I don't see a ppa active that should cause the gvfs issue, but I do see a coupld of sources for jaunty instead of karmic which could cause problems.

try this command:
```

apt-cache policy gvfs

```

I get this:
```

gvfs:
  Installed: 1.4.1-0ubuntu1
  Candidate: 1.4.1-0ubuntu1
  Version table:
 *** 1.4.1-0ubuntu1 0
        500 http://us.archive.ubuntu.com karmic/main Packages
        100 /var/lib/dpkg/status

```

---

### Post by Neezer on 2010-02-15
> **lavinog said:**
> I don't see a ppa active that should cause the gvfs issue, but I do see a coupld of sources for jaunty instead of karmic which could cause problems.

try this command:
```

apt-cache policy gvfs

```

I get this:
```

gvfs:
  Installed: 1.4.1-0ubuntu1
  Candidate: 1.4.1-0ubuntu1
  Version table:
 *** 1.4.1-0ubuntu1 0
        500 http://us.archive.ubuntu.com karmic/main Packages
        100 /var/lib/dpkg/status

```


I get this
```

nathan@lappy:~$ apt-cache policy gvfs
gvfs:
  Installed: 1.5.1-0ubuntu1~ppa2
  Candidate: 1.5.1-0ubuntu1~ppa2
  Version table:
 *** 1.5.1-0ubuntu1~ppa2 0
        100 /var/lib/dpkg/status
     1.4.1-0ubuntu1 0
        500 http://us.archive.ubuntu.com karmic/main Packages


```

One thing about the Jaunty stuff in the files, I did an upgrade to Karmic from Jaunty. i didn't do a fresh install of 9.10.

---

### Post by lavinog on 2010-02-16
basically you need gvfs-backends installed to get sftp (ssh) support with the connect ot server.  I removed it from a test install, and now I only have the custom location option like you mentioned.

the error you got is that gvfs-backends from the repository requires version 1.4.1-0ubuntu1, but some how you installed 1.5.1-0ubuntu1~ppa2 (which is newer)
I do not know why or where you got the newer version, but if you recently tried to setup an iphone, I would bet it had something to do with getting it to connect.

---

### Post by Neezer on 2010-02-16
I recently tried to set up an ipod touch. 

Can I just uninstall the newer one, remove the stuff from the ipod touch, then install the correct one? I didn't get the ipod touch working properly anyways.

I am not really sure about how to safely go through this process. Though.

---

### Post by lavinog on 2010-02-16
I am not sure of a safe way to do it.
Do you have the link to what you were following when you installed it?
Maybe I can try it out on a test platform.

---

### Post by Neezer on 2010-02-16
I have tried via synaptic to remove the 1.5.1 version of the file, but when I select it for removal, there are a BUNCH of other things that are going to automatically be removed along with it...things that really look like I need them. 

if I do it via command line will it remove all those other things too?

---

### Post by lavinog on 2010-02-16
Yes.
A lot of things depend on gvfs...there is a way to roll back to an older version, but I have never needed to do it before.

---

### Post by lavinog on 2010-02-16
In synaptic see if you can use the "force version" option under the package menu.

---

### Post by Neezer on 2010-02-18
So when I choose to remove the version 1.5.1 it tells me that I need to remove all kinds of dependencies. I have went through synaptic and listed each program or package that is going to be removed....I'm wondering if the packages will reinstall when I choose version 1.4.1 to install it, or if I'm going to just have to install them all individually....will I run into problems?

contact-lookup-applet
evolution
evolution-couchdb
evolution-exchange
evolution-indicator
evolution-plugins
firefox-3.0-gnome-support
firefox-3.5-gnome-support
firefox-gnome-support
f-spot
gdm
gdm-guest-session
gnome-about
gnome-alsamixer
gnome-applets
gnome-orca
gnome-panel
gnome-pilot
gnome-pilot-conduits
gnome-power-manager
gnome-session
gnome-utils
gnucash
gvfs
gvfs-bin
gvfs-fuse
indicator-applet
indicator-applet-session
indicator-messages
indicator-session
libbonoboui2-0
libgail-gnome-module
libgnome2-0
libgnome2.24-cil
libgnome2-perl
libgnomepanel2.24-cil
libgnome-pilot2
libgnomeui-0
libgfvscommon0
liblpint-bonobo0
libpanel-applet2-0
mousetweaks
nautilus
nautilus-share
python-gnome2
python-gnome2-desktop
python-gnomeapplet
python-pyatspi
rhythmbox
seahorse-plugins
system-config-printer-gnome
tomboy
ubuntu-desktop
usb-creator
usb-creator-gtk
vinagre
xulrunner-1.9.1-gnome-support


So that is the list....If removed those, would I be able to install them all back after putting the proper version gvfs?

---

### Post by lavinog on 2010-02-18
You should be able to install ubuntu-desktop to put them back.  Installing gvfs will not automatically add them back.
since gnome-panel will be removed, you might need to run synaptic by pressing alt-f2 and typing gksu synaptic

---

### Post by Neezer on 2010-02-18
GOT IT!!!

I had my list of everything removed, so I just used synaptic to remove it and then I went through the alpabetical list of ALL in synaptic to make sure that everything removed was installed again. 

It is working just the way it ought to!

Thanks for the help. I was really worried that when I restarted my computer it wasn't going to come back into the desktop and I'd have to wrestle with command line to get everything back.

---

### Post by lavinog on 2010-02-19
glad it worked.

---

