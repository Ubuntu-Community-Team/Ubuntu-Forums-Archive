---
title: "Postfix issue"
date: 2013-01-26
forum: Networking &amp; Wireless
---

### Post by Clauu on 2013-01-26
Hi there, i'm in a situation with a postfix mail server 2 web servers(nginx+apache) and 2ips, if postfix is running on both ips then all my sended mails from nginx and apache goes direclty to spam but if only the primary ip is specified to listen on then is ok for the nginx server that runs on the primary ip but for apache that is listening to the secondary ip mails goes to spam.. any ideas why?

UPDATE: Seems like if postfix is running on both ips then the apache server with the second ip is sending mails ok to inbox but nginx with the primary ip is sending them to spam.. :-s

---

### Post by Clauu on 2013-01-27
Any suggestions please? It's a little bit strange what is happening.

---

### Post by prodigy_ on 2013-01-27
What kind of mail your server is sending and to where? If you simply send diagnostics messages to yourself, you can whitelist your server in your e-mail client settings.

If you're sending something to the outside world though, you need to make sure your mail server has:
- at least one static public IP address (this should be the IP you bind Postfix to)
- a domain name (e.g. mail.example.com) resolvable over the Internet
- [a correct PTR record](http://en.wikipedia.org/wiki/Reverse_DNS_lookup) in DNS that matches your server's domain name and HELO
- (preferably) SPF record in DNS confirming that the e-mail server is designated by the domain it serves

There are probably other requirements I forgot to mention but the main idea is that you can't just setup a server and hope that your mail won't be filtered as spam. There are certain conventions you should follow.

---

### Post by Clauu on 2013-01-27
Well i'm sending world wide and not local, thanks for the reverse dns info now mails to gmail arrives in inbox but for yahoo still in spam.. i mean now with postfix running on the primary ip mails to gmail+yahoo sended from nginx wich runs on primary ip goes to inbox ok but if i send a mail from apache wich is running on secondary ip only yahoo is getting that as spam..gmail is ok, i'm missing something?

---

### Post by prodigy_ on 2013-01-28
It's hard to tell w/o looking at headers and even then it could be something in the message body that triggers filtering.

If you really need to run your own mail service, your best bet is to contact Yahoo support and hope for an intelligible reply. Otherwise you should check [Google Apps](http://www.google.com/enterprise/apps/business/). They offer cheap and reliable e-mail hosting.

---

### Post by Clauu on 2013-01-28
Well i just don't get it, if postfix is binded to same ip as nginx then the sended mail from php mail function goes to inbox but the mail sended from apache's php goes to spam and this is happening only with yahoo.. :neutral:

---

### Post by SeijiSensei on 2013-01-28
If you mean mail sent to Yahoo is tagged as spam, then your IP address, or more likely the block of addresses in which your server is running, is probably blacklisted.  If you're using a residential connection, that could be the reason right there.  If you have your server hosted in a co-location facility, or you're using a virtual machine like ones from [Linode]("http://www.linode.com/"), you should speak to your ISP.

You also need to expand the entire mail message that is tagged and see all the headers.  Often the reasons for the blocking will appear there.

---

### Post by Clauu on 2013-01-29
Header..
```

From mydomain.com Sat Jan 26 03:06:52 2013
X-Apparently-To: myemail@yahoo.com via 98.138.210.211; Sat, 26 Jan 2013 03:06:53 -0800
Return-Path: <www-data@mydomain.com>
X-YahooFilteredBulk: myip
Received-SPF: pass (domain of mydomain.com designates myip as permitted sender)
X-YMailISG: EQwSQJwWLDt0JfsuquRMKsp574SdIGKhxTXSPbS8KxR56Cc8
 qhm9AW_uMfxz_QBohK0qZqj_pDAIeD0aKXA8tnJOwEvW9LDccR5AnrkYp6Zq
 ruv5jc6OtPA_qRVxp67sbyrdCrRKlzAcX9KvKcQa03EaYfTu33IbGvFadcHH
 V4EaLQTIvODGF_IUnYAQ2tT2O3c0440VCt3gG02BnFboVr2hW2odaIIO9sja
 Fm95TqicU9jj_A2LKAF5hb6qq9hzVvkgppMY45XrszdHq8gsRJROKhqxzy1u
 AdP.OjdR67cjmYkuMouNhI77cGPgf9Xj_8NXjSuCeVyAs_vRSnbbcWhiTVnG
 POfxKW9vp56xRuBXH6eHD_r501pyMqcqimX6MC5YTkX3CzuxDmJewK0foum8
 L1ZwIlIulaKl.hWkxf7tmbiMg7ppiPGug8WKr5RWqEWzhiiBC4qZqHOahccU
 sNzk8d1SWvq0jkJjurszaylI7qx03HPkjWhAzTEkr43MFlTMp_2ewO0Fw2hd
 MCZ21DDgr4p7n2lK4E3F3gc3U79vf4DN2id6LrUnZBx2O_VYMo0ZjpgGUVGM
 u4nS6_MjHank2uAb2PHCD5V.NFpZ_jBWEPb9p5rg3dWN6PjIVLafaoy.XvuD
 yOgMz2.Sy7A3T1GU_B7WcpEoEeIC7pEjR_4qEI2JFZZktWVFY.cdfgK6Q0_C
 Unsn6QNvzXSIL8UQTosghY5gHimoNwV1vGgNPB8j0WftyGeztHhNdZ6zpHtr
 hv7RWir2ZYs2yCoQN.4ZJoWTvw1XQi6VdXx7hhaOE._MuCG2MLkLactwzq_P
 HfiJiPKbA7r_t0UttQf18YXSMcWIYHpazzEBsVfx1C9u75stRdnFxdQtH1jB
 AHGwar6JGJXzTvISqcRNkwV1cP2ylbx8yuQvGEi2rHdslKluJZWjqbtNHb_5
 5IRmUPORp8IIFyAC233uDDFG8yO.0F1ybwEVsHvdnfuXpoGij.tLuTS5ZS.M
 tXJ7qx._iOxGqo9RX3kmBaQKK3j0OX05IGIsew3UJKG79EYGensNXvwzi8bt
 J1I4ApK05OxsWIEK0T0DJPdQtmBvLheJIk5ADnobkIjhXVNk_o9nO_381LwO
 f58-
X-Originating-IP: [myip]
Authentication-Results: mta1112.mail.bf1.yahoo.com  from=; domainkeys=neutral (no sig);  from=mydomain.com; dkim=neutral (no sig)
Received: from 127.0.0.1  (EHLO mail.mydomain.com) (myip)
  by mta1112.mail.bf1.yahoo.com with SMTP; Sat, 26 Jan 2013 03:06:53 -0800
Received: by mail.mydomain.com (Postfix, from userid 33)
    id 795CF58502D; Sat, 26 Jan 2013 13:06:52 +0200 (EET)
To: myemail@yahoo.com
Subject: aaaaa
X-PHP-Originating-Script: 33:functions.php
From: mydomain.com <contact@mydomain.com>
Reply-To: contact@mydomain.com
MIME-Version: 1.0
Content-type: text/html; charset=iso-8859-2
Message-Id: <20130126110652.795CF58502D@mail.mydomain.com>
Date: Sat, 26 Jan 2013 13:06:52 +0200 (EET)
Content-Length: 332

```

---

### Post by SeijiSensei on 2013-01-29
```
X-YahooFilteredBulk: myip
```
Yahoo [believes]("http://www.zimbra.com/forums/administrators/39083-solved-outgoing-mails-yahoo-spam-folder.html") your IP address sends spam.  You can request that it be whitelisted by filling out a [form]("http://help.yahoo.com/l/us/yahoo/mail/postmaster/bulkv2.html"), but I'd talk to your ISP first unless you're on a residential connection.

---

### Post by Clauu on 2013-01-29
Well finally problem solved, seems like a yahoo address in the sender=spam, thanks guys for your time and interest in helping me out.

---

