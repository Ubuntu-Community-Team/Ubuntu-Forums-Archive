---
title: "Unable to connect to wireless network"
date: 2010-04-20
forum: Networking &amp; Wireless
---

### Post by geitliefje on 2010-04-20
Hi, 
I just installed Ubuntu yesterday and this is the only problem I'm having *fingers crossed* :P
I can't connect to my wireless network at all on ubuntu (though I can on Vista). I'm using it through an ethernet cable for the moment. I've tried going through sytstem > administration > hardware drivers to activate the wireless driver but it says that' no proprietary drivers are in use on this system' and doesn't list anything. I've got a Netgear DGN2000 router and Broadcom wireless. Thanks in advance!

---

### Post by bkratz on 2010-04-20
> **geitliefje said:**
> Hi, 
I just installed Ubuntu yesterday and this is the only problem I'm having *fingers crossed* :P
I can't connect to my wireless network at all on ubuntu (though I can on Vista). I'm using it through an ethernet cable for the moment. I've tried going through sytstem > administration > hardware drivers to activate the wireless driver but it says that' no proprietary drivers are in use on this system' and doesn't list anything. I've got a Netgear DGN2000 router and Broadcom wireless. Thanks in advance!

You might want to go to the terminal (Applications>>Accessories>>Terminal) and enter in

```
lspci | grep Network
```

(that is LSPCI in lowercase and N in upper case) and copy/paste what is returned back here so we can see which Broadcom card you have.

---

### Post by geitliefje on 2010-04-20
It says

04:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)
lauren@lauren-laptop:~$ ^C

:)

---

### Post by bkratz on 2010-04-20
> **geitliefje said:**
> It says

04:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)
lauren@lauren-laptop:~$ ^C

:)



It should be as simple as connecting your ethernet cable and executing.

```

sudo apt-get update
sudo apt-get install bcmwl-kernel-source
```

Note these will require your password which will not be echoed during typing--just hit enter when done.

---

### Post by geitliefje on 2010-04-20
Thanks, it's working great now :)

---

