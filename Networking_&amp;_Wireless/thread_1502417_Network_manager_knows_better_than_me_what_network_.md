---
title: "Network manager knows better than me what network i should use - how to make it know"
date: 2010-06-05
forum: Networking &amp; Wireless
---

### Post by Istrebitel on 2010-06-05
Greetings.

I have recently tried to switch from windows to kubuntu. Kubuntu 10.04 has some "network manager" application that manages your network. Unfortunately, there seems to be no way to configure it! Sure, you can add plenty of connections and stuff, yes, but i will anyway do its own thing (i.e. use eth0 and connect with DHCP). I have DHCP turned on my home router to ease connection of pdas and my wife's laptops w/o need to manually assign something. I dont want to turn it (DHCP) off just because of network manager. I am used to having power over my computer in taking decisions, and i hear on linux it is so, but with network manager so far it is not the case...

So, 
1) Is there any way to make KDE Network Manager connect by default to what I tell it to connect to, not what IT thinks i should connect to? I want it to use specific address, not DHCP. Making a single entry and checking "Always connect" does not help. There is no option like "use by default" to be seen...
2) Is there probably a command-line alternative or program from the NM package?
3) Is there a way to learn where it's configuration files are stored?
4) If no, how do i remove it (it has so many packages with similar names...) and will changes i make with ifconfig persist through reboot?
5) Where are the linux's config files that ifconfig uses (cant find it in manpages or anywhere)?
6) Is there a good alternative gui networking setter you can recommend (all i actually ever want is a network manager that has "use by default" option!)

Thanks in advance!

---

### Post by Istrebitel on 2010-06-10
Gotta confirm it myself, problem is unsolvable. For an odd reason in Ubuntu you get to edit auto eth0 config but in kubuntu you dont. Therefore you're stuck with either totally text mode internet setup or totally no control over your networking. Duming kubuntu for ubuntu looks like the only solution...

---

