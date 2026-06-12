---
title: "some website namely mozilla.addon page does not load in firefox ubuntu 12.04"
date: 2012-10-20
forum: Networking &amp; Wireless
---

### Post by s_c_sahoo on 2012-10-20
Dear Sir,
I have got a typical problem. While running ubuntu 12.04 in live cd mode I was not hving any problem loading "https://addons.mozilla.org/en-US/firefox/" addon pages. Web browsing was normal.

After installing the OS, started experiencing problem i.e. firefox did not load the page - "https://addons.mozilla.org/en-US/firefox/". Other pages like "www.google.com" etc are being loaded smoothly.

I sincerely request for helping me in finding the reason for this strange behavior and how to over come this.

Thanks to all in advance.

---

### Post by vasa1 on 2012-10-20
> **s_c_sahoo said:**
> Dear Sir,
I have got a typical problem. While running ubuntu 12.04 in live cd mode I was not hving any problem loading "https://addons.mozilla.org/en-US/firefox/" addon pages. Web browsing was normal.

After installing the OS, started experiencing problem i.e. firefox did not load the page - "https://addons.mozilla.org/en-US/firefox/". Other pages like "www.google.com" etc are being loaded smoothly.

I sincerely request for helping me in finding the reason for this strange behavior and how to over come this.

Thanks to all in advance.
Did you try accessing Tools, Add-ons, Get Add-ons? Does that work?

---

### Post by s_c_sahoo on 2012-10-21
I did try this but without any result. I also tried to open the using chrome but without any improvement.

Help in understanding the problem is required. Thanking you all in advance.

---

### Post by vasa1 on 2012-10-21
Can you try with all add-ons disabled? Perhaps some add-on is blocking the site?

---

### Post by vasa1 on 2012-10-21
And what happens when you run this from a terminal?
```
ping addons.mozilla.org
```

---

### Post by s_c_sahoo on 2012-10-23
Thank you for the quick response.

The page addons.mozilla.org does not load even when firefox running in all addons disabled.

Output of ping command is as given bellow:
subash@suubhras-computer:~$ ping addons.mozilla.org
PING addons.dynect.mozilla.net (63.245.217.112) 56(84) bytes of data.
64 bytes from addons.zlb.phx.mozilla.net (63.245.217.112): icmp_req=1 ttl=52 time=387 ms
64 bytes from addons.zlb.phx.mozilla.net (63.245.217.112): icmp_req=2 ttl=52 time=395 ms
64 bytes from addons.zlb.phx.mozilla.net (63.245.217.112): icmp_req=3 ttl=52 time=377 ms
64 bytes from addons.zlb.phx.mozilla.net (63.245.217.112): icmp_req=4 ttl=52 time=399 ms
64 bytes from addons.zlb.phx.mozilla.net (63.245.217.112): icmp_req=5 ttl=52 time=393 ms
64 bytes from addons.zlb.phx.mozilla.net (63.245.217.112): icmp_req=6 ttl=52 time=393 ms
64 bytes from addons.zlb.phx.mozilla.net (63.245.217.112): icmp_req=7 ttl=52 time=376 ms
^Z
[1]+  Stopped                 ping addons.mozilla.org
subash@suubhras-computer:~$ 

When I try to open the same page on Chrome installed on the same computer- It loads text only and all other things are not loaded.

Please help
Thanks in advance.

---

### Post by s_c_sahoo on 2012-10-27
Is there any around to help me solve the problem? Please spare some of your valuable time. Thanks in advance for the solution.

---

