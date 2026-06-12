---
title: "Weird IP address when connecting to SSH"
date: 2010-02-05
forum: Networking &amp; Wireless
---

### Post by NertSkull on 2010-02-05
I don't know if this should be security or networking, sorry.

So I have often connected to my machine's remotely through ssh.  Today I noticed that when I connect, the "last login" IP seems a little weird to me.  I'm on my home network, so I connect directly with the IP of the computer within the router.

But after the IP I get this XXX.XX.X.XXX.dedicated.neoviatelecom.com.br

What is the neoviatelecom part?  Is that normal?  I don't remember ever seeing that there before.

If I connect a couple of times from my win7 laptop (through cygwin) I get the correct IP address, but followed with the other part.

If I connect with my other desktop (running Karmi 9.10) I get the same neoviatelecom thing as above.

Does anyone have any idea what this is?  And is is something I should be worried/concerned about?  I tried googling it, and I couldn't come up with much I understood.

---

### Post by Will Shackleton on 2010-02-05
I think that that is actually a web address, assigned by your ISP to your router. This is the web address that is seen publicly on the internet.

Some ISPs assign some form of domain name to each customer, which is what yours have done. This is perfectly normal, and appears instead of your local IP because that is hidden from the internet.
The domain name is just a very long one, made up of your IP address and dedicated.neoviatelecom.com.br

Nothing to worry about.

---

### Post by NertSkull on 2010-02-05
Interesting.  So even though my external IP is different, connecting within my home network, i.e. 192.168.0.12.dedicated.neoviatelecom.com.br, is normal?  I would think that if I'm connecting within my network, my external internet provider would have no bearing on that connection.  My laptop is through my wireless to my computer plugged into my router.

Interesting that somehow it still picks that up.

---

### Post by Will Shackleton on 2010-02-05
Hmm... I thought that you meant your public IP... I'd guess it's not much to worry about, though.
Just to make sure, you should change your password, in case someone has guessed it.

You could also try contacting your ISP.

