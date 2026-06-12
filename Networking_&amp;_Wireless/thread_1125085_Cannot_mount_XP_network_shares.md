---
title: "Cannot mount XP network shares"
date: 2009-04-14
forum: Networking &amp; Wireless
---

### Post by dhochmuth on 2009-04-14
I am brand new to Ubuntu (<1 week).  I am trying to network a Ubuntu 8.10 machine [wired] with my home network (2 XP Pro desktops [wired], an XP Pro laptop [wireless], and a Linksys network storage device). I use a TRENDnet wireless router with DHCP server enabled. The router is "downstream" of my telephone company-provided DSL modem. 

I can see and access shared folders on the Ubuntu machine from one of the XP machines (haven't checked the others yet).  But every time I try to access any device from the Ubuntu machine (Places>Network>Windows Network>Home [my workgroup name]) I receive the following message:

Unable to mount location
Failed to retrieve share list from server.

I have read the following threads (among others, not to mention countless pages of documentation):

[http://ubuntuforums.org/showthread.php?t=1111565&](http://ubuntuforums.org/showthread.php?t=1111565&)

and

[http://ubuntuforums.org/showthread.php?t=1082148&](http://ubuntuforums.org/showthread.php?t=1082148&)

I tried some of the "fixes" to no avail.  Part of my problem is that I am such a Ubuntu and network noob, much of the nomenclature goes way over my head.  Can someone give me the elementary school version of how to troubleshoot/solve this?  I would appreciate the help of any patient soul who doesn't mind giving very specific instructions without lots of shorthand/acronyms/implied steps etc.

Thanks

Dave

---

### Post by inobe on 2009-04-14
you shouldn't really need to do anything in terminal except setup user and password for outsiders and starting shares admin.




here's how it's done

[https://help.ubuntu.com/8.10/internet/C/networking-shares.html](https://help.ubuntu.com/8.10/internet/C/networking-shares.html)

start with "Sharing folders via the Shared Folders application" in the link, steps "1 to 11".

then if you want to have secure login scroll down to "Accessing shared folders via Windows" and follow steps "1 to 6", this section requires about one minute in terminal.

---

### Post by jonandrews on 2009-04-14
I’ve put a step-step illustrated guide to networking between Ubuntu & Windows pc’s, aimed at people coming from a Windows background, on my website:
[www.europe.eclipse.co.uk/Ubuntu/](www.europe.eclipse.co.uk/Ubuntu/)

It's generally quick & easy to do, so give it a try

---

### Post by dmizer on 2009-04-14
Step 1:
Edit /etc/nsswitch.conf. To do this, open a terminal (programs > accessories > terminal) and copy/paste this command:
```
gksudo gedit /etc/nsswitch.conf
```
Find the line that looks like this:
```
hosts:          files mdns4_minimal [NOTFOUND=return] dns mdns4
```
And just in front of "dns" add "wins" so it looks like this:
```
hosts:          files mdns4_minimal [NOTFOUND=return] [COLOR="Red"]wins[/COLOR] dns mdns4
```
Save the file, and close gedit.

Step 2:
Install winbind by copying and pasting the following command:
```
sudo aptitude install winbind
```
See if that fixes your problem.

If that still doesn't work, try this: [http://ubuntuforums.org/showthread.php?t=288534](http://ubuntuforums.org/showthread.php?t=288534)

---

### Post by dhochmuth on 2009-04-14
inobe:  Thanks for the suggestion.  I was aware of that documentation.  Unfortunately my problem was NOT accessing the Ubuntu machine from the XP machines (which is supposed to be more difficult), but rather accessing the XP machines from the Ubuntu machine.

jonandrews:  I checked out your site. You sound a lot like me!  I remember at my first job working on a DEC machine with 8" floppies....but I digress.  Your guide was nearly the perfect level for me, but alas, it did not address my problem.  It assumed the XP machines would show up in the browser.  That part of it is supposed to just "work." Mine didn't.  But thanks for the suggestion anyway, and for the trip down memory lane.

dmizer: THANK YOU.  Your instructions were easy to follow and fixed the problem.  If I could ask one more favor...can you (or anyone else) briefly explain to me in layman's terms what I just did? I saw this solution (or one very similar to it) in another thread and was not sure if it applied to my case.  I don't understand the terminology, but is this fix related to WINS?  I thought it might be, but WINS is not enabled on the XP machines.  For that reason I was unsure whether it applied.  Was the problem because of a hardware idiosyncrasy? ...a Ubuntu bug?  I'd like to have a basic understanding for future reference.  Thanks again.

Dave

---

### Post by inobe on 2009-04-14
i would like to know how winbind came up short if you followed the steps correctly :)

---

### Post by dmizer on 2009-04-14
> **dhochmuth said:**
> If I could ask one more favor...can you (or anyone else) briefly explain to me in layman's terms what I just did? I saw this solution (or one very similar to it) in another thread and was not sure if it applied to my case.  I don't understand the terminology, but is this fix related to WINS?  I thought it might be, but WINS is not enabled on the XP machines.  For that reason I was unsure whether it applied.  Was the problem because of a hardware idiosyncrasy? ...a Ubuntu bug?  I'd like to have a basic understanding for future reference.
There is a lot of good information in the [wins wikipedia article](http://en.wikipedia.org/wiki/Windows_Internet_Naming_Service#Samba). Notably:
> The WINS client from Microsoft is common across all its operating systems including DOS.

> **inobe said:**
> i would like to know how winbind came up short if you followed the steps correctly :)
Are you sure that wins is placed before dns? Order DOES matter in this file. If you place wins at the end of the line, then dns requests get queried before wins. Some hosts dns servers respond with a search page if dns queries are not successful. This counts as a resolution, so wins is never queried.

---

### Post by GMachine_24 on 2009-11-17
I realize this problem has been *resolved*, however I thought it might be useful for someone in the future to know this:

I've had the same problems as dhochmuth with the same equipment, i.e. the Trendnet wireless/wired router.

The important part is this: I cannot connect this laptop to the other computers on my network using Samba via a wireless connection. I've tried many "fixes" but am still working on it.

However, when I plug in a network cable, I have instant access to all computers on the network. I do not have to change anything.

So, the problem is somewhere in the wireless connection, that is somewhere in the software.

I will post back when/if I get this fixed.

I am using Ubuntu 9.04, Jaunty Jackalope. Yes, I know 9.10 is out.

GM

---

