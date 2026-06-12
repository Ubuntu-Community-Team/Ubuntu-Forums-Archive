---
title: "Static IP"
date: 2008-01-15
forum: Mythbuntu
---

### Post by chymmylt on 2008-01-15
Pardon my stupidity ;)

When I go to set a manual IP through the network manager it keeps reverting back to a roaming profile - how do I set a static IP in mythbuntu so I can route the frontends correctly to it without it changing IP's upon reboot?

Thanks

---

### Post by murchball on 2008-01-15
Here's how I did it. In the Network dialog (Applications, System, Network) I clicked the Properties of the wired connection, unchecked 'Enable Roaming mode', selected static IP from the dropdown and filled in the info. Then OK and Close. Sudo should prompt you for a password.

Is this what you're doing?

---

### Post by chymmylt on 2008-01-15
That's exactly what I tried to do but when I when I ifconfig to check the IP it is still a DHCP'd IP - I restarted the computer just to check to make sure for some reason it wasn't going to start on next boot but no luck- went back in to check and while it had all the info correctly in the boxes, it had rechecked roaming mode on it's own and nothing I can do makes it stay unchecked :(

I've also just noticed this strange unchecking problem in the Mythbuntu Control Center when I try to check the enable daily cron and optimization checkmarks on the last page.  I check them -  they close - run the installer and then nothing - I go back and they are still unchecked.  I read somwhere this is a bug and I need the install cd in the computer which I've tried but it still doesn't stick :(

---

### Post by aaltieri on 2008-01-15
Greetings!

Here is a good walk through on setting a static IP address:

[http://www.cyberciti.biz/tips/howto-ubuntu-linux-convert-dhcp-network-configuration-to-static-ip-configuration.html]("http://www.cyberciti.biz/tips/howto-ubuntu-linux-convert-dhcp-network-configuration-to-static-ip-configuration.html")

I would uhm...advise against doing this over an SSH connection though.  *cough*   Not that _I_ would ever do anything like that.  That would just be silly!

Anyway, it's pretty straightwarward and will tell you how to set everything up via command line.  Honestly, I don't even know where the GDM utilities are for this kind of thing.

Peace


--anthony

---

### Post by chymmylt on 2008-01-17
Well that solved the IP issue - I have no idea why I couldn't get it to stick.  However, I noticed I had issues with apache being bound to the old dhcp'ed IP - driving me crazy - anyways, the solution I had was to re-install Mythbuntu and set the IP using the guide you provided below BEFORE I installed - so now I had my static IP and everything knew where to look :)

I still seem to have problems with the Mythbuntu Control Center not allowing the options to stick (defrag xfs volumes, opt. mysql etc)  Now I just need to figure this out :)

Thanks for you help though! :)

---

