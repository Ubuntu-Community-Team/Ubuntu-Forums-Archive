---
title: "kismet and/or aircrack not working on my hp 6830s"
date: 2009-01-15
forum: Networking &amp; Wireless
---

### Post by neverone on 2009-01-15
[COLOR="Green"]i admit i'm new to ubuntu, i used to have some earlier issues with my old laptop that prevented me from further exploring any linux distro.

**here's the problem**:[/COLOR]
[COLOR="Green"]
i can't get kismet to work. the problems appeared right from the start. first, by following some online tutorial i tried installing all that i should need for nice wepcracking:[/COLOR]
[B]sudo apt-get install build-essential
sudo apt-get install aircrack
sudo apt-get install kismet
sudo apt-get install airsnort
sudo apt-get install linux-source
sudo apt-get install linux-headers
sudo apt-get install sharutils[/B]

[COLOR="Green"]and here's what i got  from all of that:
[/COLOR]
[B]neverone@n1_:~$ sudo apt-get install build-essential
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
The following packages were automatically installed and are no longer required:
  libgmp3c2 liblua5.1-0 libadns1 wireshark-common
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 39 not upgraded.
neverone@n1_:~$ sudo apt-get install aircrack
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package aircrack
neverone@n1_:~$ sudo apt-get install kismet
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  festival gpsd sox
The following NEW packages will be installed:
  kismet
