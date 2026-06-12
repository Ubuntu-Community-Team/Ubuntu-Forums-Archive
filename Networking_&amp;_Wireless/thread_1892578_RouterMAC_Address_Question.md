---
title: "Router/MAC Address Question"
date: 2011-12-08
forum: Networking &amp; Wireless
---

### Post by R3cKL3SS_aM on 2011-12-08
I am with Comcast as my ISP, my IP doesn't change a whole lot nor do I need it too, but I just read a tutorial if I enable 'MAC address clone' and click 'Clone my PC's MAC' after changing the sixth spot hex number to something like 16 it will change my IP address after restarting my modem/router. I tested that and it does.

My question is, what does enabling or disabling 'MAC address clone' do?

Is it good or bad?

Do I want to do it or not want to do it, or does it matter?

I guess I'm just confused as to what it does, I know what a MAC address is and what it's for from reading up on it, but what am I gaining or losing if anything from cloning my MAC address?

[COLOR="Red"][SIZE="1"]Sorry if this is in the wrong section, I know it has nothing to do with linux really whatsoever, I figured maybe i'd post it here as I always seem to get quick and help results from the community.[/SIZE][/COLOR]

---

### Post by jonobr on 2011-12-08
afaik, some isps check the mac address connected to their service (i believe comcast in the US do this) and will give you access .

They know based on the first 3 octets of your mac address what equipment vendor your using so can prohibit service based on that.

Mac address cloning gets away from that where the mac address can be changed so it looks like a device the ISP is ok with.
This negates the need for you calling the ISP and asking them to change your mac address recorded etc.

Long story short, unless you desperately need to change the mac, then I wouldnt.

---

