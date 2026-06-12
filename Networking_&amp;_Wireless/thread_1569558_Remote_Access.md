---
title: "Remote Access"
date: 2010-09-06
forum: Networking &amp; Wireless
---

### Post by k7faq on 2010-09-06
Ok. I have spent most of the day scouring the Internet searching and trying to no avail, so here I am.

Present  objective is to configure ability to access the host pc via Remote Desktop.

I realize I am new to Linux, but am baffled as to how complicated configuring this service can be.

I appreciate any and all thoughts.

Steven

---

### Post by zpletan on 2010-09-06
What OS are the host and client systems running?

---

### Post by k7faq on 2010-09-06
Ubuntu 10.10 is the host OS.
When I go to: System | Preferences | Remote Desktop the Preferences window reports "Your desktop is only reachable over the local network. Others can access your computer using the address localhost."

I believe this indicates there is an issue with the firewall / permissions. (Which I am struggling with greatly.)

Thanks.

---

### Post by MaindotC on 2010-09-07
You are likely on a home network that has an access point (AP) as a gateway.  The AP is performing something called Network Address Translation so multilple devices on your network can communicate with services on the Internet using on public IP address.  If you're not familiar with networking concepts this may be difficult to grasp.

You'd need to log into your AP and map the 5900 port to the machine in which you want to connect remotely.  Are you familiar with these procedures?

---

### Post by k7faq on 2010-09-07
I reviewed the Router configs and added 5900 port forwarding to the pc.

There remains no change in status. Remote Desktop Preferences still reports desktop is accessible to localhost only.

---

### Post by MaindotC on 2010-09-07
It says that regardless.  Try remoting in using your public IP.

---

### Post by k7faq on 2010-09-07
ahhh. Rookie misunderstanding. 

When I connect via SSH I am able to authenticate into the desktop.
When I connect via VNC I receive a box message "Connection to host 10.100.99.10 was closed."

It seems VNC is my current issue

Additionally I can not connect to the notebook via SSH or VNC.

Thanks.

---

### Post by MaindotC on 2010-09-07
The notebook has to have openssh-server installed and remote desktop configured as I directed earlier.

If 10.100.99.10 is your IP address then you don't have the AP configured properly.  I scanned and found nothing open.  If you want to access your laptop and your desktop via vnc, and you've already forwarded the 5900 port to your desktop, then you need to forward an additional port to your laptop (such as 5901) and you need to configure your laptop to receive incoming remote desktop requests on 5901, and you need to configure the client you are using to establish a remote connection to use port 5901.

The same thing goes for ssh.  If you want to access both machines from your public ip address then they each must have a separate port to use.

---

### Post by pricetech on 2010-09-07
Please don't expose VNC to the Internet.  It's a security risk.

You never answered the part about what OS is the "client".

---

