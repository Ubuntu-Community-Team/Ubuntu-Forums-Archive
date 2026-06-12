---
title: "myth listing times as UTC but correct time in corner of mythweb and Backend recording"
date: 2013-03-13
forum: Mythbuntu
---

### Post by kiwamacey on 2013-03-13
I have had issues since upgrading to 0.26.. Once I resolved all the database and password issues (converg not converge really threw me) all seem to be ok until I went to mythweb and noticed that the listing times seems to be 13 hours behind. I am in NZ which is +13:00 UTC at the moment due to daylight savings so can safely assume that the listing programs are on UTC, ie at 6:00pm the breakfast show is listed.. the only special thing i did was set a different port instead of port 80 for the apache server and i am running another website (just a simple local links kind of site) alongside mythweb. Both sites are nowup and running. I have set the default.timezone = Pacific/Auckland option in /etc/php5/apache2/php.ini file and restart the server/pc but to no avail. Have I missed something in mythbackend setup? Am clutching at straws now.. Pls Help

---

### Post by kiwamacey on 2013-03-30
Looks like mythbuntu was somehow using the testing repositories not 0.26. corrected and all now ok

---

