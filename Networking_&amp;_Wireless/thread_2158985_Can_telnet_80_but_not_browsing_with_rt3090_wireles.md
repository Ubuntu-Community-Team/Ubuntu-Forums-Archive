---
title: "Can telnet 80 but not browsing with rt3090 wireless card."
date: 2013-07-01
forum: Networking &amp; Wireless
---

### Post by dongil on 2013-07-01
hello,


I am using Ubuntu 13.04 and Rlink3090 wireless card. Whenever I access to the router, connection is ok and browse any website. But after 3-4 minute later, I can't browse any site with Chrome and Firefox etc.

The command "telnet site address 80" gives me a normal connection and returns the expected result. Thus I think the problem is browsers and some applications. 

 I do not have any proxy neither firewall. I tested the router with the other note book,but it does not have such a  problem. The strange thing is that sometime browsing rejuvenates without any further action. I have no idea, how browsing comes back. With  rt2800pci and rt3090sta drivers I have the same problem. So, i do not think driver problem. And no power saving problem.

 Whenever browsing with the wireless router(netgear) is blocked, I check it with wired connection  and I can browse any site. 

Please help me to solve the wireless browsing issue. 

Thank you in advance.

---

### Post by sanderj on 2013-07-01
I have not idea, but can you run wget / lynx --dump / curl to see what they say about your web connection?

---

### Post by dongil on 2013-07-01
Thank you for your suggestion.

The output were taken when the chrome browser failed to get the data.
Here are the output:

 telnet [www.baidu.com](www.baidu.com) 80
Trying 119.75.217.56...
Connected to [www.a.shifen.com](www.a.shifen.com).
Escape character is '^]'.
GET /index.htm HTTP/1.0


HTTP/1.1 200 OK
Date: Tue, 02 Jul 2013 01:49:15 GMT
Server: BWS/1.0
Content-Length: 10427
Content-Type: text/html;charset=utf-8
Cache-Control: private
Set-Cookie: BDSVRTM=3; path=/
Set-Cookie: H_PS_PSSID=2754_2777_1429_2704_2725_1788_2250; path=/; domain=.baidu.com
Set-Cookie: BAIDUID=89702D1CA9DF74B564B9ECCE3D3C4A12:FG=1; expires=Tue, 02-Jul-43 01:49:15 GMT; path=/; domain=.baidu.com
Expires: Tue, 02 Jul 2013 01:49:15 GMT
P3P: CP=" OTI DSP COR IVA OUR IND COM "
Connection: Close

curl -i [www.baidu.com](www.baidu.com)
HTTP/1.1 200 OK
Date: Tue, 02 Jul 2013 01:47:06 GMT
Server: BWS/1.0
Content-Length: 10437
Content-Type: text/html;charset=utf-8
Cache-Control: private
Set-Cookie: BDSVRTM=4; path=/
Set-Cookie: H_PS_PSSID=1452_2703_1788_2250_2254; path=/; domain=.baidu.com
Set-Cookie: BAIDUID=8934CE5CFA2952821CAD402F9E7D66B8:FG=1; expires=Tue, 02-Jul-43 01:47:06 GMT; path=/; domain=.baidu.com
Expires: Tue, 02 Jul 2013 01:47:06 GMT
P3P: CP=" OTI DSP COR IVA OUR IND COM "
Connection: Keep-Alive

 wget [www.baidu.com](www.baidu.com)
--2013-07-02 09:45:46--  [http://www.baidu.com/](http://www.baidu.com/)
Resolving [www.baidu.com](www.baidu.com) ([www.baidu.com](www.baidu.com))... 119.75.218.77, 119.75.217.56
Connecting to [www.baidu.com](www.baidu.com) ([www.baidu.com)|119.75.218.77|:80](www.baidu.com)|119.75.218.77|:80)... connected.
HTTP request sent, awaiting response... 200 OK
Length: 10447 (10K) [text/html]
Saving to: ‘index.html.5’


 0% [                                       ] 0           --.-K/s   in 18s     


2013-07-02 09:46:05 (0.00 B/s) - Read error at byte 0/10447 (Connection reset by peer). Retrying.


--2013-07-02 09:46:06--  (try: 2)  [http://www.baidu.com/](http://www.baidu.com/)
Connecting to [www.baidu.com](www.baidu.com) ([www.baidu.com)|119.75.218.77|:80](www.baidu.com)|119.75.218.77|:80)... connected.
HTTP request sent, awaiting response... 200 OK
Length: 10447 (10K) [text/html]
Saving to: ‘index.html.5’


But  lynx --dump [www.baidu.com](www.baidu.com)

Nothing comes up.

However when the browse is ok, the output is:

[1]&#25628;&#32034;&#35774;&#32622;|[2]&#30331;&#24405;[3]&#27880;&#20876;


   [bdlogo.gif]


    .

  
   ©2013 Baidu [25]&#20351;&#29992;&#30334;&#24230;&#21069;&#24517;&#35835; &#20140;ICP&#35777;030173&#21495;  [gs.gif]


References


   1. [http://www.baidu.com/gaoji/preferences.html](http://www.baidu.com/gaoji/preferences.html)
   2. [https://passport.baidu.com/v2/?login&tpl=mn&u=http%3A%2F%2Fwww.baidu.com%2F](https://passport.baidu.com/v2/?login&tpl=mn&u=http%3A%2F%2Fwww.baidu.com%2F)
   3. [https://passport.baidu.com/v2/?reg&regType=1&tpl=mn&u=http%3A%2F%2Fwww.baidu.com%2F](https://passport.baidu.com/v2/?reg&regType=1&tpl=mn&u=http%3A%2F%2Fwww.baidu.com%2F)
   4. [http://news.baidu.com/](http://news.baidu.com/)
   5. [http://tieba.baidu.com/](http://tieba.baidu.com/)
   6. [http://zhidao.baidu.com/](http://zhidao.baidu.com/)
   7. [http://music.baidu.com/](http://music.baidu.com/)
   8. [http://image.baidu.com/](http://image.baidu.com/)
   9. [http://video.baidu.com/](http://video.baidu.com/)
  10. [http://map.baidu.com/](http://map.baidu.com/)
 
This is a Chinese site, you may have scramble characters if you do not install the language pack.

It seems to me wget, curl, and telnet responded with connection, but not for lynx. 

Any idea to continue testing. Or what is wrong on my system?

---

### Post by sanderj on 2013-07-02
baidu.com ... that makes me a bit suspicous: are you in mainland China? If so, you're behind the Great Firewall?

---

### Post by dongil on 2013-07-02
I finally found the real reason for the problem. Actually the problem resulted from the damn wireless card (Ralink 3090). It is so sensitive to receive signal from the router. It is only far away 10 m from the router. Every blocked browsing search has gone when I do the job near the router. Bingo! My restless painful job of the last three month has been ended today including installing the new driver(rt3090sta from rt2800pci) and replacing the router. Terrible the chip set Rt3090. 

Thank you for your comment. I wish my experience will help someone in future.

---

### Post by dongil on 2013-07-02
The problem has been solved.

---

