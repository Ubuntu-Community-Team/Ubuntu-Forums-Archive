---
title: "Sluggishly slow loading/access of sites using https"
date: 2011-07-08
forum: Networking &amp; Wireless
---

### Post by pushkar_k on 2011-07-08
Hi ,

I'm on Ubuntu 11.04 and have wired internet connection.

Some sites (particularly https) take very long time to load . Sometimes I get "Page is taking a long time to load . Reload the page later" message.

Now , this is happening for some http webpages also.

This is not a problem with browser. 

I have firefox , chrome , chromium and konqueror installed.

Also I can access all these sites properly from windows so it is not problem with my internet connection either.

Can someone suggest a solution/ workaround ?

Thanks in advance
Pushkar

---

### Post by jmoorse on 2011-07-16
Do you have a proxy set up?  Please run 'gnome-network-properties' and check.

What DNS server do you use?  'cat /etc/resolv.conf'

Please perform some test queries and provide the output:

dig [www.google.com](www.google.com)
dig [www.youtube.com](www.youtube.com) @8.8.8.8

Also run an mtr for me:

mtr -r [www.google.com](www.google.com) 

Feel free to blank out your public IP if you feel like it.

---

