---
title: "openDNS web filtering wont work and firefox question"
date: 2011-06-09
forum: Networking &amp; Wireless
---

### Post by anton706 on 2011-06-09
Hello,I am trying to block unappropriated sites on my ubuntu 11.04 with openDNS I installed it and in addithion to the catagoriegs I checked I also added some sites to the always block list, everything according to the site should work.
But the problem is that nothing is blocked (also the sites in the always block list).
I cleared the browsers cache but it didn't help when i try to clear the local cache with the provided command in their site I think it says it ignored my network.


About firefox,I want to block images only on facebook automatically so I added 
facebook.com to the always block list in the images category and it should work
but it just won't block the images.
I should note that I use the same method on chrome and there it work like a charm.
Any ideas how to get that working on firefox?

---

### Post by anton706 on 2011-06-09
Bump,please its really important.

---

### Post by novinick on 2011-06-09
Hi.

You may need to disable ipv6 acces since it is not blocking over it
i've overheard

Also need to set it up to do "ip updating"
by using some programs.

Also need to set up DNS resolver to use those adreses
or put it in router.

---

### Post by anton706 on 2011-06-10
Can you tell me how to do it?what programs to use? etc.....

---

### Post by novinick on 2011-06-11
depending on your connection , if over eth0 , like broadband cable
[network-connections-ipv6-ignore.png](http://docs.redhat.com/docs/en-US/Red_Hat_Enterprise_Linux/6/html/Installation_Guide/images/netconfig/network-connections-ipv6-ignore.png)
may be put to ignore it. most likely is NOT the issue here with you.



it was here sugested to put into router
the glith is majority of routers do not support updating opendns only dyndns 
which one is completly different
[http://ubuntuforums.org/showthread.php?t=1760694&highlight=opendns](http://ubuntuforums.org/showthread.php?t=1760694&highlight=opendns)
you may however put that adreses in ANY router outthere,that works
208.67.222.222
208.67.220.220

for updating try **Inadyn**
```
sudo apt-get install inadyn
```

and combining information from two places here and here
[http://www.opendns.com/support/article/190](http://www.opendns.com/support/article/190)
[https://help.ubuntu.com/community/DynamicDNS#inadyn](https://help.ubuntu.com/community/DynamicDNS#inadyn)

---

### Post by anton706 on 2011-06-13
Is it possible that my provider doesn't use DNS but something else like L2TP?
Also my router is edimax 802.11g BR 6204 Wg and I can't there is no place in the DNS settings to put ip addressees  like provided in the OpenDNS site.

---

### Post by crispy_420 on 2011-06-13
There has to be DNS involved or else if you typed ubuntuforums.org could never be found and you would have to type an IP address. 

I just downloaded the manual and on page 34 it shows how.It looks like the setting is under WAN. See picture below.

Then you will also need a way for them to track your Dynamic IP. I believe they provide a client that can be installed for that.

[http://www.opendns.com/support/article/90](http://www.opendns.com/support/article/90)

---

### Post by anton706 on 2011-06-14
I tried once to type the IP provided by DNS there and it disconnected me from the internet.
Is that because I havn't had a dynamic IP updater?

---

### Post by crispy_420 on 2011-06-14
No. The dynamic IP updater only helps OpenDNS keep track of your IP so it can maintain those filters. Ideally that should not boot you from the internet.

That brings me to the whole booting you off the internet thing. What exactly do you mean? Your ISP took away your IP address or you just couldn't get to websites? Most likely you had a name resolution issue related to DNS would be my guess. Try it again and verify the IP addresses you plug in are correct. I think something may have not been done correctly, maybe a typo? Maybe try Google's public DNS servers as a test to verify if it an OpenDNS issue too.

OpenDNS uses: 208.67.222.222 and 208.67.220.220
Google uses: 8.8.8.8 and 8.8.4.4

After inserting lets ensure we start from a clean slate. Reboot the router and log back into it after to make sure your DNS settings are correct. Also make sure that the Ubuntu machine is using the correct DNS servers by running 'cat /etc/resolv.conf' in the terminal.

---

### Post by anton706 on 2011-06-23
thanks, I added the openDNS ip into my router but now I have another problem how to install the dynamic IP updater in linux?
When I download the dynamic IP updater for linux it gives me a perl script how do I use it?

---

### Post by anton706 on 2011-06-26
Also I have a router so do I even need IP updater for open DNS?
please answer.

---

