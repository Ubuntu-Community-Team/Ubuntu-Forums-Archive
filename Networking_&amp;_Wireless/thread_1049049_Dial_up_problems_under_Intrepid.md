---
title: "Dial up problems under Intrepid"
date: 2009-01-24
forum: Networking &amp; Wireless
---

### Post by ranch hand on 2009-01-24
There is another thread on dialup problems <http://ubuntuforums.org/showthread.php?t=1031014>.  I have been trying to sort this out without any luck at all.

I had a lot of trouble getting my internal modem to work under hardy but that was mostly lack of knowledge and no connectivity through Ubuntu so I had to switch back and forth with Vista.

Now I do have an installation of Intrepid and I can't get it to hook up at all.

I have 2 installations of Hardy.  I am on the "playtime" one now.

First off, I am connected by first running pppconfig and then network manager in Hardy.  wvdial never helped at all.

I read that gppp was the default dialer for Intrepid.  I got it installed in my Intrepid and on this Hardy.  I ran wvdial on Intrepid and then gppp.  It dials and dies with an error about not being able to use /usr/sbin/ppd.

I disabled the configuration in network manager in Hardy and configured through gppp.
I have to believe that this worked or I would have trouble sending this post.

I have run pppconfig in both Intrepid and Hardy.  I ran wvdial in Intrefpid.  I, do not know if it has ever been run in this Hardy.

The wvdial.conf from Intrepid;
```

[Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Modem Type = Analog Modem
Baud = 115200
New PPPD = yes
Modem = /dev/ttyS0
ISDN = 0
Phone = 7844688
Username = *******.net
Password = ************* (removed for obvious reasons)

```

The wvdial.conf file from this Hardy (using gppp)
```

[Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Modem Type = Analog Modem
Baud = 115200
New PPPD = yes
Modem = /dev/ttyS0
ISDN = 0
; Phone = <Target Phone Number>
; Password = <Your Password>
; Username = <Your Login Name>

```

The information in pppconfig is identical on all installations.

I am interested to know if anyone has connected an internal modem under Intrepid or if this is a bug that should be reported.

I am using a USR5610c modem.

---

### Post by oygle on 2009-01-24
> **ranch hand said:**
> 
I ran wvdial on Intrepid and then gppp.  It dials and dies with an error about not being able to use /usr/sbin/ppd.


Usually a permissions error. i used to see this when using wvdial under Hardy, and it never made a difference to the connection.

> **ranch hand said:**
> 
I disabled the configuration in network manager in Hardy and configured through gppp.


If that worked for hardy, then try it for Intrepid, maybe ??

Oygle

---

