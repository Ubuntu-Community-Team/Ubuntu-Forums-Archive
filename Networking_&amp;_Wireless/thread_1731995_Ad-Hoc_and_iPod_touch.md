---
title: "Ad-Hoc and iPod touch"
date: 2011-04-17
forum: Networking &amp; Wireless
---

### Post by CaptainJamie on 2011-04-17
I'm trying to connect to my 1st gen iPod touch using an Ad-Hoc network, but I can't find it on my iPod. I want to use it to do a presentation, not internet share or anything too complicated.
I set the network up as follows (I'm on 10.10 by the way).
Create new wireless network > Network name: xyz Wireless security: none - Create
Then I went to edit connections and set an IP address and subnet mask and gateway (to 192.255.0.1, 255.255.255.0, 1.1.1.1 respectively) and set Band to "B/G 2.4 GHz".
My iPod doesn't seem to be able to find the network. (It doesn't show up and typing it into "other" it "can't find the network xyz")
Thanks, Jamie

---

### Post by CaptainJamie on 2011-04-20
Bump

---

### Post by CaptainJamie on 2011-05-02
Bump... Please someone reply! Even if it's just "Yeah I'm having the same problem too..." Oh and I'm on 11.04 now.. still not working

---

### Post by joel_gil on 2011-06-08
Hey man
so if ur using natty
GUI way to do it is:
1. right click on the network manager icon.
2. click on "edit connections"
3. go to "wireless" tab
4. Click on "add"
5. Tick "connect automatically"
5. Set and SSID (the connection name doesnt matter)
6. In the "Mode" dropdown list select "Adhoc" and leave the rest of that tab options as they are
7. Change to "Wireless Security" tab, if ur just presenting (meaning a temporal network) avoid complications and leave "none" (i wouldnt recommended but u look like u need sth quick and simple)
8. Now change to the "IPv4" tab, u MUST select "shared to other computers" and tick (if it isnt) the "Require IPv4 adressing blabla"
9. DONE


now save everythign and back in the desktop right click on the network manager icon again a click on "create new wireless network", then select the one u just configured. once u click connect the adhoc should be up and appearing in ur ipod, do givie a couple of mins to connect, idk why mine took up 5 mins "obtaining an address" the first time but after that if connects automatically

good luck!

---

