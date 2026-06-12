---
title: "C902 - Internet? O2 Contract"
date: 2009-02-18
forum: Networking &amp; Wireless
---

### Post by davestar7 on 2009-02-18
Hi All,

Have done extensive searches before signing up and posting this!

Have installed Ubuntu on my Thinkpad T41...downloaded yesterday - 8.10.

I use my phone to connect to the internet, on Windows XP I have the Sony Ericsson PC Suite 4.006.00. Obviously - this works fine! I plug my C902 in via USB, start up the Suite and hit the connect button - no setup required. Phone flashes up "connecting", and tada, I have an amazing 460 kps internet connection.

On to Ubuntu - completely fresh install, nothing added nothing taken away. I plug the phone in, select "phone mode", an image is mounted where I can see the usual folders on my phone but no files/photos/music.
It also pops up "network disconnected", so I take a closer a look - oh it has a list of Orange/O2/Vodafone - I'll select O2 obviously..
Phone pops up 'connecting'...................but NO DEUCE. :(
I've taken closer looks at editing settings, but I'm lost.

Anyone help? :)

---

### Post by davestar7 on 2009-02-18
I've gone and looked at XP's "Sony Ericsson PC Suite", and grabbed the following info:
Username - o2web
Password - Don't know ... that's a slight issue!
APN - mobile.o2.co.uk
And PDP type is set to IP
IP is dynamic, and DNS fixed 193.113.200.201

But Ubuntu wants alot more settings than that..?

---

### Post by davestar7 on 2009-02-18
bump :)

---

### Post by davestar7 on 2009-02-18
bttt :)

---

### Post by davestar7 on 2009-02-19
bump!

---

### Post by influencd on 2009-04-27
Hey,

I just thought I'd let you know that I have this working without having to mess about with any settings on ubuntu - you configure it all on your phone.

FYI I'm using Mint linux based on Ubuntu Hardy - there should be no difference.

Firstly make sure you have the correct WAP settings on your phone - these can be sent to your phone from the O2 website.
On you C902 select the following settings:

Settings > Connectivity > USB > USB Network > *Phone as modem*
Settings > Connectivity > USB > USB Data Accounts > *O2 Postpay GPRS*
Settings > Connectivity > Internet Settings > Allow local connection > *On*

When I plug my phone in to USB, I select phone mode and the internet symbol appears. On ubuntu the network manager automatically connects to the local connection. There's no connection config etc as the phone is taking care of this as per usual.

Ta-da!!

I'm going to do some investigation to make sure all this falls under my "Unlimited internet" bolt on and there's no extra charges - though I can't see how it would be any different.

Good luck :)

---

