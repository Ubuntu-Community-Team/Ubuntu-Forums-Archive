---
title: "Newby Networking Help"
date: 2009-11-25
forum: Networking &amp; Wireless
---

### Post by JoeFriday49 on 2009-11-25
Well I downloaded and am trying to use Ubuntu on a spare desktop here at home.  My only problem seems to be sporattic internet connection.  I have read all I could find quickly in the help files but I'm still stuck.
 
It seems to do updates and connect to the software upgrades, but Firefox refuses to go to anything with Google or Yahoo in the name.  It also won't go anywhere near Delphi forums, or even these forums, but does fine on my website and a very few others...  Someone said it sounded like that sort of problem may be a firewall, so I checked that and discovered I didn't have a firewall.  I've since downloaded the firewall and tried it both on and off with the same results.  Someone else commented that it might be a router/gateway problem, so after a few resets I tried plugging straight into the dsl modem.  Same problem without the router.  Connects but will never download anything...  I can boot into XP and everything works fine with the same hardware so I know it's not the eithernet card.  Even ping works in Ubuntu for some internet sites, but don't in others.  
 
When I go into network connection through the little icon on the top right of the screen and do an "edit connection" it reports that auto eth0 has never been used.  That just don't seem right to me.  All the ifconfig settings seem right with what others are reporting.
 
Open for suggestions before giving up...  I'm really trying to make this work, but being the new kid on the block i don't know where to look next...

---

### Post by pdc124 on 2009-11-25
your browser, or something else along the way , may be cacheing pages so forget about the browser for now 

simple stuff first 
has your linux box got an address from your router/server

sudo ifconfig -a 
lists all NICS
sudo ifconfig will list the active ones 
you are looking for 192.168.x.x. or somesuch.

Can you get to your router?
ping -c4 router IP adress ( usually 192.168.0.1, 192.168.1.1, 192.168.1.2)
depending on make 

can you get to the outside world ? 
ping -c4 [www.google.com](www.google.com)
if you cant , can you get to
ping -c4 66.102.9.99
if you can , but not to [www.google.com](www.google.com), its a DNS problem

---

### Post by JoeFriday49 on 2009-11-25
> **pdc124 said:**
> your browser, or something else along the way , may be cacheing pages so forget about the browser for now 
 
simple stuff first 
has your linux box got an address from your router/server
 
sudo ifconfig -a 
lists all NICS
sudo ifconfig will list the active ones 
you are looking for 192.168.x.x. or somesuch.
 
Sorry, have to toggle back and forth between two machines.
Reported IP is 192.168.1.101  Which seems correct.  I have the router set to use the range between 100 and 150 and this windows box that's connected to the same router reports 192.168.1.100  The Ubuntu machine will also log into and control the router and even on past the router the modem at 192.168.0.1...
 
Can you get to your router?
ping -c4 router IP adress ( usually 192.168.0.1, 192.168.1.1, 192.168.1.2)
depending on make 
 
Yes, see above...
 
can you get to the outside world ? 
ping -c4 [www.google.com]("http://www.google.com")
if you cant , can you get to
ping -c4 66.102.9.99
if you can , but not to [www.google.com]("http://www.google.com"), its a DNS problem
 
Lo and behold, for the first time I can see [www.google.com]("http://www.google.com")  but still can't log into my Igoogle account.  Can't get to yahoo, can't get to ubuntuforums.org can't get to delphi forums, but when I ping ubuntuforums.org it works fine rtt about 119ms.  I also pinged it from this windows box and got the same numbers.  For some reason it seems like simple websites load fine (like [http://weislake.com](http://weislake.com)) but complicated ones like [http://ebay.com](http://ebay.com) just sit there.

---

### Post by pdc124 on 2009-11-25
are you sure its a networking issue and not a browser?

Javascript working for all sites?
if you are using kde try konqueror as a browser.
Download  and install opera and see if its the same

---

### Post by JoeFriday49 on 2009-11-25
What I've done so far seems to work...  I blew away Grease Monkey and a script I had installed to add a WYSIWYG editor to Delphi forums...  I've reinstalled them both and it's still working fine now.  Don't you just hate fixes that break stuff...  LOL
 
Now I just need to find out if I can blow away the old windows stuff somehow without having to reinstall all this stuff...
 
Thanks!

---

### Post by JoeFriday49 on 2009-11-29
Ok, we can mark this one up as complete...  Seemed like everytime i rebooted the problem came back.  I logged into Go Firefox forum on delphi and posed the question and got this answer.  It has cured the problem completely...

[4346.2]("http://forums.delphiforums.com/gofirefox/messages?msg=4346.2") in reply to [4346.1]("http://forums.delphiforums.com/n/mb/message.asp?webtag=gofirefox&msg=4346.1#a1") 
Enter about:config in the URL box in firefox. You get a long list of settings. There's also a Filter box. Enter ipv6 there. You'll get a setting called network.dns.disableIPv6 - this is set to false. Double-click it to set it to true. Restart Firefox and the problem should be gone.

This is caused by providers still not supporting the ipv6 standard, which Firefox supports out of the box. 

Robin

---

