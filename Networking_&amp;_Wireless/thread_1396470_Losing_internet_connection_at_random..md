---
title: "Losing internet connection at random."
date: 2010-02-02
forum: Networking &amp; Wireless
---

### Post by momist on 2010-02-02
Hi there,

I am running Karmic AMD64 on a homebrew desktop PC, but I also previously had this trouble on 32 bit with different hardware and on Ubuntu 9.04 and 8.10.  The router is now an ADSL+ Thomson TG585n supplied by O2 and badged O2 Wireless box III.  The PC has a direct ethernet connection.  The router was replaced by O2 when the problem first appeared, as the Wireless box II was suspect.  However, I still have the problem and it is getting more frequent.

The symptoms are these:

I generally shut down the PC each night, and only fire it up again when needed, which is usually the following evening, but it remains on for most of the day at the weekend.  Very often when started, I find I have no connectivity to the internet, and cannot retrieve my emails.  Strangely though, the Skype connection is still present and works, although not every time.  My wife's laptop is connected over the wireless link - and that STILL WORKS!  Sometimes I can connect to the router interface, but sometimes I can't.  I've never lost the connection while the PC is running.

I have tried everything I can find in the router (when I can connect) and also in the System:preferences:Network Connections and also in System:Administration:Network Tools, but can't find anything that helps.  A re-boot of the PC doesn't help.  A re-boot of the router doesn't help.  A hard reset of the router on it's own doesn't help.  The only solution to restore the connection is a hard reset of the router (using the recessed reset switch in the back) followed by a re-boot of the PC.

Since the Skype service remains working, and the lights on the router remain normal and wireless service doesn't fail, I think this has to be a DNS server problem.  In the previous release, Jaunty, I changed the DNS service to OpenDNS within Ubuntu, overriding the router's settings.  That seemed to help a great deal, although there was still the occasional outage which might have been another cause.  I can't find anything in the GUI interface in Karmic that will let me do this, and I can't now remember how I did that in Jaunty. 

Can anyone please suggest some diagnostic approach that will let me see what is causing this, and deduce a possible fix?  Thanks.

---

### Post by rrinjapan on 2010-02-02
I'm having the same problem. I'm running Mint 8 main version on a Dell mini 10 though (it's a project with another professor). I also have tried everything. I get signals running other software, for example Frostwire still works as normal ... 

I was connecting fine for the first few days after I re-installed everything after trying out another distro for a few days, but now really nothing and I'm too busy to keep trying the same thing for an hour or so til it finally decides to connect for 5 or 10 minutes.

I was working backwards looking for conflicts (took out Cairo-dock ...) but next is skype and I used to run that and had no trouble so I don't think that is the problem. I'm really running out of ideas ...

Can anyone help? I'm getting desperate.

RR

---

### Post by rrinjapan on 2010-02-02
A funny thing just happened. My system crashed and re-started on it's own, (it does this now and then). It said "could not access PID file for nmb" at the top of the screen then restarted. It asked me to sign in, and since then the internet has been connected and fine .... like an hour now and that's rare .... 

I'm not sure what can be taken from this but I will do some investigating over the next few days to see if I find anything useful...

RR

---

### Post by rrinjapan on 2010-02-02
I'm not sure this makes sense but it might be something in my start up settings anyway. I just logged off and on again, this time I set it so that I have to log in at start up and it's still going. This is the longest I've been on in a few days uninterrupted. 

I don't know if it's going to work tomorrow ... or if it'll work for you .. or why it might work .... but it's got me smiling at the moment ...

RR

---

### Post by momist on 2010-02-02
Well rrinjapan, mine is set to always require a login already - in fact I have several different users on the system.  Today, for the first time I can recall, I have lost connection during the day while it was running, but I wasn't here to witness that.

I'll keep looking.  Can anyone else suggest what I should look at when it gets lost?

---

### Post by rrinjapan on 2010-02-02
Sorry about that false lead. I had a great few hours there for no clear reason. I came back this morning and it doesn't work again ... :(, this time even Frost wire isn't working so I've got no connection apparently ... it'll likely change again for a bit just before I get really frustrated ...

I heard a rumor that 9.1 doesn't support pppoe and you need to get some package to install but I haven't been able to find that link again ... will report back.

Sorry again for the bad information.

RR

---

### Post by rrinjapan on 2010-02-03
Hi again Momist,

Apparently my problem is solved. I've been through about 7 restarts and 1 connect without restarting the machine after starting up while out (I'm on a netbook). 

I made three changes yesterday so I'm not sure which helped but I think it is changing the default connection in Network Manager, what is the name of your wired connection? Mine was ifupdown(eth0). Here is the link for the thread that told me how to fix that. 

[http://ubuntuforums.org/showthread.php?t=1316705&highlight=line+pppoe](http://ubuntuforums.org/showthread.php?t=1316705&highlight=line+pppoe)

Let me know how that works (or doesn't).

RR

---

### Post by momist on 2010-02-03
> **rrinjapan said:**
> I made three changes yesterday so I'm not sure which helped but I think it is changing the default connection in Network Manager, what is the name of your wired connection? Mine was ifupdown(eth0). Here is the link for the thread that told me how to fix that. 

[http://ubuntuforums.org/showthread.php?t=1316705&highlight=line+pppoe](http://ubuntuforums.org/showthread.php?t=1316705&highlight=line+pppoe)

RR

OK RR, thanks for the pointer.  You have actually jogged my defective memory (personal, not PC) and I remember when I was running the 32 bit version I went round this loop and found a solution.
  [http://ubuntuforums.org/showthread.php?t=1311363](http://ubuntuforums.org/showthread.php?t=1311363)  
I don't have any evidence of ifupdown on my system, but the NetworkManager is the strange sort of square target looking thing in the panel. 

Right click that, select "Edit Connections" and mine is called Auto Ethernet.  Select "Edit" for this and then the IP4 Settings tab.  If this is set to Auto DHCP and an alternative (I use Open DNS) set of IP addresses entered for the DHCP Client ID, it seems to have stopped me losing the connections.  The box can support multiple IP addresses with comma separation.

For those who wish it, the Open DNS IP addresses are:
208.67.222.222, 208.67.220.220

This has worked for me so far, but only time will tell.

Phew, how could I have forgotten that?  I'm getting old.

---

### Post by rrinjapan on 2010-02-03
Hi Momist,

I hope that works for you. Sorry none of my answers were helpful really but I'm glad you're headed in the right direction. I think my problem may have actually been my BIOS settings which were set for some other work that I did last year and hadn't completely re-set.

In any case, whatever gets your problem solved ...

RR

---

