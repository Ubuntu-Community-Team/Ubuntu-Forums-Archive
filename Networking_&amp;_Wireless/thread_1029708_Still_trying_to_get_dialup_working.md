---
title: "Still trying to get dialup working"
date: 2009-01-03
forum: Networking &amp; Wireless
---

### Post by GuyK on 2009-01-03
I'm still struggling to get a working dialup. I'm presently going in through pppconfig and making as much or better progress so far.

The modem is recognized, dials up and, presumably, connects. Not sure wheter handshaking goes on.

I offer the plog below and wonder what the significance of the indicatied line is? (ethernet address/proxy ARP)

**********
Jan  3 16:41:46 guy-laptop pppd[10316]: rcvd [IPCP ConfRej id=0x1 <compress VJ 0f 01>]
Jan  3 16:41:46 guy-laptop pppd[10316]: sent [IPCP ConfReq id=0x2 <addr 0.0.0.0>]
Jan  3 16:41:46 guy-laptop pppd[10316]: rcvd [IPCP ConfNak id=0x2 <addr 66.19.242.75>]
Jan  3 16:41:46 guy-laptop pppd[10316]: sent [IPCP ConfReq id=0x3 <addr 66.19.242.75>]
Jan  3 16:41:46 guy-laptop pppd[10316]: rcvd [IPCP ConfAck id=0x3 <addr 66.19.242.75>]
[COLOR="Teal"]Jan  3 16:41:46 guy-laptop pppd[10316]: Cannot determine ethernet address for proxy ARP[/COLOR]
Jan  3 16:41:46 guy-laptop pppd[10316]: local  IP address 66.19.242.75
Jan  3 16:41:46 guy-laptop pppd[10316]: remote IP address 192.168.254.1
Jan  3 16:41:46 guy-laptop pppd[10316]: Script /etc/ppp/ip-up started (pid 10336)
Jan  3 16:41:46 guy-laptop pppd[10316]: Script /etc/ppp/ip-up finished (pid 10336), status = 0x0
*******

Any suggestions as to how I should move?

Thanks in advance for any info.

Guy K

---

### Post by gettinoriginal on 2009-01-03
Don't have dial up, so never tried solutions, but I found this, hope it helps:

