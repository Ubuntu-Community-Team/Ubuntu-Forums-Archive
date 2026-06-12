---
title: "WPA help???"
date: 2005-12-19
forum: Networking &amp; Wireless
---

### Post by pugs on 2005-12-19
I did not see that there was a networking section when I signed up so I already have this posted in the Kubuntu forum, but I will do a quick summary.

I just installed Kubuntu on my IBM A20m.  I have a D-link DWL-G650 card and a D-link DI-624 wireless router.  At first I was trying to get it setup with the GUI, which I eventually did.  Since then I have ditched that POS and started editing files.  I can now get it running with or without WEP just fine.  Everything works great.  But I am greedy and wanted more.  So I tried to get WPA-PSK working.  I followed this tuturial after getting the latest madwifi driver:

[http://ubuntuforums.org/archive/index.php/t-90450.html](http://ubuntuforums.org/archive/index.php/t-90450.html)

I dont know if there is anything that would make it vastly different on kubuntu, but it did not work.  The communication between the card and the router seems fine, but DHCP is not working.  I get no DHCP offers.  I did have it working on an old lease though...but most of the time when ifdown/ifup it will never get an IP and just go into sleeping mode.

Do I not have something I need?  Is that tuturial the right way to go about this?  Is there something I am missing?

Anyone have a similar setup that wouldnt mind sharing their interfaces and wpa_supplicant.conf files? ;)

---

### Post by Lambert on 2005-12-19
See this link about madwifi and wpa-psk

[http://madwifi.org/wiki/UserDocs/WPA_PSK_on_Both_Ends](http://madwifi.org/wiki/UserDocs/WPA_PSK_on_Both_Ends)

I'm curious about your experience with updating madwifi as the few guides I saw seemed to miss some steps. 

Run this command

sudo lshw -C network

In the section on the card there is a line starting with configuration: You'll see in that line driver= ath_pci driver driverversion=

What version does that say currently? What guide did you follow to install latest madwifi?

---

### Post by pugs on 2005-12-19
I used this from the wiki:
[https://wiki.ubuntu.com/MoreRecentMadwifiHowto?highlight=%28wifi%29](https://wiki.ubuntu.com/MoreRecentMadwifiHowto?highlight=%28wifi%29)

It may not be the latest version of madwifi...but its the latest Package available that matches the kernel I am using.

driverversion=0.9.6.0 (EXPERIMENTAL)...UH OH...

---

### Post by Lambert on 2005-12-19
experimental is fine because that's what stage it is currently. The first stable release (1.0) doesn't have a set release date yet so it is a work in progress.

Are you sure it's .9.6 and not .9.0.6

---

### Post by pugs on 2005-12-19
Well to be honest I dont know anymore...sometimes my typing gets a little dyslexic...one hand gets ahead or out of sync of the other and I transpose things ;)

And I cant check anymore as I just started installing a fresh copy.  I am gonna give it one last try from a fresh start.  I found another HowTo in the wiki:

[https://wiki.ubuntu.com/WPAHowto?highlight=%28wpa%29](https://wiki.ubuntu.com/WPAHowto?highlight=%28wpa%29)

I will go through and upgrade the madwifi and kernel before anything else and let you know the version once I am back up and runnin here.  Should be soon, I am around 85%.

---

### Post by pugs on 2005-12-20
Hopefully the repository will be back up tommorrow...no luck getting that madwifi package tonight.  Did a quick check on google and found another server, but I think it points to the same one because it is down as well. :(

However it is back up and running smooth with the WEP.  I guess I will have to wait till tommorrow to break it again ;)

---

### Post by pugs on 2005-12-20
Grrr...still seems to be down.  Can anyone else get to this repository?

deb [http://seveas.ubuntulinux.nl/](http://seveas.ubuntulinux.nl/) ubuntu-seveas madwifi

Or is there some other place I can get the madwifi-modules-2.6.12-10-686 package from?

---

### Post by Lambert on 2005-12-20
You can try these repositories

deb [ftp://debian.marlow.dk/]("ftp://debian.marlow.dk/") sid madwifi
deb-src [ftp://debian.marlow.dk/]("ftp://debian.marlow.dk/") sid madwifi
I had problems building this source though.

I also wrote a howto using the svn snapshot of the new madwifi-ng driver if you want to try that. 

[http://www.ubuntuforums.org/showthread.php?t=105437&highlight=madwifi]("http://www.ubuntuforums.org/showthread.php?t=105437&highlight=madwifi")

---

### Post by firecat53 on 2005-12-21
[Here's]("http://ubuntuforums.org/showthread.php?p=537499#post537499") a link to a post I made awhile back about downloading and compiling the older madwifi drivers(before they switched to the ng version) from source.  It's what I'm currently using, along with wpa_supplicant version .4.6 (I think), also compiled from source. 

I haven't tried the madwifi-ng drivers yet because the usage is a little a different, so I'd have to go back and change all my config files!  Right now I have a laptop that boots right into my WPA-psk home network....so....if it's not broke.....play with it later :)

Good luck, 
Scott

---

### Post by pugs on 2005-12-22
Well I hope that someday this silly server comes back up...seems to be the only one that had a nice package I could just use the manager to get...

I really dont want to have to compile this and go through all that especially since I had it working with the package before I decided to do a fresh install to try WPA again...GRRRRR.  It may come down to that though.

---

### Post by scifan on 2006-08-06
The DHCP non-offer is a problem of the firmware on the DI-624.  Upgrade the firmware to 2.75 and it will work with WPA enabled... :)

---

