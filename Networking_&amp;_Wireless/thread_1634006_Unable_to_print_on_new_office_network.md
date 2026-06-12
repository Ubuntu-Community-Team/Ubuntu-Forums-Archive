---
title: "Unable to print on new office network"
date: 2010-11-29
forum: Networking &amp; Wireless
---

### Post by travelour on 2010-11-29
I'm a beginner here so go easy on me.  ;)

I live in Japan and am trying to print to a network printer (Richo Ipsio C411 PS).  Couldn't find the ppd in the foomatic database.  At my previous school, I had no problems printing to the printers on the network once I found the ppd. A few months ago, I transfered to a new site.  Unfortunately, when I send a print job on the network here, the printer just gives a Japanese message that says "command error."    I've tried other printers on the network (all different models of the Ipsio).  

I went to the Japanese Ricoh website and it recommended a generic printer ppd.  I downloaded that, but it didn't work.  Then I got the ppd off of the windows driver CD and tried that.  Again, no success.   I have no idea what I'm doing (obvious, but should be noted) or how to get this started.  I also tried 2 versions of Ubuntu -- I'm running 8.04 and 10.04.

Attached are copies of the ppd files if it helps.  

Any help you can provide would be immensely appreciated.  The idea of being forced to return to Windows because of stupid printer issue is giving me nightmares.

---

### Post by uncaspi on 2010-11-29
You could address it with http in cups depending if it support it. Go into the cups GUI and take it from there.

---

### Post by travelour on 2010-12-01
I'm not sure if I followed you on that.  Do you mean to enter the network address (10.3.3.176) where it asks for a URL?  
I wrote Ricoh to see if they had a solution.  Their response was that the printer does not support Adobe PS3 - that I needed to buy an $800 card for it. I printed out the system settings list and it shows the printer emulation as RPCS.

---

### Post by walt.smith1960 on 2010-12-02
Possibly not the best  solution for you, but I have 2 networked Brother printers.  Brother seems to have reasonably good Linux support.

---

### Post by uncaspi on 2010-12-02
I meant the network address of the printer. If it's connected to a windows box and the windoze are connected to the network, you can use the windows drivers. Access it by http in cups. i.e. http:\\x.x.x.x\printer\epson

where x.x.x.x is the host address of the windoze connected to an epson printer.

---

### Post by travelour on 2010-12-02
Unfortunately, it isn't attached directly to a box.  But the idea has me wondering if I had a coworker's network address (and she was willing) if I could route the print jobs through her computer.  
Under the network address on the printer is an SDO address.  Is this something that could be useful?

---

### Post by uncaspi on 2010-12-02
You could try the network address of the printer, but then you must have the cups driver as I said.

---

### Post by uncaspi on 2010-12-02
You can probably access cups GUI with this file: Type it in the address bar of the browser.

[http://localhost:631](http://localhost:631)

---

### Post by travelour on 2010-12-10
Thanks for your suggestions.  Unfortunately, I'm still unable to get it to work.  I guess unless someone has written a linux driver for RPCS printers, I'm out of luck.

---

