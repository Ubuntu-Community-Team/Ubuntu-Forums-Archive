---
title: "Extremely slow wireless internet"
date: 2009-11-29
forum: Networking &amp; Wireless
---

### Post by gooberguy on 2009-11-29
hello all, i am new to the linux world, and being a CIS major and computer enthusiast, i have installed ubuntu on my aspire 3050 laptop. everything seems to be going well (i didnt do anything, ubuntu install makes it that way :P) except for the fact that my internet (wireless) is really really slow! it works but something like google will take litterally 15-30 seconds to load! on wired, it is fine, and works as expected.

any ideas?

---

### Post by opt1k on 2009-11-29
This could be caused by a number of things.
The top 2 on my list are your ISP's dns servers are causing problems or your drivers for your wireless card are still in development and a little buggy
First try to change to the OpenDNS name servers.  This can be accomplished through network settings in the network manager applet.
# cat /etc/resolv.conf
nameserver 208.67.222.222
nameserver 208.67.220.220

Second try installing the ndiswrapper + windows drivers for your wireless card.

If its a b43 driver you are using or an old prism2 card with an ancient firmware you will almost definately have problems.


> **gooberguy said:**
> hello all, i am new to the linux world, and being a CIS major and computer enthusiast, i have installed ubuntu on my aspire 3050 laptop. everything seems to be going well (i didnt do anything, ubuntu install makes it that way :P) except for the fact that my internet (wireless) is really really slow! it works but something like google will take litterally 15-30 seconds to load! on wired, it is fine, and works as expected.



any ideas?

---

### Post by gooberguy on 2009-11-29
my car is an atheros 5001. i'm pretty sure its not my dns settings because other wireless devices run fine. i will try the wrapper once i find some drivers online

---

### Post by jward3010 on 2009-11-29
Phase out the not so obvious stuff of being close to the Access Point and not trying to go through walls. Can you do that or do you think that this is probably not a problem because other machines have no problem from the same location.

---

### Post by gooberguy on 2009-11-29
not to sound offensive, but i have tried all the obvious things, distance, bandwith, etc. it is definitely a problem with the software. (also i am litterally 2 feet away from the router :P)

i have installed madwifi drivers according to _[COLOR=Black][drpjkurian]("http://ubuntuforums.org/member.php?u=805294")'s[/COLOR]_ post, but wireless is still very slow. i had a hard time finding drivers (.inf) for my wireless card. im in a rut!

---

### Post by sgosnell on 2009-11-29
If you installed 9.10, you need to disable ipv6, and perhaps change to OpenDNS.  It's a known bug in 9.10, and there are a number of threads on here discussing it.

---

### Post by gooberguy on 2009-11-29
> **sgosnell said:**
> If you installed 9.10, you need to disable ipv6, and perhaps change to OpenDNS.  It's a known bug in 9.10, and there are a number of threads on here discussing it.

tried disabling ipv6 using ```
gksudo gedit  /etc/modprobe.d/aliases
```


but that only brings up the text editor with a blank file

---

### Post by sgosnell on 2009-11-29
Try [this fix](http://www.joehacker.com/index.php?title=Ubuntu_Tips#Disable_IPv6_on_Karmic_9.10).  I think that's what most people have done.  I initially changed to OpenDNS, then because of many other problems reinstalled 9.04.  I may upgrade when 10.04 comes out in April, but I'll wait to make sure it's ready.  Karmic wasn't, and still isn't, IMO.

---

### Post by jward3010 on 2009-11-29
> **gooberguy said:**
> not to sound offensive, but I have tried all the obvious things
You don't sound one bit offensive, I'll always mention them due to the experience I've had with wireless in general. It's a great technology but fraught with mystery and beguilement when it comes to getting it's signal to different areas. I've sorted the oddest wireless problems before by moving the AP from one shelf on a cabinet to the shelf above.

Obviously you're problem is different but you just didn't mention in your first post that you had already done those obvious things so glad you did.

---

### Post by teachop on 2009-11-29
This happens on my Acer 3100 on wireless intermittently, and on wired it works correctly with no problems.  I have tried all of the IPV6 and DNS issue fixes and they don't work.  Some other new Linux distros also have this problem on this machine.  I had to go back to Mint7, which is based on Ubuntu 9.04.

These I have tried and exhibit the issue:  Ubuntu 9.10, Fedora 12, Mint 8, Xubuntu 9.10.

These work fine on the same machine:  Ubuntu 9.04, Mint 7

Only on the wireless does the problem show up, and only on new Linux versions.  With so much attention on the IPV6/DNS bug, I fear this, which is different, gets lost in the sauce.

---

### Post by ath007 on 2009-11-30
Same situation here. Internet on Wireless on Ubuntu 9.10 running on an Acer Aspire 5930G is ultra slow... its actually taking 5-10 minutes to load the Google start page itself. 90% of the time it doesn't even load.

I never had this issue with my connection before. So I know its my side, or say, Ubuntu's side of the problem. I tried a small Fix here... which seemed to at least speed up the browsing in a small manner.

In Firefox
```
about:config
```

Search for IPV6 and disable it.

I played around with the 'Pipelining requests' command line but it doesn't seem to make that much of a difference. 

Have you guys tried using a different Browser? Like Opera or Chromium? I haven't, just a thought that just passed through me... lemme try it.. i will be back.

---

### Post by ath007 on 2009-11-30
Funny thing... 

I changed the these options in about:config of firefox.

Pipelining          > TRUE
Pipelining Requests > 10
Pipelining SSL      > TRUE
Pipelining Proxy    > TRUE

IPV6 Disabling      > TRUE

Just waited for sometime.. and now its fast.. browsing is fast.. did i miss something somewhere?? Can you guys clarify? :D :D :D

---

### Post by gooberguy on 2009-12-02
may be the cards they put in the aspires, I myself have an acer aspire 3050. I needed my laptop for a presentation for school, so for the time being I have switched back to windows 7.

---

