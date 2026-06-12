---
title: "Firefox and evolution not connecting to internet"
date: 2010-07-02
forum: Networking &amp; Wireless
---

### Post by sndarvekar on 2010-07-02
I had installed Ubuntu 10.04 yesterday. When I see the network tab, it shows it is connected to the web via eth0. I could download all the packages for updates.
But when I try to connect to internet via Firefox, or by evolution or other software, I am unable to connect.
The configuration of the ethernet card is proper as I checked that via terminal window.
It is a peculiar problem, where I can download update pakages but unable to connect via browser or email client.
when I ping to ubuntu.com is shows it is healthy and successful
I have a Acer dual core laptop, and connect to internet via wired lan .
Rest everything is fine and running in impeccable condition
Please help

---

### Post by puppywhacker on 2010-07-02
the network layer between a succesful ping and a failing http connection is the DNS lookup (which seem to work for you) and PROXY settings.

The proxy in ubuntu can be set in the administration tab, but Firefox can set it's own proxy in [edit] [preferences] [advanced] [network] [configure how firefox connects to the internet]

to rule out a DNS problem try to browse to ubuntu.com based on the IP-address
[http://91.189.94.156/]("http://91.189.94.156/")

---

### Post by sndarvekar on 2010-07-03
Firefox network setting is set to system default, and in the system, it is set to no proxy.
Tried your suggestion but still not working.

---

### Post by bogo-mips on 2010-07-03
I've noticed that Firefox does not really listen to the global proxy settings... If you have connected via proxy previously, or do not want to connect to a proxy, I'd check both the global proxy setting and firefox's network settings - just to make sure.

Have you looked into IPv6 issues? I've read that there is a way to get FF to not make use of IPv6 or something like that?

Have you tried wget? any success?

Have you looked at the MTU setting on your eth0 / ppp0?

If you have ping working but unable to DL in FF - it could be that the MTU is set too high for your networking device.
*(Though you said your updates where working, so it might not be this)*

Good luck!

---

### Post by sndarvekar on 2010-07-05
> **bogo-mips said:**
> I've noticed that Firefox does not really listen to the global proxy settings... If you have connected via proxy previously, or do not want to connect to a proxy, I'd check both the global proxy setting and firefox's network settings - just to make sure.

Have you looked into IPv6 issues? I've read that there is a way to get FF to not make use of IPv6 or something like that?

Have you tried wget? any success?

Have you looked at the MTU setting on your eth0 / ppp0?

If you have ping working but unable to DL in FF - it could be that the MTU is set too high for your networking device.
*(Though you said your updates where working, so it might not be this)*

Good luck!

IPv6 issues has been looked into and it seems it is not a problem.
MTU was checked but there too no issue.
Dont really know what is going wrong?

---

### Post by Barry_IA on 2010-07-05
[QUOTE=sndarvekar;9537257]I had installed Ubuntu 10.04 yesterday. When I see the network tab, it shows it is connected to the web via eth0. I could download all the packages for updates.
But when I try to connect to internet via Firefox, or by evolution or other software, I am unable to connect.


Sndaryekar:

FWIW I have the same problem: Firefox and wget do not connect but apt-get, updates, Movies and Weather updates do.  Have subscribed to this thread hoping for a solution.

---

### Post by Barry_IA on 2010-07-05
> **sndarvekar said:**
> I had installed Ubuntu 10.04 yesterday. When I see the network tab, it shows it is connected to the web via eth0. I could download all the packages for updates.
But when I try to connect to internet via Firefox, or by evolution or other software, I am unable to connect.


Sndarvekar:

Me again! <g>   Found a potential solution (thanks to "t3ubu" is a post in another forum):


**Disabling IPv6 in Firefox:**

(1) Type "about:config" in Firefox's address bar.  (I think I hit the stop icon first to avoid waiting for the timeout.)
 
(2) Type "ipv6" in the filter.

(3) Change the value of "network.dns.disableIPv6" to true.  (I didn't see a popup menu so hit the <enter> key and it automatically switched.)

At this point I guess just close Firefox and reopen to test -- I didn't see a proper 'save and close' method.  Worked here.  No time to test what happens with wget (see my earlier "me too!" post) as need to get ready for work but appears the solution might have something to do with IPv6.

Hope this helps you!

(Now where's that BBS tagline about me no wanna go to work me wanna bang on keyboard?!)

---

### Post by sndarvekar on 2010-07-07
Thanks Barry_IA
Indeed your suggestion was absolutely right.
It has indeed started working.
How can we solve the problem in the entire ststem.
Firefox is connecting to the internet but evolution is not.
Can there be some centralized correction.
And profound thanks, and it is because of you people that this forum rocks.
Thanks again.

---

### Post by Barry_IA on 2010-07-07
> **sndarvekar said:**
> Indeed your suggestion was absolutely right.
It has indeed started working.
How can we solve the problem in the entire ststem.
Firefox is connecting to the internet but evolution is not.
Can there be some centralized correction.
And profound thanks, and it is because of you people that this forum rocks.
Thanks again.

Sndarvekar:

I have been looking around for a fix/solution -- thought I found one using a Blacklist but hasn't worked here.  The entry was supposed to disable IPv6 in the system so I switched the Firefox entry back to False (default) before rebooting -- oddly Firefox still connects but I still can't connect via the Terminal commands.  (Wanted to test the disabling of IPv6.)

FWIW I found two command lines which are supposed to show if IPv6 is enabled or not:

  (1)  ip a | grep inet6

  (2)  lsmod | grep ipv6

#2 is supposed to show if the module is loaded and #1 ...um,, checks something else I don't understand. <g>


We'll keep working on it! <g>

And yes, sooooo glad we have forums like this to help!

---

### Post by Hopalong on 2010-07-22
I'm taking this up elsewhere.

---

### Post by Easy Limits on 2010-07-22
Try disabling your firewall (GUFW).  Worked for me.

---

### Post by Barry_IA on 2010-07-23
> **Hopalong said:**
> I'm taking this up elsewhere.

Hi Hopalong!

Well, that's weird -  my e-mail shows this message from you: "I had this trouble, suddenly a few weeks ago, on here (Lucid on a desktop)  and on UNR on an Asus 1005P. there's a 'solution' on the Firefox forums, but it  didn't work with me. So -- I reinstalled Lucid from the disk, and all now works.  What's happened is that Mozilla have shot themselves in the foot: somewhere one  of their online updates is duff, and since we can't contact them about it,  they've no idea what's going on.
  Can someone tell me how I can find the  version number of Firefox I am using here? A date for the latest update would be  even better, but I don't suppose there's much chance of that' I can then start a  conversation with Mozilla about this."  Didn't see it in this thread.

I had re-installed Mythbuntu (10.04) several times to try to resolve the problem I was having with the HVR-2250 cards (see the thread I started ""HVR-2250 - not displayed") -- think I was deleting the old data by changing partition sizes. <shrug>

Anywa, to find the version number in Firefox, in Windows it's the Help tab, About; in Linux it's also Help tab, About.

---

### Post by linux18 on 2010-07-23
can you get anywhere with the command:

w3m [www.google.com](www.google.com)

---

### Post by sndarvekar on 2010-07-26
Are we getting anywhere.

---

### Post by Barry_IA on 2010-07-26
> **sndarvekar said:**
> Are we getting anywhere.

Hi Sndarvekar!

I am on my problem (put a 'solved' on it even) but appears we're not getting anywhere with your's.  Did modifying the about: connect option for Firefox help you to connect at all?  Won't do a darn thing for Evolution, unfortunately.

I don't know anything about Evolution (the Scope's Monkey Trial was before my time <g>) but if there is something in its configure for it to link to a specific IP address double-check that with what is on the Desktop's (right-click the icon at the upper right).

---

### Post by sndarvekar on 2010-07-27
Oh Sorry Barry_IA, Actually my problem is solved to with your suggestion.
Thanks a lot, and the previous mail was just a crazy mail just to check out if people are still awake.
Just a funny prank;)
Thanks and Sorry

---

### Post by Barry_IA on 2010-07-29
> **sndarvekar said:**
> Oh Sorry Barry_IA, Actually my problem is solved to with your suggestion.

Hi Sndarvekar!

Glad my suggestion worked for you!  Now remember to write it down/electronically file it someplace where you can find it again! :)


> **sndarvekar said:**
> Thanks a lot, and the previous mail was just a crazy mail just to check out if people are still awake.
Just a funny prank;)
Thanks and Sorry

Just for that we're soaping your windows!  ...Wait, we do Linux here -- nevermind! <ggg>:lolflag:

---

