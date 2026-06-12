---
title: "Freezing up RTL8188CE"
date: 2011-08-09
forum: Networking &amp; Wireless
---

### Post by nicknitro71 on 2011-08-09
Laptop:  Toshiba Satellite C650D
Wireless card:  Realtek RTL8188CE
Ubuntu version: 11.04 with all the latest updates (unsupported as well)

Issues:

When I plug the Ethernet cable everything is just fine, zero issues.

When the cable is unplugged and the system defaults to the wireless, I have all sort of free-up issues from not being able to log-in, to random freezes if I'm able to log-in, to inability to shut down.

I have reinstalled the driver that I have downloaded from Realtek and pretty much did everything suggested by other people with similar issues.

The problem did not go away, the wireless causes all sort of freezing issues.

Given that this is my only computer and I use it to work, I find this unacceptable but at the same time I refuse to reinstall Windows.

Any ideas and help will be greatly appreciated it!

:confused::confused::confused:

---

### Post by nicknitro71 on 2011-08-10
Anyone here?

---

### Post by 1richard on 2011-08-13
I have the same problem with the Toshiba C655 and the same wireless card, I connect the LAN and it works perfectly, disconnect the LAN and it freezes up, also I cannot install from the CD if the lAN is disconnected, it freezes up, connect the LAN and it will install. I think the wireless driver is linked to the LAN driver somehow

---

### Post by gcave on 2011-08-20
Netbook: Toshiba NB505
Wireless NIC: RTL8188CE

My issue is similar, I did go to Realtek and compile the latest driver.  This fixed my issue until I got a Kernal upgrade, now every two minutes or so my wireless connection disconnects.  Did you all compile the latest driver from Realtek?

[http://www.realtek.com/downloads/downloadsView.aspx?Langid=1&PNid=48&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true](http://www.realtek.com/downloads/downloadsView.aspx?Langid=1&PNid=48&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true)

make
make install

The solution came to me after the post.  I had to recompile the driver after I upgraded my kernal. Seems to work now.  Will give an update in a few days.  This should work though.

---

