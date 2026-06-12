---
title: "Misterious Internet issue"
date: 2009-09-04
forum: Networking &amp; Wireless
---

### Post by jmvidalvia on 2009-09-04
I am running Intrepid Ibex.
Apparently my Firefox runs ok but I cannot access (timeout error) different websites, for instance:
I can not log into my bank account.
Youtube videos dont work, although flash is properly installed and running.
Xmarks can not synchronise
Cannot access pages like salesforce.com
And some more...

I tried with chromium, and happens the same.
I run IE inside Virtualbox and cannot access to those page but Youtube videos work (¿?).
To discard problems with my network (firewall, switch, etc) I connected a labtop runnung XP to my ethernet cable, and all works fine, so..it must be a problem from:
1- My box
2- My OS

Does anybony have an idea about where/what should I check?
Thanks!

PS: another example I just discovered, I cannot "submit new thread" to this forum, althoug I can log in and write.

---

### Post by superprash2003 on 2009-09-04
things you could try
1)disable ipv6 [https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4](https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4)
2)change MTU [http://www.prash-babu.com/2009/06/how-to-change-mtu-in-ubuntu-using-gui.html](http://www.prash-babu.com/2009/06/how-to-change-mtu-in-ubuntu-using-gui.html)
3)opendns servers - 208.67.222.222 and 208.67.220.220

---

### Post by jmvidalvia on 2009-09-07
> **superprash2003 said:**
> things you could try
1)disable ipv6 [https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4](https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4)
2)change MTU [http://www.prash-babu.com/2009/06/how-to-change-mtu-in-ubuntu-using-gui.html](http://www.prash-babu.com/2009/06/how-to-change-mtu-in-ubuntu-using-gui.html)
3)opendns servers - 208.67.222.222 and 208.67.220.220

Thank you for your help.
Unfortunately, no one of this 3 solutions worked :(
Any other ideas? :confused:
Thanks!

EDIT: a new clue that might help is that I can not send a reply to this forum. After a long wait, a dialog box appears asking what program should run the script reply.php. I have to open VirtualBox-IE and send it.

---

