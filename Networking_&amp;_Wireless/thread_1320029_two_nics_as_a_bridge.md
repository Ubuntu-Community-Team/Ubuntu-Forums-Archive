---
title: "two nics as a bridge"
date: 2009-11-08
forum: Networking &amp; Wireless
---

### Post by oospill on 2009-11-08
I just order another NIC for $5, so I can use my desktop as a bridge, and be able to watch incoming and outgoing data.  (for fun. dono why =).

desktop running ubuntu server, and laptop running ubuntu desktop.

currently, my cable modem goes into my wireless router, which has my server plugged into #1, and my laptop using wireless.

when I try to assemble this little project, will I plug the cable [as in modem] into the server, & server to the router?  if so, will I plug the server into the router's 'internet' port, like the cable modem is now, or will I plug it into one of the four LAN ports?

oh, and are there any cool tricks I should do once it's all setup?

thanks for the feedback.  keep linux alive!

---

### Post by peepingtom on 2009-11-08
You'll plug your Cable modem into an NIC, another NIC into the WAN (internet) port of your router.

Then plug ANOTHER NIC into the LAN port of your router. How else would your router route traffic to your computer?!

[http://www.linuxfoundation.org/en/Net:Bridge](http://www.linuxfoundation.org/en/Net:Bridge)

I assume you just want to use wireshark or something.
You'll use brctl somehow, and lose a bunch of user-friendly guis like NetworkManager. Good luck!

---

### Post by oospill on 2009-11-09
yeah, I found that same website (trying to about RTFM messages. =) yeah, I'll mess with a sniffer or two.  but I really whanna test out the firewall abilities.  

thankyou for the post!!

---

