---
title: "Dell M1530 Wireless on Intrepid fixed"
date: 2009-05-04
forum: Networking &amp; Wireless
---

### Post by Dr-Jim on 2009-05-04
***Brief version - I changed my router to channel 1 from channel 13, I guess channel 13 is outside the range of the wirelss settings used in the Ubuntu wireless software?***

Hi all, I had problems with getting my particular Wireless network to be detected at all on Intrepid.  At first I thought it was something to do with my Dell M1530 laptop and Intel wireless that seems to have many threads for not working.  However, I could see other networks from around my area but not mine.  The network is WPA secured.

Using I think it was iwconfig and various other commands found around this forum/Google, I found the correct driver was being used and I knew it was working as I could connect to an unsecured network in my area.  

After some time I checked what channel my router was using and it was channel 13.  Manually setting the channel to use for wlan0  (or whatever your wireless is called) using 
*[FONT=monospace]sudo [/FONT]iwconfig* *wlan0* *channel* *13 *gave an error.  A quick google only seemed to show channels going up to 11.  So I changed the router to use channel 1 and hey presto it worked, I just followed the on screen instructions from the network manager.

I guess there is a limit on the number of frequencies in iwconfig or some other part of the network stuff that I don't know about?

Hope this helps someone out there I was tearing my hair out as Vista keeps needing restarting to get my wireless back so Ubuntu was my only hope :)

---

