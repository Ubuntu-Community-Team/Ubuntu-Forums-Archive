---
title: "Asus WL-700gE wireless storage router"
date: 2009-06-15
forum: Networking &amp; Wireless
---

### Post by nemo.r on 2009-06-15
I recently bought the Asus WL-700gE to replace my old router and to enable me to download torrents via a central source.

According to its specs it's usable with linux, but I can't find any tutorials on the net that are at my level of expertise, (complete beginner). My computer is running Ubuntu 8.04 (hardy), it is connected via ethernet to the router, but the other computers at home will all be connected via wireless. The ASUS is connected to an ADSL modem-router, (for ethernet only, no wireless) this modem-router is only being used as a modem, i.e. there are no computers connected to it directly, it just has an ethernet cable going from the back to the WAN slot in the ASUS.

All the lights that should be are, (WAN, AIR and Ready, and on the modem, ADSL), so it seems to be working. I can ping the router by typing ping 192.168.1.1, but I can't ping a web page, (like google.com or ubuntu.com) and I can't access the internet via firefox or ktorrent. If I try connecting directly into the ADSL modem-router and turning off the ASUS I still can only ping 192.168.1.1 not any web pages. Do I need to configure the modem-router as well as the ASUS? Becasue I didn't think of that and didn't check if it was linux-compatable, (it's just a "Maplin Value 4-port ADSL Modem Router").

I tried loading the Asus CD into ubuntu, the .exe windows files wouldn't run, (I haven't yet installed wine, and I'd rather do it directly in ubuntu not have to go through wine unless there's no other way). I opened the GPL folder on the cd and there were two .tar.gz files, but I don't know what to do with them. I extracted them to the desktop, but now they just sit there, should I be compiling them? how do I do that? is that all the 'make' and 'make dir' commands etc?

I went onto the 192.168.1.1 page via firefox, and tried to configure the ASUS, but I can't see that it made any difference, I set it up as DHCP and basically left everything as default beyond changing the password and the SSID.

Also the wireless is intended to be used by many different computers and some are linux, (ubuntu, kubuntu and arch linux) one is windows and one is mac, will that affect anything, or will that be irrelevant?

Any help on this would be much appreciated, I'm having to use our old router for now, which is broken and causing lots of problems.

---

### Post by superprash2003 on 2009-06-16
so your internet doesnt work when you try connecting the  modem directly?? if so , you should try fixing that first..
  is this an ADSL connection? do you have an ISP username/password ?

---

### Post by nemo.r on 2009-06-16
OK

Yes this is ADSL. I got the modem working, we do have an ISP username and password, so I put them in. The internet seems to be working now.

I'm not sure how to use the download master on the ASUS though.

---

### Post by superprash2003 on 2009-06-16
ok , read through this , the steps(idea) are similar but not exact same as your hardware is different [http://www.prash-babu.com/2008/12/how-to-connect-dsl-isp-modem-with.html](http://www.prash-babu.com/2008/12/how-to-connect-dsl-isp-modem-with.html)

---

