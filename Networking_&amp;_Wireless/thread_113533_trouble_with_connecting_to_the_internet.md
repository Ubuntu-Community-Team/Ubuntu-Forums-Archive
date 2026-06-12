---
title: "trouble with connecting to the internet"
date: 2006-01-06
forum: Networking &amp; Wireless
---

### Post by paulsj on 2006-01-06
I have a small home lan with a few pc running win98se or win2k ok on p to p no server basis. Talking to each other and the internet via a bt broadband connection ok. So I have installed a couple of versions of linux on a couple of the machines as well as mswindows one being ubutu and am trying to configure them. The ubuntu machine can run as a peer with the other win98 machines but I seem unable to configre it to connect to the internet under ubuntu although as its multi boot the machine connects ok running win98 or win 2k so the hardware must be ok i think but I just cant work out the settings for ubuntu. New user to linux. I am currently favouring ubuntu/gome over mandriva/kde as it seems much snapper on similiar low spec machines. A couple of other thing but I think will probable be easy to sort out once I can get on the internet with that machine.
thanks for any help its probable just finger trouble on my part.

---

### Post by heftigrat on 2006-01-06
What do you get from typing "ifconfig" in a terminal?

---

### Post by paulsj on 2006-01-06
This, but I barly know what I'm doing.


paul@mboot1:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0E:2E:59:71:06
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20e:2eff:fe59:7106/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:436 errors:0 dropped:0 overruns:0 frame:0
          TX packets:484 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:72779 (71.0 KiB)  TX bytes:44878 (43.8 KiB)
          Interrupt:5 Base address:0xe400

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:666688 errors:0 dropped:0 overruns:0 frame:0
          TX packets:666688 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:56988345 (54.3 MiB)  TX bytes:56988345 (54.3 MiB)

paul@mboot1:~$

---

### Post by heftigrat on 2006-01-06
Can you ping your gateway (probably 192.168.1.1 or possibly 192.168.1.254)?  Type "ping 192.168.1.X", where X is either 1 or 254.

If you can, also try to ping a remote host by IP address, such as any of the following...
www.iana.org has address 192.0.34.162
yahoo.com has address 66.94.234.13
yahoo.com has address 216.109.112.135
www.l.google.com has address 72.14.203.104
www.l.google.com has address 72.14.203.99

If you can ping any of those, this is probably a DNS resolution issue.  Let us know what you find from the above t/s-ing steps.

---

### Post by paulsj on 2006-01-06
Yes it appears to get a reply allthough I have to close the terminal window down to stop it running. Is there a better way ? It must be something silly I'm not doing ? Its all automatic in mswindows I just click dont dail a connection and it connects to the internet via the lan. I had to set up the adslmodem router first but since then it has all worked automaticaly with mswindows. The lan dns server is all built into the router I thought and normaly seems to know that I want an internet address by the http:// prefix I think.

---

### Post by darth_vector on 2006-01-06
to stop the pinging press Ctrl-c. what is it you can ping; the router or the outside things like yahoo and google?

---

### Post by paulsj on 2006-01-06
Thanks for the control c (:-)
More data