[https://help.ubuntu.com/community/DialupModemHowto](https://help.ubuntu.com/community/DialupModemHowto)

---

### Post by greadey on 2009-01-03
My first observations are - have you configured the correct interface for ppp to work i.e. does ttyx point to e.g. /dev/modem.  Have you looked to see if your modem card defaults to a funny tty number i.e. it might not be tty0, tty1 but in fact tty5 or something.  I seem to remember that pppconfig asks which com port your modem talks to.

---

### Post by GuyK on 2009-01-03
I appreciate the reference that getinoriginal suggested and made use of it.

Have made a bit of progress. 
Have some more information. BTW, haven't mentioned it before but this is in 8.10.

Here is a related message log:

***********
Jan  3 21:15:51 guy-laptop pppd[6537]: pppd 2.4.4 started by root, uid 0 
Jan  3 21:15:52 guy-laptop chat[6539]: abort on (BUSY) 
Jan  3 21:15:52 guy-laptop chat[6539]: abort on (NO CARRIER) 
Jan  3 21:15:52 guy-laptop chat[6539]: abort on (VOICE) 
Jan  3 21:15:52 guy-laptop chat[6539]: abort on (NO DIALTONE) 
Jan  3 21:15:52 guy-laptop chat[6539]: abort on (NO DIAL TONE) 
Jan  3 21:15:52 guy-laptop chat[6539]: abort on (NO ANSWER) 
Jan  3 21:15:52 guy-laptop chat[6539]: abort on (DELAYED) 
Jan  3 21:15:52 guy-laptop chat[6539]: send (ATZ^M) 
Jan  3 21:15:52 guy-laptop chat[6539]: expect (OK) 
Jan  3 21:15:52 guy-laptop chat[6539]: ATZ^M^M 
Jan  3 21:15:52 guy-laptop chat[6539]: OK 
Jan  3 21:15:52 guy-laptop chat[6539]:  -- got it 
Jan  3 21:15:52 guy-laptop chat[6539]: send (ATDT2153717827^M) 
Jan  3 21:15:52 guy-laptop chat[6539]: expect (CONNECT) 
Jan  3 21:15:52 guy-laptop chat[6539]: ^M 
Jan  3 21:16:13 guy-laptop chat[6539]: ATDT2153717827^M^M 
Jan  3 21:16:13 guy-laptop chat[6539]: CONNECT 
Jan  3 21:16:13 guy-laptop chat[6539]:  -- got it 
Jan  3 21:16:13 guy-laptop chat[6539]: send (\d) 
Jan  3 21:16:14 guy-laptop pppd[6537]: Serial connection established. 
Jan  3 21:16:14 guy-laptop pppd[6537]: Using interface ppp0 
Jan  3 21:16:14 guy-laptop pppd[6537]: Connect: ppp0 <--> /dev/ttyUSB1 
Jan  3 21:16:16 guy-laptop pppd[6537]: PAP authentication succeeded 
Jan  3 21:16:16 guy-laptop kernel: [  511.125589] PPP BSD Compression module registered 
Jan  3 21:16:16 guy-laptop kernel: [  511.227752] PPP Deflate Compression module registered 
Jan  3 21:16:17 guy-laptop pppd[6537]: local  IP address 66.19.241.132 
Jan  3 21:16:17 guy-laptop pppd[6537]: remote IP address 192.168.254.1 
[COLOR="MediumTurquoise"]Jan  3 21:16:29 guy-laptop pppd[6537]: Terminating on signal 15[/COLOR] 
Jan  3 21:16:29 guy-laptop pppd[6537]: Connect time 0.2 minutes. 
Jan  3 21:16:29 guy-laptop pppd[6537]: Sent 0 bytes, received 0 bytes. 
Jan  3 21:16:29 guy-laptop pppd[6537]: Connection terminated. 
Jan  3 21:16:30 guy-laptop pppd[6537]: Exit.
******

Seems that Signal 15 indicates "peer not responding to echo request" which makes sense since the modem dials  and connection happens but with no handshaking for login, password, etc.

So, does anybody see what I need to do now to confront this issue?

With appreciation for the help.

Guy K

---

### Post by malspa on 2009-01-03
Is the problem in 8.10?  Just curious because I have dial-up working in 8.04 with and I'm wondering if there will be problems with Intrepid Ibex.  In Hardy I used the Networking Option as shown here:  [http://www.debianadmin.com/setting-up-dial-up-connection-in-ubuntu.html](http://www.debianadmin.com/setting-up-dial-up-connection-in-ubuntu.html)

But some things were slightly different for Hardy.  Still, got it to work, then downloaded gnome-ppp, which I am using now.  Not sure if I can be of any help, but let me know, I still have my notes from when I tried the Networking Option.

---

### Post by malspa on 2009-01-03
Shot in the dark, maybe paste your /etc/ppp/options file, might provide some clues.

---

### Post by sreeyeshns on 2009-01-03
I hope you r working with gnome desktop environment. If you are, try installing gnome-ppp, which will provide you an easy GUI interface to configure your dialup connection.

It's really working. I have successfully established a dialup connection using this tool.

Use the following command to install gnome-ppp if you have another Internet connection or download it from [http://packages.ubuntu.com/](http://packages.ubuntu.com/)(I think there will be no dependency problem)

command:
         sudo apt-get install gnome-ppp

If necessary I will mail you the package. OK?:)

---

### Post by GuyK on 2009-01-04
Thanks for the info sreeyeshns.

Thanks for the offer. I'll go to the local library and use my wireless link there. If it turns out to be necessary I'll get back to you.

You might consider editing your reply to knock off the last couple of characters of the overly-long hyperlink. It might be more convenient for others who might want to try it.

I'm also going to look into the options issue suggested by the respondent above in the thread.

Happy New Year!

Guy K

---

### Post by GuyK on 2009-01-05
Here I am again.

I've made some progress and getting close.

I have gone the pppconfig//po/poff route. Here is the plog:

**********
Jan  5 09:58:45 guy-laptop pppd[7820]: rcvd [LCP ConfReq id=0xa <asyncmap 0x0> <magic 0x49b1007f> <pcomp> <accomp>]
Jan  5 09:58:45 guy-laptop pppd[7820]: sent [LCP ConfNak id=0xa <magic 0xd97802d5>]
Jan  5 09:58:45 guy-laptop pppd[7820]: rcvd [LCP ConfNak id=0xa <magic 0xd97802d5>]
[COLOR="Green"]Jan  5 09:58:45 guy-laptop pppd[7820]: Serial line is looped back.[/COLOR]
Jan  5 09:58:45 guy-laptop pppd[7820]: sent [LCP TermReq id=0xb "Loopback detected"]
Jan  5 09:58:45 guy-laptop pppd[7820]: rcvd [LCP TermReq id=0xb "Loopback detected"]
Jan  5 09:58:45 guy-laptop pppd[7820]: sent [LCP TermAck id=0xb]
Jan  5 09:58:45 guy-laptop pppd[7820]: rcvd [LCP TermAck id=0xb]
Jan  5 09:58:45 guy-laptop pppd[7820]: Connection terminated.
Jan  5 09:58:46 guy-laptop pppd[7820]: Exit.
******************

Serial line loop back is the issue now.

I have seen a couple of suggestions to handle this. One is to extend the LCP max in "options" and I have tried that. (Just prolongs the time until it quits.) Another which, if I remember (or interpret) correctly, was to introduce an E0 in the modem initializing string. I both question that and don't know how to do it. I've looked into the chatscripts/provider file but am not sure that this is to be the place where I can get at that. 

Will stand by for any response.

Guy K

---

### Post by Oceola on 2009-01-06
Having the same difficulty with a dial up modem.

What I've tried after first error message in Intrepid Ibex telling me I was not a member of the "dip" group.
1.) used sudo adduser (myname) dip
* this managed to let the pppconfig setup connect but there was no real service though the connection was there.
2.) Opened /System/Administration/Users& Groups
* didn't see the "dip" group until I changed the setting in the gconf.editor to show all users.
3.) Dip was added again and I followed the instructions on Launchpad to change the GUID to 30.
* still no change in conditions.
4.) Made and tried a static and a dynamic setup for my provider, neither worked. The dynamic performed as the previous post by GuyK stated and broke contact after a brief time. Still no real transfer rate or speed.

