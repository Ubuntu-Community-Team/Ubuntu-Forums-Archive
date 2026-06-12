---
title: "Ubuntu wont share!"
date: 2006-07-16
forum: Networking &amp; Wireless
---

### Post by Bios___ on 2006-07-16
As the name suggests, Ubuntu will not share the internet connection with a windows computer connected to it via a network card. 

But! Ubuntu will allow me to connect remotely from the windows machine. But the windows machine is unable to connect to the internet.

It might be something ive missed, but I am unsure, any help would be greatly appreciated.

Thanks.

---

### Post by gborzi on 2006-07-16
First, you have to enable ip forwarding, by setting the content of /proc/sys/net/ipv4/ip_forward to 1 and uncommenting the related line in sysctl.conf > #net/ipv4/ip_forward=1. Then you have to set the iptables as such:
> sudo iptables -t nat -A POSTROUTING -o ppp0 -j MASQUERADE if you use a dialup or a pppoe connection. If you have a LAN connection use ethX instead of ppp0.
More details in this post of mine
[http://www.ubuntuforums.org/showthread.php?t=212448](http://www.ubuntuforums.org/showthread.php?t=212448)

---

### Post by Bios___ on 2006-07-16
ok, I cant edit the ip_forward file, apparently I am not the owner :S

---

### Post by gborzi on 2006-07-16
To change files in /proc you must have root privileges, so:
> sudo -i
echo 1 > /proc/sys/net/ipv4/ip_forward
then edit sysctl.conf .

---

### Post by Bios___ on 2006-07-16
ok, done that. Now how do I edit sysctl.conf? 

I dont even know where to begin for that.

I do apologize.

---

### Post by gborzi on 2006-07-16
> **Bios___ said:**
> ok, done that. Now how do I edit sysctl.conf? 

I dont even know where to begin for that.


sudo gedit /etc/sysctl.conf

---

### Post by Bios___ on 2006-07-16
ok I added the line to the file, tried the windows machine and didnt work :s

Did I do something wrong?

---

### Post by gborzi on 2006-07-16
Did you give the iptables command in message #2 ? It would be helpful to know how you want to configure net. If I understood well, the ubuntu PC is connected to internet (dialup, adsl+pppoe or something else ?), then it is connected through an ethernet card to the windows PC. Is it right ? If so, you need to use a cross cable for the ubuntu <==> windows connection.

---

### Post by Malac on 2006-07-16
To be honest the easiest way I found was to use firestarter(available in the repositories) which handles all the iptable entries for you. Just enable Connection Sharing in the preferences and if you want DHCP for the clients and that was it.

Hope this helps.

---

### Post by Bios___ on 2006-07-16
sorry, I haven't been that helpful, especially when I need the help.

Firstly, I know for a fact that both PC's are connected, because I can use the Ubuntu machine remotely from the windows machine, all the wires are correct.

My set up is

Internet ---- |Router| ---- Ubuntu ----- Windows

The ubuntu machine has an internet connection.

The windows machine doesn't, but can use the ubuntu machine remotely via Ultra VNC.

And I did the *sudo sudo iptables -t nat -A POSTROUTING -o ppp0 -j MASQUERADE  * in a terminal, was that correct?

---

### Post by gborzi on 2006-07-16
> **Bios___ said:**
> sorry, I haven't been that helpful, especially when I need the help.

Firstly, I know for a fact that both PC's are connected, because I can use the Ubuntu machine remotely from the windows machine, all the wires are correct.
Do you mean you can ping the ubuntu PC from windows and/or doing ssh connections ? If so, it's fine. Remember that the gateway for windows must be the IP address of the ubuntu PC, NOT the gateway used by ubuntu. Perhaps you have already done so, but just to be sure.

> **Bios___ said:**
> 
My set up is

Internet ---- |Router| ---- Ubuntu ----- Windows

The ubuntu machine has an internet connection.

From this scheme it seems that your connection to the internet is done through an adsl router. Please check with the ifconfig command if there is a ppp0 entry. If not, then you have a LAN connection, otherwise you have a Point-to-Point connection. If possible, please post the output of ifconfig.

> **Bios___ said:**
> 
And I did the *sudo sudo iptables -t nat -A POSTROUTING -o ppp0 -j MASQUERADE  * in a terminal, was that correct?
It's correct if you are using a Point-to-Point connection. Otherwise use ethX (where ethX is the interface connected to internet) instead of ppp0.

---

### Post by Bios___ on 2006-07-16
Yup, I can ping the ubuntu machine from windows.

And the default gateways are all set up correctly, as I said, the windows machine can control the ubuntu machine remotely, it just doesnt have its own internet connection (windows machine that is).

My router is a cable/dsl router.

And for the record, the Ubuntu machine has two NIC one which handles the internet connection, then the other which handles the connection for the Windows machine. 


Also I entered this code: -
> sudo iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE

eth0 is the card that handles the windows ethernet connection. I did two variations of the above code, one with *eth0* and the other with [I]eth1[I].

And it still didnt work.

---

### Post by gborzi on 2006-07-16
So eth1 on ubuntu PC is connected to ethernet, eth0 to the windows PC. So the right command is >  sudo iptables -t nat -A POSTROUTING -o eth1 -j MASQUERADE
I think it's not working because the previous iptables commands messed the iptable. The output of iptables-save on my office PC (which is configured as a router and connected to the internet through eth0, eth1 is used to share the connection) is
> # Generated by iptables-save v1.3.3 on Tue Jun 20 13:11:12 2006
*nat
:PREROUTING ACCEPT [2606:315366]
:POSTROUTING ACCEPT [3:180]
:OUTPUT ACCEPT [72:4341]
-A POSTROUTING -o eth0 -j MASQUERADE
-A POSTROUTING -o eth0 -j MASQUERADE
COMMIT
# Completed on Tue Jun 20 13:11:12 2006
If you have something really different, then you have to clean you iptables. I don't know how to clean iptables rules, other than rebooting the ubuntu box, sorry.

---

### Post by Bios___ on 2006-07-16
How do I get that table up?

And this all going odd, wouldnt be anything to do with me having 5.10?

---

### Post by gborzi on 2006-07-16
> **Bios___ said:**
> How do I get that table up?
with > sudo iptables-save

> **Bios___ said:**
> 
And this all going odd, wouldnt be anything to do with me having 5.10?
I don't think so, I used this method on ubuntu 5.10 too.

---

### Post by Bios___ on 2006-07-16
ok,......now ive lost internet for the Ubuntu machine :S

---

### Post by gborzi on 2006-07-16
You only need to reboot, and the iptables will be cleared.

---

### Post by Bios___ on 2006-07-16
wooooooohooooooo!

I found the problem!

It was that damn /proc/sys/net/ipv4/ip_forward file!

I either forgot to change it to 1 or it did itself (probably me)

But i checked it, changed it, and it works now! I have internet on both machines!

Thank you. Thank you. Thank you. Thank you. Thank you. Thank you. Thank you. Thank you. Thank you. Thank you. Thank you. Thank you. Thank you. Thank you. Thank you. Thank you. Thank you. Thank you. Thank you. Thank you. Thank you. Thank you. Thank you. Thank you. Thank you. Thank you. Thank you. Thank you. Thank you. 

Thank you Gborzi.

*bows*

Thank you.

---

### Post by gborzi on 2006-07-16
I learned something too in this thread: that it's possible to use firestarter to get the work done. I have installed and configured it, works fine.

---

### Post by Bios___ on 2006-07-16
yea I cant even find that......

and oh this is my iptables-save

> root@ubuntu:~# iptables-save
# Generated by iptables-save v1.3.1 on Sun Jul 16 23:07:12 2006
*nat
:PREROUTING ACCEPT [89:12162]
:POSTROUTING ACCEPT [6:371]
:OUTPUT ACCEPT [398:23991]
-A POSTROUTING -o eth1 -j MASQUERADE
-A POSTROUTING -o eth1 -j MASQUERADE
COMMIT
# Completed on Sun Jul 16 23:07:12 2006


and also, for some reason ive lost connectivity from my windows machine,...so back to square one. :(

---

### Post by gborzi on 2006-07-16
> **Bios___ said:**
> yea I cant even find that......
What ? firestarter ?

> **Bios___ said:**
> 
and also, for some reason ive lost connectivity from my windows machine,...so back to square one. :(
After a reboot ? If so, check /etc/sysctl.conf for the line that enables ip forwarding and make sure iptables are restored at each boot. E.g., save the output of iptables-save to a file in /etc such as /etc/iptables-saved, then add the following lines to rc.local
> . /lib/lsb/init-functions

if [ -r /etc/iptables-saved ]; then
   log_begin_msg "Setting iptables"
   /bin/cat /etc/iptables-saved | /sbin/iptables-restore
   log_end_msg $?
fi
before the exit 0 line.

---

### Post by Bios___ on 2006-07-16
There you are, one sysctl.conf file everything that i get when i open, just so I dont mess up. lol.

> #
# /etc/sysctl.conf - Configuration file for setting system variables
# See sysctl.conf (5) for information.
#
# Be warned that /etc/init.d/procps is executed to set the following
# variables.  However, after that, /etc/init.d/networking sets some
# network options with builtin values.  These values may be overridden
# using /etc/network/options.

#kernel.domainname = example.com
#net/ipv4/icmp_echo_ignore_broadcasts=1
#net/ipv4/ip_forward=1

Im guesing the bottom line is what enables ipforwarding?

And no, I can't find Firestarter, I have looked in the repositories aswell.

---

### Post by gborzi on 2006-07-16
> **Bios___ said:**
> There you are, one sysctl.conf file everything that i get when i open, just so I dont mess up. lol.



Im guesing the bottom line is what enables ipforwarding?
Yes, you are right. Please note that simply changing that line will enable ip forwarding at next reboot, not immediately.

> **Bios___ said:**
> 
And no, I can't find Firestarter, I have looked in the repositories aswell.
If I'm not wrong it's in the universe repositories, they can be enabled from Synaptic. Look at the ubuntu guide
[https://help.ubuntu.com/ubuntu/desktopguide/C/index.html](https://help.ubuntu.com/ubuntu/desktopguide/C/index.html)

---

### Post by Bios___ on 2006-07-16
ok this is gonna sounds daft, but once again, I can't edit that file its a read only becaue im not the owner (which is silly because I am!)

So  how can I edit that file, and what do I do with the code above?

> After a reboot ? If so, check /etc/sysctl.conf for the line that enables ip forwarding and make sure iptables are restored at each boot. E.g., save the output of iptables-save to a file in /etc such as /etc/iptables-saved, then add the following lines to rc.local
Quote:
. /lib/lsb/init-functions

if [ -r /etc/iptables-saved ]; then
log_begin_msg "Setting iptables"
/bin/cat /etc/iptables-saved | /sbin/iptables-restore
log_end_msg $?
fi
before the exit 0 line.

---

### Post by Bios___ on 2006-07-16
ok i just checked my sysctl.conf, and its emptpy!

No code or anything! 

:confused:

How can I make it so im the owner, as then I can just copy and paste what i pasted on here.

---

### Post by gborzi on 2006-07-16
To edit a file owned by root you have to use *sudo <editor name> <file name>*, e.g *sudo gedit /etc/sysctl.conf*. The text editor gedit is installed by default with ubuntu.
Then, after issuing the command *sudo iptables -t nat ...*, save the iptables configuration with *sudo iptables-save > ~/iptables-saved*, copy this file in /etc, i.e. *sudo cp ~/iptables-saved /etc*, the *sudo gedit /etc/rc.local* and put the code in message #21 in it, before the exit 0 line.

---

### Post by Bios___ on 2006-07-16
when I do this:-

> To edit a file owned by root you have to use sudo <editor name> <file name>, e.g sudo gedit /etc/sysctl.conf. The text editor gedit is installed by default with ubuntu.

I get this: -

> root@ubuntu:~# sudo gedit /etc/sysctl.conf

(gedit:9380): Gtk-WARNING **: cannot open display:
root@ubuntu:~#


I dont think thats supposed to happen :confused:

---

### Post by Bios___ on 2006-07-16
ok never mind that it seems to work without going into root :confused:

I'll carry on.

---

### Post by gborzi on 2006-07-16
> **Bios___ said:**
> ok i just checked my sysctl.conf, and its emptpy!

No code or anything! 

:confused:

I'm confused too. How did it become empty ? Anyway, open it with the command *sudo gedit /etc/sysctl.conf* and put this line in it > net.ipv4.ip_forward=1 use dots instead of slashes, I remember that with the 2.6.12 kernel dots were used instead of slashes.

> **Bios___ said:**
> 
How can I make it so im the owner, as then I can just copy and paste what i pasted on here.
To copy and paste at will use _sudo_ !

---

### Post by Bios___ on 2006-07-16
ok new problem there isnt anything in rc.local

Is that right and do i just copy the code into it?

---

### Post by Bios___ on 2006-07-16
The *iptables-saved*file

> # Generated by iptables-save v1.3.1 on Mon Jul 17 00:12:59 2006
*nat
:PREROUTING ACCEPT [117:17277]
:POSTROUTING ACCEPT [11:671]
:OUTPUT ACCEPT [1283:77127]
-A POSTROUTING -o eth1 -j MASQUERADE 
-A POSTROUTING -o eth1 -j MASQUERADE 
-A POSTROUTING -o eth1 -j MASQUERADE 
-A POSTROUTING -o eth1 -j MASQUERADE 
-A POSTROUTING -o eth1 -j MASQUERADE 
COMMIT
# Completed on Mon Jul 17 00:12:59 2006

---

### Post by gborzi on 2006-07-16
> **Bios___ said:**
> ok new problem there isnt anything in rc.local

Is that right and do i just copy the code into it?

Yes, it's right. rc.local by default does nothing. But if you want to execute some command at startup, put your commands there. In dapper (ubuntu 6.06) the default content is the following:> #!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.


exit 0

---

### Post by Bios___ on 2006-07-16
Ok I pasted the code, and put *exit 0* at the end of it one line down. All ok now?

Anything I've missed? 

Or shall I just reboot and find out?

---

### Post by Bios___ on 2006-07-16
oh!
That iptables-saved file is still in /etc

Was I meant to move it? or is it ok where it is?

---

### Post by gborzi on 2006-07-16
> **Bios___ said:**
> oh!
That iptables-saved file is still in /etc

Was I meant to move it? or is it ok where it is?
No, you don't have to move it. Simply check that rc.local is executable. If it's not, make it executable. Then reboot.

---

### Post by Bios___ on 2006-07-16
rc.local is a plain text document

I dont think thats executable, how do i make it one.

I must sound really dumb lol, sorry about all of this and I am very grateful for your help.

---

### Post by gborzi on 2006-07-16
> **Bios___ said:**
> rc.local is a plain text document

I dont think thats executable, how do i make it one.

I must sound really dumb lol, sorry about all of this and I am very grateful for your help.

A plain text file can be executable. rc.local is a shell script, something like a .BAT file under DOS/Windows. To check if it is executable give the command > ls -l /etc/rc.local the  output should be something like this > -rwxr-xr-x 1 root root 631 2006-07-11 23:00 /etc/rc.local
the "x" in the first string means it is executable by the owner (the first "x"), by the members of the group (the second "x") and  by everyone (the last "x"). If there are no "x" then give this command > sudo chmod a+x /etc/rc.local
Please let me know if it's already executable, if it isn't there will be some more things to do.
BTW, you don't look dumb, only a newby, and I was a newby too, and still I am for many things.

---

### Post by Bios___ on 2006-07-17
it wasnt, I got what you said with no "x" at all, so i gave the command you gave me, and looked again and it had the "x".

So now what ?

---

### Post by gborzi on 2006-07-17
> **Bios___ said:**
> it wasnt, I got what you said with no "x" at all, so i gave the command you gave me, and looked again and it had the "x".

So now what ?

I have looked at an old ubuntu installation (5.10) and there is not rc.local there. So do the following:
> sudo mv /etc/rc.local /etc/init.d/local
sudo update-rc.d local defaults
Then reboot.

---

### Post by Bios___ on 2006-07-17
ok, I found out that in order to reset the iptables, you use the command iptables --flush.

I did that, then followed the previous instructions from the begining, and it all works now, I think it was just that.

I have a stables (well so far) connection on both computers :d

Thank you so much for your help.

---

### Post by Bios___ on 2006-07-17
oh how ironic!

Just as I posted that, my connection was lost!

Any idea why that is happening?

---

### Post by gborzi on 2006-07-17
> **Bios___ said:**
> oh how ironic!

Just as I posted that, my connection was lost!

Any idea why that is happening?

No, I have no idea. Please post the output of iptables-save, of ifconfig and of *cat /proc/sys/net/ipv4/ip_forward*. Have you moved rc.local to /etc/init.d/local and runned update-rc.d ?

---

### Post by Bios___ on 2006-07-18
Ok, I must be a huge pain now, I re-installed Linux (still 5.10) went through the previous instructions, works ok now. 

But I have found firestarter, and I was wondering will that stop me from getting signed out of MSN or is that some other problem with the windows machine?

---

### Post by gborzi on 2006-07-18
Firestarter is a firewall, so if MSN uses some ports, you have to open that ports. I don't know which ports are used by MSN, I don't use Windows since several years, so no MSN.

---

### Post by Bios___ on 2006-07-18
I havent installed Firestarter yet, I am unsure how.

---

### Post by gborzi on 2006-07-18
Use Synaptic. Have you enabled the universe repositories ?

---

### Post by Bios___ on 2006-07-18
i have, ive downloaded and installed it from the synaptic package manager, I just dont know how to enable or start, and configure it. lol.

---

### Post by gborzi on 2006-07-18
It should appear in the menu, unser Applications -> Internet . But I suggest you to learn more about GNU/Linux before using firestarter.

---

### Post by Bios___ on 2006-07-18
ok, will do, but is there any reason why I keep losing my internet connection on Ubuntu and Windows after a while? and then it just comes back :confused:

---

### Post by gborzi on 2006-07-18
> **Bios___ said:**
> ok, will do, but is there any reason why I keep losing my internet connection on Ubuntu and Windows after a while? and then it just comes back :confused:

What do you mean by losing the connection ? That your browser and other internet applications fail with a timeout message ? In this case it can be your ISP. Or do you get a message like "no route to host" ? In this case, I don't know.

---

### Post by Malac on 2006-07-19
For a really good linux replacement for MSN Messenger try aMSN it is in the repositories.

---

