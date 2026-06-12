---
title: "Resolution: Likewise Open failing to join ActiveDirectory domain"
date: 2011-04-02
forum: Networking &amp; Wireless
---

### Post by SiliconDragon on 2011-04-02
I've installed a couple dozen Ubuntu 10.10 servers and desktops over the last week. The issue I most frequently encountered was a failure of Likewise Open to join a Windows Active Directory domain with 1 of several errors (which I've also seen in many forum posts, here and elsewhere). After trying many solutions posted from other users and Support people, I finally found an officially-supported (by Likewise) method of installing and configuring Likewise Open to properly join Ubuntu (and other 'nix variants) to an AD domain. Also note that the steps are pretty simple, espeically handy for a 30-yr IT veteran who's a 30-day 'nix noob.
 
Overview:
1. The goal is to install Likewise Open 6 instead of version 5 which is what Ubuntu officially supports at this time. (Version 6 is supposedly getting rolled into Ubuntu 11.4, btw.)
2. Open the Likewise installation web page
3. Make sure your config files are prepared
4. Download either the 32- or 64-bit install script
5. Install Likewise Open 6
6. Join the AD domain
7. Optionally adjust your post-install config files for improved login/permissions support of the AD domain (e.g. FQDN machine names)
 
Here's the URL for the installation guide: 
[INDENT][http://www.likewise.com/resources/documentation_library/manuals/open/likewise-open-guide.html](http://www.likewise.com/resources/documentation_library/manuals/open/likewise-open-guide.html)
[/INDENT]Sections 3-5 are the ones you want for prep, install, and joining the AD domain.
Tip: Read the other sections as well, especially 1-2 for increased reliability, SAMBA integration, etc.
 
That's it! The web guide is an easy read, is pretty concise, and great for noobs like myself. Best of all, it just plain works.
 
Note: Here are the 2 most common errors I saw others having--plus consitently encountered myself--which the web guide addresses:
1. The command to join the domain failing because of an LSASS error. the cause is the **hosts** line in [FONT=Courier New][COLOR=blue]/etc/nsswitch.conf[/COLOR][/FONT] which governs dns lookups.
2. The DNS-related entries in [FONT=Courier New][COLOR=blue]/etc/resolv.conf[/COLOR][/FONT] needed adding/editing so Likewise Open could obtain needed domain settings from the domain controller.
 
Summary:
Likewise Open 6 is a solid improvement over version 5, both in terms of reliability and performance. Best of all, it just plain works. Most critical to it working, though, is section 3 in the web installation guide, most notably the 2 issues I mentioned above. It should also be noted that my Ubuntu 10.10 Server deployments were able to successfully join AD domains even with Likewise 5.4 once the 2 config file adjustments were made. I've abosolutely no clue why Desktop failed, though it apparently has worked for some people after applying the same config file updates; but not on the networks I worked with.
 
G'luck, g'day, and g'computing!
SD
 
PS Using Likewise Open 6 might not be necessary for everyone if you care to try adjusting the config files and restarting lwiod; then if that doesn't work, then use the Likewise Open 6 upgrade route.
 
PPS Most of my installations were VMs atop VMware ESXi or Workstation using bridged networking, if that helps anyone.

---

