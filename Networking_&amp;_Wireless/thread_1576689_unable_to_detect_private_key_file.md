---
title: "unable to detect private key file"
date: 2010-09-17
forum: Networking &amp; Wireless
---

### Post by forax on 2010-09-17
I'm running Karmic Koala on my laptop and I'm attempting to connect to my university's secure wireless network.  I was directed here by the university's computer help website: 
[https://wiki.thayer.dartmouth.edu/display/linux/Connecting+to+Dartmouth+Secure](https://wiki.thayer.dartmouth.edu/display/linux/Connecting+to+Dartmouth+Secure)

I've followed all the steps, but when I open the wireless network authentication applet and try to browse to my private key, I can't find it.  The "chose your private key" window claims to be looking for "DER, PEM, or PKCS#12 private keys (*.der, *.pem, *.p12)," and while my private key file shows up as a .p12 file when I open that location with my file browser, the file doesn't show up when I try and browse to it from the authentication applet.  I've attached an image which shows the file in one window, but not in the other for clarification.

Thanks in advance for any help you can offer!

---

### Post by gzarkadas on 2010-09-17
First try to rename your folder to remove the space from its name. Say make it `secure-cert'. Some programs have still difficulties to handle spaces. If it is not the cause of the problem, then report back.

---

### Post by forax on 2010-09-17
Thanks for the quick response.  Tried changing the name, but still no luck.

---

### Post by gzarkadas on 2010-09-18
I tried to repeat the steps and it didn't show files in my case either. However, when I moved the files in another folder outside of Desktop it showed them. So I suggest to move the folder directly under your home folder (/home/<your-account>/securescert. 

If it works, post a note here so I can file a bug report to the network manager project at launchpad.

---

### Post by forax on 2010-09-18
I tried moving the folder and the certs themselves to a variety of locations, but no luck so far :(.

I'll swing by the college computer help desk on monday.  Hopefully they will have seen this before.  

Any other ideas?

Thanks again for the help!

---

### Post by gzarkadas on 2010-09-18
You can try to type the filename in the "Location" text box and press the Open button. It may work - after all this *is* a buggy situation, so you can expect anything :P.

Alternatively you may try to directly create a configuration file in /etc/NetworkManager/system-connections (use an existing one as template) and then find the appropriate fields to fill in section "[802-11-wireless-security]" (use the [project site]("http://projects.gnome.org/NetworkManager/") to locate documentation).

---

### Post by forax on 2010-09-20
So after messing around a bit more, I found a highly non-technical solution.  I opened the directory containing the certs in a file browser window, then opened the network authentication applet and attempted to browse to the same location.  Again, the certs were not showing up, but once I dragged and dropped the cert from the file browser window into the private key selection browser window, it appeared in both and I was able to select it and connect to the network.

---

### Post by gzarkadas on 2010-09-21
Nice that you managed to find a work-around - this isn't always possible; I have noted it for my use also :). I have filed a [bug report]("https://bugzilla.gnome.org/show_bug.cgi?id=630280") up-stream for this; I hope in a future release it will be fixed.

---

