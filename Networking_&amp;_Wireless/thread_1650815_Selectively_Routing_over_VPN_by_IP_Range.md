---
title: "Selectively Routing over VPN by IP Range"
date: 2010-12-22
forum: Networking &amp; Wireless
---

### Post by Another Monkey on 2010-12-22
At home I can VPN to my office network (using PPTP) and it works great right OOTB.  What I want to do is have all office traffic routed over that VPN, but all other traffic left alone.  I am fairly sure that this should be possible, please correct me if I am wrong!

If I open the VPN settings from "Network Manager", select "IP4 Settings" and click "Routes" I see a table and a couple of options.  I assume this is where I can configure the routing, but what do I fill in?
Address - do I have to specific the IP of every machine on the office network?  Or can I use some kind of range?
Netmask - I see "Genmask" in the result of running "route".  Is that the same thing?  There are multiple entries, which one do I choose?  And do I use value from Home or Office?
Gateway - My home router, the office router or something else?
Metric - Same question, I see multiple metrics in the "route" table, which one do I use?
"[] Ignore automatically obtained routes" - should I check or uncheck this? (I think I should check it)
"[] Use this connection only for resources on its network" - should I check or uncheck this? (I think I should check it)

I have already searched high and low and still but can't find this documented anywhere  (I have read the [VPNClient]("https://help.ubuntu.com/community/VPNClient") page).  I found a couple of forum posts, but they went over my head a bit.  I'd rather understand what I am doing than just plugging numbers in.

Thanks in advance.

---

### Post by Another Monkey on 2010-12-26
I now understand that this is called "split tunnelling", but I am still struggling to find documentation that explains what the various setting are for in order to set it up.
Can anyone point me in the right direction?
----
Eventually found the answer, described [here]("http://ubuntuforums.org/showthread.php?t=1702720")

---

### Post by Jefferythewind on 2013-02-19
I am trying to do exactly the same thing, and still have not found the answer.  My current VPN connection is using the TLS type, all configured through Network Manager.

---

