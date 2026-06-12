---
title: "how to debug dns slow"
date: 2009-12-26
forum: Networking &amp; Wireless
---

### Post by rswan on 2009-12-26
Hi All;

DNS has recently (some time in the last two months or so?) become very slow. Seems like the server refuses to respond for ~5-30 seconds. I tried watching packets in wireshark and everything seems to be working normally, but the DNS queries go out and no response comes back for a long time.

Both knoppix and windows get almost instant response to all DNS queries. Also ubunut used to be fine I think the problem started some time after upgrading to 9.10.

I have tried the following
 - disable ipv6
 - uninstall samba
 - put my isp's nameservers in /etc/resolv.conf, instead of my wireless router's ip
 - put only "host: files dns" in /etc/nsswitch.conf

None of these things help.

Any suggestions on how to figure out what's going wrong?

Thanks,
Robert

---

### Post by Brandon Williams on 2009-12-27
Do you have this problem with all applications? If not, which specific apps does it apply to? 

What happens if you just use 'dig <hostname>' to look up an address on the command line? Do you experience the same delay with dig? If so, then try 'dig -4 <hostname>'. Do you still see the delay?

When you use wireshark to trace the DNS queries, what type of query is going out that takes so long to resolve? Is it an A query or an AAAA query? Look at the details of the DNS exchange (I think wireshark will show it to you). When the response finally comes back, is it a response to the original query? Or did another, different query go out and elicit a response?

And finally, if you use wireshark on the knoppix box where query responses come quickly, does the interaction look distinctly different somehow than on the Ubuntu box?

Although I don't recommend switching permanently to public dns server's like opendns or google public dns (they can have a negative impact on the performance of some web sites by causing you to be directed to a bad server), such services can be useful for diagnosis. Try switching to either opendns (208.67.222.222 and 208.67.220.220) or google public dns (8.8.8.8 and 8.8.4.4). Do you get more snappy responses from either of them?

---

