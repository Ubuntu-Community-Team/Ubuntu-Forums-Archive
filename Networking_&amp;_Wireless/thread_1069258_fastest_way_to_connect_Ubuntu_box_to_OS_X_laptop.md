---
title: "fastest way to connect Ubuntu box to OS X laptop?"
date: 2009-02-13
forum: Networking &amp; Wireless
---

### Post by woodybrando on 2009-02-13
Hi All,
I need to connect my ubuntu box to my os x laptop to transfer 10gb's of files pretty much daily for video work. And I want to do this with the fastest connection possible here's what I've got: 

ubuntu box has 1 ethernet port1000baseT, 1 firewire 400 port

macbook has 1 ethernet port 1000baseT, 1 firewire 400 port, 1 wifi

router has 4 ethernet port 100baseT, 1 wifi b,g

Here's my options:

the fastest connection would be to have an ethernet cable go between my macbook and my ubuntu box. But I don't know how to do that. Plus, then I won't have ubuntu connected to the internet. 1000mb/s

So maybe firewire would be a better solution since then I wouldn't lose my internet connection on ubuntu and 400mb/s isn't too bad. But again I don't know how to connect the two computers over a firewire connection.

and my next option is to plug ethernet cables from both computers into the router and use the router's 100baseT connection but for some reason os x is not getting the router's ip address and instead has a self assigned address. BUt if I could get this working I could deal with the 100mb/s.

and lastly which is what i've been doing so far is just use the laptop's wifi g connection and the ubuntu's ethernet connection and transfer the files at 50mb/s which gets the job done but very slowly.

so I'm just looking for some general suggestions on how I can get a faster connection between these two computers working. Thanks, jayson

---

### Post by bhaverkamp on 2009-02-13
I would go the ethernet route myself if both systems can connect to the switch. For 10GB of data you could also consider burning a CD or using a flash stick. Tar your data down and untar on the OSX side. The choices are many.

---

### Post by woodybrando on 2009-02-13
is it me or is that first reply in chinese? 

bhaverkamp,
I guess I'd really like to figure out how to connect via fire wire or ethernet crossover cable style. I'd rather not burn dvd's daily although it's a nice way to have extra backups but I'm not a big fan of having anymore stacks of dvd-r's laying around. 

I should mention also that I'm exporting my ubuntu hard drive with nfs. So I'd like to use a firewire cable or ethernet cable to directly connect the os x laptop to my ubuntu box and be able to access the nfs export. Any guides to do that here that someone could point me to?

---

### Post by zander1013 on 2009-02-14
enable sharing on the mac and connect via firewire.

select System Preferences -> Sharing then enable the services you want to share. i think that File Sharing is it but you may have to play around a bit to get what you want.

you enable the connection you want from that control panel in os x.

hope this helps.

zander

---

