---
title: "using get_iplayer in the USA"
date: 2012-01-07
forum: Multimedia Software
---

### Post by scampbell70 on 2012-01-07
I am using tor in the USA to watch bbc iplayer and other shows and I am trying to download the shows using get_player but I get ERROR: Failed to record every time. I am assuming it is because the terminal isnt using tor. How can I set this up? I was using a paid vpn service and windows for a long time and have windows software to do this. I cant afford a paid vpn anymore  and I am to get rid of windows as well. I am using Ubuntu 11.10

---

### Post by iml on 2012-01-08
Tor isn't a free VPN, nor is it UK-based. It won't help with iplayer.

---

### Post by scampbell70 on 2012-01-08
I know tor isnt a free vpn. I am able to watch bbc iplayer just fine with tor. I just cant get the get_iplayer program to work in terminal. It sees the show but throws an error when I try to download it. 

What I meant was when I was using windows I used a paid vpn service to watch bbc iplayer. I am trying to get away from the vpn service and replace it with tor. In windows I used a program to download them which I am trying to replace with get_iplayer.

---

### Post by iml on 2012-01-08
If you can connect to a UK exit node consistently, it will work. But it's a very inefficient use of the tor network, as your traffic is also going through a number of intermediaries. Anyway, you could try using the SOCKS proxy normally used by polipo and your browser, under system network settings. That might work.

---

### Post by carl4926 on 2012-01-09
I know users in the US who do this via proxy

You should probably take your question to the get_iplayer mailing list
```
get_iplayer@lists.infradead.org
```

---

### Post by shantiq on 2012-01-09
this guy [here]("http://bbs.scoobynet.com/showpost.php?p=8488441&postcount=30") said it works for him   [from topic [here]("http://bbs.scoobynet.com/computer-related-34/658352-how-to-get-bbc-iplayer-to-work-outside-uk.html") ]

---

### Post by nothingspecial on 2012-01-09
From the BBC's ToS

> 3.2.1	If you are outside the UK
You may not access, view and/or listen to certain parts of BBC Content (such as video or live television services) using BBC Online Services if you are outside the UK, although you may, in accordance with the Terms, access and view bbc.co.uk or other websites and listen to some (but not all) BBC radio content. The types of BBC Content that may be available outside the UK will usually depend on the BBC's agreements with the persons who own rights in such content.

From the Ubuntu Forums Code of Conduct

> We do not support circumventing TOS, EULA, etc here. Such threads will be closed

Closed

---

