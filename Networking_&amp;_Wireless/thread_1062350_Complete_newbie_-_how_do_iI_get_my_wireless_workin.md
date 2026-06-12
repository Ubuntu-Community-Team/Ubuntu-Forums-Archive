---
title: "Complete newbie - how do iI get my wireless working - Broadcom 4311?"
date: 2009-02-06
forum: Networking &amp; Wireless
---

### Post by JohnCaper on 2009-02-06
I think I've read just about every site on this subject. I even installed a linux driver from Broadcom, but don't know how to install it. Most of the site say to get updates etc from repository, BUT I have no internet on this computer. Can I download the needed file to a thumbdrive and then use them? What commands do I use?
I ran lshw and my network and wireless device showed up, but it says both networks are dsabled. How do I get them running - and remember I'm a newbie so the simpler the better.
Thanks

---

### Post by da mono on 2009-02-06
the easiest way is to hook up to the computer to the internet and let it downlad form the restricted driver site

---

### Post by JohnCaper on 2009-02-06
Do you mean just bypass the router? What then?

---

### Post by da mono on 2009-02-06
no just plug it with a patch cable to the router

---

### Post by superprash2003 on 2009-02-07
hope this helps [http://www.prash-babu.com/2008/11/how-to-configure-broadcom-wireless-in.html](http://www.prash-babu.com/2008/11/how-to-configure-broadcom-wireless-in.html)

---

### Post by Ayuthia on 2009-02-07
If you are using Intrepid (or Hardy 8.04.1 or 8.04.2 not 8.04), you can activate the Broadcom STA module by going into System->Administration->Hardware Drivers and select the Broadcom STA option.  If this is not clear, please check out superprash2003's link in the previous post.

The other option is to download the firmware and b43-fwcutter.  Here is a link to a guide that might help:
[http://ubuntuforums.org/showpost.php?p=6077792&postcount=72](http://ubuntuforums.org/showpost.php?p=6077792&postcount=72)

---

### Post by JohnCaper on 2009-02-07
Thanks da mono - worked like a charm!

---

