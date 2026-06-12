---
title: "get_iplayer recording mode problem"
date: 2012-04-03
forum: Multimedia Software
---

### Post by paulemony on 2012-04-03
Ubuntu 11.10 get_iplayer 2.79-2

When I try to record something using **$ get_iplayer --get 123** I get:

**INFO: No specified modes (flashhigh,flashstd,flashnormal) available for this programme with version 'default' (try using --modes=)**

Tried:

**paulemony@ubuntu:~$ get_iplayer --g 260 --modes=flashhd,flashvhigh,flashhigh,flashstd,flashnormal,flashlow,n95_wifi,flashaac,flashaachigh,flashaacstd,flashaaclow,flashaudio,realaudio,wma**

Same result. What does it want from me!

---

### Post by nothingspecial on 2012-04-03
Hi, try grabbing the latest version from this PPA

[https://launchpad.net/~jon-hedgerows/+archive/get-iplayer](https://launchpad.net/~jon-hedgerows/+archive/get-iplayer)

---

### Post by shantiq on 2012-04-03
hi paul   you are missing a bit is why it is not kicking in


try   > get-iplayer --vmode=flashvhigh2 --get 123


where you stipulate the video mode you want   here flashvhigh2



========================

to see what formats are available run    ```
get-iplayer  --get 123  ** --test**
```

if a program shows hd

run ```
--vmode=flashhd
```    otherwise ```
--vmode=flashvhigh2 
```  covers all 480p files

---

### Post by paulemony on 2012-04-03
Tried answer 2 & managed as far as instructions in pop-up went, at least I think I did but as you suggest Linux thinks that everybody in the world knows everything about it. I assume the entry "Replace ppa:user/ppa-name with the PPA's location that you noted above" should be **sudo add-apt-repository ppa:jon-hedgerows/get-iplayer**. When I look in Software sources I can see **[http://ppa.launchpad.net/jon-hedgerows/get-iplayer/ubuntu](http://ppa.launchpad.net/jon-hedgerows/get-iplayer/ubuntu)** twice so I suppose that's correct? I'm then told **Now you're ready to start installing software from the PPA!**. Great, but what software? Does existing installation have to be removed or does it update?

Tried answer 3 but same problem:

**paulemony@ubuntu:~$ get_iplayer --get 260 --test**
Answer:
[B]INFO: No specified modes (flashhigh,flashstd,flashnormal) available for this programme with version 'default' (try using --modes=)
[/B]

---

### Post by paulemony on 2012-04-03
P.S. Tried **sudo apt-get dist-upgrade** which seemed to do the trick, now have 2.8. Guess what?

**INFO: No specified modes (flashhd,flashvhigh,flashhigh,flashnormal) available for this programme with version 'default' (try using --modes=)**

AAAAAAAARRRGGGHHH!!!!!!!!!!!!!

---

### Post by shantiq on 2012-04-04
**This** is the line ====>

> [SIZE="3"]get-iplayer --vmode=flashvhigh2 --get 123[/SIZE]

---

### Post by paulemony on 2012-04-04
OK thanks, that seems to work with 2.8, although first time it starts by listing programme index (presmably just those that use flashhigh2?) before downloading, second time went straight in. Also then tried without **--vmode=flashvhigh2** and it works anyway now.

---

### Post by paulemony on 2012-04-09
Spoke too soon, using** paulemony@ubuntu:~$ get-iplayer --vmode=flashvhigh2 --get 206** with or without **--vmode=flashvhigh2  ** results in:
 [B]ERROR: RTMP_Connect0, failed to connect socket. 111 (Connection refused)
INFO: Command exit code 3 (raw code = 768[/B])

Back to Windows!

---

### Post by paulemony on 2012-04-11
P.S. Think I've solved it, it's version "default" it didn't like, just stick **--versions signed,audiodescribed,default** on the end & it'll pick the one that applies.

---

