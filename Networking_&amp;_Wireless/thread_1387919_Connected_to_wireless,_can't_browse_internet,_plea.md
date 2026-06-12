---
title: "Connected to wireless, can't browse internet, please help!"
date: 2010-01-22
forum: Networking &amp; Wireless
---

### Post by clayk on 2010-01-22
Hi! 

Pretty new to Ubuntu (and this forum), so bear with me. I looked around and saw people with similar problems, but none that *quite* describe my situation.

I'm running Ubuntu 9.04 and having problems browsing the internet. I have wireless, and can access the network at my apartment complex via secure passcode (network manager icon shows bars, says connected), but for some reason can't browse web pages in Firefox. Additionally, I can ping IP addresses but can't ping web addresses. I've tried to check to see if I'm behind a firewall or something, but can't figure that out. 

A few more things that might be significant: I know other people in the building who are running Windows OS and able to connect to the internet, although they initially had the same problem as me, and were able to reconfigure some part of their wireless setup to fix it. Also, I never have the above problem in other places with other wireless networks; i can connect and browse just fine. 

I'm pretty computer illiterate, so please excuse me if some of this isn't as specific as it could be. This problem is really driving me crazy, any help anyone could provide would be very much appreciated! 

Thanks!

---

### Post by sefs on 2010-01-22
In your terminal do a 

```

dig google.com

```

and paste the results here.

Also paste the contents of your /etc/resolv.conf file.

---

### Post by clayk on 2010-01-22
After running the dig google.com command, i got this (couldn't directly copy and paste):

Warning: query response not set

DiG 9.5.1 -P2 <<>> google.com
global options: print cmd
Got answer:
-->>HEADER<<-- opcode: QUERY, status: NXDOMAIN, id: 15022
flags: aa rd; QUERY: 1, ANSWER: 0, AUTHORITY: 0, ADDITIONAL: 0

WARNING: recursion requested but not available

-----------------------------------------------------------------------------------------------------------

In my /etc/resolv.conf file, there's a folder titled "update-libc.d", and in that folder there's an executable text file called "avahi-daemon". I tried executing the daemon but it didn't seem to do any good.

---

### Post by TranDog on 2010-01-22
Sorry about using this in a reply, but I can't find the way to make a direct post.  

I am very new to Linux.  I installed Ubuntu 8.0.4 and got the basics working.  I can connect via wire to my US Robotics MaxG router, but when I try to connect via wireless, I get the message "Network Manager Applet wants access to the default keyring, but it is locked".   It is asking for a password, but I have no idea what that should be.  I don't know how to get the keyring unlocked.  The system recognizes the wireless Router, but I can't access it.  I can access with other devices (Vista, XP,  Mac, Itouch, etc.), but not Ubuntu. 

My wireless does pickup and connect through a neighbor's system, but I need to get my own access.  

What can I do to get access?  I tried modifying /etc/pam.d/gdm by appending a line "@include common-pamkeyring", but that has no effect. 

How do I get the system to logon and automatically connect via my wireless router?  Or even how do I unlock the keyring, or how do I find this mysterious password?

---

### Post by Swab on 2010-01-22
> **clayk said:**
> 
In my /etc/resolv.conf file, there's a folder titled "update-libc.d", and in that folder there's an executable text file called "avahi-daemon". I tried executing the daemon but it didn't seem to do any good.

Not the resolvconf folder but the file named resolv.conf

---

### Post by clayk on 2010-01-22
How do I find that?

---

### Post by Swab on 2010-01-22
> **TranDog said:**
> Sorry about using this in a reply, but I can't find the way to make a direct post.  

I am very new to Linux.  I installed Ubuntu 8.0.4 and got the basics working.  I can connect via wire to my US Robotics MaxG router, but when I try to connect via wireless, I get the message "Network Manager Applet wants access to the default keyring, but it is locked".   It is asking for a password, but I have no idea what that should be.  I don't know how to get the keyring unlocked.  The system recognizes the wireless Router, but I can't access it.  I can access with other devices (Vista, XP,  Mac, Itouch, etc.), but not Ubuntu. 

My wireless does pickup and connect through a neighbor's system, but I need to get my own access.  

What can I do to get access?  I tried modifying /etc/pam.d/gdm by appending a line "@include common-pamkeyring", but that has no effect. 

How do I get the system to logon and automatically connect via my wireless router?  Or even how do I unlock the keyring, or how do I find this mysterious password?

Were you previously asked to setup a password for the keyring?  Perhaps it's your user password or just blank?

---

### Post by Swab on 2010-01-22
> **clayk said:**
> How do I find that?

Go into the terminal and type "cat /etc/resolv.conf" and post the output here.

---

### Post by clayk on 2010-01-22
After cat /etc/resolv.conf command:

# Generated by NetworkManager

nameserver 192.168.1.1
nameserver 192.168.2.1

---

### Post by Swab on 2010-01-22
> **clayk said:**
> After cat /etc/resolv.conf command:

# Generated by NetworkManager

nameserver 192.168.1.1
nameserver 192.168.2.1

OK so do you know if these are the DNS servers that you should be using?  Also, can you ping these servers?

Try these:
dig @192.168.1.1 google.com
dig @192.168.2.1 google.com
dig @8.8.8.8 google.com

Any different output that the original dig command you ran?

You said you could ping ip addresses, were these internet IPs?  For example can you ping 4.2.2.2 ?

---

### Post by clayk on 2010-01-22
Yes, those are the DNS servers I'm supposed to be using; primary and secondary.

I ran the dig commands you suggested; for the 192.168.1.1 address I got the same message I posted above. For the other two I got network timeouts. 

I was able to ping 4.2.2.2, so yes, I am apparently able to ping internet IPs.

---

### Post by Zimmer on 2010-01-22
Suggestion:
Right click on your Network icon on the Gnome Panel and select 'Edit Connections'

Choose to Edit the connection you are using .

You will be asked to Authenticate this with your Ubuntu user password.
Without changing any settings click the Apply button at the bottom.

This should have the effect of communicating with the network router with root privileges enabled on your machine and for the router to alter the settings for the correct DNS servers...

(those 192... addresses look like internal routes )  

Worked for me the other day when I could not alter my router settings for DNS.

Hope this helps..

---

### Post by tjsummers51l on 2010-01-22
Go to your network connections and edit the wireless connection. Make sure that dhcp is selected and not just dhcp (address only). Sorry no command lines here, that's why I use ubuntu.

---

### Post by Swab on 2010-01-22
See if you can open a webpage by IP address: [http://72.30.186.249/](http://72.30.186.249/)

You said others with Windows machines had similar problems on this network initially.  Have you connected with a windows pc yourself?  Perhaps you need to register your MAC with the network operator.  

It's strange that you were not able to resolve with the 8.8.8.8 DNS server.

---

### Post by Swab on 2010-01-22
Would be interesting to traceroute to somewhere on the internet to see if we get any clues.

Sadly I don't think traceroute is installed by default, but you could download it from [http://packages.ubuntu.com/jaunty/i386/traceroute/download](http://packages.ubuntu.com/jaunty/i386/traceroute/download) (assuming you are running 32bit 9.04)  Then just copy it on to your machine and double-click it to install.

Once installed you can do "traceroute 4.2.2.2" from terminal.

Edit:  Actually forget installing it, you can run a traceroute graphically via System > Administration > Network Tools > Traceroute tab

---

