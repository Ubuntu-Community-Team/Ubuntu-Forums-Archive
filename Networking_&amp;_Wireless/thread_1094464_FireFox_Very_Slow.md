---
title: "FireFox Very Slow"
date: 2009-03-12
forum: Networking &amp; Wireless
---

### Post by bond17_007 on 2009-03-12
I am running default firefox with Ubuntu 8.10 (Installed in WUBI, cannot get rid of windows as i need that for school :@)

Just a few days ago, I started noticing slugish performance of firefox, it takes a LONG time to load any webpage. 
I even installed Firefox under WINE (i heard in some cases, its faster)
but no luck
After searching for a while, all lead me to disable IPv6, which I did,
even updated firefox config and disabled IP6..
even after all that updates I see the browser is taking a LONG time to load any page :(

Can you guys help me figure out this issue... (I had this issue before too but then i re-installed ubuntu.. then it was faster but cannot afford to reinstall ubuntu all the time :S) 

thank you,

---

### Post by gnusci on 2009-03-12
Well here I have a collection of useful tips to get you Firefox speed back... read them below:

In Firefox, press Ctrl+T. Write about:config in the address box. You have to promise to be careful. Then and search for ipv6, and make sure the Value is True.

Comment all ipv6 related lines in the /etc/hosts
$ gksudo gedit /etc/hosts

Open:
$ gksudo gedit /etc/modprobe.d/aliases

And make sure this lines appear like:
#alias net-pf-10 ipv6
alias net-pf-10 off

Set the rate:
$ sudo iwconfig wlan0 rate 54M 

Change 54MB/s for the speed of your network...

EDIT: Dont forget restart Firefox or the machine.

---

### Post by bond17_007 on 2009-03-12
Thanks for the quick reply.
thats exactly what i did before too.. 

but still, no performance gain.. 
i have tired in different network (home / office) etc but still no performance difference.

---

### Post by gnusci on 2009-03-13
Well, the worked for me... Are you sure the problem is with FF?.... Did you try another browser?... Try with Epiphany...

---

### Post by WatchingThePain on 2009-03-13
Yeah most of those fixes don't speed it up and wreck the browser.
Better to tackle the root problem Does your pc have adware on it?.
Have you cleaned the temp files?.
Is it only firefox thats slow?.
Are you using a proxy?.
Is it firefox 3 or is it trying to upgrade.
You might need to refresh the tcp stack and I don't know how to do that on linux.
Ping a site and see if your losing packets.
Try disabling all non-vital extensions.
Try reinstalling the browser.

---

### Post by bond17_007 on 2009-03-14
Thanks all for the response.. 
I think my problem was the FLEX builder. When I had flex builder installed, it was very slow once i removed it now my browser is fast as before.

---

### Post by gnusci on 2009-03-14
Cool you solve the problem... happy surfing with FF......

---

