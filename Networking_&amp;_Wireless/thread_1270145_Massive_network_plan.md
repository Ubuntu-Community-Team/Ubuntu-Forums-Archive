---
title: "Massive network plan"
date: 2009-09-19
forum: Networking &amp; Wireless
---

### Post by Vignesh S on 2009-09-19
OK, we have always wanted a network over here, and now that I have some time to, I would like to know how to network a desktop with a dual boot Ubuntu 8.10/Windows 7, a desktop running Windows 7, a laptop running Ubuntu 9.10 (Alpha 3 I think), a laptop running XP SP3, and a laptop running Vista Business. 

When I mean network, I mean being able to share files with ease, and being able to print stuff from another computer (the printer is currently on the Ubuntu 8.10 computer). With the printer, would I also need to need to set up the printer driver on that networked computer? I probably think so, but I'm not entirely all that sure how to set that up.

OK, I'll break it down for ya's. 

How do I network between:
Windows 7 and Ubuntu 8.10
Windows 7 and Ubuntu 9.10 alpha 3
Windows 7 and Vista business
Windows 7 and XP SP3
Ubuntu 8.10 and Ubuntu 9.10 alpha 3
Ubuntu 8.10 and Vista business
Ubuntu 8.10 and XP SP3
Ubuntu 9.10 alpha 3 and Vista Business
Ubuntu 9.10 alpha 3 and XP SP3

If I've missed something, then I'll put it this way: How do I set up the network so that any computer can access any other computer in that network?

---

### Post by hal10000 on 2009-09-19
samba is your friend.
install it from the repository, then take a look at [http://us1.samba.org/samba/](http://us1.samba.org/samba/)
or another of the millions of documentatios about samba.
You may hae to configure a lot of things according to your needs.

---

### Post by Vignesh S on 2009-09-19
Whoa, the tutorial in their website is MASSIVE! Its gonna take some time for me to navigate my way through it... :-)

---

### Post by hal10000 on 2009-09-19
Here are some other links which might be easier for a first step:
[https://help.ubuntu.com/9.04/serverguide/C/samba-ldap.html](https://help.ubuntu.com/9.04/serverguide/C/samba-ldap.html)
[http://www.ubuntugeek.com/howto-setup-samba-server-with-tdbsam-backend.html/comment-page-1](http://www.ubuntugeek.com/howto-setup-samba-server-with-tdbsam-backend.html/comment-page-1)
[http://www.howtoforge.com/samba_domaincontroller_setup_ubuntu_6.10?go=](http://www.howtoforge.com/samba_domaincontroller_setup_ubuntu_6.10?go=)
[http://www.unixmen.com/linux-tutorials/17-install-samba-server-on-ubuntu](http://www.unixmen.com/linux-tutorials/17-install-samba-server-on-ubuntu)
[http://tldp.org/LDP/solrhe/Securing-Optimizing-Linux-RH-Edition-v1.3/soft-fileshrng.html](http://tldp.org/LDP/solrhe/Securing-Optimizing-Linux-RH-Edition-v1.3/soft-fileshrng.html)
[http://tldp.org/HOWTO/Debian-and-Windows-Shared-Printing/sharing_with_windows.html](http://tldp.org/HOWTO/Debian-and-Windows-Shared-Printing/sharing_with_windows.html)
[https://help.ubuntu.com/community/MountWindowsSharesPermanently](https://help.ubuntu.com/community/MountWindowsSharesPermanently)
[http://www.unixmen.com/linux-tutorials/148-sharing-printer-on-ubuntu-linux-with-windows-](http://www.unixmen.com/linux-tutorials/148-sharing-printer-on-ubuntu-linux-with-windows-)
[http://www.ubuntugeek.com/how-to-add-ubuntu-804-to-win-server-2003-active-directory-domain.html](http://www.ubuntugeek.com/how-to-add-ubuntu-804-to-win-server-2003-active-directory-domain.html)

Also there are alot of packages related to samba e.g. administrative tools like webmin (not in the repositories), swat, system-config-samba or gadmin-tools and others you may need depending on your demands.

---

### Post by tgalati4 on 2009-09-19
I don't know if Windows Vista or 7 have Bonjour, but you can simply turn sharing on in Ubuntu and those shares will show up in file manager.

---

