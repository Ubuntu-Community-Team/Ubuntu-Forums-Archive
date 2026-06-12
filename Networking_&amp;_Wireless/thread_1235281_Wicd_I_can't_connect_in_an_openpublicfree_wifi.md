---
title: "Wicd: I can't connect in an open/public/free wifi"
date: 2009-08-08
forum: Networking &amp; Wireless
---

### Post by komikieee on 2009-08-08
Hi people, this is my first message :)

I have an eee 901 with UNR and Wicd instaled. At home I use a wifi (wep) and I don't have any problem but I can't connect in my usual pub. The pub has open wifi (non password) and the Wicd detect the signal, but when I click CONNECT wicd stars "connecting to ip" and then... nothing.

:confused::confused:

(sorry for my english)

---

### Post by komikieee on 2009-08-09
Nobody? :(:(

---

### Post by bpalone on 2009-08-09
I have seen other threads dealing with similar events with wifi.  I have had trouble on a ship with wifi, where it would not always connect and then would be slow.  I finally just used the other OS (Windoze) when I needed to connect.

The world is hooked on the Redmond, Washington U.S.A. coolaid, so most programmers never give a thought to any other OS.  From the threads I have read, it is something that the router is looking for in the packets that M$ sends.  If you have the time and know the party responsible for the IT at your point of question, then you can probably get it worked out.

Sorry, I don't have a better answer for you.  But do search for something along the lines of "unable to access school wireless" and hopefully that will turn some threads.  Also, don't be afraid to use Google.

Good luck.

---

### Post by komikieee on 2009-08-10
Thanks bpalone,

I am sure that the problem is very easy to solve for expert people but I am lost with this. If I can't connect to wifis with ubuntu I don't need ubuntu :(

---

### Post by bpalone on 2009-08-11
I haven't had widespread issues with wifi and Linux.  It does happen from time to time though.  If the place giving you trouble is a place you frequent regulalry then I would say it is worth the effort to figue it out.  Any opportunity to learn should be grasped with both hands and held on to and appreciated.  Look at it as an opportunity to learn more about how wifi works and the next time you will know just what to do to overcome the issue.

Don't throw in the towel just yet.

---

### Post by komikieee on 2009-08-11
> **bpalone said:**
> I haven't had widespread issues with wifi and Linux.  It does happen from time to time though.  If the place giving you trouble is a place you frequent regulalry then I would say it is worth the effort to figue it out.  Any opportunity to learn should be grasped with both hands and held on to and appreciated.  Look at it as an opportunity to learn more about how wifi works and the next time you will know just what to do to overcome the issue.

Don't throw in the towel just yet.

I want to learn but if nobody teach, show or answer me is very difficult. I've the same question with the same problem in different forums (official wicd, spanish linux forums, etc) and nobody answer or knows the solution :(

---

### Post by bpalone on 2009-08-11
Try a google search with a search term of:

Linux connecting on open wifi


This is one I found there:

[http://www.devhardware.com/forums/networking-34/unable-to-connect-wifi-in-linux-203374.html](http://www.devhardware.com/forums/networking-34/unable-to-connect-wifi-in-linux-203374.html)

You may have to dig for a while, but someone has had the same problem and it has been cured. (I would be willing to bet, anyway.)

Have you been able to connect at the point with Windows?  If so, were there any special screens or anything before it connected to the web?  I haven't needed to this, as I haven't really needed to use my Ubuntu when I was out.  You may have to sniff some packets in order to figure out what is going on.  Do you know anyone where you live that is a Linux Guru, if so that would be a good place to start.

Sorry, that I don't have definitive answers for you.  But I hope the thoughts I have had will help you locate an answer.

---

### Post by komikieee on 2009-08-11
> **bpalone said:**
> Try a google search with a search term of:

Linux connecting on open wifi


This is one I found there:

[http://www.devhardware.com/forums/networking-34/unable-to-connect-wifi-in-linux-203374.html](http://www.devhardware.com/forums/networking-34/unable-to-connect-wifi-in-linux-203374.html)

You may have to dig for a while, but someone has had the same problem and it has been cured. (I would be willing to bet, anyway.)

Have you been able to connect at the point with Windows?  If so, were there any special screens or anything before it connected to the web?  I haven't needed to this, as I haven't really needed to use my Ubuntu when I was out.  You may have to sniff some packets in order to figure out what is going on.  Do you know anyone where you live that is a Linux Guru, if so that would be a good place to start.

Sorry, that I don't have definitive answers for you.  But I hope the thoughts I have had will help you locate an answer.

Thanks **bpalone** for your interest :)

Windows users don't have any problem with the open wifi conection, just me, the ubuntu user :( There is another friend who use ubuntu and he has the same problem and unfortenally he is not a linux guru, so I still waiting [-o<

---

### Post by DW1988 on 2009-12-05
Not that it's much help but I too have similar problem

I can connect to my wep home wireless but not my university's PEAP-MSCHAP wireless or the wireless in the lab I work in, which has not security it's just locked to mac addresses.

I've tried using the following plus combinations of them

Wicd/Network Manager

Ubuntu/Broadcom Propriety drivers

dhcp3 client/ dhcpd

I believe it's something to do with the DHCP as when I try and connect with wicd it fails when attempting obtain an ip.

Annoyingly I can use wicd and dhcpd on my openSuse laptop and can get connected straight away. So either it is a network card problem or I'm missing some other thing required to connect. It's bloody annoying as I bought my mini 10v for university and working in the lab and so it is completely redundant until I can get wireless working. I'm even considering trashing ubuntu and trying openSuse or even XP :(

---

### Post by JBAlaska on 2009-12-05
Have you tried using wifi-radar instead of wicd? I've not used it but have heard it may do better in public (open) access points.

---

### Post by DW1988 on 2009-12-06
Thank you for the suggestion, but wifi-radar didn't help. I have now solved my problem, and it only took the last 4 weeks since my mini 10v arrived :(. Anywho in case anybody else comes across this with a similar problem. This is the final combination that allowed me to connect to a public wifi points.
[B]
Broadcom Proprietary Driver[/B] (Not sure if this was actually important)
**wicd wireless daemon** (used the latest version, had to install it manually as there is no netbook repository, i just used the hardy standard version and it seems to work)
**pump  **DHCP client (downloaded this via synaptics, once installed you need to change the dhcp settings in wicd from auto or whatever to pump)

This combination seems to work for my ubuntu remix on dell mini10v so maybe it will be for you. 

We know how to get it to work now, spread the word ;)

---

### Post by burton247 on 2009-12-07
I shall try this tomorrow :)
I've been unable to connect to my uni network that uses peap as well. I have found weblogs of staff telling us how to get it to work with linux, even teching us to make our own CA. It didnt look like they were using ubuntu though. I was gna boot up zenwalk tomorrow and see if i could get it working with that, however i shall try this first

---

