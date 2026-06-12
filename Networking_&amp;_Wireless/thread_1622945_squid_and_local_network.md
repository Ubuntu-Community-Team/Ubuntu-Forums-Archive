---
title: "squid and local network"
date: 2010-11-16
forum: Networking &amp; Wireless
---

### Post by karche on 2010-11-16
Please evreybody excuse my bad english so i'm new in linux 
recently i've installed the new version of ubuntu mavericks in a computer that i use to distribute internet in my local network
 . ,i've installed firestarter and squid for proxy , my problem is that i use that computer for routing , and  I would like to force all computers of the local network  to connect to Internet via squid . i've tried these two commands
 
iptables -t nat -A PREROUTING -i eth1 -p tcp --dport 80 -j DNAT --to 192.168.1.1:3128
iptables -t nat -A PREROUTING -i eth0 -p tcp --dport 80 -j REDIRECT --to-port 3128

with no succee  please can anybody help me ?

---

### Post by linux-hack on 2010-11-16
First of all you need to enable the forwarding on the system.
You can do that with this command :

```
echo 1 > /proc/sys/net/ipv4/ip_forward
```
more info on iptable : [http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch14_:_Linux_Firewalls_Using_iptables](http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch14_:_Linux_Firewalls_Using_iptables)

And to make routs with iptable take a look at this : [http://www.hackorama.com/network/portfwd.shtml](http://www.hackorama.com/network/portfwd.shtml)

---

### Post by karche on 2010-11-19
hi linux-link i've tried all of your guide but i've a same problem please can you help me with an example?  that's my configuration 

my local network is connected to linux server (who is used for routing) on interface eth1
linux server is connected to internet with interface eth0 (linux server has two network card)
squid 2.7 stable 9 is installed in linux server (and uses port 3128)
in my local network linux server has ip address : 192.168.10.1 (eth1)

so when i enter the two commands  :

 iptables -t nat -A PREROUTING -i eth1 -p tcp --dport 80 -j DNAT --to 192.168.10.1:3128
iptables -t nat -A PREROUTING -i eth0 -p tcp --dport 80 -j REDIRECT --to-port 3128

and  try to connect internet with one of the machines of the local network i've error :
   
 **ERROR**

 **The requested URL could not be retrieved**

 
    **Invalid Request** error was encountered while trying to process the request:
  [INDENT] GET / HTTP/1.1
Host: [www.lemonde.fr](www.lemonde.fr)
User-Agent: Mozilla/5.0 (Windows; U; Windows NT 5.1; fr; rv:1.9.2.12) Gecko/20101026 Firefox/3.6.12
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,*/*;q=0.8
Accept-Language: fr,fr-fr;q=0.8,en-us;q=0.5,en;q=0.3
Accept-Encoding: gzip,deflate
Accept-Charset: ISO-8859-1,utf-8;q=0.7,*;q=0.7
Keep-Alive: 115
Connection: keep-alive
Cookie: RMID=29cd43554ce18540; RMFD=011PJSEVO106Sh; xtvrn=$43260$; __utma=194882738.1553961808.1289848170.1289852258.1290178010.3; __utmz=194882738.1289848170.1.1.utmcsr=(direct)|utmccn=(direct)|utmcmd=(none); _chartbeat2=imfsxbbe2ucklww3; __adpurl_125179267215=2010-11-15|1289852731; oas_prehome=ok; orangehomes=6; __utmb=194882738.6.10.1290178010; __utmc=194882738
Cache-Control: max-age=0

 [/INDENT]  Some possible problems are:
 
[LIST]
[*]Missing or unknown request method.
[*]Missing URL.
[*]Missing HTTP Identifier (HTTP/1.0).
[*]Request is too large.
[*]Content-Length missing for POST or PUT requests.
[*]Illegal character in hostname; underscores are not allowed.
[*]HTTP/1.1 Expect: feature is being asked from an HTTP/1.0 software.
[/LIST]
  Your cache administrator is [EMAIL="webmaster%W"]webmaster[/EMAIL].
 
 
    Generated Fri, 19 Nov 2010 15:12:36 GMT by Anrs (squid/2.7.STABLE9)
   

 please help me with an example i 'm begginer in linux and please excuse my bad english.

---

### Post by SeijiSensei on 2010-11-19
> **karche said:**
> ```
iptables -t nat -A PREROUTING -i eth1 -p tcp --dport 80 -j DNAT --to 192.168.10.1:3128
iptables -t nat -A PREROUTING -i eth0 -p tcp --dport 80 -j REDIRECT --to-port 3128
```

Delete the first of these and remove "-i eth0" from the second.  Does that work?

---

### Post by karche on 2010-12-01
[SIZE=4]excuse  me for the late, I had serious connection problems, I did what you  asked but i have  have the same error screen when trying to connect  from a machine on the  Local network. can you have another solution ? please help me.
[/SIZE]

---