This is the link to the bug report: [https://bugs.launchpad.net/ubuntu-doc/+bug/310331](https://bugs.launchpad.net/ubuntu-doc/+bug/310331)

There is also another similar discussion where I found the things I tried: #278828
[https://bugs.launchpad.net/ubuntu-doc/+bug/278828](https://bugs.launchpad.net/ubuntu-doc/+bug/278828)

I'm dual booting Hardy with Intrepid and was wondering if I can access the repositories for Intrepid, copy any fix, then transfer the fix to the apt/cache for dpkg or gdebi install?

---

### Post by GuyK on 2009-01-06
Well, this has certainly been interesting information. From the looks of it, judging by the launchpad info, there is a big problem for those of us who might want to go with dialup.

As it happens, a technician is scheduled to come day after tomorrow to install cable service, at which time I hope to be able to have a wireless net implementation that should reduce my dependence on dialup. I still am interested in having the dialup capability for backup or portability uses.

I'll give up for a while the energy for dialup and go back to my other problem—a non-functional installation of Kubuntu-desktop. I hope that that feature hasn't gone off to la-la land as dialup has.

If anyone has can report that they have succeeded in dragging that into Ubuntu 8.10 I would appreciate hearing of it. I have a posting in one of the desktop forums but it has been dormant for several days. Will probably stick my toe in the water again and post something where it might get some attention.

Regards to all who have chipped in here. Nice meeting you folks.

Guy K

---

### Post by malspa on 2009-01-07
So, from what I'm reading here, nobody's able to use dial-up with Intrepid?  (I'm still using Hardy, so I don't know.)  Anybody tried wvdialconf and wvdial?

And I'm assuming that dial-up works with Kubuntu Intrepid, using kppp.  Anyone know if that's so?

---

### Post by GuyK on 2009-01-07
Thanks for the info. Looks as though dialup is broken in 8.10.

All hope is not lost. In the next day or two we're getting a cable connection installed that will move us into the 21st century, finally.
Would like to have dialup accessible for possible off site use when needed.

Thanks to all who have helped me along.

Guy K

---

### Post by Oceola on 2009-01-08
I'm dual booting with Hardy and replaced Feisty with Intrepid Ibex. Gnome not Kde. I tried again to re-install and also took a close look at the wvdial and wv folders. Everything seems to be the way it should except for one folder which has a permission of "s" instead of an "x." Usually Hardy seems to work pretty well for a dial up in either a static or a dynamic setup. 

I also looked at permissions for groups and users but can find no reason why things do not work. Same settings as Hardy and previously Feisty. This is posted using Hardy. 

I'm up for suggestions but until I see something substantive I'll probably fiddle with Intrepid a bit but stick with hardy for now.

Since Intrepid makes an indicated connection which doesn't break but has no rate of access it may be some verifying signal is missing, needed by the servers you connect to either in static or dynamic.

We have no one honorable to connect to locally so dial up is my only option, or so it seems. Costs for Cable and Fiber Optic are too high and going up even further in the near future and the available systems technical people will not support any form of Linux.

---

### Post by hari168 on 2009-01-19
I am trying to get my dialup working for xubunti 810,i have tried both wvidal, gnome-ppp but both are failing with no modem found error. I have /etc/tty, /etc/tty0 ..tty5.. but these are not detected.. i am using dell inspiron 8600 laptop with xubuntu 810 (no dual boot)

---

### Post by xxxxme on 2009-01-19
> **malspa said:**
> So, from what I'm reading here, nobody's able to use dial-up with Intrepid?  (I'm still using Hardy, so I don't know.)  Anybody tried wvdialconf and wvdial?

And I'm assuming that dial-up works with Kubuntu Intrepid, using kppp.  Anyone know if that's so?

I -have- been able to get dialup working with Ubuntu 8.10, but it took some work and isn't as nice as it should be.  I'm using kppp.  I still have problems.  My post complaining about my problems: [http://ubuntuforums.org/showthread.php?p=6562434](http://ubuntuforums.org/showthread.php?p=6562434) .

What I did:
- Using gentoo, I downloaded and built the latest "stable" version of kppp from portage (kppp-2.3.2): PKGDIR="/home/<my name>/Desktop" emerge -aBv kppp
- Copied the .tbz2 made to the Ubuntu machine and unpacked it into /, ignoring the error.
- Attempted to run kppp from the console, copying all the libraries it says it needs from the gentoo machine.

If you have access to a machine running gentoo, this is useful : ).  But if you don't, well, it isn't.

Edit: Would it be allowable, a good idea, etc. to post a binary in .tbz2 here with kppp and all the libraries it requested when I tried it for others, warning YMMV?

Edit again: Does anyone even **want** that ^ ?  I found that gnome-ppp also works for me.

---

### Post by xxxxme on 2009-01-23
I installed gnome-ppp just for kicks, and that works well for me, even though I don't like the program as much.

U.S. Robotics 56k PCI FaxModem (3Com chip, I think) on /dev/ttyS1.  Didn't need any drivers/modules that weren't installed by default.

[quote=GuyK]I'll give up for a while the energy for dialup and go back to my other problem—a non-functional installation of Kubuntu-desktop. I hope that that feature hasn't gone off to la-la land as dialup has.[/quote]
I had issues with both KDE and gnome desktops, too.  The second time I reinstalled Ubuntu, it worked, but neither the upgrade from 8.04, nor my first tries as installing Kubuntu or Ubuntu worked.  What's up with this release?  Or are only a few people having troubles?

[quote=Oceola]* this managed to let the pppconfig setup connect but there was no real service though the connection was there.[/quote]
This happened to me before I reinstalled.  I was able to connect to my ISP, but I wasn't able to even ping what should have been the gateway.  For some reason, a route through the modem was not being added, and adding it manually (route add ...) gave different errors than I got without it.  Also, nothing was added to /etc/resolv.conf (it -was- told to use dynamically set DNS).  The second was probably a symptom of the first, is my guess.
My ISP is locally owned and "supports using whatever operating system you want to", but the guys who had used Ubuntu couldn't fix the problem either.

---

