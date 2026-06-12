---
title: "KVM eth0=&gt;br0 slow on laptop, Shared Blackberry ppp0"
date: 2009-04-27
forum: Networking &amp; Wireless
---

### Post by hamannp on 2009-04-27
Greetings.  First post.  It's kinda strange, so here goes.

I have a new Toshiba laptop with the Marvell Yukon 88E8040T Ethernet card. I installed Jaunty and KDE. I ditched the network manger, and configured the /etc/network/interfaces file for a static eth0 and a br0 interface for my KVM VMs. I've got bind9 working for dns. Finally, I installed barry [from source!] so that I can share my Blackberry modem between my laptop and all my VMs.  I got that working with NAT. I figured out that I had to specify my laptop eth0 IP as the gateway setting in the VM's eth0 configuration.  This Blackberry interface is set up as ppp0.  Again, this all works great, except one problem.

I'm getting 11 second page loads from my VM running SugarCRM.  Not good.  On my Jaunty desktop machine, the same VM clone gets .5-1.5 second page loads.  So, I did some debugging.  I did all the SugarCRM tuning possible -- definitely not that.  I also tried using the IPs instead of the domain names, so it's not the dns. I removed ipv6 from the guests, and even recompiled the Jaunty kernel on my laptop to get rid of ipv6.  Still, no joy.  I found a guy that said acpi was causing a slow network, so I disabled that.  Nope.  I installed wireshark, which finally led me to post here.  It gets no traffic on eth0 whatsoever. Ever.  For example, if I set a VM to ping my laptop IP address defined for eth0 wireshark sees Nada on my laptop eth0.  Bupkiss.  

I followed a post to get the Marvell NIC recognized, and it shows up fine with the lspci command.  But if I ifdown eth0, the network behaves exactly the same as if eth0 were up. If I'm bridging eth0 to br0, shouldn't I see some traffic on my laptop's eth0 interface?  I know that this Marvell NIC has caused problems for people.

That's it. I'm stuck.  Any help greatly appreciated.

Cheers! Paul

---

### Post by hamannp on 2009-04-29
Bump!

---

### Post by hamannp on 2009-05-01
bump!

---

### Post by hamannp on 2009-05-01
OK people.  I'm stuck no more.  [Although I still need help.  Read on!] 

I think I've eliminated all possible causes but one.  What you ask?  The !@#(*)*#@! Marvell Yukon Fast Ethernet controller using the standard sky2 driver.  I tried installing the sk98lin driver, but I don't think it took.  And by what super cow powers did I ascertain all of this?  Well, I decided it was time to open that spare can of Whup@ss that I've been saving.

I had this 320 GB external HD sitting around.  I installed Intrepid on it since it's more stable and better understood.  I left it pretty much standard, except of course I removed NetworkManager and Avahi-daemon.  And I setup a bridge network, br0.  Then I cloned my VMs from my desktop straight to the USB HD.  The VMs on my laptop also were clones from my desktop.  Minus a little entropy, they should be identical.

The results?  Well, booting into the external HD on my desktop system the VMs served up the applications -- well -- "Blaze fast!".  Booting into the laptop, which should be "Blaze fast", the VMs served up the same applications, "Blaze slow".  I mean "Molasses slow".  Booting into the external HD on the desktop machine again, "Blaze fast!" What's different between the two?

Desktop: Amd64 dualcore 1.66ghz [overclocked beyond that] with 4GB blaze fast RAM.

Laptop: Intel dualcore 2.0ghz with 4GB ram.  And a Marvell Yukon Ethernet card.

Possible solutions:  
1. Take another crack with the sk98lin driver on the Intrepid external HD booted into the laptop.  If that works, take another crack on the Jaunty laptop internal HD.
2.  Go to Fry's and get another laptop NIC that is well-liked by Ubuntu.
3.  Go to NO-IP.com and setup their client to serve-up my [Blaze fast!] desktop.  NAT to all my VMs.  Show off my handy-work through a browser on my laptop. 
4.  All of the above.

As I mentioned, SOMEONE PLEASE HELP!  I make this stuff up as I go along.  And all this talking to myself is doing nothing to help my schizophrenia, people.

Thank you, and good night.
--Paul

---

### Post by hamannp on 2009-05-03
Ok, so I've tried a few other things.  I burned a VM with the default network 192.168.122.1, and it was still slow as molasses.  That has led me to ask a more fundamental question.

Do either the sky2 or sk98lin drivers support bridging?  I haven't had any luck building the latter.  But methinks, no.  That would be the obvious answer. I tried googling, but no luck.

Anyone coming across this thread, consider it abandoned.  I've given this effort more time [and ultimately money] than I can possibly justify.

The obvious solution: dig into whether there is a network card that I can plug into my laptop that supports bridging AND is well liked by Ubuntu.

---

