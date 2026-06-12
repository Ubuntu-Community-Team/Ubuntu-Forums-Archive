---
title: "belkn f5d7000 v2 worked in dapper betas but not now"
date: 2006-06-03
forum: Networking &amp; Wireless
---

### Post by oly on 2006-06-03
decided to clear my computer and reinstall the final release of dapper, i have been using the beta since the beginning, the beta worked fine with my wifi card how ever it does not since the re-install.

i have blacklisted the bcm45xx module and installed ndiswrapper, i have got the drivers from the ndis list and also tried the previously working ones, however i still can not get the networking to work, wlan0 does not show up in my interfaces and i get the feeling ndiswrapper is choking some where slow start ups and shutdowns or freezing on boot which ctrl + c fixes.

anything i can try log files i can view or anything, and i can not try native drives really till the wifi is up and running to get the tool to grab the firmware.

i have also tried anything i can find from these forums to no avail

](*,)

---

### Post by oly on 2006-06-05
got it working by downloading ndiswrapper from the ndis website, and running make and make install.

not ideal as really you need a internet connection i have to transfer no end of deb files via usb stick like build-essentials and its dependancies.

so possibly a bug in the default dapper ndiswrapper deb

---

