---
title: "is their any howto guide for Internet connection sharing? plz help"
date: 2006-06-22
forum: Networking &amp; Wireless
---

### Post by vevak on 2006-06-22
I have recently installed Ubutu 6.06 on Inspiron 1300 and a complete newbie too on linux. I want help on howto to allow Internet sharing as I have a usb cable modem and want to share my internet connection through wireless or lan; this was perhaps the easiest task on windows but in Ubuntu I am lost because I don't have any background knowledge regarding Internet Sharing or Networking.

PLEASE HELP REGARDING THIS THROUGH LINKS OR GUIDES, WOULD LOVE TO CONTINUE WITH UBUNTU BUT THIS KIND OF STUFF LETS YOU DOWN.

---

### Post by zxee on 2006-06-23
I think you might start here: [http://www.ubuntuforums.org/showthread.php?t=24994&highlight=lan+networking](http://www.ubuntuforums.org/showthread.php?t=24994&highlight=lan+networking)
This how to is for an older version of ubuntu but it may work-be on notice however that dapper, as the latest release, seems to have some problems with wireless and networking.

---

### Post by mercenary on 2006-06-26
This as it turned out was much harder then I would have thought.  I can try to find some of the links that I used and post them.  Basically, you have to install and configure the DHCP software to do the routing and then you can install Firestarter to set up the sharing.  Firestarter is just a frontend to configure iptables which controls ports, but I don't know if it is essential to sharing but it is what I used.  There are some other secrets that you have to know about to get the 2 of these working together, I found them in one of the threads.  I know enough to know that without these tidbits, you will not get the 2 of these working together.  Finally, even with the secrets, it was harder than heck to get the thing working.  I was toggling settings back and forth and finally got it to work.  Once it was working, I was able to set things back to the way the directions said but when I added another pc, I had to change the configuration, do my toggle, do an ipconfig /renew on the new client and then set the settings back.  I'm not sure why it's so problematic, probably has something with Windows poor networking software.  

So if you are still paying attention to this thread, go figure out how to get dhcp loaded and firestarter.  You'll need to read about adding repositories because Firestarter is not included with Ubuntu.  If you search for any threads I posted, there may be some hints there.  Note that it took me several days to get this working.  In that time, I probably could have bought XP and been done with it in a few hours.  Also note that I didn't get much help from individuals other than the old stuff I found posted.  I don't know if this is because people think the task is trivial, if they don't know how to get it working, they aren't using it or if I just seem to have more problems than most people.

Note that once you get up and running, you may still not get everything you wanted.  I set this up for my brother and he wanted a firewall server running something similar to Norton on his old 98 machine.  I haven't been able to find similar software that does everything Norton did.

---

### Post by kingedwin on 2006-06-27
Could you be a little more specific as to these "secrets" you talk about?  I've been over every post I can find, and I still can't get it to work.  I don't care a bit about local network security since I'm in a remote area, I just WANT IT TO WORK.

I've tried DHCP + Firestarter, manually configuring the network, and using a DHCP replacement, with no success.

---

### Post by zhopudey on 2006-06-29
Hi,  I'm a supernoob when it comes to linux :P  I've just jumped onto the Ubuntu bandwagon, and was wondering about internet sharing as well. I have two PCs connected via a crossover cable, and want to share my adsl connection between them. One has XP, other has Ubuntu. 
Any help would be greatly appreciated.

---

### Post by mercenary on 2006-07-07
Sorry all, I was out of reach of the net for the last several days.  Here is a link to what I believe is critical info.  (It takes me a while to find it everytime I go looking for it, but now I've written it down/printed it out.)  It is older and probably was written with 5.10 installed, but it is still REQUIRED for 6.0x.

[http://ubuntuforums.org/showthread.php?t=74925](http://ubuntuforums.org/showthread.php?t=74925)

I want to reiterate that it took me hours to get this to work and some how I blundered across the correct combination.  There were a number of times when it looked like Firesarter had started, but it produced a generic error message that finally went away after many configuration attempts.  I can not tell you the exact steps, and I'm not of a mind to clean off the machine and start over.

Note that when you install Firestarter, if memory serves me correctly, it loads it's own init files for dhcp so you can ignore dhcp configuration steps you may have seen on other posts or the WIKI.

Step 1 was straight forward and correct.

Step 2 I had issues with.  I couldn't get the DHCP clients to obtain an IP from the DNCP server/firewall without setting the gateway to the same IP as the DHCP server (192.168.0.1).  Knowing ipconfig commands (on the windows side) comes in handy.  ipconfig /release, ipconfig /renew... check out the Windows help for ipconfig.  Note that once I got the DHCP client to see the server, I removed the gateway IP otherwise no one clients could get to the Internet.  Once a client has seen the server, you can do a release/renew and get an IP assigned again.  Go figure.  I don't know if this is a goofy MS networking issue or what.

Step 3: IS ABSOUTELY CRITICAL.  I verified that I had the current version of Firestarter so no fix has been included with their release.  I looked at the init script and found that without the symbolic link, Firestarter won't work.  I also tried to edit Firestarter's init script so that I wouldn't have to create the link and found that there were too many places that were dependent on the link.  They weren't all in the Firestarter's init file either.

Step 4: I can't remember if I found this necessary or not.  I do remember swapping out my 2 NICs, alternating between eth0, eth1 and initially, I had eth0 and eth2.  What I thought was the correct configuration wasn't working so I tried what I figured was incorrect.  I can't say at what step things started working.  I didn't find a way to confirm (via a command-line command) which NIC was set to 0/1.  That would have helped, there probably is a way.  I think on one of my attempts, I skipped this step and had to go back and set it.  I can check tonight to see if/how it's configured.

Step 5: When I started Firestarter, one of the check boxes (either Enhable DHCP or Enable Internet connection sharing) was grayed out and I had to go configure it in under the prefs.  (It was probably DHCP since someone else mentions that issue later in the thread.)  I also know there is something not quite right with the comment about the DNS server field, but I'll have to go check it out on my machine.  I remember playing with this setting, but I don't remember how it was left/worked last.  I remember not being happy with the comment "Simply look at your /etc/resolv.conf file if you need inspiration." in his instructions.

I wish I had been able to write the exact steps down.  I started to, but ended up trying things that weren't logical and finally bumbled across a working configuration.  Once everything was up and running, we added a 3rd XP box to the system and I had to once again go in and put in the IP for the gateway and then remove it.  On one of my other threads, someone posted that "Firestarter works just fine" and then pointed out some obvious things (that I wasn't having any issues with.)  It's clear to me that Firestarter doesn't work just fine unless you know about the symbolic link and probably some of the other configuration issues that aren't "pretty freaking simple" just because there is a wizard involved.

I always thought Microsoft's wizards were a bane to the system.  They hide what's going on and if something gets hosed or it doesn't work, there's no help or knowledge about doing a manual configuration.  Ubuntu/Firestarter seem to be headed in that same direction.


The only thing that feels better than not using Microsoft products is to help others not use them.

---

### Post by Sonofmoog on 2006-07-07
> **zhopudey said:**
> Hi,  I'm a supernoob when it comes to linux :P  I've just jumped onto the Ubuntu bandwagon, and was wondering about internet sharing as well. I have two PCs connected via a crossover cable, and want to share my adsl connection between them. One has XP, other has Ubuntu. 
Any help would be greatly appreciated.

zhopudey, I think I can help you.  On the XP box, do this:

Control Panel--->Network Connections
Properties, LAN or High Speed Internet
Scroll Down to TCP/IP, Select, Click Properties
On the general tab, you'll need to enter five IP addresses.  I'll give you examples from my system.  (Be sure the radio button Use the following IP address is enabled)

IP Address:  192.168.1.65
Subnet Mask:  255.255.255.0  

(Your subnet mask is almost always going to be this)


Default Gateway:  192.168.1.64  (In your case, IP of your Ubuntu box)

DNS Server:  68.94.156.1
Secondary DNS  68.94.157.1

Get the IP's of your DNS Servers from your ISP.

Plug the Ubuntu box into your DSL modem/router, and you should be good to go.  Click on Firefox in Ubuntu to see if you're connected; then on IE in XP.  If you don't get a connection on XP, reboot both machines and try again.

HTH

---

