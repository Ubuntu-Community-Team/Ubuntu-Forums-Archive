---
title: "ATI Mobility FireGL V5000 + Hp nc8240  woes"
date: 2006-07-28
forum: Multimedia &amp; Video
---

### Post by rmsh on 2006-07-28
Hi

I've a HP nw8240 laptop with ATI Mobility FireGL V5000 video card. I've created a virtual m/c using MS Virtual PC and installed Dapper in there. 

This is the output in Ubuntu terminal 

```
lspci | grep VGA
0000:00:08.0 VGA compatible controller: S3 Inc. 86c764/765 [Trio32/64/64V+]
```

I've no clue what this S3 Inc is ???

Few other symptoms 
[LIST]
[*]"sudo dpkg-reconfigure xserver-xorg" leaves me with a blurred screen, if I select "ati"
[*]I'm stuck with 1024x768 screen resolution. I can't go any further
[/LIST]

How can I increase my screen resolution?. Install ATI custom drivers?

I've tried things that were mentioned in other threads, but nothing was useful.

Any help is higly appreciated.

Thanks in advance
Ramesh

---

### Post by JeffTP on 2006-08-31
Go ahead and install the ATI proprietary drivers. So far they've worked without issue on the nw8240.

---