Try going to [http://ipchicken.com](http://ipchicken.com) and paste the IP address into [http://www.hcidata.info/host2ip.cgi](http://www.hcidata.info/host2ip.cgi) and see what comes up then. (This find's your domain name).

Quite an interesting one, though.

---

### Post by NertSkull on 2010-02-05
So I won't lie this does seem somewhat concerning to me.  I did as you suggested and checked my public IP and it comes back as I would expect XXX.XXX.XXX.XXX.abcabc.abc.rr.com (I have cable to road runner).

But that is definitely not the .dedicated.neoviatelecom.com.br  address.

Looking that up all I can find is this [http://www.robtex.com/dns/dedicated.neoviatelecom.com.br.html#summary](http://www.robtex.com/dns/dedicated.neoviatelecom.com.br.html#summary)

which i'm not sure I have enough knowledge on to know what it means.  Other than I can't figure out how in the world logging in from my laptop, connected to my home wireless, to my home desktop 2 feet away can possibly be routing through a brazil server/ip address.

I did just change my password, I'm usually pretty good about that.  And even when I connect to my SSH I always do it through a non-standard port.  I've never had it open on port 22 to hopefully (in theory, but probably doesn't) add just a little bit more security.  I do have samba and NFS set up, but I don't see how they can be involved in this.  But I don't think I have any other services running I'm aware of that anyone could get in through.

I'm starting to read up on the how to know if someone is in your computer literature, but i've never done that before, so it may take me a while to figure out what's going on there.

Is this something to not be concerned about at all?  Or should I be investing some time to figure out what's going on?

---

### Post by Will Shackleton on 2010-02-06
Does it always show as this being the last logged on user's location?
You could try searching both computers for the string dedicated.neoviatelecom.com.br and see if it comes up in any configuration files. (It will be in log files, but try to look for conf files)

Neovia ([http://www.neovia.com.br/v1/home/index.php](http://www.neovia.com.br/v1/home/index.php)) are a Brazilian network company; they provide parts of the network infrastructure in Brazil (I think!)
They might be part of the UK Neovia ([http://www.neovia.com/](http://www.neovia.com/)).

Have you or either of your computers ever been to brazil?

---

### Post by noway2 on 2010-02-06
I think that this is definitely something to worry about, but I also think you should take a look in the security forum.  There are some real experts there when it comes to security.  Personally, I routinely log into my server remotely from different places and I make note of the last log in information.  I have NEVER seen it say something like that, I have always gotten something corresponding to where I am or have been, even if it is a hotel.  If you have a road runner account, I will take a guess that you are in the states and it is a safe bet that this will not reverse lookup to a domain in brazil.

Out of pure curiosity I also did a little checking on the domain reported, such as doing a whois, dig, and nslookup.  The results were strange.  Normally you get information regarding who runs the system, who to contact for abuse etc.  Try it on your own domain if your curious.  This group seems to be very secretive and blocks everything, which deepens my concern for you.

I suggest that at the very least you switch to using key based authentication for your SSH and turn passwords off.  There are many posts in the security and server forums that will tell you how.  You should also install an intrusion detection system and watch your system.  The sticky on by bodhi.zazen in the security forum is excellent.  Unfortunately if you have been cracked, you will probably want to completely reformat and re-install - and then harden your system.

---

### Post by NertSkull on 2010-02-06
Well great.  Glad I asked.  I haven't ever been to brazil, so I can't see that being an issue.  I already have keys set up for my SSH, but I haven't turned off passwords, I'll do that tonight. 

Time is super tight for me right now so a full re-install would be great, but no way I can get to it for a week or two.  I used firestarter to block everything (at least as well as I know how).  Can I assume that firestarter and iptables are enough to keep me ok for a week until I get to a re-install?  Or should I just keep the computer off as much as possible?

Also, if I re-install, and I am compromised, I assume that I am likely to have the same person try again?  Is the best way to prevent that just tight security measures?  Or is there any other way to change my identification to make a new install not even look like the same area.  I don't know if that made any sense.  I don't know if I even understand what I'm thinking.  Basically, besides re-installing and enhancing my security is there anything else I can do that may help prevent future problems?

Thanks everyone, I appreciate the help.  I'm sure I'll be back a lot when it comes time to re-install to make sure I have everything as secure as possible.

---

### Post by Will Shackleton on 2010-02-06
Just in case, you should virus scan all your windows PCs.
Also, what is the output of the 'route' command on the server and the Ubuntu computer? Is there any difference than 'route -n' (-n = don't look up domain names)?
Maybe change your SSH port to another non-standard one, and check 'dmesg | grep neovia' on both computers to see if anything is in the logs.

The IP address before the .dedicated.neoviatelecom.com.br, is that the IP address of the last computer you logged on from? And what about if the last one was logging in remotely, does this still have the neovia part?

Best of luck with finding this problem.:D

---

### Post by noway2 on 2010-02-07
Assuming that your system was compromised, there is the possibility that the person installed some form of back-door to allow them access, even if you turn off password protection.  Turning off passwords and using the RSA key would be a good firs step.

I don't know much about fire starter, but I assume that it is a firewall.  What you may want to do is set it up to block or drop all traffic from that network.  If fire starter can't do this, IP tables can.  The ubuntu wiki pages have good documentation on setting up IP tables black list locations.  You can set things up permanently, or you can simply add an IP tables command that will hold until a reboot.  The problem is that this is easily subverted by using a proxy.

If you only access the server from specific locations, you would be better off to block everything EXCEPT those location(s).  That should make things much more difficult for anyone to try to get access.

---

### Post by NertSkull on 2010-02-09
Ok, this may be long, but this is what I've done/figured out.

I tried the route command, and the route -n command and they are different.  My home IP address that I have from my router to all my computers is 201.23.0.X  This is what route gives me on my SERVER computer.

```
Kernel IP routing table
Destination     Gateway           Genmask             Flags Metric Ref    Use Iface
201.23.0.0      *                      255.255.255.0      U     0        0        0 eth0
link-local        *                      255.255.0.0           U     1000   0        0 eth0
default          201.23.0.1.dedi   0.0.0.0               UG    100     0        0 eth0

```(that didn't turn out to well, sorry)
If I do the route -n everything looks the same except the "default Gateway" where the ".dedi" is no longer there.  I'm assuming that .dedi is the same thing I've been referencing.

Next.

In a fit of concern, I decided I would re-install linux.  Which was actually ok, because I've been meaning to do that for a while now anyway to encrypt my entire filesystem.

So I re-installed from the alternate CD and have my entire file system encrypted with LUKS.  Then I installed firestart (yes its just a manager for IP tables). 

Then I re-installed openssh server.  I set up my port to be something random to test (I chose 6571).

I then tried connecting again from my Win7 Laptop, Ubuntu Laptop and other ubuntu desktop.  I log in once, then exit, then log-in a second time to see where the last login came from.  In ALL cases I get the .dedicated.xxxx crap again.

This is a fresh install, so I tried the route command again.  EXACT same as above.

Next...

I got my brother to login from cygwin (they only have XP) into my computer.  That looks pretty normal.  The second login he reads something from HIS IP address  XX.XX.XX.XX.his.internetprovider.com

So that looks normal.  So I'm back to square one.  Mine still looks like something coming from brazil on a fresh install.  I even hard reset my router and set up into WPA2 (I was using WEP, which yes I also knew for a while I should have changed).  

I've tried everything I can think of, still kind of concerned that somehow someone is on my connection.

So...

What do I do next?

What exactly do you call the part after the IP address.  I was thinking of calling Time Warner (my provider) and saying, hey, whats the deal with "this".  I don't know what to say though?  

Or should I not call, is this a problem on my end still?  True I have not re-installed ubuntu on my laptop yet (I'm doing that tonight, to see what happens there), but I'm kind of at a loss for what I could be doing wrong.

Any help/guidance would be greatly appreciated.  And again, sorry for the long post.  Let me know what I can clarify more.


p.s. this is a dual booted machine into XP - just in case that somehow could be messing with things

---

### Post by NertSkull on 2010-02-09
So if I plug my cable directly into my computer straight from the modem (not through my router) I don't get this problem.  Everything looks and appears to be normal if I by pass my router.

So this leads me to have to ask, is it possible my router is somehow the problem?  I have the linksys wrt54g.  Can it somehow be sending my data through some weird connection?  This is the only thing I can possibly come up with.

I'm at a loss.

---

### Post by amac777 on 2010-02-09
What IP address is your router assigning to your computer? Perhaps it's not using the standard 192.168.x.x, and what it is using reverse maps to that brazil domain?

---

### Post by NertSkull on 2010-02-09
Yeah it definitely is not using the normal 192.x.x.x I never have used that.  I seldom use default settings, don't know why.  But that has never given me a problem before.  I was using a 201.23.0.1.

So I was actually thinking about that.  And when I reset all my wireless router settings I had changed it back to the 201.23.0.1 address.  And I was still getting the weird 201.23.0.1.dedicated.neoviatelecom.com.br adress.

So I decided to change the IP my router was assigning to something totally new, never been used before in my home, 132.56.4.1

I rebooted everything and now everything looks normal.  When I run the route command, or log in from my other computers, everything comes back simply as 132.56.4.1

So I guess sucess? kind of?  I'm happy letting this be this way.  But I'm really hoping for insight from everyone on here who understands MUCH more than I do.

Am I okay moving on from this problem?  I didn't seem to do anything to solve it other than just choose an assigned router IP that was new.  I still kind of feel like its just as possible that soon this new IP will be hijacked to the neovia IP.

Any thoughts?  Do I need to worry about it coming back?  Or do I say as long as I keep my iptables configured, strong WPA, and keyfile access to my ssh only, will I be likely be ok?

---

### Post by jamesman on 2010-02-09
Google:  "whois lookup". Both of these are taken.  The new number is in from Alabama.  The 192.168.1.1 etc. have been set aside for routers and are not assigned elsewhere.

---

### Post by amac777 on 2010-02-09
> **NertSkull said:**
> I was using a 201.23.0.1....So I decided to change the IP my router was assigning to something totally new, never been used before in my home, 132.56.4.1

There are only a limited number of IP4 addresses and most are unique meaning that there can only be a single computer connected to the Internet using that address. You may have heard that IP4 addresses are running out - this is the reason. But there are several ranges of private network IP4 addresses that can be used for internal networks and will not be forwarded through gateways. One example is the range in 192.168.x.x. There are two other ranges, both explained in this wikipedia article:

[http://en.wikipedia.org/wiki/Private_network](http://en.wikipedia.org/wiki/Private_network)

You should use an IP address on your LAN that is within one of those private networks to avoid problems caused by using someone else's IP address.

---

### Post by NertSkull on 2010-02-10
Well that article was exceedingly helpful in teaching me more about how this all works.  I feel much better now about things.  I've set up my private IP to be something in the specified ranges like it should have been forever ago.  Everything looks great.

Also the old private IP I was using definitely routed to that weird address I was getting.

So I think all is well.  Thanks a million to all the helpful input from everyone.

---

### Post by noway2 on 2010-02-11
NertSkull, lets go get a virtual beer together!  I think after this one we could both use it.

I am glad that you received a reasonable explanation for this problem.  I must admit, it never occurred to me that you were using a public IP address range for your LAN and that the reverse lookup on this was decoding as logins from Brazil.  I guess it worked for you because the router recognized the addresses as being it's range and kept traffic for that range on your LAN, performing NAT when going outside.  

In any case, this is certainly better than the idea that your system had been violated.

---

### Post by NertSkull on 2010-02-11
Oh man its a much better result than what the alternative could have been.

In the end its probably a good thing though.  It forced me to getting around to encrypting my entire file system and backing up all my data.  And I learned a lot about security and privacy, which is always a good thing.

---

