---
title: "Network Ubuntu 10.04 to Windows 7"
date: 2011-05-31
forum: Networking &amp; Wireless
---

### Post by darren123web on 2011-05-31
Hey Guys, 

I see a lot of tickets on this general issue trying to get 

My Windows 7 PC can see the home folder I have shared on 10.04 Ubuntu no probs.

I can see in Nautilus my WORKGROUP, and Windows 7 machine, but was  getting 'Nautilus cannot handle "network" locations' type error, now I  get:

''Failed to mount Windows share'' 

when I try to navigate there from  within Nautilus.

Have tried

sudo apt-get install samba
sudo apt-get install gvfs-backends

in both cases both are the latest versions already....

I've only been tinkering with Ubuntu for a very short time, so I'm a  little hesitant to start uninstalling stuff I'm not sure about - but is  the best way forward to remove samba and gvfs through Synaptic?

It did work for a moment - I could see a shared folder on my windows machine and my files within it.  Then it decided not to work about 2 minutes later...


Any ideas anyone? I'm fried.....

( 
pinging between the two no problem,
using same user name and password on both machines
that user setup for read & write on Win7 machine shared folder
File & printer sharing/network discovery enabled on Win 7
Encryption lowered to 40 / 56 bit
password protected sharing = off
use user accounts and passwords to connect to other computers selected. 

using same WORKGROUP when setting up in Ubuntu >Places > Connect to Server:

This worked :-

This works for me:

Service Type: Windows Share
Server: 192.168.2.5 (also tried DARRENWIN7)
Share 
Folder: MyDocumentsOld
User Name: darrenwin7_2
Domain Name: WORKGROUP

A note on 'User Name' - my User details in Win Control Panel say 'darren' - however, when i go to one of my shared folders > right click > properties > Sharing tab > click Share > hover over 'darren' - it shows me DARRENWIN7\darrenwin7_2.  Using darrenwin7_2 as User Name in Ubuntu Windows share above helped.
)

Hope that helps someone at some poing ;-)

Many Thanks.
D

---

