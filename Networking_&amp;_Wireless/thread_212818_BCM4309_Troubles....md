---
title: "BCM4309 Troubles..."
date: 2006-07-10
forum: Networking &amp; Wireless
---

### Post by spidey867 on 2006-07-10
Hey, I recently switched over to Ubuntu from Windows, so I'm new to all of this. All my other hardware seems to function perfectly, but my wireless card just won't get going. I am not sure how to work the ndiswrapper app and the bcm43xx-fwcutter gave me trouble too. After trying that method, every time I would boot up the kernel, it would just lock up at "Loading hardware drivers..." and I'm forced to manually power it down. 

If anyone has had any luck with this wireless card, I'd really appreciate any insight.

---

### Post by neilp85 on 2006-07-29
I'm having the identical problem, has anyone had any luck with this card yet?

---

### Post by zytsef on 2006-08-23
Sorry to resurrect an old thread but I just encountered the very same problem on a Dell Latitude D600 with a TrueMobile 1400.  All attempts to use bcm43xx-fwcutter on the Dell driver fail (despite the fact that the driver is mentioned in the README as an option) and attempts to use the provided script result in a hard lock of the system when I try to load the driver.  Any help will be appreciated.

---

### Post by hangfire on 2006-10-17
I have the same problem, some howto's get me close, but none actually get me connected and a DHCP IP assigned. 

These card seems to be the orphan stepchild of the Broadcom line, a line that doesn't support Linux well in the first place (witness the use of ndiswrapper to game support).

---

### Post by kikos on 2006-10-17
The 4309 is hit-or-miss when it comes to dhcp.  I gave up on it since, too often, it would fail to get an ip address from dhcp or locked up my machine.  

I had a Intel ProWireless 2100 card lying around which I swapped with the 4309.  The ipw2100 works flawlessly.  Like the above person said, the fw-cutter & bcm43xx methods have issues when it comes to the 4309.

---

### Post by hugo8100 on 2006-10-19
This fellow seems to have gotten it to work with ndiswrapper.
[http://ubuntuforums.org/showthread.php?t=197706&highlight=TrueMobile+1400]("http://ubuntuforums.org/showthread.php?t=197706&highlight=TrueMobile+1400")

I've been trying to get it to work with ndiswrapper for three days without any luck, though.

---

### Post by bicchi on 2006-10-22
On Edgy RC i am having the same problem since it fails to assign an IP address to my laptop. I have tried both methods: ndiswrapper and bcm43xx-fwcutter with both giving me the same results. [This]("http://ubuntuforums.org/showpost.php?p=1643068&postcount=557") link shows my original problem.

---

