---
title: "see if someone logs onto my wireless network"
date: 2010-10-30
forum: Networking &amp; Wireless
---

### Post by rudeboyskunk on 2010-10-30
Ok, so when I use my wireless router, I use WPA2 password protection, but I know for a smart person that can be easy to get around. What I want is for a pop-up to show up notifying me if somebody logs onto my wireless network and gives me the option to boot them off / ban their IP address.  Is this possible? Is there a package in the repos that can do this?

---

### Post by iponeverything on 2010-10-30
> **rudeboyskunk said:**
> Ok, so when I use my wireless router, I use WPA2 password protection, but I know for a smart person that can be easy to get around. What I want is for a pop-up to show up notifying me if somebody logs onto my wireless network and gives me the option to boot them off / ban their IP address.  Is this possible? Is there a package in the repos that can do this?

as far as I know, wpa2 has no known issues.

---

### Post by bigfootnmd on 2010-10-30
Most Routers have an internal Web page.  My router's page lets me see who is connected to my router, and who was connected.
So, even if somebody cracked your WPA password you should be able to see them on the my network page or something similar. Then you could ban that person by the mac address of their network card.

Another thing to do is to disable your SSID broadcast.  That way only connections that specifically configured for your wifi router will connect.  By not broadcasting the SSID you prevent any one that is fishing for a WIFI connection from even trying to connect to your router.

If you really want to make things harder try basing your password/shared key on something only you know. For example take your favorite book and base your shared key on the first letter of every fourth word in the third page of the fourth chapter.  Or some other frequency.  Or use a historical document for your state, province or country.
Or your favorite song. The point here is the shared key or password is not based on a word which would make the password easier to crack using a dictionary attack.  

If you really want to make your shared key hard base in first in ASCII and then convert it to HEX.  When I first had WIFI in my home I started with my WEP password in ASCII and then converted it to hex.  Even I could never remember the HEX password and would always have to print it out to re-enter it.

Lastly, Kudos to you for using WPA instead of WEP.

---

