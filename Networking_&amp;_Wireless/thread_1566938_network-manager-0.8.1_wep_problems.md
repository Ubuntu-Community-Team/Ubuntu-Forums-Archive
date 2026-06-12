---
title: "network-manager-0.8.1 wep problems"
date: 2010-09-03
forum: Networking &amp; Wireless
---

### Post by mch0lic on 2010-09-03
hi

I decided to upgrade my network-manager to get my gsm network indicators to be represented but the problem i have right now is I cant connect to the wep networks it keeps asking me for password even if im giving the right one. 

I googled the same problem but the solution there (remove connection information (Network Indicator -> Edit Connections -> Wireless) but it didnt helped at all.

I also tried to downgrade the network-manager to the previous version and indicator applet but I couldn't find the indicators package (and I doubt there is one coz I installed it from sources).

Any suggestions? PS: 3g works fine, and I dont have a chance to try unsecured wireless connections...

---

### Post by ajgreeny on 2010-09-03
When entering your password, is the dropdown box on the "WEP 64/128 password/key" box or the "WEP passphrase"?  You must use the passphrase box, not the key, or your entry will not work.  I have been caught out a few times with that problem.

If that is not your answer, I do not know where to help you.

---

### Post by mch0lic on 2010-09-03
I just tried it but it doesn't work. Oh and it's not limited only to one wep network. There is at least 2 networks i cannot connect to so I assume something went wrong while installing network-manager-0.8.1 or any related libs.

Any thoughts how to downgrade the indicator applet? I want to try to do that and then run dpkg-reconfigure just in case some configs left from 0.8.1.

---

