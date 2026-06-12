---
title: "eth1 gone from network interface"
date: 2006-05-26
forum: Networking &amp; Wireless
---

### Post by dspring on 2006-05-26
I think I screwed this up yesterday in terminal and upon reboot the eth1 does not show up in the networking interface anymore so it can be selected. Anyone know how to correct this? Get it to show up again?

thanks,
David

---

### Post by MrChonks on 2006-05-26
Take a look at /etc/interfaces and see what is in there.  Let us know if there is anything in there for eth1.  Better yet, just post the contents here.

---

### Post by dspring on 2006-05-26
[QUOTE=MrChonks]Take a look at /etc/interfaces and see what is in there.  Let us know if there is anything in there for eth1.  Better yet, just post the contents here.[/QUOTE]

HMMM. I don't have that folder. I have the latest updates to Dapper Drake as of today, I did get some yesterday while trying to get the wireless working, after reboot eth1 was gone from the networking window. Cards light was on before.

David

---

### Post by MrChonks on 2006-05-26
interfaces is a file in the etc directory.  If you do a cat of that file, you can then copy the output to here by just typing in what you see.

---

### Post by dspring on 2006-05-26
dspring@laptop:/etc$ dir
acpi                  group                openalrc
adduser.conf          group-               openoffice
adjtime               gshadow              opt
aide                  gshadow-             orbitrc
airstrikerc           gtk                  pam.conf
aliases               gtk-2.0              pam.d
aliases.db            gxine                pango
alternatives          hal                  paper.config
anacrontab            hdparm.conf          papersize
apm                   host.conf            passwd
apt                   hostname             passwd-
apt.conf.d            hosts                pcmcia
at.deny               hosts.allow          perl
bash.bashrc           hosts.deny           pmount.allow
bash_completion       hp                   pnm2ppa.conf
bash_completion.d     iftab                popularity-contest.conf
belocs                imlib                postfix
bluetooth             inetd.conf           power
bonobo-activation     init.d               ppp
brlapi.key            inittab              printcap
brltty                inputrc              profile
brltty.conf           iproute2             protocols
ca-certificates.conf  irssi.conf           python2.4
calendar              issue                qt3
cdrecord              issue.net            rc0.d
chatscripts           java                 rc1.d

Am I in the wrong place? Is it missing?
David

---

### Post by MrChonks on 2006-05-26
sorry...too early for me.  go to etc/network.  interfaces is in there.

---

### Post by dspring on 2006-05-26
[QUOTE=MrChonks]sorry...too early for me.  go to etc/network.  interfaces is in there.[/QUOTE]
That's ok!
here it is:
auto lo
iface lo inet loopback


iface eth0 inet dhcp




iface eth1 inet dhcp
wireless-essid 2WIRE700
wireless-key 1777698029

david

---

### Post by MrChonks on 2006-05-26
Let me ask you this: What is eth1?  Is it a wireless card or on board nic?  Also, what are you connecting to?  Router?

---

### Post by Iowan on 2006-05-26
[QUOTE=dspring]That's ok!
here it is:
[COLOR="Red"]auto lo[/COLOR]
iface lo inet loopback


iface eth0 inet dhcp




iface eth1 inet dhcp
wireless-essid 2WIRE700
wireless-key 1777698029

david[/QUOTE]
Still a rookie here - wonder if **auto eth0** and/or **auto eth1** would help?

---

### Post by MrChonks on 2006-05-26
give it a shot.  can't hurt at this point.

---

### Post by dspring on 2006-05-26
eth1 is the wireless card to the wireless dsl router
eth0 is the ethernet connected directly to wireless dsl router through ethernet cable

I'll try changing those to auto and see.
david

---

### Post by MrChonks on 2006-05-26
ok, then what you need to try is iwconfig and post the output.

---

### Post by dspring on 2006-05-26
how do i change the permissions or change the files using root
david

---

### Post by MrChonks on 2006-05-26
sudo chmod 755 <filename>

---

### Post by dspring on 2006-05-26
[QUOTE=dspring]how do i change the permissions or change the files using root
david[/QUOTE]
dspring@laptop:~$ sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

dspring@laptop:~$

---

### Post by MrChonks on 2006-05-26
looks like it isn't picking up your wireless card at all.  What kind of wireless card is it?

---

### Post by dspring on 2006-05-26
Having problem getting root access to edit this file.
david

---

### Post by MrChonks on 2006-05-26
Do this:

sudo passwd root