I can address my router with [http://xxx.xxx.x.x](http://xxx.xxx.x.x) , it automaticaly inserts the http:// if i just type the numbers into firefox and can most probably reconfigure my router if i need to but as it works ok with mswindows so I'm not keen on doing that at present.

If I type in [http://66.04.234.13](http://66.04.234.13) which I believe is yahoo.com firefox says its trying to connect to us.i1.yring.com and a "sorry the page you requested was not found" message comes back from some yahoo site. So some layer of ubuntu 5.10 is scrambling the addressing as my hardware and software work ok using mswindows. Any idea which bit or bits ? (:-)

---

### Post by darth_vector on 2006-01-06
[QUOTE=paulsj]If I type in [http://66.04.234.13](http://66.04.234.13) which I believe is yahoo.com firefox says its trying to connect to us.i1.yring.com and a "sorry the page you requested was not found" message comes back from some yahoo site. So some layer of ubuntu 5.10 is scrambling the addressing as my hardware and software work ok using mswindows. Any idea which bit or bits ? (:-)[/QUOTE]

i get nothing from that link either. try google: [http://66.102.7.104/](http://66.102.7.104/) and try pinging the yahoo and google IP's heftigrat suggested.

---

### Post by heftigrat on 2006-01-06
[QUOTE=paulsj]...in mswindows I just click dont dail a connection and it connects to the internet via the lan.[/QUOTE]

I'm not sure at this point.  If you're talkin about dialing a connection, you *may* need a specific username and password for your ISP.

Correct me if I'm wrong though, but it sounds like you can ping outside by IP.  If this is the case, I am convinced that this is a name resolution issue and that perhaps there is some kind of WINS or DHCP configuration that your MSWin machines recognize, but your Linux machines don't.  I would try checking what DNS servers your Linux machines are set to use and at least set them to what your ISP recommends.

I dunno, hopefully other ppl have different/better suggestions than I do at this point.  Hope you figure it out!  :D

---

### Post by paulsj on 2006-01-07
Transfering that text file from the ubuntu multiboot machine to this mandriva multiboot machine so I could post to this group with mswindows had trashed the mswindows instalation when I rebooted this morining and I have had to restore it from image files and replace the mandriva lilo mbr with the w98 mbr so I am not best pleased with linux this morning as it sems more like a virus (:-)

The   [http://66.04.234.13](http://66.04.234.13) was a typo in my post to this forum I had typed  [http://66.94.234.13](http://66.94.234.13) into firefox.

It seems to work ok with 3 group addresses but produces rubish with 4 group. I noticed that others are having problems with this version of the distro. I'm probably to old to dig out the source and recompile the buggy module(s) so I think I'll dump it and wait for somebody younger to fix it. Btw the hp 500c printer module is bugged in 5.10 as well and free mandriva 2006 has similair bugs. Somebody with deep info can probably go striaght to it with the conversion data I gave in one of my previos post but I have no ideas on the printer driver at the moment.

All my internet dns stuff is on my router none of my lan machines has any internet isp data to work with. Btw as far as I remember bt broadband has no isp info it like a dedicated cable not even a full password from my end as the know wich wire I'm talking out of (i hope) (:-)

Bye for now I will keep a watching brief while I trash grub and ubuntu of my other multiboot machine and work on multi boooting more versions of dos.

---

### Post by paulsj on 2006-01-07
[http://66.94.234.13](http://66.94.234.13) firefox/umuntu5.10 converts to us.i1.yring.com

Thank for the memory (:-) 
paulsj

---

### Post by heftigrat on 2006-01-07
um, what?

Yahoo is probably using web aliases, so typing the IP address won't get you anywhere.  When I mentioned trying to ping public IP's I literally meant to type "ping x.x.x.x" in a terminal.

And again, um, what?  I didn't understand most of what you were talking about.  I would stick with MS Win if I were you.  Good luck.

---

### Post by mips on 2006-01-07
BT ? What brand& model router do you have ?

---

### Post by paulsj on 2006-01-08
d-link dsl-g604t it all works fine with win95, win98se and win2k machines.
I have a broadband usb modem that I might try with ubuntu if I cant get the router up perhaps.

I have just about got this machine I'm posting with to a Ghosting state so I can try connecting to it and doing file tranfers from/to the ubuntu machine without having to reinstall everything if things go pear shaped again. As I said before ubuntu seems ? to connect with 3 group addresses (so it works with my lan and router set up) but mucks up 4 group ones (so it dont work on the internet) but the signal is getting out and in as I get error pages back.
I did notice that pm reported a chs and lba mismatch after the ubuntu install but I let it fix it after I could not see a problem so I may have to reintall ubunto if it still trashes machines it sends files to. Btw what sort of printers have you got out there I cant print this forums pages without missing the right hand side even with zero margins unless i go landscape. I will be back (:-) even after the brush off from the iron cross.

---

### Post by mips on 2006-01-08
Your problem should be easy to fix as you are not the first, upgrade the routers firmware to v2.

[http://ubuntuforums.org/showthread.php?t=78337](http://ubuntuforums.org/showthread.php?t=78337)
[http://ubuntuforums.org/showthread.php?t=86890](http://ubuntuforums.org/showthread.php?t=86890)
[http://ubuntuforums.org/showthread.php?t=78271](http://ubuntuforums.org/showthread.php?t=78271)

---

### Post by heftigrat on 2006-01-09
[QUOTE=paulsj]I will be back (:-) even after the brush off from the iron cross.[/QUOTE]

My apologies, I honestly wasn't trying to give you the brush off.  I really couldn't understand what you were saying, and that's not an insult.  **mips** obviously understood, so this is probably more a comment on my technical comprehension of the situation.  Anyway, I hope you got it working.  Best wishes.  ;)

EDIT:

OK, just re-read my previous post, and I sounded like an a55h013.  Many, many apologies, I was probably drunk (though that's no excuse).

---

### Post by 504harry on 2006-01-10
Hi guys, pse, may I ask _you that seem to know_?
/
When I boot Ubuntu5.10 I get a Gnome pop-up that says... Ubuntu is missing from  /etc/hosts.
Under Terminal, I find the word "Ubuntu" only in that file - others here, say it should be numbers and "Local host", plus  , "my computer name"  - 
However, I'm not sure how to insert these, nor if  "local host" is substituted by "blueyonder.co.uk" which is my ISP.
Somewhere I found a Ubuntu PC-name ref to "Blueboy" - but can't remember the process and that was in 5.04  - which worked without a hitch as far as Internet connection.
I believe the ethernet card is Netgear as I found it amongst a long list, again I can't recall the route I took, sorry.
The Modem, cable, ethernet card are all working as I send this, using another OS. There is no Wireless link to my Broadband Modem.

---

### Post by heftigrat on 2006-01-10
[QUOTE=504harry]Hi guys, pse, may I ask _you that seem to know_?
/
When I boot Ubuntu5.10 I get a Gnome pop-up that says... Ubuntu is missing from  /etc/hosts.[/QUOTE]

Do you have a line in "/etc/hosts" that looks like this?...

```
127.0.0.1	localhost.localdomain localhost ubuntu
```

The default Ubuntu install sets your machines hostname as ubuntu, that may be why the error specifically states that "ubuntu" is missing from "/etc/hosts".

Also, localhost is your machine, so you should definitely not set it as the host name of any device on your ISP's network, or any potential device on their network, as this will inevitably cause a name conflict unless you set something up with them explicitly where you can have a hostname "harrysmachine.blueyonder.co.uk".  Let me know if this made sense at all.

---

### Post by paulsj on 2006-01-11
Thanks it was me was posting a load of rubbish so I'm not surprised rereading what I posted that you did not understand it, as I was not very familiar with the insides of networks but am learning. (:-)

---

### Post by paulsj on 2006-01-11
I tried option 2 and my d link is on its way back to the factory for a full reset but they gave me another one and on this I tried option 1 which sorted out my internet connection with firefox any way. I am now up and running again with win98, win2k and ubuntu 5.10 all taking to each other and the internet hoorray and thanks as the failure of the dlink under fw update showed up a problem with my network switch which I think was screwing up my file tranfers. Still have not worked out how to get the printer working on ub 5.10 as it works fine with win98 and win2k ?

---

### Post by mips on 2006-01-12
Rather start a new thread for your printer in the hardware section after you have done a search there.

Put your printer brand&model in the subject line to catch the right kind of attention.

---

