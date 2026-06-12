---
title: "Many people seeing DNS issues, but not many solutions ..."
date: 2006-05-16
forum: Networking &amp; Wireless
---

### Post by Noir on 2006-05-16
Hi there, 

I am brand new (i.e. < a week) with Ubuntu and Linux in general, but I decided to sample a taste and installed Ubuntu 5.10 on an archaic but wiped Thinkpad, with no other OS on it.  The setup was really smooth and quick and the whole environment was set up in no time.  The Setup app even recognized my DWL-G630 wireless card and prompted me to set up the WEP info.

However, when I started to get connected to the internet I began to see many issues.  I'm going to skip over the challenges to find pppoeconf (but thanks to some forum members who pointed me there) and skip right to my current problem at hand, with which I have been stuck for the last few days.

So what I am seeing is that whenever my PPPOE connection fires up, the system detects the 2 DNS servers provided by the ADSL Broadband ISP (everything is running DHCP on my network), and my box gets internet connectivity, where Firefox, ping, ftp and all the tools work properly.  Open System->Administation->Networking and under the DNS tab you will see these DNS server IPs.  Great!

But don't get too comfy, just browse a bit more and after a couple of minutes, you would start seeing name resolution errors and Firefox will start reporting the domains not found.  Now if you open the System->Administration->Networking UI again and go to the DNS tab, you will see that the DNS server IPs have disappeared, and you will see something like 192.168.1.1 as your DNS server.  This is really unusual.

You can delete that DNS IP and re-enter the old DNS IP addresses from your ISP (make sure you click OK on the UI), reopen Firefox again, and your internet connection will work again.  Of course, the problem recurrs after a few minutes, as expected.

I've searched on the web and it appears that a lot of people are seeing this problem, but not a lot of people know what is really going on.  From my limited knowledge, it seems almost like there is a daemon running somewhere in the background that keeps resetting the DNS server to soemthing invalid (192.168.1.1, which happens to be the admin configuration IP for my Linksys router).  I've seen some threads speculate that something is replacing the resolve.conf file with this invalid address, but once again, I don't know Linux that well.  

I have a relevant [thread ]("http://www.ubuntuforums.org/showthread.php?t=175894")posted in the beginner forum but I am not getting too much traction there so I decided to move this conversation here.  It would be great if someone with more networking experience can shed some light over this...  :-)

Once again, thanks in advance!
- Noir / K.

---

### Post by cfroese on 2006-05-16
You'll probably find the answer [here]("http://www.ubuntuforums.org/showthread.php?t=87643").

Follow the instructions step-by-step! My guess: Disableing IPV6 will fix the problem.

---

### Post by Iowan on 2006-05-16
[http://ubuntuforums.org/showthread.php?t=172881]("http://ubuntuforums.org/showthread.php?t=172881")
Here's another possibility. Does it seem curious that a Linksys router is frequently mentioned in the discussion?

---

### Post by dmizer on 2006-05-16
my money is on ipv6 too.

here's an two line how to for disabling ipv6: [https://wiki.ubuntu.com/WebBrowsingSlowIPv6IPv4?highlight=%28disable%29%7C%28ipv6%29](https://wiki.ubuntu.com/WebBrowsingSlowIPv6IPv4?highlight=%28disable%29%7C%28ipv6%29)

---

### Post by Noir on 2006-05-17
Hi cfroese, Iowan and dmizer - thanks for your reply posts!

So I disabled IPv6 and rebooted (and verified that IPv6 is not loaded), I am still seeing the same behavior.  I was deflated and about to give up.

However, reading Iowan's thread, I am seeing the exact same thing as the person in that thread.  My DNS just gets stomped over every so often by the rogue 192.168.1.1 address.  I read in the reply thread that I can try specifying the DNS addresses of my ISP into the router DHCP configuration, and so I tried.  And voila - that did the trick!  I have now been browsing the net for about half an hour and the DNS is holding up strong.

So I think the combined result of turning off IPv6 and hard-coding the DNS server IP addresses in the router DHCP configuration really did the trick.  I hope I don't jinx myself here, but I am really glad that I came to a solution that does not require me to hard-code anything on my Ubuntu configuration.  After all, the intention for this laptop is to be able to roam about various wireless hotspots and still be able to be online.

I am so grateful to everyone who helped me get through this, as my Linux enthusiast buddy was already trying to convince me to download Fedora Core instead, but I am glad I stayed and believed in the power of the forums.  Kudos to you all.   :-)

Have a nice day!
- Noir / K.

---

