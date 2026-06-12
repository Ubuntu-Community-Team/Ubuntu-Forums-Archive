---
title: "Azureus DHT firewalled"
date: 2006-06-06
forum: Networking &amp; Wireless
---

### Post by NiksaVel on 2006-06-06
Hey all,

pls help me out configuring azureus... I'm really getting sick of this....   

it installed okay, chosen a random port - 12348 and added it to firestarter as an exception.

but I get DHT firewalled, only get 5-10 seeds/peers out of thousands and my speed is SLOW!!!  ...   and after a couple of minutes drops to 0 and waits there..


I have a feeling I didn't set up everything I should have with ports and firewalls, but I am out of my league here...  help me out pls...   this is the original reason why I moved to linux, to have a more stable and safe comp for downloading on 24/7 100mps connection and I can't get it to work....  ](*,)

---

### Post by NiksaVel on 2006-06-06
deffinitelly didn't configure something right, same thing happening with ktorrent...   starts up for a little bit and drops down to zero speed.... every now and than (seems to be as soon as a new seeder appears)...


can someone pls explain to me what do I need to configure except from just simply installing a client?


thank you very much!

---

### Post by NiksaVel on 2006-06-06
kay... I've been running azureus, ktorrent and bittornado independantly each for some 30minutes and they all show me the same thing: CRAP!

the leachers/seeders keep at single digits (i.e. 2/1184) and my dl speed keeps fluctuating between 8 and 0 kps....   

I connect to the internet through the uni 100mps LAN and this comp downloaded great under windows+azureus.

I believe I have a problem with some firewall/port configuration, but I don't really know much about this so if anyone can help, I will REALLY appreciate it...


P.S.  I am also running MoBlock to block out unwanted reports if anyone thinks this might cause a problem....

---

### Post by NiksaVel on 2006-06-06
heh...  here's another report from the front :)
(you can see I'm pretty stressed by this situation by posting so much:)


anyways, I tried downloading mission impossible 3 to see how that would work....  

what I learned so far is that it's downloading in some kind of spikes...  it goes up to 300kps and than drops down to zero within seconds, then again hi-speed, than drops again.... and it's going on continously....  seems I'm either blocking others as soon as I start downloading or they are blocking me for some reason...

---

### Post by NiksaVel on 2006-06-06
okay...  somebody help me or shoot me...  I just tried torrents on my other comp (laptop) this one running ubuntu and the same thing is happening...

---

### Post by pelle.k on 2006-06-09
I dont know how to help you.
Can you 'tail -f /var/log/moblock.log' and watch it during download sessions to see if it blocks unusual high number of ips?
If it is, try stopping it; 'sudo /etc/init.d/moblock-nfq stop'
Have you got a router or just a modem?
In case it's a router is it configured to open ports to your ip?
It may be that your bittorrent client or ip is banned by some trackers/seeders/clients...
Try running the same torrent file with bitcomet under windows or something, see if it yields the same result.

---

### Post by NiksaVel on 2006-06-09
thanks for the reply!   :)

I tried it on my laptop computer that doesn't have moblock installed and it was working the same....

I am connected via my college LAN.


And I think :oops:  that I figured it out...  it seems that linux cannot take too many open programs at the same time ? ...  I read somehting like that on a ktorrent forum. After those 20 or so minutes when azureus just stops all downloads, ktorrent pops some error - following up on it I found on the ktorrent forums that it appears when you have too many open programs and that the limit for linux is 1024...



So what I did is  limit the simultaneous downloads to 6 and it downloaded some 10+ gigs in less than 20 hrs, which I am happy with...


btw...  kTorrent kicks Azureuses a$$, at least under linux...

---

### Post by pelle.k on 2006-06-09
Great!
I think you mean TCP/UPD connections at the same time. Not open programs.
As the linux kernel is as much a server kernel as a desktop kernel, there is no theoretcal limit a number of connections at the same time, though there might be a config file somewhere holding it to a maximum...

Ktorrent is great, i agree....

---

### Post by NiksaVel on 2006-06-09
I meant open files :)

this thread should explain what I mean:
[http://ktorrent.pwsp.net/forum/viewtopic.php?t=309&highlight=1024](http://ktorrent.pwsp.net/forum/viewtopic.php?t=309&highlight=1024)

---

### Post by pelle.k on 2006-06-09
I see you are correct, but in any case ktorrent is the one to blame cause it doesn't open and close files when necessary as ktorrent 2.0 CVS does, but keeps accessed files open during the particular torrent file session (ktorrent 1.2)

---

### Post by NiksaVel on 2006-06-10
Okay, thanks for the info! I'll install 2.0 as soon as I get back to that comp...

Will let you know how it turns out...

---

### Post by hellfried on 2006-08-05
you may want to check out this thread. it resolved my 'dht firewalled' issue and  its all green on my azureus! something to do with the version of java that may be causing the problem.

[http://www.ubuntuforums.org/showthread.php?t=133340&highlight=azureus+dht+firewalled](http://www.ubuntuforums.org/showthread.php?t=133340&highlight=azureus+dht+firewalled)

i am running azureus 2.4.0.2 on dapper.

---

