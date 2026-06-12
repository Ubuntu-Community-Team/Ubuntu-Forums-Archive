---
title: "Wireless working, Firefox Not"
date: 2011-01-21
forum: Networking &amp; Wireless
---

### Post by kgriff on 2011-01-21
Hello all.  I loaded 10.10 on my new laptop a couple of days ago.  Until this morning everything was fine.  Now, today, Firefox doesn't seem to be able to connect to the internet.  My wireless connection is working, as evidenced by the fact that ping -c 5 google.com tells me 5 packets transmitted and 5 received.  However, if I try [www.google.com](www.google.com) in Firefox (or yahoo, or anything else) Firefox times out.
Additionally, Synaptic Package Manager works fine.  I just installed something using it.  Anyone have any ideas what I could have broke in Firefox?
Should I delete the Firefox profile and start over?

---

### Post by sikander3786 on 2011-01-21
Go to Firefox > Edit > Preferences > Advanced > Network > Settings and make sure "No Proxy" is selected.

---

### Post by kgriff on 2011-01-21
Unfortunately, I've been there already.  That's not it.
I did figure something else out, though.
Command line ping works, but the gui ping in Administration - Network Tools does not.

---

### Post by kgriff on 2011-01-22
Bump.
Ideas anyone?  I'm stumped.  I've looked at every post I can find here, as well as google searches, but I've not made any progress.

---

### Post by kgriff on 2011-01-22
So, I may have this solved, but I don't know what was wrong.  I installed Epiphany browser and it works fine.  As if by magic, Firefox also seems to be working correctly now.
So, for what it's worth, I can now load web pages with Firefox, but I'm still perplexed as to what was wrong.

More experimentation, new information.  Firefox only works with Epiphany running, and Firefox will only load pages that Epiphany has already loaded during the current session.  For example, in Firefox, I can load google, but only if Epiphany has already loaded google.  I can successfully perform a search in google using Firefox, but cannot load any of the search results, without first loading the result in Epiphany.
Any thoughts, or is this a brand-spanking new, unique to me, problem?

---

### Post by TBABill on 2011-01-22
Did you disable IPv6 in Firefox? That's a constant source of trouble and something I disable upon install of a distro. Go to ```
about:config
``` in the URL bar of Firefox and hit enter. Then there is a search bar and you can search for ```
network.dns.disableipv6
``` and just double click it till it shows "true".

---

### Post by kgriff on 2011-01-22
Thanks for the info.
Oddly enough, I had just found that on Mozilla's web site and disabled IPv6.  I'm typing this in Firefox, so apparently it did the trick.

---

### Post by HouTex on 2011-01-23
I have the same problem and disabling IPv6 did not help.  I still can not connect with Firefox although I can connect to the WAP.

---

