---
title: "unable to open some web sites"
date: 2009-01-14
forum: Networking &amp; Wireless
---

### Post by linuxrockz on 2009-01-14
Hi everyone :)

I have a strange problem.
I can't open a few websites (such as [www.rxlist.com](www.rxlist.com)) though I am able to ping them:confused:.
Whenever i try to open in firefox it remains in "Waiting for www.rxlist.com".
This happens with few other websites also.
I am also not able to open them using a different browser such galeon or epiphany even elinks:(.

I connect to internet through D-Link (GLB-502T) modem (router inbuilt) connected to my pc using the ethernet port.

I am using ubuntu 8.04 (hardyheron) kernel 2.6.24-21-generic

I have also tried resetting the modem.

Thanks.

---

### Post by Macchi on 2009-01-14
Hi,
The problem you are experiencing could be some type of DNS problem or eventually the effect of filtering at some level.

Check your DNS settings all the way:

Your connection to the internet could have automatic and/or manual settings for obtaining an IP adress and often two DNS servers. Then normally the default behaviour is that the router may either pass these DNS servers to your clients automaticaly through DHCP or that you also have to enter it manually. 
Goto Applications->Accessories->Terminal and give the command:
```
 cat /etc/resolv.conf

```
This should either show a couple of public IP addresses for the DNS servers or the address of your gateway (router, firewall) that sometimes work as a DNS cache for your local network.



There are several possible explanations for the same problem. Servers may change addresses or stop working etc and only a few adresses would remain in you cache.
Hope it works, I will have to run to have dinner.

---

### Post by puppywhacker on 2009-01-14
Hi,

For me the site is rather slow, it runs Microsoft-IIS/5.0 as a webserver and it is misbehaving. I wouldn't be surprised if you are connecting via an HTTP-Proxy (knowingly or unknowingly) that can not handle this.

1. It upgrades the HTTP version which it is not allowed to do
2. It rewrites all URL by prepending "www." which is not correct
   So we can't check [http://images.rxlist.com/Default.htm]("http://images.rxlist.com/Default.htm")

you could traceroute to see how far the site is away from you
```
traceroute 66.161.82.16
```

you could try this in a terminal to fake an http request, to see if you get any response.
```
telnet 66.161.82.16 80
GET / HTTP/1.0

``` (and hit enter twice)

There are a lot of other possible issues. So I'm afraid you have to trouble shoot quiet a bit.

Goodluck

---

### Post by linuxrockz on 2009-01-14
Hi!
I am posting the outputs of the commands

**cat /etc/resolv.conf**

[I]### BEGIN INFO
#
# Modified_by:  NetworkManager
# Process:      /usr/bin/NetworkManager
# Process_id:   4821
#
### END INFO


nameserver 192.168.1.1[/I]

[B]
traceroute 66.161.82.16[/B]

[I]traceroute to 66.161.82.16 (66.161.82.16), 30 hops max, 40 byte packets
 1  mygateway1.ar7 (192.168.1.1)  3.683 ms  3.907 ms  4.153 ms
 2  117.197.240.1 (117.197.240.1)  32.341 ms  36.078 ms *
 3  * * *
 4  202.54.185.170 (202.54.185.170)  118.363 ms * *
 5  59.163.16.130.static.vsnl.net.in (59.163.16.130)  365.626 ms * *
 6  if-11-0-7.mcore4.PDI-PaloAlto.as6453.net (207.45.213.153)  361.997 ms * *
 7  if-4-0.mcore4.LAA-LosAngeles.as6453.net (216.6.86.10)  396.702 ms  377.813 ms *
 8  * * *
 9  192.205.35.129 (192.205.35.129)  309.534 ms  311.976 ms  314.638 ms
10  cr1.la2ca.ip.att.net (12.122.128.34)  317.674 ms  319.359 ms *
11  * * *
12  * * *
13  core2-z-g1-1.irv.sbcidc.com (216.65.209.14)  300.397 ms  300.313 ms  299.822 ms
14  * * dst1-c-g4-1.irv.sbcidc.com (216.65.208.198 )  301.305 ms
15  66.161.82.16 (66.161.82.16)  301.037 ms  301.275 ms  302.050 ms[/I]

[B]
telnet 66.161.82.16 80
GET / HTTP/1.0[/B]

[I]Trying 66.161.82.16...
Connected to 66.161.82.16.
Escape character is '^]'.


HTTP/1.1 200 OK
Server: Microsoft-IIS/5.0
X-Powered-By: ASP.NET
Connection: keep-alive
Content-Location: [http://www.medicinenet.com/Default.htm](http://www.medicinenet.com/Default.htm)
Date: Wed, 14 Jan 2009 18:31:49 GMT
Content-Type: text/html
Accept-Ranges: bytes
Last-Modified: Mon, 22 Mar 2004 23:25:39 GMT
ETag: "d6fd79fc6410c41:a1d"
Content-Length: 78

<HTML>
<META HTTP-EQUIV=REFRESH CONTENT="0;URL=/script/main/hp.asp">
</HTML>Connection closed by foreign host.

[/I]

Well I don't understand them all But I did learn quite a lot new things :D.
Though I don't seem to be getting anywhere closer to solving my problem :(.

Thanks a lot for trying to help me and responding so quickly to my question.

---

### Post by puppywhacker on 2009-01-15
Hi

We are getting closer since we have troubleshooted a few things, so we are zooming in to the cause of the problem. I still don't know if you are using a proxy in your browsing, but Macchi seems to be right in suspecting the DNS lookup.

For DNS you are using 192.168.1.1 (your gateway, since it is an internal ip-address) You might consider using your providers DNS servers instead

/etc/resolv.conf
218.248.240.23
218.248.240.79

which are respectively ns1.bsnl.in and ns2.bsnl.in they may help you better.

We also learned you are 15 hops away from the webserver and you can connect to it in roughly 300ms, not fast, but not bad either. So your connection problem has nothing to do with not being abled to connect to the server

Last thing, the telnet ... 80 showed that you can actually retrieve the website, so we now know there is also nothing wrong with the retrieval of information

goodluck

---

### Post by linuxrockz on 2009-01-16
Hi !!!!!!!!!!
Thanks a lot to all of you for all the replies.
I was pulling my hair since the last 5 days. 
I had also changed the /etc/resolv.conf 's name server to 218.248.240.23 but it kept changing back to 192.168.1.1 every time i rebooted my pc.

Any way I have solved my problem (not exactly) using a proxy server (browsing via [http://anonymouse.org](http://anonymouse.org)) i.e. the web sites open normally.

Thanks a lot puppywhacker for asking me whether i am using a proxy server or not.

Then it hit my head why not try a proxy server.

:guitar:

Thanks every one again.
But my real problem still persists :confused::confused:


All hail linux :KS

---

