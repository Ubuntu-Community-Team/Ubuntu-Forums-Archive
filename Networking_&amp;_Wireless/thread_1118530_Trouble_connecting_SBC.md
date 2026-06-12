---
title: "Trouble connecting SBC"
date: 2009-04-07
forum: Networking &amp; Wireless
---

### Post by Digital Cactus on 2009-04-07
Hello.  I'm new to both the forums and to Ubuntu/Linux in general.  I've noticed that this seems to be a common problem, but I couldn't find any answers from my searches that helped this particular curve ball.

I installed Ubuntu on a secondary machine.  I decided to use the same DSL modem (wired--ethernet) that I'm using for my XP machine--I just want a backup to connect the the outside world when things WILL go wrong with Windoze.  I used the pppoeconf in terminal and it seems to find my ethernet card with no problems and sets up rather easily.  But when I try to surf I'm being redirected to the dreaded AT&T Change Password page (someone here MUST know of this page--god I hate it).  It seems that when you get your username or password wrong enough times AT&T in their infinite wisdom sees fit to lock you out.  Further--the little symbol showing a connection in the upper right corner isn't visible either (just a quick detail that I'm wondering about).

Now, if I plug my XP machine back in, it handles the connection fine.  I thought that maybe there was a file on my Ubuntu machine flagging it so AT&T would return me to their page over and over, so I reinstalled Ubuntu 8.01, but to no avail.  Even with the proper name and pass I'm redirected.

On the redirect page they say I'm using an unsupported browser or some such--I don't think tech will help with Linux based stuff.

Is there anyone that can help?  It'd be much appreciated--I'm pretty excited about digging into the Ubuntu world, but I'm pretty dead in the water without a connection.

Thanks in advance.

---

### Post by superprash2003 on 2009-04-07
you could try this out.. im not sure if this would work.. its usually the ISP's DNS servers which redirect you to that page.. so try changing your DNS servers to opendns - 208.67.222.222 and 208.67.220.220 .. maybe that might stop it

For reference : [http://www.prash-babu.com/2008/04/how-to-configure-dns-servers-in-linux.html](http://www.prash-babu.com/2008/04/how-to-configure-dns-servers-in-linux.html)

---

### Post by Digital Cactus on 2009-04-07
Hey Super--thanks for the response.

I checked out that blog and entered the commands it suggests--however, when I enter the gedit part I get this:

# Configuration file for /sbin/dhclient, which is included in Debian's
#	dhcp3-client package.
#
# This is a sample configuration file for dhclient. See dhclient.conf's
#	man page for more information about the syntax of this file
#	and a more comprehensive list of the parameters understood by
#	dhclient.
#
# Normally, if the DHCP server provides reasonable information and does
#	not leave anything out (like the domain name, for example), then
#	few changes must be made to this file, if any.
#

send host-name "<hostname>";
#send dhcp-client-identifier 1:0:a0:24:ab:fb:9c;
#send dhcp-lease-time 3600;
#supersede domain-name "fugue.com home.vix.com";
#prepend domain-name-servers 127.0.0.1;
request subnet-mask, broadcast-address, time-offset, routers,
	domain-name, domain-name-servers, domain-search, host-name,
	netbios-name-servers, netbios-scope, interface-mtu;
#require subnet-mask, domain-name-servers;
#timeout 60;
#retry 60;
#reboot 10;
#select-timeout 5;
#initial-interval 2;
#script "/etc/dhcp3/dhclient-script";
#media "-link0 -link1 -link2", "link0 link1";
#reject 192.33.137.209;

#alias {
#  interface "eth0";
#  fixed-address 192.5.5.213;
#  option subnet-mask 255.255.255.255;
#}


This is a sample configuration file?  How do I edit the correct file if so?  I did add the proper DNS at the end and saved it, but when I restarted, as you can see, it isn't there.  Any suggestions as to how to proceed?  Thanks again.

---

### Post by superprash2003 on 2009-04-08
well .. are you sure you saved it correctly?? go to file->save and save.. does it give any error while saving.. it's supposed to retain that line there..

---

### Post by Digital Cactus on 2009-04-08
I saved it--but it wasn't changed on reboot (I'll try again and see if it works).

Either way, I solved the problem--I just hard-reset the modem and went from there.  Everything seems to be working fine now.

When connected should there be a connect icon in the upper right?--it seems to be permanently gone.

Thanks for the help Super.

---

