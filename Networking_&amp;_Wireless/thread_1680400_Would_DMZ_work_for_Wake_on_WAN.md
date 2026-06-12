---
title: "Would DMZ work for Wake on WAN?"
date: 2011-02-02
forum: Networking &amp; Wireless
---

### Post by adamluck on 2011-02-02
If I were to put my ubuntu 10.10 server on the DMZ in a Linksys WRT54G router, would I then be able to use a wake on wan utility to wake it up over the internet?  

So far, I'm able to wake it up even from shutdown over my LAN using a batch file with the wolcmd utility.  Additionally, last night I tried using the [http://www.depicus.com/wake-on-lan/woli.aspx](http://www.depicus.com/wake-on-lan/woli.aspx) utility to wake up my server over the internet and after I set the subnet mask to 255.255.255.255 it worked...  I'm wondering if setting the server to be in the DMZ of the router rather than just forwarding the port to the server would consistently work for the wake on wan (and lan) functions....

And by the way, I haven't messed with the dd-wrt utilities.  As of now I think I'd like to just keep using the router the way it is instead of potentially wrecking the hardware during the installation. :)

---

