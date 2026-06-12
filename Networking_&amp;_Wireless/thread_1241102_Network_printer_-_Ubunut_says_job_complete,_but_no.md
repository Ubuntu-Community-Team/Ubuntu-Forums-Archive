---
title: "Network printer - Ubunut says job complete, but no printout"
date: 2009-08-15
forum: Networking &amp; Wireless
---

### Post by LinuxBob on 2009-08-15
I have set up my LaserJet 4L which is connected to my LAN using a Dlink DP 301+ printer server.  I have assigned an IP address to the Dp 301.  I ping it and it is there.  The printer will not print.

Using localhost:631 in the web browser I have added this printer.  I have used ipp and ldp and am using the HP device with following set up:

Description: HP LaserJet 4L
Location:  office
Printer Driver: HP LaserJet 4L - CUPS+Gutenprint v5.2.3
Printer State: idle, accepting jobs, published.
Device URI: socket://192.168.0.1xx 

Again, I installed using both ipp and lpd option.

I cannot print a test page.  Ubuntu reports that the print job completes but nothing happens at the printer, no data light blinks nothing, just a steady ready light.  I can ping the DP 301 IP addy fine.  

I have been posting this problem all week, googling and see a lot of hits but nothing has worked.  No one is helping me in this forum which is hugely disappointing.  I am sure, based on my google hits, others have encountered and solved this.

---

### Post by LinuxBob on 2009-08-15
Posting and this and getting no replies makes you wonder about th eutility of this forum

---

### Post by LinuxBob on 2009-08-15
We want Linux to be used more widely but no one responds to a question tht  people have surely dealt with successfully before.  

Look it was easy to add network printers with the initial 9.04 now the updates have changed the interface and these problems arise.  

Can anybody read this thread and offer suggestions???????!?

---

### Post by dbalascak on 2009-08-16
Do you see the printer being "servered" by the DP 301 print server.  

You added the printer to your Ubuntu machine with a WEB browser, correct?

With a browser look at [http://192.168.0.1xx:631](http://192.168.0.1xx:631) ( IP of DP 301).  It should display the printers available on that print server. It also displays the directory path to the printer.  Do you see the printer?

---

### Post by LinuxBob on 2009-08-18
The network printing problem is solved.  I bought a new all in one wireless capable printer and it worked first time with the Zareason using the localhost:631 network printer setup.  That led me to believe the Dlink printer server had a permission issue.  That was the case.

The DP-301P+ requires a mac address when the user permission feature is turned on.  The Dlink accepts a mac address with a space between the hexadecimal pair of numbers, not a colon.  

Thanks for all the helpful responses to my posts.

t is unfortunate CUPS had reported these test page print jobs as completin successfully.  That really sends you off looking in the wrong direction.

---