### Post by ModelM on 2009-01-24
Have a look at [_this thread](http://ubuntuforums.org/showthread.php?t=1045924)_.

---

### Post by ranch hand on 2009-01-24
oygle
The network manager has been changed in Intrepid and it is not possible to configure a dialup connection from there.  That is why I disabled it in the Hardy installation, to make it as simular as I could.

ModelM
I had not seen that post but had already tried that.  When to that install just now and tried it again.

```

sudo] password for slade: 
--> WvDial: Internet dialer version 1.60 
--> Initializing modem. 
--> Sending: ATZ 
ATZ 
OK 
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 
OK 
--> Modem initialized. 
--> Sending: ATDT7844688 
--> Waiting for carrier. 
ATDT7844688 
CONNECT 34666/ARQ/V90/LAPM/V42BIS 
--> Carrier detected.  Waiting for prompt. 
login: 
login: 
--> Looks like a login prompt. 
--> Sending: ***@****
***@****
Password: 
--> Looks like a password prompt. 
--> Sending: (password) 
Request Denied 
login: 
--> Looks like a login prompt. 
--> Sending:  ***@****
***@****
Password: 
--> Looks like a password prompt. 
--> Sending: (password) 
Request Denied 
login: 
--> Looks like a login prompt. 
--> Sending:  ***@****
***@****
Password: 
--> Don't know what to do!  Starting pppd and hoping for the best. 
--> Starting pppd at Sat Jan 24 08:12:27 2009 
--> Pid of pppd: 7633 
--> Using interface ppp0 
--> pppd: &#65533;[07]&#65533; H[05]&#65533; 
--> pppd: &#65533;[07]&#65533; H[05]&#65533; 
--> pppd: &#65533;[07]&#65533; H[05]&#65533; 
--> pppd: &#65533;[07]&#65533; H[05]&#65533; 
--> Disconnecting at Sat Jan 24 08:12:30 2009 
--> The PPP daemon has died: A modem hung up the phone (exit code = 16) 
--> man pppd explains pppd error codes in more detail. 
--> Try again and look into /var/log/messages and the wvdial and pppd man pages for more information. 
--> Auto Reconnect will be attempted in 5 seconds 
--> Initializing modem. 
--> Sending: ATZ 
ATZ 
OK 
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 
OK 
--> Modem initialized. 
--> Initializing modem. 
--> Sending: ATZ 
ATZ 
OK 
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 
OK 
--> Modem initialized. 
--> Sending: ATDT7844688 
--> Waiting for carrier. 
ATDT7844688 
CONNECT 36000/ARQ/V90/LAPM/V42BIS 
--> Carrier detected.  Waiting for prompt. 
login: 
login: 
--> Looks like a login prompt. 
--> Sending: metalsmith@rangeweb.net 
metalsmith@rangeweb.net 
Password: 
--> Looks like a password prompt. 

```

This is the result.  It goes on indefinately.  This is an improvement over last time.  Last time I tried it it froze up my box so hard that I had to unplug it to shut down even with power management set to shutdown when power button is pushed.

I have checked and double checked all information to the Intrepid installation and it is correct.

This really has me stumped.

I installed Intrepid because I tried it in town on DSL from the Live CD and it cooked away automatically (tried Hardy later and it does too).  I thought that I could get it set up before I moved in there (at sometime this year, boss died, ranch for sale).  It seems nice but it is a bugger to get dialed in.

---

### Post by ranch hand on 2009-01-24
oygle;
The permissions on the Intrepid /usr/sbin/pppd and the Hardy /usr/sbin/pppd are identical.

I looked at that right off and checked with both Hardy installations.  I have been known to change them but even I am learning that this is not a good idea (there is a reason that I have a "playtime" installation).

---

### Post by ModelM on 2009-01-24
In /etc/wvdial.conf, try adding the line (or changing, if the line is already there)

Stupid Mode = 1

---

### Post by ModelM on 2009-01-24
This appears to be a problem with authentication. Some ISPs don't allow plain text login. The line in the message above, when added to the /etc/wvdial.conf file, will change authentication from plain text to pap/chap. Don't worry about which you need, the correct one will be found & used automatically.

If that doesn't work, carefully examine your username & password in the /etc/wvdial.conf file. Does your password contain any non-alphanumeric characters? Spaces? Try preceding any non-alphanumeric characters with "\" and, if you need to send "\", precede it also with "\" so it appears in the file as "\\".

---

### Post by ranch hand on 2009-01-24
I will give that a try.  Need to reboot to that installation.

We use pap.

---

### Post by ranch hand on 2009-01-24
That is not the problem.  I did not think so but it is easy to check.  There is an option in gppp to go to stupid mode.  It did not work there earlier and I do not use it under Hardy so I don't think that can be it.

The problem seems to be in pppd.  Gppp was getting unstable but I grabbed several pages of this;

```

--> Check permissions, or specify a "PPPD Path" option in wvdial.conf. 
--> Don't know what to do!  Starting pppd and hoping for the best. 
--> Unable to run /usr/sbin/pppd. 
--> Check permissions, or specify a "PPPD Path" option in wvdial.conf. 
--> Don't know what to do!  Starting pppd and hoping for the best. 
--> Unable to run /usr/sbin/pppd. 
--> Check permissions, or specify a "PPPD Path" option in wvdial.conf. 
--> Don't know what to do!  Starting pppd and hoping for the best. 
--> Unable to run /usr/sbin/pppd. 

```

It is interesting to me that kppp may do the job if I could get it installed.  To time consuming.  I have connected very easily with several KDE distros.  I prefer Gnome but kppp seems to work well.

I have another 8.10 install in town on an external HDD at my dreaded mother in laws house.  I will put kppp on it before i bring it home and try that.

In the mean time I guess I had better study up on pppd, man here I come.

---

### Post by ModelM on 2009-01-24
I was working with the log you posted above from wvdial. This latest log is not from a "sudo wvdial" command, but from something else. If you compare, you'll see the "permissions" line is not in the wvdial log. I was trying to get wvdial working.

You are apparently using gppp or something else. I only know wvdial, so I guess I'd better back out of here.

---

### Post by ranch hand on 2009-01-24
I don't care what we use.  I just want it to work.

That log was from gppp (gnome-ppp).  I was under the impression that it was a front end gui for wvdial and supposed to be the default dialer for Intrepid.  I got the default idea from ubuntuguide.org and the gui idea from a thread on the forums here.

I would love to get wvdial to work as it has never worked for me in Hardy either.  I do nt care about the Hardy part as I am connecting with no problem, but still it is supposed to work and Intrepid is set up so that the solution that  worked in Hardy does not work in Intrepid.

There are a lot of use out here using dial up and it is the one thing that has really got on my thungas in Ubuntu.  Other than that I am just crazy about it.

---

### Post by oygle on 2009-01-25
> **ranch hand said:**
> 
```

--> WvDial: Internet dialer version 1.60 
--> Initializing modem. 
--> Sending: ATZ 
ATZ 
OK 
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 
OK 
--> Modem initialized. 
--> Sending: ATDT7844688 
--> Waiting for carrier. 
ATDT7844688 
CONNECT 34666/ARQ/V90/LAPM/V42BIS 
--> Carrier detected.  Waiting for prompt. 
login: 
login: 
--> Looks like a login prompt. 
--> Sending: ***@****
***@****
Password: 
--> Looks like a password prompt. 
--> Sending: (password) 
Request Denied 
login: 
--> Looks like a login prompt. 
--> Sending:  ***@****
***@****
Password: 
--> Looks like a password prompt. 
--> Sending: (password) 
Request Denied 
login: 

```

The 'request denied' would have to be coming from your ISP. I used wvdial on Hardy for a number of months, and if my username/pwd was authenticated okay, then the login was successful. I'd be asking the ISP what settings are required for login, or trying the same modem with a windooze box.

For some reason, authentication is not working.

Oygle

---

### Post by oygle on 2009-01-25
> **ranch hand said:**
> oygle
The network manager has been changed in Intrepid and it is not possible to configure a dialup connection from there.  That is why I disabled it in the Hardy installation, to make it as simular as I could.


I have had no end of trouble with network manager in Intrepid, but finally did get around a problem by circumnavigating network manager.

Possibly if you can check/double check that network manager is not trying to 'manage' the dialup connection, as it's better to just let wvdial do it all. If there is a dialup connection in NM 9even if it is grayed out), it would probably be better to delete it.

If you right click on the NM applet, you shouldn't see any info for a dialup connection.

Oygle

---

### Post by ranch hand on 2009-01-25
I gave the same information that I am using right now to connect to my ISP.  I have used the same information from 2001 through now.  All that has changed is the password (twice) in that period.

I will go to the Intrepid install and wipe out all traces of trying to configure this and start over.

One thing I am sure of is that there is no dial up mention in NM in Intrepid.  I was actually hoping for some improvement in the direction of dial up but I guess we are concidered to be extinct.

All of the KDE flavors that I have tried detect the modem and have a 3 or 4 line gui form to fill out and you are connected, on the Live CD no less.  It is just silly that Gnome flavors discriminate this way.  I am not going to switch to KDE because it is too much like the "Vista Experience" for me.

As a side note; my son reccomended Ubuntu to me.  I looked it up and the first place that had a reference to Ubuntu bragged that it was the closest thing to the Vista Experience that you can have in Linux.  Just about turned me away.

I like the Vista Experience ratings that you get under Vista.  The sucker torments you and then tells you how much you like it.  All I can say is that it is worse than 98 but has a good self image.

---

### Post by oygle on 2009-01-26
> **ranch hand said:**
> One thing I am sure of is that there is no dial up mention in NM in Intrepid.  I was actually hoping for some improvement in the direction of dial up but I guess we are concidered to be extinct.


Well, I must be extinct as well, because I had to use it for a few months, no broadband out in the country here, but did finally get mobile broadband service.

I was going to post all my wvdial files for you to look at, but then remembered they were from Hardy, not Intrepid.  :(

Oygle

PS  No doubt you have looked at the driver side of things ? I used an external modem, but for an internal, you may well need drivers, .... do they 'work' for Intrepid ?

---

### Post by ranch hand on 2009-01-26
I have to report the results of yet another attempt to connect under Intrepid.

I went to synaptic and removed gnome-ppp.  I went to terminal and ran "sudo pppconfig" and removed the information there.  Then "sudo wvdial".  It dialed.

IT WORKED.  I am on Intrepid right now.

Gnome-ppp should work from what I read.  Don't really care, this does.

Is there some way besides going to terminal to connect?  It is not that big a deal to do it this way, I sure don't mind.  Some may though and I would like to know.

Thanks a whole bunch for this.  I don't know why it never worked in Hardy but wvdial sure does it here.

---

### Post by oygle on 2009-01-26
> **ranch hand said:**
> 
Is there some way besides going to terminal to connect?  It is not that big a deal to do it this way, I sure don't mind.  Some may though and I would like to know.


That's great news about getting it going on Intrepid.  :popcorn:

You can just modify the 'menu' and add wvdial as one of the options, probably under 'Internet' menu item I guess.

Just right-click on 'Applications' and there is an 'edit menu' function there.

Oygle

---

### Post by ranch hand on 2009-01-26
What about "ppp tray"?  It is in aplications and claims to be a "Tray Icon interface to Pon/Poff commands".

---

### Post by ranch hand on 2009-01-27
Just thought I should update this a little.

Gnome-ppp did not work because it could not get into the pppd files.  Your user needs to be part of the "dip" group, what ever that is.  This group does nt show up in my Users an Groups manager.

Just typing wvdial into terminal will connect you.  It does not seem to be a very stable connection but it works.

Searching for gnome-ppp comes up with several bug reports.

<https://bugs.launchpad.net/ubuntu/+source/gnome-ppp/+bug/289575>

This page has the answer to joining the dip group.  Run the 
```

ls -l /usr/sbin/pppd

```
and you should get
```

-rwsr-xr-- 1 root dip 273064 2008-10-16 03:51 /usr/sbin/pppd

```

Gnome-ppp should now work and it seems to reconnect when you loose connection and everything.

---

