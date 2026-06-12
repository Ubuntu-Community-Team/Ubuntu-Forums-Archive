---
title: "wireless filesharing without internet"
date: 2013-07-16
forum: Networking &amp; Wireless
---

### Post by silconsystem on 2013-07-16
HI,

I have been puzzling about this for time now and I think its time to ask:
I got to linux boxes sitting next to eachother, one has an wireless internet connection from wich I cant access the router, the other has a wireless card too but its antenna is not strong enough to pickup the signal. Is there a way I can share the internet connection, ad-hoc is not an option since I cant alter the signal received by the other PC.
I've got no crossover cable at the moment either.
I can however setup a wireless network thats not online and pick it up with the other box, is there a way to share files this way?
Or is there a way to send the internet connection over eth0 without using a crossover cable i.e. a virtual switch/hub?

I know I could just run down the street for a crossover cable but I'd like to learn some wireless tricks aswell and I have a feeling there must be some way to do this.

I run Kubuntu and Xubuntu and both machines have Backtrack 5 installed aswell (hence the wifi connection... ;)
Both wlan card are TP-Link with Atheros chipsets: Ath9k driver.

Some pointers would be very much appreciated thank you !

---

### Post by zero2xiii on 2013-07-16
Hay,

First of all, if any of the computers has a "gigabit" network card any cable will do since it no longer requires the old school x-over and straight bull twang.

Secondly, one card, one function. You can not set up 2 connections with one card to run simultaneously. You can simply do an ad-hoc connection and then access the network like you would for a wired connection, however samba might need to be installed on the "off line" computer as well and this might prove difficult. 

If you only want to transfer from the computer with internet to the computer without, you want want to set up a small FTP server and just copy the files over ftp (after establishing an ad-hoc connection of course).

I hope this answers your question.

---

### Post by silconsystem on 2013-07-16
Hi There, 

Thanks for your reply, if I try to setup an ad-hoc connection I lose the internet connection. I have no access to the router or the signal, just uname&passw.
I guess if I make changes to the connection in the network manager the manager sees this as a new connection and it doesnt connect to the net anymore although both computers make a connection suspiciously fast to this network. No internet however.
Also the cards are not Gigabit, just plain old 150Mbps dinosaurs I'm afraid.

Surely there must be some way to share files with my current kit that doesnt involve usb-sticks?

---

### Post by zero2xiii on 2013-07-16
>  if I try to setup an ad-hoc connection I lose the internet connection

Exactly what I said above, one card, one function. It is like trying to plug 2 cables into the same port on a network card. A router is specially made to accept more than one wireless connection, a normal internal card however can NOT make more than one connection (one to the router, and one to the other computer, thus 2 connections). So then sadly, the short answer it seems is "no, it is not possible" to have internet AND file sharing over the same wi-fi cards. You can have only one of the two, unless the second computer can also some how be connected to the router/switch.

A ethernet cable is dirt cheap, i would just buy one x-over then and set up a bridged connection. Would in my opinion be the best bet (also file transfer over wifi is much slower than cable, if not 11n)

Cheers and good luck

---

### Post by silconsystem on 2013-07-16
Hi again,

Sorry 4 the late response, work an' all...
So than it is possible to set up a new adhoc network thats not connected to the internet but can be used to share files then?
If so how do I get the 2 machines to communicate or is an internet connection always required when using wlan? I've read some thing about creating IP addresses in iptables but I cant get the machines to see eachother, I can however setup a new adhoc network that both machines can connect to, give it a name and an ipaddress it is just not connected to the net.
I know the cable is the awnser to sharing the connection, but if I can set up a connection to just share files it'd be fine 4 the moment.
Also its about learning a thing or two along the way like I said before...


Cheers,


Rob

---

### Post by Bashing-om on 2013-07-17
silconsystem; Hi !

This howto is the easiest method I have ever seen in respect to file sharing between 2 ubuntu machines; all that is required is a shared router.
[thread]2159449[/thread]

[INDENT][INDENT]sure hope this helps
[/INDENT][/INDENT]

---

### Post by silconsystem on 2013-07-17
Hi,

