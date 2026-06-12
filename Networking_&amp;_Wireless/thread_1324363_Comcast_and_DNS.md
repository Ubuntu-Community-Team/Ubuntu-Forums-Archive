---
title: "Comcast and DNS"
date: 2009-11-12
forum: Networking &amp; Wireless
---

### Post by jimbo99 on 2009-11-12
Under Windows XP, Vista, and 7, the DNS servers in comcast are working nicely.  Under Linux, all my linux boxes, every one of them, there's a long time for a server to respond.  I may spend 5 to 10 seconds waiting for a server to respond.  Programs like last.fm refuse to work at all.  Hulu desktop for linux is so sluggish that it is extremely irritating.

Those same programs under Windows work perfect.

I've traced the problem down to comcast's DNS servers.  If I use the open dns servers 208.67.220.220 and 208.67.222.222 then these programs work properly under linux.  No delays, no fubars....

When I do another problem crops up.  This problem is that using fstab to mount network shares via cifs no longer works.  If I try to use a program such as smb4k it also fails.  If I switch back to the DNS provided by my router then the mounting of the shares works but I'm back to the delays.

I need ideas on how to resolve this once and for all.  I have a dlink dir655 router.  Is there a way to change the router and to have this work from there?  I would appreciate it.

Needless to say Comcast has become one big FU after the other.  They need to be chopped down more than a notch.

---

### Post by Mgiacchetti on 2009-11-12
What I usually do is program my router to go to OpenDNS, forward that to my desktop, and use 4.2.2.1-4.2.2.4 (verizon) on my laptop.

