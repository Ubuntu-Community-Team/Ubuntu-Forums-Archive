---
title: "Wireless router question..."
date: 2006-05-23
forum: Networking &amp; Wireless
---

### Post by shorty0927 on 2006-05-23
Hope this question isn't  a "dumb" one.  I've been using Macs so long and used to things "just working" that diving into Linux has been a trial for me.

I think this question is generic enough (not ppc-specific) that I can ask everybody...

If I'm using a wireless router to connect to the internet, does there have to be a router-specific component installed on the Linux system that would allow my wireless card to communicate with it?? 

In my case, my Airport Extreme is one of the dreaded Broadcom 43xx cards and I'm trying to get an internet connection via our Linksys WRT54G router.  I've been able to pick up other wireless networks in our building, but can't seem to communicate with them, which makes me wonder if I need something that'll deal with the router, too.  I haven't seen any HOWTOs that indicate that a router driver is needed, but I'm beginning to wonder...  :-k

---

### Post by jml on 2006-05-24
I have not used the ppc version of Ubuntu, but here are some general thoughts.  I assume from your post that you have successfully installed Ubuntu and that it recognizes the wireless card, (you refer to seeing other wireless networks.).  To confirm this, open up your network manager and see if the wireless card is listed as a connection option.  If it is, click on properties and fill in the required information.  close that window and then deactivate any other connection options, (eth0 for example)  Then highlight the wireless card, and click on the activate button.  The process may take several minutes to complete.  Close out the application and see if you can connect.  If not, try rebooting the system and try to connect again.

A couple other suggestions, temporarily disable any encryption on your wireless access point and the laptop first.  Once you have an unencrypted connection, then turn on WEP if needed.  By the way, WPA encryption is not yet supported by Ubuntu outof the box.  Hopefully, version 6.06 (Dapper Drake) will support it.

Here is a link to Ubuntu's Wireless Troubleshooting guide, it may be of help to you.
Goo luck.

[https://wiki.ubuntu.com/WirelessTroubleshootingGuide](https://wiki.ubuntu.com/WirelessTroubleshootingGuide)

Joe

---

### Post by shorty0927 on 2006-05-24
Yes...Ubuntu's installed.  I've downloaded and installed all the appropriate supporting programs at least a half dozen times (all on fresh Ubuntu installs--I've become a pro at installing Ubuntu, actually).  My router shows up on the list, along with everyone else's in the building.  I click on my router, set up the configs correctly, try to connect, but nada.  When looking at the logs, it looks as though I MAY have been connected a few times, but if I was, it was for a few seconds--hardly enough time for me to notice.  When I try to use internet apps after "activating" my wireless connection, I get errors  saying that the site wasn't found.  I can't even ping the router...which is why I was wondering about a router driver.  I'm picking up wireless signals, but none of them are "listening" to me, it seems.

I haven't tried totally deactivating the security--my SO's pretty anal about keeping the security up.  I have turned off WPA, MAC filtering and made the SSID visible (leaving only WEP active), but it hasn't worked.  I'll try turning all security off this morning to see if I can get it to work.

---

### Post by shorty0927 on 2006-06-01
Well, I have good news and bad news...for about a minute last week, my wireless was working in Linux.  But I have no idea how or why it started working.  I was running through the wireless troubleshooting guide when all of a sudden, my Gmail Notify window popped up to let me know I had mail.

I don't have my logs handy, but when looking at them later (when it wasn't working again), I saw a message in the syslog instructing me to review the README about broadcast addresses.  I didn't find any useful documentation that helped me figure out what might have been wrong with my broadcast address.

At a different point, there was another message about needing to be in a queue in order to be authorized, or something like that.  There were a few others, but I can't remember what they were.  I didn't get a clear idea of what might be wrong after going through the troubleshooting guide again, either.  

My frustration is growing by leaps and bounds, and I'm starting to doubt that anybody's Airport Extreme is actually working for them.   The posts in the forums and wikis out there on the internet make the fix seem simple, but I've tried them all at least twice and they just don't work.

Are there any wireless PCMCIA cards out there that are guaranteed to work?  Preferably a card that works with wireless security measures?

---