Thanks for your advices, if I have to buy something its probably gonna be the x-over cable or a hub/switch since I've got an old mac G3 bronze that I'm currently trying to set up with Lubuntu or Mint or similar (now its terminal only linux so far).
Just a shame theres no intranet solution for 2 boxes that actually stand next to eachother possible (so far, still not giving up!).
Also a shame that at any modern computer store they just sell stuff for the latest generation of PC's and I have to order an x-over cable online even though theres 4-5 stores in my region only that call themselves PC stores, one guy even said a crossover cable didnt exist anymore and isnt being made anymore either, total BS ! An online order for a 3 euro cable costs me over 15 due to shipping costs, etc also...
I got into computing with the Commodore64 and my first home computer was the MSX 1. In these days a PC store would house a fat aged and bearded wizard that would take you in the backroom and would solder a cable for you to share files from C64-ZX-Speccy to MSX to IBM and whatnot if you wanted that.
God I miss these days... people working in a PC store would actually know everything about hardware there was to know.


Thankfully I got introduced to GNU/Linux in 2005-6 since my girl worked at Novell, started fiddling with it and instantly got this vibe I got when I was figuring out my MSX1 with a massive book. Als its an amazing achievement that a project started in 1992 has become so big and so advanced and continues to grow so rapidly. Thats the real power of community effort !!
Simply amazing...


Well thank you all for your great advice, I'm gonna hunt down a set of cable pliers and a second hand hub or switcher !!


PS: I will try to awnser some other users questions when I have some time, it would be nice if I could give something back to such an amazing community aswell I think too

---

### Post by Bashing-om on 2013-07-17
silconsystem; Hey ....

What a testament... and I too go way back to the 60's , remember the Commodore 64 and the trash 80 well - my poorest of memory !
Yeah the good ole days... one built the hardware on the kitchen table, and actually know the software and a smattering of assembly language !

Anyway to the situation at hand... what results from the link I provided ?... should work great, last long time for simple file sharing. For dedicated file sharing between two ubuntu boxes back in 10.04 all I had to do was enable file sharing - on the particular folders - on each box, having a common router.
If you can just see the router simultaneously from each box by any method, should not be a problem.

[INDENT][INDENT]just try'n to help
[/INDENT][/INDENT]

---

### Post by silconsystem on 2013-07-17
Hi, thanks for your reply,

Always nice to share memories with fellow Z80 addicts ! I know all the solutions already but my problem at the moment is that theres no internet connection at my house, my neighboor has a wired connection but is unwilling to share it with me unless I pay him the absurd amount of 400 euros ! I told him that he could put a router in the electricity cabinet where the phone, electrics, gas, water, etc enter the house. Even offered to help set it up and split the bill all to no avail. Some thieving electrician told him that he HAS TO HAVE a wire going straight from the cabinet to his room/computer.
Offcourse then he could put the router there aswell but he insists its impossible and the only way is pulling more wires going to my room/computer and also I would have to cough up the 400 euros I mentioned earlier to pay this to HIS electrician, while even if it would have to be wired I could still set it up for him and save him a load of money !!
This is all  offcourse total BS and he's being totally ripped off but theres no way of convincing him otherwise. Also its not possible to get my own subscription since my neighboor is also the one who has the keys to the electricty cabinet, being a kind of jack of all trades around the house and very unreasonable aswell (his nephew owns the houses)

So... I helped myself to some network connections and had some fun with Backtrack at the same time. But this way I cant access the routers offcourse and I got only one computer with a strong enough antenna to connect to the internet. Ik know I can share files if I can connect both.So to buy a crossover cable, Gigabit ethernet cards, stronger antennas maybe a switcher would be the easiest solution offcourse and by the looks of it I dont have any other options (the switch would be nice for my mac G3 bronze ppc linux project anyway and I'm moving out there soon anyway and have my own internet, subscriptions, routers, bills 'an all).

Still its just itching me that both machines are next to eachother, and I can create an offline wireless network but I cant get them to actually communicate. To me it seems that if I create a new ad-hoc network that is not connected to an internet signal but does connect both machines it must also be possible to use ssh or ftp and send some files back and forth:confused:
I guess that the internet connection is needed to use the ftp and ssh protocols properly then, I've been fiddling around for quite some time now, but I think wireless is just not designed for intranet setups like this.


Thanks for all your replies, I'm marking this thread as solved.
If I do find a way to set up this little intranet I'll let u know, Your replies are bookmarked and ready to use as soon as my new x-cable and 15dbm antenna arrives.

---

