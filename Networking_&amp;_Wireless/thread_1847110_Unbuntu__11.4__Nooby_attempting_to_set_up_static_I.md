---
title: "Unbuntu  11.4  Nooby attempting to set up static IP"
date: 2011-09-20
forum: Networking &amp; Wireless
---

### Post by Spiralite on 2011-09-20
Basically I am trying to set up a Minecraft server for my friends to play on.  The problem appears to be that my room mate has an airport extreme router.  According to portforward.com this means I will need to set my computer to static so that the router can port forward the participants to my computer.  Since I am totally new to Ubuntu(linux in general) I have been trying to rely on my "Google Foo" to get me through this exercise in frustration.  However I finally joined the forum and found out there are really knowledgeable people on here so I felt like I should post a message and hope for some amazing person or persons to point out how easy it is.  
  I have run ifconfig, but it only gives me the ip, broadcast, and mask.  However on the gui under settings-> network connections-> auto eth0->Ipv4 settings when I go to change to manual it asks for the gateway too.  This I have not been able to elucidate and was hoping someone had a quick way to find this.
  Basically, I am at a loss.  Searches of the forum don't seem to help, and Ive gone through pages and pages of the forum and not found anything  related.  
The other option seems to be that I could go terminal style with sudo vi etc/network/interfaces... but the terminal is kinda scary at this point, and I dont want to have to do a tone of work reinstalling if I mess it up... 
Lastly maybe there is some awesome linux way just to connect to the airport and portforward the connection without all of this hassle.
Thank you in advance for any help steering me in the right direction.

---

### Post by agillator on 2011-09-20
As I understand it you are not connected to the outside world, you are connected to your roommate's router and the network it creates and IT is connected to the outside world. This also probably means the router is providing your ip address on its network. So you don't need to do anything on your computer, and probably shouldn't if you ever connect elsewhere. The solution is the router. You (or your roommate) need to log on to the router and go its dhcp server function. It should list current connections. Find your computer by ip address. Then there will probably be a check box or button to convert that to a static ip, or else it will allow you to do it manually. If doing it manually you will most likely need your MAC from that screen. Once you have told the router to give you a static ip, go to its port forwarding section and set up the port forwarding you need. If your static address will be different than your current ip address, reboot YOUR machine. That should do it. If it doesn't, let us know because you are getting your ip from some other dhcp server and that is going to be a different (and unusual) problem.

---

### Post by Spiralite on 2011-09-22
I will give it a shot.  Sounds easy enough! Thanks a lot!

---

### Post by Spiralite on 2011-09-23
Yep... That just about wraps this case up.  Mission complete.... Thank You!!!!

---

