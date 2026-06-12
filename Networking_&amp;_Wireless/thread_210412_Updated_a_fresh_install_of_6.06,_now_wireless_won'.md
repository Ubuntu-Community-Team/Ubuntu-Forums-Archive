---
title: "Updated a fresh install of 6.06, now wireless won't connect.."
date: 2006-07-06
forum: Networking &amp; Wireless
---

### Post by shockme17 on 2006-07-06
I just did a fresh install of 6.06, my wireless card was recognized and able to connect to the network.. i then had a list of 97 updates.. which i did.. i rebooted, and now my wireless card won't connect.

it is still recognized, and appears to be connected to my network, but it's not.. i deleted the name of my network and other settings, and hit ok.. and it stays on "activating interface wlan0" and just hangs there for nearly a minute or two. 

i dont have access to a wired connection with this computer, so i can't get online from it.. 

how can i remedy this situation?

thank you.

---

### Post by atrus123 on 2006-07-06
Hello,

What driver are you using?  If you are using ndiswrapper w/broadcom, you may have to blacklist the Ubuntu default driver, or it will keep popping up every time your reboot.

Edit: disregard.  I just noticed that your wireless was working at install, so it probably isn't  ndiswrapper related ;-)

---

### Post by shockme17 on 2006-07-06
thanks for replying though.. 

any other suggestions?

---

### Post by orb9220 on 2006-07-07
Dapper assign ath0 to the wireless because its using restricted mode drivers or some such.

Had to congif my applets to ath0 not wlan0 those are zero's

I think until they include support in the kernal wlan is not supported yey.

Me just guessing about why ath0 but that is what dapper does then the updates
change it to wlan0 for some reason.

I changed all my wireless apps to ath0 reboot making sure sessions manger has 
save sessions on logut checked then rebooted.

Hope this helps

---

### Post by shockme17 on 2006-07-07
how would i go about that?

---

### Post by orb9220 on 2006-07-07
Go to menu > internet> wireless assistance
click on it then it should show up in sys tray.

left click for options

If not there you will have to install from synaptic packages.
Just search wireless for search term 

There is also one that is called gnome defalt one that should be starting up
showing no connection at least. And in the settings if any are wlan0
Then change to ath0

The other is right click on panel add to panel is one called network monitor
but it is a very basic one

Sorry but my durcell's are at 3,53435 % and I need to kick into Hibernate mode for next 8 hours.

---

