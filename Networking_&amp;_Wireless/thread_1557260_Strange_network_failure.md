---
title: "Strange network failure"
date: 2010-08-20
forum: Networking &amp; Wireless
---

### Post by budgie9 on 2010-08-20
I have just changed from one ISP to another. All the internet connections worked fine on the day of the change over.
The following morning after shutting down the computer for the night, there was no connection to the Internet, by any program that would normally make a connection. The network manager settings were set to DHCP and were exactly the same as the previous day. Having tried numerous times, changing the settings, nothing would allow the browsers to access the Internet. 
I had removed the router from in-line so that was not the cause. The ISP tech's could find no problem with the service and neither could I. Because my other computer was connecting, and I was able to ping the service and OpenDNS servers, from this troublesome computer. I even shut down the other computer and used it's settings, but nothing changed Ubuntu still failed to connect. 
It took nearly 7 hours before I could get the service up again, following all the tips and tricks I could find on here, and yet I still have no idea why the service came back, it just did. I was unable to access the Internet from the three browsers I have installed or using Skype 
Can anyone throw any light on this strange behaviour. 
The Ubuntu ver 10.4 
Browsers Firefox, Opera, Seamonkey.

---

### Post by Iowan on 2010-08-20
Do you happen to remember which "magic bullet" caused the network to start working again? IPv6 *can* cause problems (slow response, ...) MTU is another possibility. Did you have any problems getting an IP address - or was it just browsing that failed?

---

### Post by budgie9 on 2010-08-20
Hi Iowan
I have absolutely no idea why and or how it started again.
I had disabled IPV6. early in the day, believing this may be the cause but it was not. In fact since then I have re-enabled IPV6 and it does not stop the service. But to be safe, I have today stopped it again. 
The only thing I know I was doing prior to the service becoming active again was again clearing out the Network Manager settings. I did not expect it to start but it did.
Now I have the router back in-line and the Network manager has the settings for it. I will say again I was directly connected - without router - whilst testing.
MTU was not the cause as that had been changed a few times.
I could ping sites, and do other tests, all the time. But the browsers, Skype and torrent programs, in fact nothing that I could use to access the Internet would see the Internet.

---

