---
title: "ping ok, nslookup ok, skype ok, but browsing not ok"
date: 2008-12-02
forum: Networking &amp; Wireless
---

### Post by KIAaze on 2008-12-02
I'm having a problem I don't understand. My mom's PC (windows XP pro) had a working WPA wireless internet connection.
Suddenly, it stopped working, but only for browsing.

To sum it up:
**ping ok, nslookup ok, skype ok, but browsing not ok**

And the connection settings of IE7+FF were set to no proxy.

I booted into an Ubuntu 8.04 Live CD and was able to establish the wireless connection, but the problem was the same: everything works, except browsing.

In the meanwhile, my laptop had no problems connecting over wireless.

Router: T-Sinus 1054 DSL
Wireless card: MSI Model: PC54G2 / MSI part nb: ms-6834

This page here: [http://www.msicomputer.com/product/p_spec.asp?model=PC54G2](http://www.msicomputer.com/product/p_spec.asp?model=PC54G2)
doesn't mention WPA support.

However, it has always been working before and I never got a message saying WPA not supported.
**Is there something special about WPA making it not work after a while when using a device not supporting WPA?**

Anyway, I finally got the internet connection working again by rebooting the router from my laptop (I first made a manual hardware reboot, but this didn't work and broke the DNS settings somehow since I could ping google IPs from my laptop, but not google.com).

Any ideas what's wrong with my setup?

It works now, but I'm afraid there might be problems again suddenly.

Note:
I already had wifi connection problems after upgrading to SP3: [http://forums.windowsforum.org/index.php?showtopic=38779](http://forums.windowsforum.org/index.php?showtopic=38779)
It kept connecting/disconnecting.

Removing SP3 seemed to have solved the problem, then after a few days, wireless broken again. This time with the symptoms mentioned above: ping/nslookup/skype ok, browsing not ok.

So I did a system restore: wireless ok again until today. Same symptoms.

But the fact that the wireless showed the same strange symptoms with an Ubuntu Live CD makes me think that it won't be solved by reinstalling windows/installing Ubuntu.

---

### Post by toallpointswest on 2008-12-02
To me it sounds like your firewall settings are blocking port 80. 

Fire up Firestarter and see what is says.

---

### Post by KIAaze on 2008-12-02
Does the ubuntu live CD have a firewall enabled by default blockig port 80?
And I did try quitting zonealarm... :/

It just doesn't make sense.
I mean, my mother's PC is even set up to boot into a non-admin/restricted account by default!
How can it suddenly not work anymore?

---

