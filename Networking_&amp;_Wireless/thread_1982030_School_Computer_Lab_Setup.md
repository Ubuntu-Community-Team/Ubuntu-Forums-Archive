---
title: "School Computer Lab Setup"
date: 2012-05-17
forum: Networking &amp; Wireless
---

### Post by Electrobricks on 2012-05-17
Hello. My school is getting 40 - 100 computers from a company changing their os. Since my school doesn't have a lot of money we are going to have to use Ubuntu. How do I go about doing this? I was hoping to have system that allows students to log in with a code and access their data. But keep in mind some are 2-4 years old. Also how would I protect the other students from dangerous websites?  Help?

Thanks in advance,
Electrobricks

---

### Post by lisati on 2012-05-17
Others more experienced in networking than myself for a school might be able to advise on options such as PXE (e.g. set up each computer as a workstation that boots Ubuntu from a central server rather than a local copy).

For protection from dangerous websites one of your options might be using something like Squid together SquidGuard: this would have the double advantage of helping save on internet bandwidth as well as providing *some* protection from "bad" websites. Other options to consider for the protection might include using something like OpenDNS which has options to limit which websites users can visit.

No doubt the ideas will start rolling shortly.

---

### Post by Megaptera on 2012-05-18
Don't forget to have a look at the features included in Edubuntu, which is designed for school use.
[http://www.edubuntu.org/](http://www.edubuntu.org/)

---

### Post by Lars Noodén on 2012-05-18
Edubuntu is a good choice, if you have two servers for your lab.  Same for [LTSP](http://ltsp.org/), from which Edubuntu comes, and [K12 LTSP](https://fedorahosted.org/k12linux/).  These are all thin client set ups and do what you are asking to do.

If you want to stay with fat clients, then you'll probably still want some kind of central file server (using NFS or Samba) for the home directories and some kind of central user management like Kerberos + LDAP.

Tools like [puppet](http://puppetlabs.com/puppet/what-is-puppet/) or [radmind](http://rsug.itd.umich.edu/software/radmind/) can be used to keep the individual desktop machines in sync and up to date.

Sounds exciting.

---

### Post by Paddy Landau on 2012-05-18
If you find Edubuntu is too slow for your computers, you can have a look at [Lubuntu]("http://lubuntu.net/").

---

### Post by Electrobricks on 2012-05-18
Wow thanks for the suggestions. Give me a few days to look over the info you guys have given me. And then provide some feedback.

Thanks,
Electrobricks

---

### Post by Electrobricks on 2012-05-23
So after looking over what you guys have posted here, this is what I think I should do:
1. Install Edubuntu (Install Lubuntu on older computers with the      software that Edubuntu has.)
2. Select 10 computers to host some servers. I will use LTSP.
3. Connect the other computers to the servers. (How do I do this?)
4. Sync Files and keep computers up to date. (How do I do this?)
6. Setup the servers to allow student login. (How do I do this?)
5. Use OpenDNS to prevent the viewing of bad websites.

More Questions:
Would I have to upgrade the internet speed to support the servers and computers? (It isn't that fast right now.)
Do I need direct connection or a wireless connection between the servers and the clients?
What are libraries doing to setup computer labs?

Thanks in advance!
Electrobricks

---

### Post by Lars Noodén on 2012-05-23
The Internet connection is not so important in LTSP, but the LAN speeds are at least within each lab.  You do need a direct wired connection between each pair of servers and the lab they are supporting.  The sites dedicated to LTSP will have a lot of details as to how much is good or how little you can get away with, but ideally the LAN should be 1Gbps.  There is also a formula for the amount of RAM needed per client.

As far as libraries go, I've seen several with standalone fat clients.  I've also seen others using LTSP, but do not know what kind of hardware they have on the back end.  A third, which I've read about and not seen, was this one:
[http://www.alandmoore.com/blog/2011/11/05/creating-a-kiosk-with-linux-and-x11-2011-edition/](http://www.alandmoore.com/blog/2011/11/05/creating-a-kiosk-with-linux-and-x11-2011-edition/)

---

### Post by rg4w on 2012-05-23
This is only tangentially related, but you may enjoy corresponding with 16-year old Ubuntu powerhouse John Kim, who's begun the process to initiate an Ubuntu rollout at the high school he attends:
[http://epikvision.blogspot.com/2012/05/game-changing-proposal-ubuntu-for.html](http://epikvision.blogspot.com/2012/05/game-changing-proposal-ubuntu-for.html)

He's a regular member of our local Ubuntu Hour in Pasadena, and attended UDS-Q in Oakland a couple weeks ago, where he got good guidance on how he can contribute to MOTU.

On the technical side, he may benefit greatly from your experience.  And in return I'd be surprised if his intelligent enthusiasm wasn't helpful for you as well.

---

### Post by Electrobricks on 2012-05-27
So it looks like I need to set up a thin client computer lab due to the fact my school will be getting some IBM Thinkpad T60s. Here are some questions I need to be answered:
How do I set up a server? 
How do I connect the clients to the server?
How do I keep all of the files in sync?

I am really lost. I have no clue what to do. Could someone help me? I couldn't find any guides.

Thanks in advance,
Abraham Close

---

### Post by madverb on 2012-05-27
You might be after OpenLDAP: [https://help.ubuntu.com/community/OpenLDAPServer](https://help.ubuntu.com/community/OpenLDAPServer)
Do you want a server to authenticate users against?

---

### Post by Electrobricks on 2012-05-27
> **madverb said:**
> You might be after OpenLDAP: [https://help.ubuntu.com/community/OpenLDAPServer](https://help.ubuntu.com/community/OpenLDAPServer)
Do you want a server to authenticate users against?

Yes. But right now I need some questions answered:
How do I set up a server for the computer lab? (I have decided that I need to create a THIN Client set up using LTSP.)
How do I connect the clients to the server?
How do I keep all of the files in sync?

I am really lost. I couldn't find any guides.

Thanks in advance,
Abraham Close

---

### Post by Electrobricks on 2012-05-28
Anyone? Any tutorial or guide? I am really lost.

---

### Post by Paddy Landau on 2012-05-28
> **Electrobricks said:**
> Anyone? Any tutorial or guide? I am really lost.
I think you are looking at quite advanced topics. I suggest you start one step at a time, because that's quite a big bite you're taking.

First start by setting up just one computer.

Install Samba ([system-config-samba]("apt:system-config-samba")); create a shared public folder; get Windows and the Ubuntu machines to see each other on the network.

Get the printer and any other accessories working.

Configure a few more machines and get them all working, including seeing each other on the network.

Only then start looking at setting up a server.

---

### Post by Electrobricks on 2012-05-28
Found it! So I am going to be creating a fat client server. Here is a very helpful guide on doing so: [https://help.ubuntu.com/community/UbuntuLTSP/FatClients](https://help.ubuntu.com/community/UbuntuLTSP/FatClients)
Now, I need help on three things:
How do I connect a server to a client?
How do I boot?
How do I keep the files in sync? (I will have one server per grade.)

Thanks in advance,
Electrobricks

---

### Post by Paddy Landau on 2012-05-29
> **Electrobricks said:**
> So I am going to be creating a fat client server.
Thank you for the link.

In this case, you don't have to keep files in sync, because your fat server (which better be a good machine!) will be running all the apps.

Unless I have misunderstood which files you mean.

---

### Post by Lars Noodén on 2012-05-29
It goes the other direction, you connect the client to the server.  Since your LTSP example uses NFS, you'll want to start reading on using NFS clients (rather simple).

Also, soak up anything you can find on LTSP Fat Clients specifically.  There are a lot of tutorials out there.

Since LTSP is widely used but rather specialized.  So it's no surprise that it has its own mailing list with list archive.  Try searching through the archived messages to get a feel for the list and then subscribe so you can post your own questions.

[https://lists.sourceforge.net/lists/listinfo/ltsp-discuss](https://lists.sourceforge.net/lists/listinfo/ltsp-discuss)

[https://lists.ubuntu.com/mailman/listinfo/edubuntu-users](https://lists.ubuntu.com/mailman/listinfo/edubuntu-users)

People here are likely to have experience with individual components, but in the LTSP forum or lists you will get people that have put it all together and know the big picture.

---

