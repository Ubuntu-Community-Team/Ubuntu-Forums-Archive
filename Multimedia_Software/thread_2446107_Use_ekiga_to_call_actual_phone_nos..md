---
title: "Use ekiga to call actual phone nos."
date: 2020-06-24
forum: Multimedia Software
---

### Post by porphyry52 on 2020-06-24
I have installed ekiga and can make sip to sip calls OK, and have purchased call time from diamond.com to make calls out to actual phones, and that account is registered with ekiga.  But I cannot make calls to phones, such attempts always return "so-andso is offline".  I notice that every call I make to a number is actually placed to sip:number.  So perhaps I need to specify that ekiga should use the diamond.com account to make such calls.  The help makes no mention of this, just that one needs a call-out account. Please advise.

---

### Post by CelticWarrior on 2020-06-25
Yes, you need to setup the client to use your account.

---

### Post by porphyry52 on 2020-06-25
> **CelticWarrior said:**
> Yes, you need to setup the client to use your account.

Yes, that is the problem. How is it done?

I followed the instructions in the ekiga help, used their recommended call-out provider, entered the id and password from that provider, ekiga itself tells me that account is registered and ready to go, but it never makes use of it when I try to call a phone number. It always uses the free sip account. If I remove the sip account it still will not use the call-out account.

---

### Post by CelticWarrior on 2020-06-25
[http://wiki.ekiga.org/index.php/Manual#Call_out_.28PC_to_phone.29](http://wiki.ekiga.org/index.php/Manual#Call_out_.28PC_to_phone.29)

---

### Post by porphyry52 on 2020-06-29
> **CelticWarrior said:**
> [http://wiki.ekiga.org/index.php/Manual#Call_out_.28PC_to_phone.29](http://wiki.ekiga.org/index.php/Manual#Call_out_.28PC_to_phone.29)

Sorry for long delay in replying, been out of town. The manual reference you gave me above is what I followed with the Connection Assistant, and I got the id and password from diamond .com and registration completed normally.  I have tried calling numbers 4 ways;, just the number with and without leading 00, the number + uri generated automatically by ekiga, and the number + uri shown in the manual, e.g.
18887411115
0018887411115
sip:18887411115@sip.diamondcard.us
sip:18887411115@eugw.ast.diamondcard.us

All produce the same result, "Remote host is offline"

ekiga also produces an error/advisory message at each attempt of the form
```
(ekiga:1335): GLib-CRITICAL **: 16:21:44.716: Source ID 2980 was not found when attempting to remove it

```

---

