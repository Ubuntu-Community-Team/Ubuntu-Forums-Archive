---
title: "Destination Port Unreachable !!"
date: 2009-08-19
forum: Networking &amp; Wireless
---

### Post by chinmaya_n on 2009-08-19
Hi
 
I 've got a problem ! I could not see this page [http://chinmaya_n.hyperphp.com/](http://chinmaya_n.hyperphp.com/). I created that using Drupal ( actually learning Drupal ). Recently I changed my ISP (internet service provider) from then this page dont opens on my desktop. 
I tried "$ ping chinmaya_n.hyperphp.com" in the terminal. It gives an error stating: [COLOR="RoyalBlue"]From a.7.de.static.xlhost.com (206.222.7.10) icmp_seq=2 Destination Port Unreachable[/COLOR] 
I can see it in my friends system!!:( (having a different ISP)
I tried with all the browsers in my system but of no use.

[COLOR="Red"]edit:[/COLOR] I found that this site is opening on my friends system who is having the same ISP as I 've!! 
 Does the problem lies in my system.
Can anyone please help !

---

### Post by superprash2003 on 2009-08-19
are you able to ping other sites fine? are you hosting this site or on some other server?

---

### Post by chinmaya_n on 2009-08-19
Yes I'm able to ping other sites !

I hosted this on other server.

---

### Post by chinmaya_n on 2009-08-20
I observed that even in Win XP that site is opening, but the problem comes in ubuntu only !

Edit: I also observed that no subdomain of that is loading in my linux system ! but [http://hyperphp.com/](http://hyperphp.com/) is working fine.
      I mean [http://nchinmaya.hyperphp.com/](http://nchinmaya.hyperphp.com/) have the same problem!

```
[COLOR="Blue"]chinmaya@chinmaya-desktop:~$ ping chinmaya_n.hyperphp.com[/COLOR]
PING chinmaya_n.hyperphp.com (209.190.24.9) 56(84) bytes of data.
From a.7.de.static.xlhost.com (206.222.7.10) icmp_seq=1 Destination Port Unreachable
From a.7.de.static.xlhost.com (206.222.7.10) icmp_seq=2 Destination Port Unreachable
From a.7.de.static.xlhost.com (206.222.7.10) icmp_seq=3 Destination Port Unreachable
From a.7.de.static.xlhost.com (206.222.7.10) icmp_seq=4 Destination Port Unreachable
From a.7.de.static.xlhost.com (206.222.7.10) icmp_seq=5 Destination Port Unreachable
From a.7.de.static.xlhost.com (206.222.7.10) icmp_seq=6 Destination Port Unreachable
^Z
[1]+  Stopped                 ping chinmaya_n.hyperphp.com
[COLOR="Blue"]chinmaya@chinmaya-desktop:~$ ping google.com[/COLOR]
PING google.com (74.125.67.100) 56(84) bytes of data.
64 bytes from gw-in-f100.google.com (74.125.67.100): icmp_seq=1 ttl=43 time=254 ms
64 bytes from gw-in-f100.google.com (74.125.67.100): icmp_seq=2 ttl=43 time=255 ms
64 bytes from gw-in-f100.google.com (74.125.67.100): icmp_seq=3 ttl=43 time=255 ms
^Z
[4]+  Stopped                 ping google.com
chinmaya@chinmaya-desktop:~$ 



```

 Can anyone plz help me !! :(

---

### Post by dmizer on 2009-08-21
Edit /etc/hosts so it looks like this:
```
127.0.0.1	localhost
127.0.1.1	chinmaya-desktop chinmaya_n.hyperphp.com

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
```

---

### Post by chinmaya_n on 2009-08-22
It is like this:
```
127.0.0.1	localhost
127.0.1.1	chinmaya-desktop

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
```
If i place chinmaya_n.hyperphp.com in the second line, then it behaves as a local site and shows "It Works!"

But i could not reach to the original site!
Note: I tried to view this on a live cd on my system, It worked !! ( I mean the site loaded )

---

### Post by dmizer on 2009-08-22
Is chinmaya_n.hyperphp.com hosted on a computer inside your local network?

---

### Post by chinmaya_n on 2009-08-22
Not at all!

Actually [http://chinmaya_n.hyperphp.com/](http://chinmaya_n.hyperphp.com/) is not a local site! It is on a server, I'm a user (member) of the free hosting service from [http://hyperphp.com/](http://hyperphp.com/)

---

### Post by superprash2003 on 2009-08-24
i get the same output

prash@prash-laptop:~$ ping -c 5 chinmaya_n.hyperphp.com
PING chinmaya_n.hyperphp.com (209.190.24.9) 56(84) bytes of data.
From a.7.de.static.xlhost.com (206.222.7.10) icmp_seq=1 Destination Port Unreachable
From a.7.de.static.xlhost.com (206.222.7.10) icmp_seq=2 Destination Port Unreachable
From a.7.de.static.xlhost.com (206.222.7.10) icmp_seq=3 Destination Port Unreachable
From a.7.de.static.xlhost.com (206.222.7.10) icmp_seq=4 Destination Port Unreachable
From a.7.de.static.xlhost.com (206.222.7.10) icmp_seq=5 Destination Port Unreachable

--- chinmaya_n.hyperphp.com ping statistics ---
5 packets transmitted, 0 received, +5 errors, 100% packet loss, time 4000ms


but the site opens

---

### Post by aledujke on 2009-08-25
It looks like they blocked the port that is used for pinging... since we all get the same port unreachable error.

Maybe for some reason your ip is blocked? Try using proxy or check your firewall settings. mauybe it's you who are blocking the site.

[http://www.anonymousproxyserverlists.com/FreshAnonymousProxyLists/Free%20SSL%20Proxy%20List.html](http://www.anonymousproxyserverlists.com/FreshAnonymousProxyLists/Free%20SSL%20Proxy%20List.html)

or try googling for some list if this one is not good :(

Tell us if you can access it by proxy. Once you set up the proxy try opening the [www.google.com](www.google.com) to be sure if it's working. Then try visiting your site.

---

### Post by chinmaya_n on 2009-09-04
I got it working now!!

i dont know how, Its working now !
(I 've got problem with my internet and consulted my ISP, the problem resolved. After that i could access that site i mentioned!! I really dont know what happend)

I've n't tried the ideas of our folks due to my busy works! But definitely i'll in short time and i'll post it here, if there are any fruits!

---