That will help you change the password for root users (which likely hasn't been done yet).

Then, once you do that, type the following command:

su root

That will prompt you for the password you just set.  Then you will be in super user mode (like root).

---

### Post by dspring on 2006-05-26
ok got that done, just so I don't make any mistakes can you walk me through this?
david

---

### Post by MrChonks on 2006-05-26
ok, first let's see what the following command gives us:

lspci -v | grep Ethernet

---

### Post by dspring on 2006-05-26
[QUOTE=MrChonks]ok, first let's see what the following command gives us:

lspci -v | grep Ethernet[/QUOTE]


root@laptop:/home/dspring# lspci -v | grep Ethernet
0000:0b:02.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8169 Gigabit Ethernet (rev 10)
root@laptop:/home/dspring#

---

### Post by MrChonks on 2006-05-26
Ok, that looks to be eth0 for you, thus the wireless is just not being recognized.  Can you tell me what kind of wireless card it is?  Also, try the following command and let me know what you get:

sudo cardctl ident

---

### Post by dspring on 2006-05-26
[QUOTE=MrChonks]Ok, that looks to be eth0 for you, thus the wireless is just not being recognized.  Can you tell me what kind of wireless card it is?  Also, try the following command and let me know what you get:

sudo cardctl ident[/QUOTE]

Its a broadcom 4306.

root@laptop:/home/dspring# sudo cardctl ident
Socket 0:
  no product info available
root@laptop:/home/dspring#

looks broken somewhere, card does work in windows xp as I tried to make sure the card was still working before the posts.
david

---

### Post by MrChonks on 2006-05-26
[http://ubuntu.cafuego.net/dists/dapper-cafuego/bcm43xx/]("http://ubuntu.cafuego.net/dists/dapper-cafuego/bcm43xx/")

Try this.  Here is the general contents of the page:

Section bcm43xx

Working firmware files to use with Dapper kernels and Broadcom 4306 based wireless controllers.

You can use apt to download and install the packages. Use the following lines in /etc/apt/sources.list and use the command sudo apt-get update to enable downloading from this section.

Don't forget to read the notice on the frontpage!
deb [http://ubuntu.cafuego.net/](http://ubuntu.cafuego.net/) dapper-cafuego bcm43xx
deb-src [http://ubuntu.cafuego.net/](http://ubuntu.cafuego.net/) dapper-cafuego bcm43xx
Packages

bcm43xx-firmware
    Version:	1.1-0ubuntu1
    Source (dsc):	bcm43xx-firmware_1.1-0ubuntu1.dsc
    Source (tar.gz):	bcm43xx-firmware_1.1-0ubuntu1.tar.gz
bcm43xx-firmware
    Description:	Broadcom 43xx Firmware More...

    This package contains firmware for use with broadcom 4306 based wireless controllers and the Dapper kernel.

    This package contains firmware for use with broadcom 4306 based wireless controllers and the Dapper kernel.
    Package:	bcm43xx-firmware_1.1-0ubuntu1_all.deb

So, what I would do is get your wired connection working so that you can get the firmware and then set it up from there.  Let me know how it goes or if you have any questions.

---

### Post by dspring on 2006-05-26
should mention that yesterday before this all broke, on another post regarding the wireless set up I was told to blacklist ndiswrapper and the original broadcom drivers, then go to the Dapper wireless set up page and download the drivers and install from the link there, this worked good up to a point and got the card light on which I have been unable to do until then so I was closer than ever. Would the blacklisting have anything to do with it? 
david

---

### Post by MrChonks on 2006-05-26
It might, but I don't know for sure.  If you look at /var/log/messages and see if there are any failures or errors associated with your wireless card, that could tell us something, as well.

---

### Post by dspring on 2006-05-26
[QUOTE=MrChonks][http://ubuntu.cafuego.net/dists/dapper-cafuego/bcm43xx/]("http://ubuntu.cafuego.net/dists/dapper-cafuego/bcm43xx/")

Try this.  Here is the general contents of the page:

Section bcm43xx

Working firmware files to use with Dapper kernels and Broadcom 4306 based wireless controllers.

You can use apt to download and install the packages. Use the following lines in /etc/apt/sources.list and use the command sudo apt-get update to enable downloading from this section.

Don't forget to read the notice on the frontpage!
deb [http://ubuntu.cafuego.net/](http://ubuntu.cafuego.net/) dapper-cafuego bcm43xx
deb-src [http://ubuntu.cafuego.net/](http://ubuntu.cafuego.net/) dapper-cafuego bcm43xx
Packages

bcm43xx-firmware
    Version:	1.1-0ubuntu1
    Source (dsc):	bcm43xx-firmware_1.1-0ubuntu1.dsc
    Source (tar.gz):	bcm43xx-firmware_1.1-0ubuntu1.tar.gz
bcm43xx-firmware
    Description:	Broadcom 43xx Firmware More...

    This package contains firmware for use with broadcom 4306 based wireless controllers and the Dapper kernel.

    This package contains firmware for use with broadcom 4306 based wireless controllers and the Dapper kernel.
    Package:	bcm43xx-firmware_1.1-0ubuntu1_all.deb

So, what I would do is get your wired connection working so that you can get the firmware and then set it up from there.  Let me know how it goes or if you have any questions.[/QUOTE]

Ok I'll try that again and see where it leads me next.
Thanks, will let you know.
david

---

### Post by dspring on 2006-05-26
Ok, couldn't get it with apt-get so I checked with a search in synaptic package manager and it shows that this is already installed (yesterday) from the same source and lists all the installed files. I could completely remove and reinstall if you think that would help? Mainly I just want to repair this problem with the Network Settings interface not showing eth1 anymore then I can tackle getting the wireless working, don't have a problem with the eth0 ethernet direct cable connection. 
Maybe this is a config problem? Not sure where to turn next.

---

### Post by MrChonks on 2006-05-26
so previously someone told you to blacklist the original drivers so that the new ones you downloaded can take hold?

---

### Post by dspring on 2006-05-26
yes, black list the drivers from the windows cd.
david

---

### Post by MrChonks on 2006-05-26
hrm...ok.  How about this.  Try going through the following guide step by step and put the results from each step into here so that we can see where the failure is occurring:

[https://wiki.ubuntu.com/WirelessTroubleshootingGuide]("https://wiki.ubuntu.com/WirelessTroubleshootingGuide")

---

### Post by dspring on 2006-05-26
[QUOTE=MrChonks]hrm...ok.  How about this.  Try going through the following guide step by step and put the results from each step into here so that we can see where the failure is occurring:

[https://wiki.ubuntu.com/WirelessTroubleshootingGuide]("https://wiki.ubuntu.com/WirelessTroubleshootingGuide")[/QUOTE]

I'll do that next but wanted to remind all the the ndiswrapper was also blacklisted..which I would like to also know how you bring back from blacklisting to usable state using terminal.
david

---

### Post by MrChonks on 2006-05-26
Try looking at the blacklist file under /etc/modprobe.d/ and see if it is listed in there.

---

### Post by dspring on 2006-05-26
[QUOTE=dspring]I'll do that next but wanted to remind all the the ndiswrapper was also blacklisted..which I would like to also know how you bring back from blacklisting to usable state using terminal.
david[/QUOTE]

lshw turned up the following..
 *-network:0
                description: Ethernet interface
                product: RTL-8169 Gigabit Ethernet
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 2
                bus info: pci@0b:02.0
                logical name: eth0
                version: 10
                serial: 00:c0:9f:de:56:69
                size: 100MB/s
                capacity: 1GB/s
                width: 32 bits
                clock: 66MHz
                capabilities: bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegociation
                configuration: autonegociation=on broadcast=yes driver=r8169 driverversion=2.2LK duplex=full ip=192.168.1.67 link=yes multicast=yes port=twisted pair speed=100MB/s
                resources: ioport:5000-50ff iomemory:c8209400-c82094ff irq:50
           *-network:1 UNCLAIMED
                description: Network controller
                product: BCM4306 802.11b/g Wireless LAN Controller
                vendor: Broadcom Corporation
                physical id: 3
                bus info: pci@0b:03.0
                version: 03
                width: 32 bits
                clock: 33MHz
                resources: iomemory:c8206000-c8207fff irq:5

---

### Post by MrChonks on 2006-05-26
See if this helps:

[http://www.mepislovers.org/modules/newbb/viewtopic.php?topic_id=14994&forum=34&post_id=103158#forumpost103158]("http://www.mepislovers.org/modules/newbb/viewtopic.php?topic_id=14994&forum=34&post_id=103158#forumpost103158")

---

### Post by dspring on 2006-05-26
I'm looking at everything.
Question, how do I remove the broadcom driver folder in /etc/ndiswrapper, 
I tried rm in terminal as root but it won't remove. I have used synaptic to reinstall ndiswrapper utils and the other related file and also the broadcom drivers for Dapper. I think I'll use synaptic to remove them but good to know how in terminal.
I'm going to reinstall the original drivers from the win cd which is in my home files to see if this gets recognized, if that doesn't work I'll do some more reading in these links but it sounds like ndiswrapper has something to do with it not showing up too.

David

---

### Post by dspring on 2006-05-26
Also lets go back to that problem with gaining root access to change the iface to auto, I still can't edit that file from gedit so is there a way to get access in gedit or could I change it from terminal and how?

David

---

### Post by dspring on 2006-05-26
[QUOTE=dspring]Also lets go back to that problem with gaining root access to change the iface to auto, I still can't edit that file from gedit so is there a way to get access in gedit or could I change it from terminal and how?

David[/QUOTE]

Correct me if I am wrong here but if I log out as user and login as root can this be done that way? And will the files changed be changed in the users or just in root?
david

---

### Post by MrChonks on 2006-05-26
yeah, I would just logout and login as root.  That will take care of that problem.

---

### Post by dspring on 2006-05-26
In my case here I had to reinstall the ndiswrapper utils and the ndisgtk and also the dapper broadcom drivers for my 4306 wireless card. Then I used the deb installer on the bcm43xx-firmware_1.1-0ubuntu1_all.deb file in my /home/dsping location by right clicking and using the open with "Gdebi package installer, this put the firmware into the /lib/firmware folder. This brought the eth1 wireless back into the Network Settings gui. Whew! What a pain to figure out! Being a newbie still I did have some problems with terminal commands for getting the firmware into the /lib/firmware folder... thats when I used the Gdebi package installer, went to the folder and checked and viola there they were, checked the gui and eth1 was there. Only took better part of the day. Now if I can just get the light back on I'll be where I was yesterday. Thanks guys for your help and the links, a bunch of reading did help expand my knowledge!

David

---

### Post by MrChonks on 2006-05-27
Glad to hear it David.

---

