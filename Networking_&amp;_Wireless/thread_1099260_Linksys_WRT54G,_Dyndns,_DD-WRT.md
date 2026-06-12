---
title: "Linksys WRT54G, Dyndns, DD-WRT"
date: 2009-03-18
forum: Networking &amp; Wireless
---

### Post by gibxam on 2009-03-18
I have been trying to get a DDNS service working. I am using dynds and have successfully created my host name. The linksys router that I have is WRT54G version 6 firmware version: 1.02.5.When I try to configure my linksys router to let dyndns know when my ip changes; I fill out the correct information and then try to save the changes but I get "Invalid Domain Name" (Please note my screen shot). I believe this is a problem that has been addressed on the dyndns website; this is a quote from the [dyndns site]("https://www.dyndns.com/news/releases/service_availability_notice_for_linksys_router_owners.html#conclusions") <--link,

"Linksys has largely fixed these problems in the most recent firmware release for the WRT54G. We ask that all owners of the WRT54G, whether they are actively using it to update a DynDNS hostname or not, upgrade to the latest firmware as soon as possible. You can get the latest firmware at the Linksys firmware download page. You must be running at least firmware version 1.42.3 to avoid causing serious problems for our systems."

The problem is that I think the firmware for my router is already up to date: I have firmware version: 1.02.5 which was updated Jan 9, 2008; moreover, this is also the most up to date download available for my router.

Is the problem with dyndns/linksys really because I haven't updated my firmware? Where would I find the necessary upgrade if this is the case?

Also, I am more than willing to switch over to open source firmware such as DD-WRT. Will this switch solve my problem with dyndns? Also will switching cause any problems with the rest of my household, (the rest of my family is running Windows XP)?

If this is the case then I shouldn't have a problem installing DD-WRT (or another type of open source wrt54g firmware) as there is plenty of documentation about it; however, I haven't found any describing whether this would hinder the performance of the rest of my house if we are running different OSes. Intuitively, I would guess that this wouldn't be an issue, but I would have to do more research if a switch is necessary or desirable.

Is there anything else you think I should know about switching to open source that you feel is very important?

Sorry for the long-winded post, tried to be as detailed as possible :). As always your time is appreciated.

---

### Post by kevdog on 2009-03-18
There are alternatives to dyndns as noip.com.  You may want to try this or even a third choice.

As far as switching to opensource ddwrt -- its great -- Ive done it on all my routers -- however BE CAREFUL.  Read about your version 6 product prior to doing this. I think this may be one of the more crappier versions with only 2Mb of internal RAM.  This means you may need the mini version rather than the standard or vpn version.  More featured versions of the firmware require more RAM.  I knew this prior to purchasing my router, so I bought accordingly (wrt54gl with 8MB on board memory).  I believe either version 1 or 2 came with up to 16Mb of on board memory.  Since this pinnacle, Linksys has cheapened their product significantly.

---

### Post by strife242 on 2009-03-18
You could always install the updater on one of the LAN clients if you don't want to mess with the firmware.

Both inadyn and ddclient are available through synaptic, and dyndns even provide a config-generator for them. I use ddclient myself since my Firewall does not support anything but http-poster which if I'm unlucky might make dyndns block my domains due to too many update attemts.

---

### Post by bvanaerde on 2009-03-18
I've got a WRT54GL (v1) and using DD-WRT v24.
DynDNS is working without problems here...

Also, it really doesnt matter what operating systems you have on your computers.

---

