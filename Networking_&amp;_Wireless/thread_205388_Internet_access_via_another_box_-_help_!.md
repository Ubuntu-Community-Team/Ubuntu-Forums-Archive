---
title: "Internet access via another box - help !"
date: 2006-06-28
forum: Networking &amp; Wireless
---

### Post by jrleighton on 2006-06-28
I have this setup currently.

Ubuntu (Breezy) box <-- ethernet cable --> WinXP32 box <-- wireless --> router <-- internet

My Win PC is fine with internet access, but currently I am trying to get my Ubuntu box connected.  

I have two options: use my Linksys WUSB54Gv4 wi-fi adapter, or use my Win PC to relay internet traffic via an ethernet cable connection.

Using the wi-fi adapter seems to be a dead duck as this particular adapter doesn't work on Linux, from all the postings I can see (it's misleading, as v1, v2, v3 of the same product did work, leading me and no doubt countless others to buy a duff product ).

So I have to use the ethernet cable. 

On my Win PC I have enabled Internet Connection Sharing on my wireless adapter (using the Win network connections config ), allowing DNS, DCHP, HTTP - the selected adapter to relay through the wifi adapter (in the Win config dialog that pops up ) I selected as my local area ethernet adapter.

On my Ubuntu box, I just have DCHP enabled, with no DNS servers specified.

I have read mountains of posts in this forum and elsewhere that seem to describe the same or similar issues, but no-where can I see the way through - I've fiddled a lot with settings to no avail. 

Can anyone help me please ?  I recokon that it's on the Ubuntu side of things that I don't have configured correctly ( but I may be wrong ).  In particular, I don't understand what my IP address of my Win PC should be if I need to specify this in the Ubuntu config, and vice versa. I also don't get why Ubuntu needs to have DNS servers specificed separately ( is this necessary ) and if I need to specify, which servers do I use ? ( the IPs of my ISPs DNS servers ? )

Hope someone out there can point me in the right direction.

Thanks for any help on offer.

---

### Post by ffderrick on 2006-06-28
First we need to know a little bit more about your network setup.
What router are you using?
Why do you need to got through a windows pc?

Second,  your wireless device will need some extra attention to get it working.

Have you seen this thread?
[http://www.ubuntuforums.org/showthread.php?t=118929](http://www.ubuntuforums.org/showthread.php?t=118929)

I keep an eye on this thread a help if I can?

---

### Post by jrleighton on 2006-06-28
I'm using a non-branded router (well, it's a local Hong Kong brand which anyone elsewhere won't know - assuming most reading this won't be in Hong Kong ), but it's based on the Trend chipset.  

I'm trying to go thru the Windows pc because that's the one that's working with the internet connection.  In the end I want to move away from windows !  As I cannot hook up my ubuntu box to the internet at present, I can't install updated packages ( such as the new ubuntu version ).

Thanks for the help.   I'll give it a go to get my USB adapter going as well !

---

