---
title: "How to access IPs by machine name?"
date: 2009-10-09
forum: Networking &amp; Wireless
---

### Post by shaggy999 on 2009-10-09
I have several computers on a local network with IPs handed out by a wireless router that I don't have control over. I would like to be able to connect to machines by their machine name. For example, if I have a webserver at machine1 I should be able to go to: [http://machine1/](http://machine1/).

I was always able to do this with Windows machines but it doesn't work with linux machines. The IPs are handed out dynamically by the router, which I don't have control over. But I did notice that the router starts handing out IPs starting at 100, so I set one of my computers to static IP copying over all the pertinent information and gave it a number less than 100 and that seemed to work. If I have to do that with all my machines I will, but that's kind of a nasty hack. My preference is to get IPs dynamically from the router.

Is there a way to do this other than hardcoding values into the hosts file?

---

### Post by jerome1232 on 2009-10-09
I know if you install samba and turn on wins in the config, your linux machines will be recognized by the other machines by their host names.

---

