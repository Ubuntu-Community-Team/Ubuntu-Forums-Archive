---
title: "DWA-130 won't connect to network"
date: 2010-03-20
forum: Networking &amp; Wireless
---

### Post by gg4gg4 on 2010-03-20
Hello all,

I managed to install the driver for a Dlink DWA-130 (is a ver. E) and it appears that the computer recognises it. It also sees nearby access points. But, when I try to connect to my home network it asks for the wpa password over and over again after attempting to establish a connection. I'm using 9.10 and installed the driver by using ndiswrapper.

What should I do?
Thanks for looking!

---

### Post by bkratz on 2010-03-20
> **gg4gg4 said:**
> Hello all,

I managed to install the driver for a Dlink DWA-130 (is a ver. E) and it appears that the computer recognises it. It also sees nearby access points. But, when I try to connect to my home network it asks for the wpa password over and over again after attempting to establish a connection. I'm using 9.10 and installed the driver by using ndiswrapper.

What should I do?
Thanks for looking!

Didn't know they were up to version E now! Mine is a version A. Do you know which kernel number you are using?  If not enter the following in the terminal ( applications>>Accessories>>Terminal )

```
uname -mr
```

Have you ever tried to connect to a non-encrypted A/P anywhere?

---

### Post by gg4gg4 on 2010-03-20
I'm starting to worry that ver. E doesn't work...

It's: 2.6.31-20-generic i686

No, I haven't... There aren't any around actually, I would have add one to see. (It's a desktop btw.)

---

### Post by gg4gg4 on 2010-03-20
I just tried connecting to an unsecured network and then a wep network.
The one without encryption works but, wep does the same thing as my wpa connection. Hopefully, some how it can work with wpa encryption...

---

### Post by bkratz on 2010-03-20
> **gg4gg4 said:**
> I'm starting to worry that ver. E doesn't work...

It's: 2.6.31-20-generic i686

No, I haven't... There aren't any around actually, I would have add one to see. (It's a desktop btw.)



Well I guess you have answered a question posed in another thread about that kernel. I was just curious.  It is possible to make it work in 9.10, and if you PM me I will give you directions; but it is a long process. I have recently used the next version of Ubuntu 10.04 which will be available in just about 1 month where it works perfectly with ndiswrapper. You might just wait, or feel free to PM me.  It still would be interesting to remove encryption from your A/P and see if you connect reliably, but that is just out of interest on my part.

Well that answers that!

---

### Post by waynebruce on 2010-03-22
Hey **bkratz**, any chance it would be possible for you to give me a quick run through of how I can get online with my version A1 model?

---

### Post by bkratz on 2010-03-22
> **waynebruce said:**
> Hey **bkratz**, any chance it would be possible for you to give me a quick run through of how I can get online with my version A1 model?

Be happy to; but you will run into the same encryption issues we all have ( I have the A version also). As long as you're not using encryption--no problems. I you wish I will PM you the method by which I was able to make it work in 9.10. But, 10.04 is just around the corner and I have already tried it there and it worked fine, do you want the info?  Keep in mind they all do require ndiswrapper, but I can give you directions for that too, if you have no experience.

---

### Post by waynebruce on 2010-03-22
> **bkratz said:**
> Be happy to; but you will run into the same encryption issues we all have ( I have the A version also). As long as you're not using encryption--no problems. I you wish I will PM you the method by which I was able to make it work in 9.10. But, 10.04 is just around the corner and I have already tried it there and it worked fine, do you want the info?  Keep in mind they all do require ndiswrapper, but I can give you directions for that too, if you have no experience.


Awesome, I would thoroughly enjoy the information for 9.10 as well as the ndiswrapper's too since I haven't any experience other than a few days worth of reading about it in other posts.

---

