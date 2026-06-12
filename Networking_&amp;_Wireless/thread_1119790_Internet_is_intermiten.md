---
title: "Internet is intermiten"
date: 2009-04-08
forum: Networking &amp; Wireless
---

### Post by rdumas on 2009-04-08
The problem I am having is when I use FireFox.  The network is up and running, it shows a signal of over 80%.  I know I an connected because my mail works.  What happens is I open firefox and most times it works, after going to two or three different pages the next one I go to firefox says "cant find page".  I try going back to my home page, same thing "cant find page".  I close firefox and reopen three or four times and then its back.  I almost seems as if you don't keep firefox active, like if you stay on one page to long it times out.
Has anyone experienced the same thing?
Does anyone have any ideas?
I think the problem is with FireFox, I called my IP and they went through the setup with me and they didn't see any problems.  Ubuntu shows that I am connected to the router.  I just don't get it.  But it is a real drag when you are trying to download updates, sometimes it takes three or four try's

---

### Post by acimmarusti on 2009-04-08
open up a terminal and type this:

```

lspci -v | grep Network

```

And show me the output

---

### Post by superprash2003 on 2009-04-08
try changing your DNS servers to opendns - 208.67.222.222 and 208.67.220.220 .. if you still have problems post output of ifconfig from the temrinal
for reference : [http://www.prash-babu.com/2008/04/how-to-configure-dns-servers-in-linux.html](http://www.prash-babu.com/2008/04/how-to-configure-dns-servers-in-linux.html)

---

### Post by 3rag0n on 2009-04-08
When I used SuSe there was a specifiable "idle" time for the connection - that is, if u dont do any network data transfers within the specified time, the connection will terminate....

that may be the problem... google for a command to change the idle time to zero... zero means it will be alive forever.

else post a new thread for changing that idle time.. this thread doesnt have a very .... er.. attractive/informative title.

---

### Post by rdumas on 2009-04-08
> **acimmarusti said:**
> open up a terminal and type this:

```

lspci -v | grep Network

```

And show me the output

0e:00.0 Network controller: Atheros Communications Inc. AR5008 Wireless Network Adapter (rev 01)

This is what I got.

---

### Post by rdumas on 2009-04-08
> **superprash2003 said:**
> try changing your DNS servers to opendns - 208.67.222.222 and 208.67.220.220 .. if you still have problems post output of ifconfig from the temrinal
for reference : [http://www.prash-babu.com/2008/04/how-to-configure-dns-servers-in-linux.html](http://www.prash-babu.com/2008/04/how-to-configure-dns-servers-in-linux.html)

Ok you are over my head what is DNS how do I find it and then change it.
I did the ifconfig thing all I got was command not found.

---

### Post by acimmarusti on 2009-04-08
It appears this is a common problem as evidenced here: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/298192](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/298192)

and here: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/278190](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/278190)

Also it has been documented in the Linux wireless website: [http://wireless.kernel.org/en/users/Drivers/ath9k#Mostcommonknownissues](http://wireless.kernel.org/en/users/Drivers/ath9k#Mostcommonknownissues)

> Most common known issues

Minimal kernel requirements

You want at least these kernels to use ath9k:

    * >= 2.6.27.8
    * >= 2.6.28.1
    * 2.6.29 

Ubuntu users

Ubuntu users will want to upgrade to at least 2.6.27-11


It appears that if you are able to upgrade the linux kernel to 2.6.27-11 (which I'm currently running), all problems are solved. If you are unsure which kernel you are running try:

```

uname -a

```

And post back your output. To update the linux kernel, all you have to do is fully update your system (get all available updates from canonical).

Hope this works, if not, I'm out of ideas, do a little searching on your own with the info I've provided...

---

### Post by rdumas on 2009-04-08
> **acimmarusti said:**
> It appears this is a common problem as evidenced here: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/298192](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/298192)

and here: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/278190](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/278190)

Also it has been documented in the Linux wireless website: [http://wireless.kernel.org/en/users/Drivers/ath9k#Mostcommonknownissues](http://wireless.kernel.org/en/users/Drivers/ath9k#Mostcommonknownissues)



It appears that if you are able to upgrade the linux kernel to 2.6.27-11 (which I'm currently running), all problems are solved. If you are unsure which kernel you are running try:

```

uname -a

```

And post back your output. To update the linux kernel, all you have to do is fully update your system (get all available updates from canonical).

Hope this works, if not, I'm out of ideas, do a little searching on your own with the info I've provided...

I ran the code an it would appear that my system is up to date.
Linux randy-laptop 2.6.27-11-generic #1 SMP Wed Apr 1 20:57:48 UTC 2009 i686 GNU/Linux
Thanks for trying, I will keep looking.  I am sure it is something very simple that I am just missing. :lolflag:

---

### Post by superprash2003 on 2009-04-09
DNS servers are the servers which convert google.com to x.x.x.x where x.x.x.x is the ip... if your ISP's DNS servers are overloaded , then it could cause your internet to work slow at times.. so try the link i mentioned , it would move your DNS servers to opendns ..

---

### Post by rdumas on 2009-04-09
> **superprash2003 said:**
> DNS servers are the servers which convert google.com to x.x.x.x where x.x.x.x is the ip... if your ISP's DNS servers are overloaded , then it could cause your internet to work slow at times.. so try the link i mentioned , it would move your DNS servers to opendns ..

Help here would be really nice.  I have noticed when I lose internet that if I click on my network connection and double click on me it reconnects.[IMG]/home/randy[/IMG]

---

### Post by rdumas on 2009-04-09
Thats not what I was trying to show you. Sorry. I was trying to show you my network connetion screen shot. I don't know how I guess.
When I open my network connection I only have four tabs / Wired / Wireless / Mobile Broadband / VPN / DSL This is all I have to work with.
How do I even access my DNS let alone change it?

---

### Post by rdumas on 2009-04-10
Further investigation between myself and my IP have determined that my connection is not the problem.   The problem lies with Fire Fox because my mail and pidgin still works after Fire Fox drops.
I have checked the knowledge data base with Fire Fox and have posted a question there.

---

