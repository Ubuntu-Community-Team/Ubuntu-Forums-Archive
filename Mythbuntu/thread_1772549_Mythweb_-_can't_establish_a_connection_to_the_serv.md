---
title: "Mythweb - can't establish a connection to the server"
date: 2011-05-31
forum: Mythbuntu
---

### Post by nhtrader on 2011-05-31
Mythtv version v0.24.1-9
ubuntu 10.04

Upgraded today and now Mythweb doesn't work.
I upgraded from 20110528 v0.24.1-4 to 20110531 v0.24.1-9.


I've tried the following URLs on the local PC...
[http://localhost/mythweb](http://localhost/mythweb)
[http://10.10.10.12/mythweb](http://10.10.10.12/mythweb)

Both produce the error "can't establish a connection to the server at " using FIrefox or Opera or chrome.

Also, tried to access mythbox from another ubuntu based PC within home network. Same error message appears. Also tried to access mythbox from another Windows based PC  within home network. Same error message appears.

I tried to use Mythbuntu's Control Centre to reconfigure Mythweb. This reset the user name and password. But the same error message appears - can't establish a connection to the server at 10.10.10.12.

---

### Post by nhtrader on 2011-05-31
I still don't know what happened to cause Mythweb to fail, but the solution to re-establishing a connection was to simply uninstall it and then reinstall it.

Instructions:

1. Use GUI menus: Applications|System|Mythbuntu Control Centre
2. Select Plugins
3. Unchecked "Mythweb"
4. Select "Apply" Button
5. Reboot/Shutdown/Restart
6.  Use GUI menus: Applications|System|Mythbuntu Control Centre
7. Select Plugins
8. Check "Mythweb"
9. Select Enable
10. Set Username and password
11. Select "Apply" Button

Mythweb now works as before from local PC and from intranet (home network) and internet (outside of home network).

---

