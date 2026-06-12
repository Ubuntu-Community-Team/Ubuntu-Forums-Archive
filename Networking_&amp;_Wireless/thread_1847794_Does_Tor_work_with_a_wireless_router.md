---
title: "Does Tor work with a wireless router?"
date: 2011-09-21
forum: Networking &amp; Wireless
---

### Post by Aegimius on 2011-09-21
Does Tor work with a wireless router? I want to use Tor but I access the internet through a wireless router provided by my ISP. I realize Tor can help hide your IP address from people trying to spy by jumping between servers, but I also realize the wireless router has its own IP address. So does Tor also switch around the IP address of my router, or just my computer's IP address? Or is there an extra step to get Tor to work with my wireless router? 

I'm not completely new to Tor. I used it years ago but it would slow down my connection. Now my connection is much faster(fiber optic), so I will try it out again. Thanks.

---

### Post by Beacon11 on 2011-09-21
Your router gives your computer an IP address. Your ISP gives your router an IP address. If you were to normally visit a website, the website server would notice your router's IP address, not your computer's. While using Tor, instead of connecting from your router to the website, you connect from your router to an onion router, to another onion router, etc. etc. which then finally connects to the website. The website sees the IP address of the last onion router in the chain instead of your router's IP address, which is seen by the first onion router in the chain. Whether or not your router is wireless is a non-issue.

The speed of YOUR connection won't matter-- Tor will still be very slow. Why? Because it depends on the speed of the onion routers and THEIR connection as well. You have to wait for your traffic to go through all of these onion routers-- first your request, followed by the server's response. That's just the way it is.

While you may have used Tor in the past, it seems that you aren't quite certain how it works. You will learn a lot by reading this: [https://www.torproject.org/about/overview#whyweneedtor](https://www.torproject.org/about/overview#whyweneedtor) .

---

### Post by Dangertux on 2011-09-21
You might also consider the fact that you're using a wireless router if it is not secured properly it could be rather easy for someone to sniff that traffic pre/post Tor. Keep in mind that this person has to be within range of your WAP.

---

### Post by Aegimius on 2011-09-21
That was a good read. You're right, I don't understand it that well, but I did finally manage to get Tor to work. At [http://whatismyipaddress.com/](http://whatismyipaddress.com/) I keep getting different IP addresses along with it saying I'm in a foreign country(and occasionally different cities in my home country). And Google is often in a foreign language, besides [https://check.torproject.org/](https://check.torproject.org/) saying my browser is configured to use Tor. And my connection is slower. 

Now I will try to optimise it and customize it, it seems to be blocking me from certain sites and occasionally acting "funny", but so far so good.  I do wonder though, how trustworthy are these various proxy servers I am bouncing around on? Or am I bouncing so fast even they can't tell where I am? I used to just use proxy servers without Tor or an Onion Router years back(after using Tor and not liking how slow everything was and its confusing set up - and I was still using windows at the time) and I strongly believe that opened me up to a series of hacking attacks and viruses. Nothing was stolen, but the various malware that invaded my system nearly destroyed my hard-drive and forced me to get a new PC.  I learned the hard way that proxy servers you have no control over or are unfamiliar with can make you more vulnerable to malware, even if you are anonymous to certain sites. 

Tor seems a bit easier to use now(it seems waaay faster than I remember, but last time I used it I was still using dial-up). Thanks for the info.

---

### Post by Beacon11 on 2011-09-21
> **Aegimius said:**
> That was a good read. You're right, I don't understand it that well, but I did finally manage to get Tor to work.

Now you understand it better!

> **Aegimius said:**
> I do wonder though, how trustworthy are these various proxy servers I am bouncing around on? Or am I bouncing so fast even they can't tell where I am?

Hopefully, it won't matter. The key word here is "various." If computer A is contacting website W through onion router Os, the chain would look like this:

A -> O1 -> O2 -> ... -> On -> W

I don't pretend to be a Tor expert, but if I understand correctly, O1 doesn't know that you're the original client, so none of the Os NEED to be trusted since there are multiple Os in the chain. Obviously it makes for a better system though, and I would postulate that most of them are perfectly trustworthy. Make sure your defenses are up-to-date. If you're using HTTP traffic, it would be a simple matter for a Tor proxy to use a MITM attack.

> **Aegimius said:**
> And Google is often in a foreign language, besides [https://check.torproject.org/](https://check.torproject.org/) saying my browser is configured to use Tor

One last note of caution. Even though your web traffic may be passing through Tor, DNS lookups are probably done in the clear. If you want to be truly secure, they shouldn't be. Check the Tor docs for information about that.

---

### Post by Aegimius on 2011-09-22
> **Beacon11 said:**
> 
One last note of caution. Even though your web traffic may be passing through Tor, DNS lookups are probably done in the clear. If you want to be truly secure, they shouldn't be. Check the Tor docs for information about that.

I'll be sure to look into that. I'm looking into all the holes that I need to patch up. Lately I've been trying to figure out how to configure Pidgin to use Tor. There's already a lot of information on this forum and others for how to do this, and I believe I have configured it correctly by following the instructions [http://www.totse.info/bbs/showthread.php/14368-How-to-Use-Pidgin-With-TOR-Published]("http://www.totse.info/bbs/showthread.php/14368-How-to-Use-Pidgin-With-TOR-Published%28Pidgin") works with the new settingds at least, and my account loads a little more slowly) but there doesn't seem to be an easy way to confirm this the way I can with my browser. Any ideas?

I bet it involves some terminal commands...

---