0 upgraded, 1 newly installed, 0 to remove and 39 not upgraded.
Need to get 0B/970kB of archives.
After this operation, 2540kB of additional disk space will be used.
Selecting previously deselected package kismet.
(Reading database ... 102360 files and directories currently installed.)
Unpacking kismet (from .../kismet_2007-10-R1-2build1_i386.deb) ...
Setting up kismet (2007-10-R1-2build1) ...
neverone@n1_:~$ sudo apt-get install airsnort
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package airsnort
neverone@n1_:~$ sudo apt-get install linux-source
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  linux-source
1 upgraded, 0 newly installed, 0 to remove and 38 not upgraded.
Need to get 26.5kB of archives.
After this operation, 0B of additional disk space will be used.
Get:1 [http://hr.archive.ubuntu.com](http://hr.archive.ubuntu.com) hardy-updates/main linux-source 2.6.24.23.25 [26.5kB]
Fetched 26.5kB in 0s (88.6kB/s)   
(Reading database ... 102425 files and directories currently installed.)
Preparing to replace linux-source 2.6.24.22.24 (using .../linux-source_2.6.24.23.25_all.deb) ...
Unpacking replacement linux-source ...
Setting up linux-source (2.6.24.23.25) ...
neverone@n1_:~$ sudo apt-get install linux-headers
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package linux-headers is a virtual package provided by:
  linux-headers-2.6.24-23-xen 2.6.24-23.46
  linux-headers-2.6.24-23-virtual 2.6.24-23.46
  linux-headers-2.6.24-23-server 2.6.24-23.46
  linux-headers-2.6.24-23-rt 2.6.24-23.46
  linux-headers-2.6.24-23-openvz 2.6.24-23.46
  linux-headers-2.6.24-23-generic 2.6.24-23.46
  linux-headers-2.6.24-23-386 2.6.24-23.46
  linux-headers-2.6.24-23 2.6.24-23.46
  linux-headers-2.6.24-22-xen 2.6.24-22.45
  linux-headers-2.6.24-22-virtual 2.6.24-22.45
  linux-headers-2.6.24-22-server 2.6.24-22.45
  linux-headers-2.6.24-22-rt 2.6.24-22.45
  linux-headers-2.6.24-22-openvz 2.6.24-22.45
  linux-headers-2.6.24-22-generic 2.6.24-22.45
  linux-headers-2.6.24-22-386 2.6.24-22.45
  linux-headers-2.6.24-22 2.6.24-22.45
  linux-headers-2.6.24-21-xen 2.6.24-21.43
  linux-headers-2.6.24-21-virtual 2.6.24-21.43
  linux-headers-2.6.24-21-server 2.6.24-21.43
  linux-headers-2.6.24-21-rt 2.6.24-21.43
  linux-headers-2.6.24-21-openvz 2.6.24-21.43
  linux-headers-2.6.24-21-generic 2.6.24-21.43
  linux-headers-2.6.24-21-386 2.6.24-21.43
  linux-headers-2.6.24-21 2.6.24-21.43
  linux-headers-2.6.24-19-xen 2.6.24-19.41
  linux-headers-2.6.24-19-virtual 2.6.24-19.41
  linux-headers-2.6.24-19-server 2.6.24-19.41
  linux-headers-2.6.24-19-rt 2.6.24-19.41
  linux-headers-2.6.24-19-openvz 2.6.24-19.41
  linux-headers-2.6.24-19-generic 2.6.24-19.41
  linux-headers-2.6.24-19-386 2.6.24-19.41
  linux-headers-2.6.24-19 2.6.24-19.41
  linux-headers-2.6.24-18-xen 2.6.24-18.32
  linux-headers-2.6.24-18-virtual 2.6.24-18.32
  linux-headers-2.6.24-18-server 2.6.24-18.32
  linux-headers-2.6.24-18-rt 2.6.24-18.32
  linux-headers-2.6.24-18-openvz 2.6.24-18.32
  linux-headers-2.6.24-18-generic 2.6.24-18.32
  linux-headers-2.6.24-18-386 2.6.24-18.32
  linux-headers-2.6.24-18 2.6.24-18.32
  linux-headers-2.6.24-16-xen 2.6.24-16.30
  linux-headers-2.6.24-16-virtual 2.6.24-16.30
  linux-headers-2.6.24-16-server 2.6.24-16.30
  linux-headers-2.6.24-16-rt 2.6.24-16.30
  linux-headers-2.6.24-16-openvz 2.6.24-16.30
  linux-headers-2.6.24-16-generic 2.6.24-16.30
  linux-headers-2.6.24-16-386 2.6.24-16.30
  linux-headers-2.6.24-16 2.6.24-16.30
You should explicitly select one to install.
E: Package linux-headers has no installation candidate
neverone@n1_:~$ sudo apt-get install sharutils
Reading package lists... Done
Building dependency tree       
Reading state information... Done
sharutils is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 38 not upgraded.
neverone@n1_:~$ 
[/B]
[COLOR="Green"]i've been trying this for couple of times, so i'm aware that some of them are already installed.

then i've read that i should edit the **kismet.conf** file before actually starting kismet, but first i checked my wifi hardware:[/COLOR]

[B]neverone@n1_:~$ dmesg | grep Wireless
[   32.929552] eth1: Broadcom BCM4315 802.11 Wireless Controller 5.10.27.6
[/B]
[COLOR="Green"]it states somewhere that broadcom is tricky business for using kismet, but that  **bcm43xx drivers** should work without problem. and i edited the .conf file so that it looks like this** (the edited part of it)**:[/COLOR]
[B]
 Kismet config file
# Most of the "static" configs have been moved to here -- the command line
# config was getting way too crowded and cryptic.  We want functionality,
# not continually reading --help!

# Version of Kismet config
version=2007.09.R1

# Name of server (Purely for organizational purposes)
servername=Kismet

# User to setid to (should be your normal user)
#suiduser=neverone

# Do we try to put networkmanager to sleep?  If you use NM, this is probably
# what you want to do, so that it will leave the interfaces alone while
# Kismet is using them.  This requires DBus support!
networkmanagersleep=true

# Sources are defined as:
# source=bcm43xx,eth0,broadcomSource
# Source types and required drivers are listed in the README under the
# CAPTURE SOURCES section.
# The initial channel is optional, if hopping is not enabled it can be used
# to set the channel the interface listens on.
# YOU MUST CHANGE THIS TO BE THE SOURCE YOU WANT TO USE
source=none,none,addme[/B]

and i saved all of this, and tried to run kismet, and here's what i've got:
[B]neverone@n1_:~$ sudo kismet
Server options:  none
Client options:  none
Starting server...
FATAL:  Could not find user 'your_user_here' for dropping priviledges.  Make sure you have a valid user set for 'suiduser' in your config file.  See the 'Installation & Security' and 'Configuration' sections of the README file for more information.
[1] + Done(1)                    ${BIN}/kismet_server --silent ${server}
Waiting for server to start before starting UI...
neverone@n1_:~$[/B] 

[COLOR="Green"]now i don't understand! **'your_user_here'** was default text in .conf file that was needed to be changed in my username, which i did! how come it doesn't work? and what does that mean about dropping priviledges?

i'm a newbie, and this may be really too advanced for my level, but please help! most of the time i spend in an apartment without a telephone, let alone any network, but via wireless i detect a mass of various networks, and i need web approach almost constantly! **PLEASE!**[/COLOR]

---

