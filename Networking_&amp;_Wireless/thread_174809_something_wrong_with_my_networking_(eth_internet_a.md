---
title: "something wrong with my networking (eth internet and Apache )"
date: 2006-05-12
forum: Networking &amp; Wireless
---

### Post by medya on 2006-05-12
i had problem with my apache, after one time that it worked it stopped working.
when I entered [http://localhost](http://localhost)  it said time out.

it did 4 pages discussions on the ubuntu forum and couldnt make apache work .
I reinstalled ubuntu and again it worked just one time and was broke down again.

whatever... after 2 weeks, I asked some nice guys in  apachefriends.org for help , now I can run apache but I have to do somethings every time ....
I have to enter this command everytime that I start my ubuntu .
[B]sudo ifconfig lo up
[/B]

this is not my only networking problem I have eht0 problem too , whenever I start ubuntu, I have to manualy Activate the Eth0 in Sysyem/Admin/networking
and it is so painfull ... why my eth0 doesnt start working at startup automaticly.


there should be something wrong with my ubuntu .anybody can help ?

---

### Post by Iowan on 2006-05-12
Unfortunately, I'm nowhere near my Ubuntu box, so I can only point in the general direction:  Somewhere (probably under System/Admin) is an option to edit what programs launch on startup.  Unless someone comes along with more specifics (I hope they do...), I'll post better directions when I get home.

---

### Post by medya on 2006-05-13
hello ? just nod if you can hear me.

---

### Post by medya on 2006-05-14
so nobody is gonna help me ?

---

### Post by medya on 2006-05-14
I am waiting for answer

---

### Post by medya on 2006-05-15
ok so nobody knows how to fix this problem ?

---

### Post by mpvano on 2006-05-15
Medya:

I'm just another Ubuntu user like you, but I may be able to talk you through fixing your problem if we can figure out what it is.

Normally, your network interfaces are started up in two different ways. At startup, some interfaces are already present and running very early in the bootup process. 

These interfaces are usually enabled when the entire networking system is turned on. I believe this occurs because the command "ifup -a" is given during that process.

You can read how this works and how to control what happens by reading the man pages for "ifup" and "interfaces". The scripts named "ifup" and "ifdown" enable and disable the correct interfaces  depending on what they find in a text file called "interfaces" in the directory "/etc/network".

/etc/network/interfaces is owned by the root user in Ubuntu and to make changes to it you must use the privileges of the root user by prefixing commands to modify it with the word "sudo". 

"sudo" is a program that runs the rest of the command line it is given with all the privileges (and dangers) of the use of the root account. The first account created in Ubuntu automatically is set up to be allowed to use the "sudo" command. To give commands using "sudo" you must prove you are really the user allowed to use it by giving the password for your account the first time you use a sudo command. 

Once you are authorized, you can use sudo for a few minutes without giving your password again, but after a short timeout period, you will be prompted again for your password if you try to use it.

One of the kinds of lines you can put into /etc/network/interfaces begins with the line "auto" (see "man interfaces" for full details). Interfaces listed in such lines are enabled during startup when the "ifup -a" is given during the startup process. Interfaces NOT listed in a line like that, but described elsewhere in that file are DISABLED at this time (but may be enabled later).

You can examine the file by opening a terminal window and giving the command
[INDENT]"sudo cat /etc/network/interfaces".[/INDENT]

Here's a portion of my "interfaces" file.

[INDENT]
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

auto lo wlan0 eth1

# The loopback network interface
iface lo inet loopback
[/INDENT]

It causes any interfaces described later in the file named "lo", wlan0" or "eth1" to be enabled during startup without any other event triggering their startup.

Other interfaces may be started in other ways at a later time during startup, but the type of lines shown  above are usually the only ones involved in the startup of "lo" (and any other cards loaded early in the boot process).

If the driver is NOT present at the time the bootup command is given, the auto line will NOT succeed in enabling the driver.

It is usual to have at LEAST the "lo" device described this way, since nothing else is likely to occur to cause it to be enabled.

Make sure the line:
[INDENT]
     iface lo inet loopback
[/INDENT]
is present, (it probalby is), since it DEFINES the lo interface.

Make sure "lo" is listed in  an auto line. If there are NO auo lines add one like this:
[INDENT]
    auto lo
[/INDENT]


I can't really tell you how to enable your eth devices without more information about how they are loaded, however many common interfaces are loaded during the boot process as well and are started up by having their names listed in an "auto" line like this.
[INDENT]
auto lo eth0
[/INDENT]
Sometimes there are two separate lines like this:
[INDENT]
auto lo
...

auto eth0
[/INDENT]

It's also important however that you do NOT automatically start interfaces you do NOT want running at bootup.

If you inadvertantly startup an interface that you do NOT want to use at bootup, it may become the default for some operations, and this too, can cause your networking to appear to fail at startup.

You can edit the /etc/network/interfaces file using the following command:
[INDENT]
sudo gedit /etc/network/interfaces
[/INDENT]
The behavior of interfaces AFTER initial startup can be quite confusing because there are many programs that can be installed to control the interfaces and to detect them as they are plugged in, unplugged, or connected to their cables. Often interfaces are detected late in the bootup process by automatic hardware search damons like hotplug or the pcmcia card slot drivers.

Without knowing more about your machine, it's hard to give you any advice about any other interfaces, but I think this posting should help you get your lo device running and possibly your eth0, as well.

hope this helps,

Mario

---

### Post by medya on 2006-05-16
Hey I finalled fixed my problem I know many other ppl who have the same problem , here is how to fix it !

1- edit your /etc/network/interfaces   by a Sudo and a gedit
> sudo gedit /etc/network/interfaces


OR if you have leafpad (like me):
> sudo leafpad /etc/network/interfaces

2-find this line
> auto eth0

move that line to the first line of the file .
thats all . now restart and enjoy my tutorial ! 

here is how my file looks like if you need more help :
> 
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
# added by pppoeconf
auto eth0

auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
	script grep
	map eth0

# The primary network interface
iface eth0 inet dhcp

auto dsl-provider
iface dsl-provider inet ppp
provider dsl-provider


    pre-up /sbin/ifconfig eth0 up # line maintained by pppoeconf

---