Here's a huge list. (you can add what you know if they're not there)
[http://www.dnsserverlist.org/](http://www.dnsserverlist.org/)

---

### Post by oldgeekster on 2009-11-12
> **jimbo99 said:**
> Under Windows XP, Vista, and 7, the DNS servers in comcast are working nicely.  Under Linux, all my linux boxes, every one of them, there's a long time for a server to respond.  I may spend 5 to 10 seconds waiting for a server to respond.  Programs like last.fm refuse to work at all.  Hulu desktop for linux is so sluggish that it is extremely irritating.

Those same programs under Windows work perfect.

I've traced the problem down to comcast's DNS servers.  If I use the open dns servers 208.67.220.220 and 208.67.222.222 then these programs work properly under linux.  No delays, no fubars....

When I do another problem crops up.  This problem is that using fstab to mount network shares via cifs no longer works.  If I try to use a program such as smb4k it also fails.  If I switch back to the DNS provided by my router then the mounting of the shares works but I'm back to the delays.

I need ideas on how to resolve this once and for all.  I have a dlink dir655 router.  Is there a way to change the router and to have this work from there?  I would appreciate it.

Needless to say Comcast has become one big FU after the other.  They need to be chopped down more than a notch.Jimbo, when you say "all my linux boxes", what distros/versions of linux is installed on the affected computers?

---

### Post by jimbo99 on 2009-11-12
All my Linux boxes, all 14 or so, everyone of them are running K/Ubuntu.  I own and operate a small computer repair shop.  I don't like paying Microsoft a cent.

My issue is pretty clear if you read the post.  If I don't use the open dns servers I have long delays and some products don't work properly.  If I do use them then mounting shares on other computers via fstab using cifs fail.  Currently every one is using Jaunty or Karmic.

---

### Post by jimbo99 on 2009-11-12
> **Mgiacchetti said:**
> What I usually do is program my router to go to OpenDNS, forward that to my desktop, and use 4.2.2.1-4.2.2.4 (verizon) on my laptop.

Here's a huge list. (you can add what you know if they're not there)
[http://www.dnsserverlist.org/](http://www.dnsserverlist.org/)

I've been looking around in the router settings to locate where I can change the DNS.  I haven't been able to find it yet.

I have a few Macintosh OSX machines and a couple Windows machines, including a copy of Win7 and several Vista boxes.  These all work 100% with comcast's DNS servers.  Only the Linux boxes have a problem.

---

### Post by jimbo99 on 2009-11-12
Changing the DNS server IPs in the router causes the same problem.  I can't use FSTAB to mount remote shares.  When I do a sudo mount -a all I get is that the command has timed out.

I've rebooted each machine and gotten no where.

The Mac and Windows machines properly see the Linux shares and Linux sees (via smb4k) the other Linux, Mac, and Win machines but it can't see any shares on any of the machines.  If I use the IP, via smb4k, I can mount a share on one or more of the machines.  I do not wish to use the IP addresses.  It should never be done.  A change to the router can cause the IPs to change and throw everything into a mess, not to mention that too much customization causes the KISS principle to become totally f'd up.

Any more ideas?

---

### Post by oldgeekster on 2009-11-12
> **jimbo99 said:**
> All my Linux boxes, all 14 or so, everyone of them are running K/Ubuntu.  I own and operate a small computer repair shop.  I don't like paying Microsoft a cent.

My issue is pretty clear if you read the post.  If I don't use the open dns servers I have long delays and some products don't work properly.  If I do use them then mounting shares on other computers via fstab using cifs fail.  Currently every one is using Jaunty or Karmic.I read the post - I just read it again. It sounded as though you were blaming ComCast - I am on Cox and having a similar problem but ONLY with/since I installed Karmic Koala on one of my notebooks.  Hope you find a solution.

I do have to ask, however, since you have obviously been building your business network for a while - did this problem just get started recently? Say, after October 27th?

Again, good luck.

---

### Post by dmizer on 2009-11-13
> **jimbo99 said:**
> Under Windows XP, Vista, and 7, the DNS servers in comcast are working nicely.  Under Linux, all my linux boxes, every one of them, there's a long time for a server to respond.  I may spend 5 to 10 seconds waiting for a server to respond.  Programs like last.fm refuse to work at all.  Hulu desktop for linux is so sluggish that it is extremely irritating.

Those same programs under Windows work perfect.

I've traced the problem down to comcast's DNS servers.  If I use the open dns servers 208.67.220.220 and 208.67.222.222 then these programs work properly under linux.  No delays, no fubars....

When I do another problem crops up.  This problem is that using fstab to mount network shares via cifs no longer works.  If I try to use a program such as smb4k it also fails.  If I switch back to the DNS provided by my router then the mounting of the shares works but I'm back to the delays.

I need ideas on how to resolve this once and for all.  I have a dlink dir655 router.  Is there a way to change the router and to have this work from there?  I would appreciate it.

Needless to say Comcast has become one big FU after the other.  They need to be chopped down more than a notch.

See the 2nd link in my sig. The configuration given in my CIFS howto will work with OpenDNS.

---

### Post by jimbo99 on 2009-11-13
I've been running Linux on my machines for years and I've had Comcast longer than I've been running Linux.  Comcast goes back 6 years and Linux about 5.

The issue I'm having with slow DNS responses where I get the browser messages "looking up...." and the lags in Hulu desktop as well as the inability of last.fm to work only affect my Linux boxes.  My Macintosh boxes and Windows (Vista, XP, and Win7) all do not experience this issue.

If I switch to an open dns server the "lag" problems are no longer there, and my Macintosh and Windows boxes work correctly still.

The reason I attribute this to Comcast is because they changed the DNS servers forcing customers to use their new system where they can present them with ads on those pages where they hit a bad url.  Prior to this I had little to no problems.

The problem with switching to open dns is that after changing those settings in the /etc/resolv.conf file I can no longer connect to my share on various machines.  Prior to switching to open dns servers I am able to access those shares. If I switch back to the DNS servers provided by comcast I can once again access those shares.

If I leave the /etc/resolv.conf file alone and alter the router to use the open DNS servers I have the same problem.  I cannot access my shares.

I have set the shares up using the /etc/fstab file.  I have used this file in this manner for the past 3 or so years.  

#network share mounts
//servname/sharename    /media/sharename    cifs         defaults,uid=1000,gid=1000       0  0  


I do not use IP addresses.  This creates a much greater support nightmare down the road when and if the IP addresses change.  (I know you can reserve IPs for machines using the router.)

I have several shares.  I have also tested the problem on multiple machines.

Again, if I switch back to the DNS servers provided by Comcast I can access my shares but I have the lengthy lag when opening pages or accessing sites such as hulu via the hulu desktop.

I turned off all the computers and let them sit a while.  I started up my main computer.  This then set it as the master browser.  Afterwards I turned on a few of the other machines.  They see it as the master browser. Even so, I cannot access the shares from Linux on another Linux box nor can I access a Windows or Macintosh share from the Linux boxes.

---

### Post by dmizer on 2009-11-14
I assure you, my howto allows name resolution to work along with OpenDNS.

Edit /etc/nsswitch.conf and look for this line:
```
hosts:          files mdns4_minimal [NOTFOUND=return] dns mdns4
```
Add "wins" to the line so it looks like this:
```
hosts:          files mdns4_minimal [NOTFOUND=return] [COLOR="Red"]**wins**[/COLOR] dns mdns4
```
The position of "wins" is EXTREMELY important. It must come before DNS, otherwise name resolution will not work if you're using OpenDNS servers. Look here for more information on why:  [http://ubuntuforums.org/showpost.php?p=7255859&postcount=15](http://ubuntuforums.org/showpost.php?p=7255859&postcount=15)

Then, install winbind:
```
sudo apt-get install winbind
```

Now local name resolution will work even if you're using OpenDNS name servers.

---

### Post by jimbo99 on 2009-11-14
> **dmizer said:**
> I assure you, my howto allows name resolution to work along with OpenDNS.

Edit /etc/nsswitch.conf and look for this line:
```
hosts:          files mdns4_minimal [NOTFOUND=return] dns mdns4
```
Add "wins" to the line so it looks like this:
```
hosts:          files mdns4_minimal [NOTFOUND=return] [COLOR="Red"]**wins**[/COLOR] dns mdns4
```
The position of "wins" is EXTREMELY important. It must come before DNS, otherwise name resolution will not work if you're using OpenDNS servers. Look here for more information on why:  [http://ubuntuforums.org/showpost.php?p=7255859&postcount=15](http://ubuntuforums.org/showpost.php?p=7255859&postcount=15)

Then, install winbind:
```
sudo apt-get install winbind
```

Now local name resolution will work even if you're using OpenDNS name servers.

All of that has been in place for about 2 years.  Every machine in my shop has that already set up.

Anyone else?  I would appreciate any help.

---

### Post by dmizer on 2009-11-14
> **jimbo99 said:**
> All of that has been in place for about 2 years.  Every machine in my shop has that already set up.

Anyone else?  I would appreciate any help.

Please post your /etc/samba/smb.conf file.

I know this works because I use OpenDNS myself.

---

