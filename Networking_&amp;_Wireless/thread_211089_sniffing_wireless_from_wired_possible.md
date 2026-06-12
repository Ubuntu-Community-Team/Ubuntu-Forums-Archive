---
title: "sniffing wireless from wired possible?"
date: 2006-07-07
forum: Networking &amp; Wireless
---

### Post by towsonu2003 on 2006-07-07
hi- I have a linksys wrt54gl router with wireless and wired capabilities. 

Here is what I am trying to do: My desktop (running linux) is connected via an ethernet cable to the router. It is running ethereal to capture packets from my (unsecured, open) wireless access point. To try if it's working like it should (?), I connected a laptop to the router's wireless. This laptop is a Windows XP machine. 

To see if I am capturing packets, I made it update XP as well as the virus definitions for McAffee. But ethereal only sees some weird communications like "who has 192.168.bla.bla? <mac address> have it."... 

I was expecting to see via the wired PC's ethereal that that the laptop was connected to update servers and updating itself... Why can't I do it? 

Should ethereal be run from another laptop connected to the same wireless access point, instead of my ethernet-connected PC? 

PS. I tried both the promiscuous and non-promiscuous modes. 

PSS. The reason I am trying to do this: wireless access points are not very common in my country. I really don't think there are hackers around my neighborhood (no place to park, so no wardriving, just the neighbors to worry about)... I am trying to see whether people are trying to connect to this access point and do *bad* stuff... I am hoping to decide whether I should let the access point unsecured (if those who connect don't behave like as*h**es) or to secure it (if they do behave like as*h**es)... 

Any suggestions welcome. 
Thanks :)

---

### Post by tturrisi on 2006-07-07
The reason you cannot capture the wireless packets from a wired computer bis because prior to beginning a capture in Ethreal you have to select the adapter to use, and since the wired computer has no wireless adapter you cannot monitor wireless transmissions.  You would have to stick a wireless card in the desktop to do what you want.

The only packets you'll see with Ethereal in your setup are packets sent by other wired computers on your own network (most all protocols), traffic sent by the router itself, and wifi ARP (Address Resolution Protocol) traffic "who has ip address 192,168.1.100" etc.  But you won't capture any other wifi traffic other than ARP.

You could test putting the laptop into the DMZ, but I doubt any other result will be obtained.

To capture packets outside your network using Ethereal you must either put your desktop into the router DMZ or else connect directly to the modem without using a router.

Now, your test won't pan any useful results though because one can use linux & kismet to sniff your wifi network & you would never ever know you were being sniffed.  But, you can always look if your wifi has been accessed w/out your knowledge by viewing router control panel status > local network as well as the router logs.

---

### Post by towsonu2003 on 2006-07-07
> **tturrisi said:**
> 
To capture packets outside your network using Ethereal you must either put your desktop into the router DMZ or else connect directly to the modem without using a router.
 are there any security risks if I do that (dmz)? the modem doesn't any slots left (has only one). and the router says "you'll be fully exposed" and so on for dmz host...
> **tturrisi said:**
> 
Now, your test won't pan any useful results though because one can use linux & kismet to sniff your wifi network & you would never ever know you were being sniffed. That's fine, I'm not planning to use wifi for private stuff... though my girlfriend doesn't like that idea (of not being able to login to her email account)... > **tturrisi said:**
>   But, you can always look if your wifi has been accessed w/out your knowledge by viewing router control panel status > local network as well as the router logs.
unfortunately, the logs only show the most recent stuff and the status > local network > dhcp client table doesn't have a "history" feature so it shows only the current connections... I guess linksys could have put in some better logging features (logging to a remote machine, or at least uploading the log files to a local network machine from time to time for saving space etc). 

Thanks for the reply, was very helpful... I guess the best option (except for dmz) for now is to use a laptop (or a wireless adapter for desktop -that I don't have handy) to monitor the wifi network from time to time...

---

### Post by tturrisi on 2006-07-08
> are there any security risks if I do that (dmz)? the modem doesn't any slots left (has only one). and the router says "you'll be fully exposed" and so on for dmz host.
not w/ linux for a short period of time.  The risk is if running servers or remote access services.  With Windows, one is then exposed to many bugs like code red virus, etc.
> unfortunately, the logs only show the most recent stuff and the status > local network > dhcp client table doesn't have a "history" feature so it shows only the current connections... I guess linksys could have put in some better logging features (logging to a remote machine, or at least uploading the log files to a local network machine from time to time for saving space etc)
My Linksys router (BEFSR81) has an option to send the logs to a lan computer and then view w/ the Linksys free log viewer application ([Linksys LogViewer]("http://www.google.com/search?hl=en&q=download+Linksys+LogViewer&btnG=Google+Search")).  You can view the .log file in any txt editor though, or maybe Ethereal too.  Or you could always copy+paste the log data from the browser into a txt file and save.

---

