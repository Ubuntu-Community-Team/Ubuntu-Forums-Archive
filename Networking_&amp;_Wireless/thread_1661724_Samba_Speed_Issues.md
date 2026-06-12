---
title: "Samba Speed Issues"
date: 2011-01-07
forum: Networking &amp; Wireless
---

### Post by rubicks on 2011-01-07
I have an ubuntu 10.04 server. It has samba 3.4.7.

I did some testing and found its SMB performance to be very slow compared to windows and Mac OSX.

My tests were transferring a file over 5 ghz wireless N to an iMac.  I initiated the transfer on the iMac.  The server is connected via gigabit to my router. To test Windows and OSX samba performance i connected my MacBook Pro to the router via gigabit and turned off the wireless. Again, i initiated the transfer from the iMac.  Used the same port on the router and the same ethernet cable for both the server and the laptop.  I also tested FTP for a comparison.

I didn't use a program to test the speed, but i just looked at the numbers that iStat menus said the network connection was transferring data at.

Here are my results in megabytes per second.

Linux
FTP Peaked at 10.6, averaged around 8-9
SMB  Peaked at 4.1, averaged around 3-4

Windows 7
FTP peaked at 9.4, averaged around 8
SMB peaked at 7.4, averaged around 6-7

Mac OSX
AFP peaked at 9.1, averaged around 6.5-8
FTP peaked at 11.3, averaged around 8-10
SMB peaked at 8.7, averaged around 5.9-7.8

I saw some stuff about adjusting the socket options, but i didn't see any changes, but i may have done it wrong.

Here is my current options:
socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192

So what can i do to make my speeds go up?  I didn't test gigabit to gigabit, but i get up to 25 MB/sec when booted in OS X to the linux server, initiating the transfer on the mac. I know there is a Samba 3.5 out, but i couldn't find a clear answer on how to upgrade to it.  or should i upgrade to 10.10? I believe it comes with 3.5.  Would i be able to upgrade without wiping my data?

---

### Post by rubicks on 2011-01-08
I upgraded to the 3.5.6 version of samba, but the speed remains the same.

---

### Post by rubicks on 2011-01-10
i found a work around that works in my situation. I installed netatalk using this tutorial: [http://www.kremalicious.com/2008/06/ubuntu-as-mac-file-server-and-time-machine-volume/]("http://www.kremalicious.com/2008/06/ubuntu-as-mac-file-server-and-time-machine-volume/")

it mounts just like samba shares did, but the performance is much better.  i'm getting up to 10MB/sec. Wish i coulda figured out how to get samba to work that nicely.

---

