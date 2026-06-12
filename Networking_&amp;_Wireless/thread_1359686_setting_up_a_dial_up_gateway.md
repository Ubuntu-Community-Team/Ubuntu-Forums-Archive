---
title: "setting up a dial up gateway"
date: 2009-12-20
forum: Networking &amp; Wireless
---

### Post by Skippy_X on 2009-12-20
Hope I'm posting in the right forum.

My father lives way off in the country and has dial-up. He has a desktop and two laptops and would like to be able to connect to the web with any of them without having to deal with stringing telephone cable. Essentially he's looking for a dial-up router that he can connect to wirelessly.

I've been using linux for about nine years now - but only as a desktop user. I've delved into the CLI for such things as cp, mv, rm, ./configure, make && make install. Small potatoes really.

He asked me what he should do. I know that Linux can run a router, so I figured it shouldn't be too tough to configure an old pc to be a router. All I'd need to do is put in a dial-up modem & a wireless card, do an install, install some software and configure it and be done. I had all this stuff laying around.

So far I've installed debian stable - w/out a window manager in an effort to keep the old crap machine as fast as possible - and now I've no idea what to do.

Google hasn't been much help.

Anyone care to point me in the right direction?

---

### Post by Dark_Stang on 2009-12-20
You realize that to do what you're looking to do, that phone line will have to be tied up 24/7, right? Just making sure this is acceptable.

Also, how much is this going to cost? You may want to look into a mobile broadband card and an EVDO router instead, assuming a cell signal is readily available.

I'm not much more help than this with dialup as I have no experience with it. Just trying to point out an easier path if it's available.

---

### Post by Skippy_X on 2009-12-20
Really? 24 hours? I figured that upon receiving a request from one of the clients the gateway would dial-up and then the user could close the connection after finishing what tasks he wanted to accomplish.

A cellular card is out, I'm afraid. He lives so far out in the sticks that he has trouble getting a reliable cell signal.

---

### Post by Dark_Stang on 2009-12-20
> **Skippy_X said:**
> Really? 24 hours? I figured that upon receiving a request from one of the clients the gateway would dial-up and then the user could close the connection after finishing what tasks he wanted to accomplish.

Well, think about it. If he wants instant access it's going to have to run 24/7... Or you're going to have to find a way to read his mind and dial out about 1 minute before hand. If you can figure this out let me know and we'll make a lot of money together. If he's fine with waiting 30 seconds to a minute before a connection is established, and then having the page start to load, then the line won't have to be open 24/7.

---

### Post by memilanuk on 2009-12-20
Generally setups of this sort have a dial-on-demand feature.  When you go to connect to an external web site or to download your mail to a client program such as Thunderbird, the gateway caches the request, fires up the dialer, connects, and then tries to complete the requested transaction.  Depending on how slow the dialup connection goes up, you may have to send a bogus request to google.com to get it going, and then a minute or so later, send your real website/mail request once the dialup connection has had a bit to come up.  Correspondingly, these setups have variable timeouts that will drop the dialup link after some preset time with no traffic - say 10-15 minutes.  

FreeSCO was what I used, 'back in the day'.  It all ran from a single 1.44MB floppy disk on an old POS 486 computer with a 56k hardware modem (not one of the newer 'Win' modems with software components in the drivers).  I think the program is still around, but its definitely a bit long in the tooth (10+ years).

I'm not entirely sure what else exists out there now... I thought ClarkConnect handled dial-up, but I'm not seeing anything on their site.

I'll keep looking, but in the mean time here are some documents talking about what you'd need to set it up yourself:

[http://handsonhowto.com/dodip.html](http://handsonhowto.com/dodip.html)

[http://usertools.plus.net/tutorials/id/39](http://usertools.plus.net/tutorials/id/39)

[http://www.quaking.demon.co.uk/dialmon.html](http://www.quaking.demon.co.uk/dialmon.html)

As you can see... its not entirely trivial (especially back 9-12 years ago when that was the only way I got online at all).  You need diald or some equivalent (wvdial comes to mind for some reason) to handle the dialing.  PPP was always a royal PITA, partly because finding out the necessary information from the local ISP was like pulling teeth from a chicken.  Then you need a Linux firewall set up with iptables, set to do ip masquerading, and you probably also need something like dnsmasq to take care of local name resolution, dns caching (which will *really* help on a dial-up connection) and local dhcp for the network.

If you can find a small all-in-one distro that will work, it would be way less of a headache for you *and* your dad.

Monte

---

### Post by memilanuk on 2009-12-20
Here are a couple of options for you...

[http://www.smoothwall.org/](http://www.smoothwall.org/)

[http://www.wifi.com.ar/english/cdrouter/](http://www.wifi.com.ar/english/cdrouter/)

Smoothwall's been around for a good long while... it might be a good way to go.

If you prefer to stick with an Ubuntu solution, check the Community docs for a few good pages.

---

### Post by Skippy_X on 2009-12-20
> **Dark_Stang said:**
> Well, think about it. If he wants instant access it's going to have to run 24/7

He's a 70 year old guy that lives in the middle of a national forest and has a dial-up connection. His idea of "instant gratification" is "if I get it before I die, I'm a happy guy".

> **Dark_Stang said:**
>  Or you're going to have to find a way to read his mind and dial out about 1 minute before hand.

I'm thinking we don't need to have to read his mind. The way I envisioned the system was:

1. client (windows 7, Win Vista, Win XP desktop or laptop) sends packets to the dial-up server. 

2. Dial up server says "Ok - Hang on a second" dials the ISP, connects and sends the packets through.

3. At the end of the users browsing session, the user can manually tell the dial up server to close the connection to the ISP through some mechanism (which I'm not clear on), or can physically go to the dial-up server and kill the ppp connection. The second option is not the preferable option.

> **Dark_Stang said:**
> If he's fine with waiting 30 seconds to a minute before a connection is established, and then having the page start to load, then the line won't have to be open 24/7.

He's absolutely OK with that.

---

### Post by Skippy_X on 2009-12-20
> **memilanuk said:**
> Here are a couple of options for you...

[http://www.smoothwall.org/](http://www.smoothwall.org/)

[http://www.wifi.com.ar/english/cdrouter/](http://www.wifi.com.ar/english/cdrouter/)

Smoothwall's been around for a good long while... it might be a good way to go.

If you prefer to stick with an Ubuntu solution, check the Community docs for a few good pages.

Wow - this is going to take a bit more than I anticipated.

Thanks for the URLs!

---

