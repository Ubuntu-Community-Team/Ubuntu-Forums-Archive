---
title: "Network Problem"
date: 2006-06-24
forum: Networking &amp; Wireless
---

### Post by spveer on 2006-06-24
I am using dual boot windows xp and ubuntu linux.

Internet was working properly since I have installed ubuntu, till I have updated and installed packages yesterday. The symantec package manager was telling me about broken packages and also I dont have mp3 plugins installed. For this purpose, I thought to go for an ubuntu update. And since I have updated and upgraded, I have lost internet connection on ubuntu linux. (sad part is mp3 plugins are still missing!.. so I have gained nothing and lost network connection :(  

I get the following error:

"Please contact your system administrator to resolve the following problem
S10CGIFFCAGS error : No such device"

I have no clue how to proceed from here..... Can someone plss guide me.

Thanks in advance..
Pradeep

---

### Post by woedend on 2006-06-24
can you post the contents of /etc/network/interfaces and of /etc/iftab.

---

### Post by spveer on 2006-06-25
Hi Woedend....
Thanks for ur reply...So here r the details.......


root@laptop:/home/chandraveer # jedit /etc/network/interfaces


# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
#mapping hotplug
#	script grep
#	map eth0 
	
	
# The primary network interface
iface eth1 inet dhcp
wireless-essid open

#auto eth0
#auto eth1


iface eth0 inet static
address 84.73.196.163
netmask 255.255.252.0
gateway 84.73.196.1

auto eth0

--------------------------------------------------

root@laptop:/home/chandraveer # jedit /etc/iftab


# This file assigns persistent names to network interfaces.  See iftab(5).
eth0 mac 00:0d:60:75:c8:87
eth1 mac 00:0c:f1:41:27:da

---

### Post by spveer on 2006-06-26
Can someone pls explain me what they see from the contents I posted above?

---

### Post by woedend on 2006-06-26
sorry sincen obody else responded I will but i've been drinking shh :p.  Anyhow, what kind of cards do you have?  Wireless or wired?  
What id suggest is to open /etc/network/interfaces and add a # before every line that contains eth0(and the lines describing it, such as the ip address etc etc, and the auto line), save, then do
/etc/init.d/networking restart
if you get the same error, then take out those # and put them before eth1.
this will let oyu know exactly which device is having the problem.  It sounds like a driver issue.

---

### Post by spveer on 2006-06-27
hey woedend..

thanks 4 ur reply.
Whatever I do with eth0 and eth1, at the end /etc/init.d/networking restart is failing!

I have both wireless and wired network cards. But I am using wired connection now. How can one fix driver issues with Linux? Thing is I had proper internet connection after installation of ubuntu. I only lost it now because I made some updates, and really didnt observe/know what updates Ive been making :|

Have u been drinking because of US exit from soccer... :D
I am livin in Swiss and swiss too had to leave yesterday :(

---

### Post by woedend on 2006-06-27
no no...USA is terrible at soccer as you saw.  LAck of interest mainly...i find it mildly amusing but, we don't get behind it like other countries.
anyhow, i told you wrong...well not wrong but there is a better/easier way.  Leave your /etc/network/interfaces file as it was before.
then do
sudo ifdown eth0
sudo ifdown eth1

sudo ifup eth0
sudo ifup eth1

one at a time, see if the errors appear after both cards.  By the way, is it a broadcom card by any chance?  Ive been searching and found a possible solution to point you at if so.

---

### Post by spveer on 2006-06-27
Is something wrong with my ubuntu :(
See it doesnt recognise the command u've mentioned:

root@laptop:/home/chandraveer # sudo ifdown eth0
ifdown: failed to open statefile /var/run/network/ifstate: No such file or directory
root@laptop:/home/chandraveer # sudo ifdown eth1
ifdown: failed to open statefile /var/run/network/ifstate: No such file or directory
root@laptop:/home/chandraveer # sudo ifup eth0
ifup: failed to open statefile /var/run/network/ifstate: No such file or directory
root@laptop:/home/chandraveer # sudo ifup eth1
ifup: failed to open statefile /var/run/network/ifstate: No such file or directory
root@laptop:/home/chandraveer #


The network card is what I have got together with IBM Thinkpad 41 laptop.
- Intel(R) PRO/1000 MT Mobile Connection (Gigabit Ethernet)

What now ](*,)

---

### Post by spveer on 2006-06-27
I got some more infos... may be woedend or someone can help me with these details:

During the booting procedure I see this:
---mkdir: cannot create directory 'var/run/network'  Read only file system.

And during shutting down the PC, I see the following:
---deconfiguring network devices  FAIL

Further I have tried out the following commands

root@laptop:/home/chandraveer # ifconfig eth0 down (I hear two beeps after this command)
root@laptop:/home/chandraveer # ifconfig eth0 up (No message after this command)
root@laptop:/home/chandraveer # ifconfig eth1 down(An error message as you see now)
eth1: ERROR while getting interface flags: No such device
root@laptop:/home/chandraveer # ifconfig eth1 up
eth1: ERROR while getting interface flags: No such device

root@laptop:/home/chandraveer # /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                                         [fail]
root@laptop:/home/chandraveer #

---

### Post by spveer on 2006-07-01
waoooh..... !
My network connection on ubuntu works now:-\" 

Since I saw the following message during boot up,
---mkdir: cannot create directory 'var/run/network' Read only file system.
I created manually /var/run/network directory.... 
and now I see that eth0 is UP !:D 

----
Previously I also faced with a different problem after I have updated Ubuntu. Seemed like Xserver was not configured properly, and I had to configure that again to bring back the windows on the screen using the following command:

sudo dpkg-reconfigure xserver-xorg

I am incuding this here as the info might help someone else with similar problem.

-------
Finally I feel there is still some misconfiguration with my Ubuntu, which I see through the messages coming up during boot up.

Is there a way I can record these messages into a file, so that I could post all those messages here on the forum. I am sure you guys can definitely help me set my Ubuntu straight when you see the boot up messages. This would also give me more insight into using Ubuntu.

Thanks,
Pradeep

---

### Post by abeowitz on 2006-07-10
/var/run/network is created by /etc/init.d/loopback.  Make sure it's part of your startup.

I thought loopback was for loopback block devices, not lo0, removed it from startup and got the same error.

Optionally, install sysv-rc-conf and enable loopback.  :)

dunno if this is related to your other messages or not.

---

### Post by donpdonp on 2006-09-05
> **spveer said:**
> Is something wrong with my ubuntu :(
See it doesnt recognise the command u've mentioned:

root@laptop:/home/chandraveer # sudo ifdown eth0
ifdown: failed to open statefile /var/run/network/ifstate: No such file or directory


I attempted an upgrade from breezy to dapper. during the dist-upgrade, the packages were installing smoothly until it got ot an ip<something> package. i forget the name. at that moment i lost network connectivity and my box was hosed. i had to use the recovery mode kernel as the normal kernel froze immeadiately after loading.

once i made it to a root prompt, i got the same failed to open statefile. im currently running dpkg --connfigure -a, which dpkg told me to do since "dpkg was interrupted".

this was less than a smooth upgrade. :(

---

