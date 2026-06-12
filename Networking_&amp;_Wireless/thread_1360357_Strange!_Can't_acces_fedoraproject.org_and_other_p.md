---
title: "Strange! Can't acces fedoraproject.org and other problems! LiveCDs work fine~"
date: 2009-12-20
forum: Networking &amp; Wireless
---

### Post by Zeniff on 2009-12-20
Hi~ I've been having very strange problems on Firefox in Ubuntu 9.10 for a few weeks now. 

I'll start with the strangest problem: I cannot access anything from [http://fedoraproject.org/](http://fedoraproject.org/) and haven't been able to, except for a few minutes....once..... and it never came back. This was when these problems had already been happening and after several tries to reach Fedora's site.

Other problems are just as strange but not so bad or consistent: Pages sometimes seem to randomly not be found or they are found on the wrong server or something. After several minutes, though, they usually go away after refreshing the page.

One of the strange examples from the "not found" or error pages I got was when I tried reading Wikipedia.org and it told me it "could not be found on this server," but....the server and URL it listed were from Google.com! The address bar showed that it was trying to find the page on Google! No, I didn't copy and paste or type the address, I was in an already-working Wikipedia page that stopped working and thought it was on Google's servers! Isn't that weird? (I might have screenshots somewhere...)

Anyway, any ideas? I have tried creating new, empty profiles on Firefox, but they still cannot access Fedora's sites. LiveCDs work fine, though. Also, I copied and used a profile from my Laptop to here and it also cannot access it.

I even tried System > Administration > Network tools and tried Fedora's site in the Ping tab and it usually works just fine (sometimes it gets nothing, though).

Also, I'm not using wireless or dial-up.

By the way, I've only been using Linux a couple of months now, so sorry if I don't know stuff...

Thank you very much~!!! ^_^

---

### Post by tibbitts on 2010-01-07
I just noticed the fedoraproject.org problem as well.  Sorry I don't have a solution, but was wondering if anyone else had an update.  I've had other firefox-related issues where the firefox window seems to not relinquish the mouse, but those are unrelated to the fedora issue.

Paul

---

### Post by Zeniff on 2010-01-10
I have only found some temporary workarounds that people have given me from other forums:

[http://www.linuxquestions.org/questions/linux-networking-3/strange-why-cant-acces-fedoraproject.org-and-other-problems-livecds-work-fine-777186/](http://www.linuxquestions.org/questions/linux-networking-3/strange-why-cant-acces-fedoraproject.org-and-other-problems-livecds-work-fine-777186/)
[http://forums.fedoraforum.org/showthread.php?t=236962](http://forums.fedoraforum.org/showthread.php?t=236962)

People mostly said to look at the /etc/resolv.conf file. The workarounds seem to work but I feel that file is not the main problem.

I have Ubuntu and Fedora both on the same PC, but I'm only having this problem on Ubuntu. Also, this problem happens on Opera (takes many minutes, but sometimes finally loads) as well as Firefox (many minutes, and then times out). (I'm not sure, but I think it's not related to browsers at all, since one time updating package lists in Synaptic didn't work until I did the workaround.)
   
My Ubuntu's /etc/resolv.conf file is exactly the same as my Fedora's, but only Ubuntu has problems. However, the problems are solved if I change the file (but Network Manager changes it back every time it re-connects).

Also, if I type "host fedoraproject.org" in the terminal on either Ubuntu or Fedora, they both mention a "malformed message packet" until I do that same workaround.

I think I should probably try to report this as a bug in Ubuntu in Launchpad.

---

