---
title: "need help installing sprint sierra wireless 598u mobile broadband device"
date: 2009-01-14
forum: Networking &amp; Wireless
---

### Post by mapxvc on 2009-01-14
I have just bought a sierra wireless 598u mobile broadband card and i am having some difficulty installing the device. I currently use xubuntu and ubuntu 8.1. can anyone show me in the right direction?

---

### Post by wmdiem on 2009-01-15
[http://ubuntuforums.org/showthread.php?t=779652&highlight=sprint+broadband+wireless](http://ubuntuforums.org/showthread.php?t=779652&highlight=sprint+broadband+wireless)

---

### Post by Deach on 2009-01-30
I'm curious to know if that helped since the modem in question isn't listed on the sprint list.

---

### Post by ieee488 on 2009-01-30
What do you mean that it is not *on the sprint list*?

It looks like this modem was just released this month. The HowTo was written last January.

Your only option is to give it a try.

---

### Post by Yogi291 on 2009-02-03
> **Deach said:**
> I'm curious to know if that helped since the modem in question isn't listed on the sprint list.

After you insert your card do this command in a terminal

lsusb
```
Bus 004 Device 007: ID 1199:0025 Sierra Wireless, Inc. 

```

see the ID and after the : is the product number.
I followed the guide from the link above and it worked.
Thank you guys for posting these great links.
:popcorn:

---

### Post by Alpinist on 2009-02-03
Using the manual wvdial commands in the pdf from Sprint I seem to get a connection in that it assigns an IP and dns to ppp0.  but I don't seem to have any network connection.

This may be a n00b problem but how do I get ubuntu to recognize ppp0 as my network connection?

(Frustrated that linux is so hard with stuff like this)

---

### Post by Alpinist on 2009-02-03
OK, I got it working, not sure if it was adding modprobe commands before connecting or simply that firefox had put itself into offline mode while I was testing.

---

### Post by Deach on 2009-02-09
> **Yogi291 said:**
> After you insert your card do this command in a terminal

lsusb
```
Bus 004 Device 007: ID 1199:0025 Sierra Wireless, Inc. 

```

see the ID and after the : is the product number.
I followed the guide from the link above and it worked.
Thank you guys for posting these great links.
:popcorn:

Thanks I'll try that.  I have really been fighting this one.

---

### Post by Deach on 2009-02-09
> **ieee488 said:**
> What do you mean that it is not *on the sprint list*?

It looks like this modem was just released this month. The HowTo was written last January.

Your only option is to give it a try.

Not sure which part you didn't understand.  I was sent to a link that was provided in a topic.  That link didn't provide help on the topic.  I was simply stating that at that time that link didn't help.  I'm aware of when the card was released thanks.

---

