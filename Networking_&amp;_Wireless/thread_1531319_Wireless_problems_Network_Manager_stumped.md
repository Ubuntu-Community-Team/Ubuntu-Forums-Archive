---
title: "Wireless problems Network Manager stumped"
date: 2010-07-14
forum: Networking &amp; Wireless
---

### Post by Enter t'Ibex on 2010-07-14
I seem to be making this problem worse all week. Now I cant get the wireless to work.

When I first loaded 10.04, my wireless worked unbelievably well. It found my home network and the nieghbours: I was surprised at how well it worked.

Through playing with hosting adhoc networks and adding a wireless printer (which again worked flawlessly initially) and lord knows what else I did to it I have the following situation:

1) I cannot make changes to any of the connections without a password. never did that before.
2) It only connects to the adhoc during login, I had to manually move to the home network at every login
3) In trying to diagnose that issue, I found the Network Manager was reporting the Last Used field incorrectly: updating the adhoc network at every login and NEVER updating the home network.
4) It will not scan and show any networks any more.  It wont even show my home network or the adhoc in the list. I even left it on for 3 hours today to confirm.
5) I tried to delete both connections and recreate only the home connection (WEP128 open 1) and now it never connects and always says that the passkey is incorrect. (trust me I have two mac's, a HP, and netbook on this connection I know its right!)
6) I tried to connect using a PCMCIA wireless card with the same results (and again I KNOW it worked before)

Please remember that I this thing worked great two weeks ago. So although it may be a driver/hardware issue, it is more likely something stupid that I have done along the way.

Any suggestions? Or can someone point me in the right direction?

---

### Post by Enter t'Ibex on 2010-07-14
Can I reinstall network manager?
If I remove network manager, wont it be impossible to reconnect, so I will not be able to re-install?

---

### Post by Enter t'Ibex on 2010-07-15
ok dont know why. But I killed the nm-applet is system monitor then ran it in terminal. It found the connection and set it to AUTO.
Then I ctrlC to stop the applet.
AFter I rebooted, it came up correctly and still has the AUTO connection.

However, it still is not scanning.  I normally have three networks showing, but its only showing mine.

Overall I don't care, its working, don't know why it wasnt, dont know why it is now either situation normal

---

