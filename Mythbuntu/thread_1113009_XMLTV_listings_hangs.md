---
title: "XMLTV listings hangs"
date: 2009-04-01
forum: Mythbuntu
---

### Post by Billsputters on 2009-04-01
I'm installing from fresh Mythbuntu 8.10 64 bit

Partitioned and installed OK.

It then comes to the first screen after install 'Configure Guide Data/Backend'

I skip the first one as it's for schedules direct and North America and click on Myth Setup

Get the 6 option screen

1 General, I can go through and set up no problem

2 Capture cards - I'm using Hauppuage PVR150. Should I mark that as Analogue V4L or have it as a MJPEG card?

3 The real question. It searches for XMLTV grabbers and then goes to the listings  screen. I choose uk listings from Radio Times. It goes back to the 50% searching for XMLTV scan bar and sits there. From what I've managed to find a terminal window should open, but doesn't. ALT F8 brings up the window and asks various configure questions postcode etc. It then comes up with an error 

configure tv_grab_uk_rt --config-file /home/ubuntu/.mythtv/??tv.xmltv' --configure 
(I can't read the 2 ?? as it's too small on my TV!)

The error I get is 'halted with status 20C' (or something like that)

Should the /home/ubuntu be changed to /home/richard (my user name) and how do I get back to the main Mythtv install screen

---

### Post by Billsputters on 2009-04-01
Think I've figured it.

Not connected to the internet - on wireless connection and not defined!

---

