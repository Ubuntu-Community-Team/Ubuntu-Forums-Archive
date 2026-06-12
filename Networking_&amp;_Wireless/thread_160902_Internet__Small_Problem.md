---
title: "Internet : Small Problem"
date: 2006-04-15
forum: Networking &amp; Wireless
---

### Post by Mitt3ns on 2006-04-15
Well, Ive been using Ubuntu for a little bit now. But, what I have been to lazy to figure out is my internet problem:

I can only log into root to be able to use the internet, otherwise, it wont work.

Anyone have any suggesstions?

---

### Post by CompShrink on 2006-04-15
First I would make a backup of your firefox profile. You are talking about firefox, the default browser, correct?

Use the command:
cp ~/.mozilla ~/.mozilla_backup1

Then, I would first try going into Synaptic, from the System menu on the top panel, choose Administration > Synaptic Package Manager, find firefox, and choose the Remove Completely option. Hit apply, then install it again.

Then issue the command:
cp -f ~/.mozilla_backup1 ~/.mozilla

Try running it again, it should have your bookmarks and the rest of your profile back in it.

Now, if that still doesn't work, please give me some more details. Does firefox open but give you an error page? If so, could you write that error here please. Or does it not even open up?

---

### Post by Mitt3ns on 2006-04-15
What it will do, is open and all, but when i even do [www.google.com](www.google.com) itll just go blank in the page. But, in the bottom left corner, itll still say "waiting for google.com" or "connecting to google.com". And, i just tried getting onto it with admin, and itll just load google fast, but then when i try any other page, it wont. 

I think i need to reset my network settings... i just need to figure that out now, too.

EDIT*** 

The settings that work that let me access the main page of google are:
(using eth0)

Hostname:mitt3ns
DNS Servers:
192.168.0.1
205.171.3.65
Search domains:
domain.actdslmp

Connection: DHCP   (because i dont have a static ip)

I tried experimenting using this threads advice ([http://ubuntuforums.org/showthread.php?t=536](http://ubuntuforums.org/showthread.php?t=536)) but it didn't work; it only made my internet not even work.

---

### Post by CompShrink on 2006-04-16
Try going into synaptic and installing Opera. Try that, and you can see if it's a browser problem or a general network problem.

And/or open a terminal and try:
ping -c 3 google.com
ping -c 3 ubuntu.com

and tell me if either of those are working.

---