### Post by scorp123 on 2010-09-07
Maybe this thread is useful to you?
[http://ubuntuforums.org/showthread.php?p=9806309#post9806309](http://ubuntuforums.org/showthread.php?p=9806309#post9806309)

---

### Post by k7faq on 2010-09-09
strAlan, yes openssh-server is installed on both the desktop and notebook.

> **scorp123 said:**
> Maybe this thread is useful to you?
[http://ubuntuforums.org/showthread.php?p=9806309#post9806309](http://ubuntuforums.org/showthread.php?p=9806309#post9806309)

Having skimmed through some information about NX it seems long term a viable solution to the big picture. [https://help.ubuntu.com/community/FreeNX](https://help.ubuntu.com/community/FreeNX)

Ok. I have tried following the directions as they are listed. 

While processing the sudo apt-get update I get several errors that I am not sure how to work past:
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources  
  404  Not Found
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main i386 Packages
  404  Not Found
N: Ignoring file 'freenx-team-ppa-maverick.list.save' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
W: Failed to fetch [http://ppa.launchpad.net/freenx-team/ppa/ubuntu/dists/maverick/main/source/Sources.gz](http://ppa.launchpad.net/freenx-team/ppa/ubuntu/dists/maverick/main/source/Sources.gz)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/freenx-team/ppa/ubuntu/dists/maverick/main/binary-i386/Packages.gz](http://ppa.launchpad.net/freenx-team/ppa/ubuntu/dists/maverick/main/binary-i386/Packages.gz)  404  Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.


When I run the sudo aptitude install freenx it reports it could not find a package by that name.

I tried downloading the file nxsetup.tar.gz. After unpacking the file I get nxsetup (in lime green shade). I am lost with what to do with it.

I am not sure what to do at this point...

Objective: First setup Notebook and Desktop so that they can be accessed from the other on private LAN. Desktop static ip of 10.100.99.10 and Notebook DHCP assigned.
Future objective to be able to access Desktop from WAN side of router.

Yes, I am quite familiar with not exposing various apps/ports. When I do expose ports they are not the default and typically then the application connecting to requires a password.

Once this remote accessiblility issue is resolved I would like the ability to remotely access (in my private LAN) drives located on other machines. i.e. Between the notebook, the wifes pc and my Desktop be able to access whichever drive as needed.  I have banged my head against the wall for days trying to get that to work too.

What are we running?
Notebook Ubuntu 10.10 / Windows XP SP3 Dual Boot
Desktop Ubuntu 10.10 / Windows XP SP3 Dual Boot
Wifes Ubuntu 9.10
All above located on private LAN 10.100.99.x
Wireless Access Point is on the LAN for the Notebook and other non pc toys (i.e. Sirius, etc).

Thank you.

Side note : I would prefer to steer clear of 3rd party apps, Teamviewer, etc. If it is necessary to allow other persons temporary access then this may be a solution.

---

### Post by MaindotC on 2010-09-09
You don't need to install any other applications like FreeNX - just use what is already available on your system.  The application you configure using System -> Preferences -> Remote Desktop is called vino-server and all you have to do is enable it as I instructed.  When you remote into a machine from outside the network on which it resides, then you'll need to forward the associative port on your AP to that machine.  I just realized you are using private addressing so obviously when I scanned that port nothing appeared - my bad.

---

### Post by scorp123 on 2010-09-09
> **k7faq said:**
>  I would prefer to steer clear of 3rd party apps, Teamviewer, etc. If it is necessary to allow other persons temporary access then this may be a solution. I use it because I very often work in environments where I under no circumstance can influence the port-forwarding of the firewall(s) in any way. Customer sites for example. They will let me touch their servers, parts of their LDAP or AD, their VMware infrastructure ... but the firewall? Out of question. And sometimes I have to spend months there, as if I was one of their employees. And sometimes I need to get back in remotely to equipment I had to leave behind while my project there isn't finished. 

So for such purposes TeamViewer is perfect. I can get back into my systems and I don't have to know anything about the firewall(s) between me and my remote system.

From that POV I can only recommend it.

Sorry for the marketing bla bla, but it's really a useful tool. :D

---

### Post by dmizer on 2010-09-09
> **k7faq said:**
> I reviewed the Router configs and added 5900 port forwarding to the pc.

There remains no change in status. Remote Desktop Preferences still reports desktop is accessible to localhost only.

Please see that this is disabled ASAP. This means that anyone on the Internet, anywhere in the world can attempt to log into your desktop.

Edit:
Once you get desktop sharing enabled on your LAN, you should look into configuring a VPN server so you can connect from remote. VPN is encrypted and far more secure than a password.

---

### Post by k7faq on 2010-09-10
> **dmizer said:**
>  you should look into configuring a VPN server so you can connect from remote. VPN is encrypted and far more secure than a password.

Yes. I agree. This was another long term goal, just not in the immediate picture. 

Scorp123: I have used similar apps in Windoze in the past. And I can understand your point of view as well.  In this particular case I have control over the firewall and am looking for the simplest solution possible. But, Thank You for the TeamViewer information, I will keep it in mind.

I will be, again trying strAlan's recommendations Friday. So far I am confused as to why VNC will not connect, but again, I will revisit all of this and check it again.

Thank you everyone for all your thoughts and assistance.
For now, back to the Slave Den deep down in the bottom of the Salt Mine...

---

