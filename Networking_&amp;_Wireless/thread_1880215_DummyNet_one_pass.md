---
title: "DummyNet one_pass"
date: 2011-11-13
forum: Networking &amp; Wireless
---

### Post by r0binary on 2011-11-13
Hi,  We try to use DummyNet in linux because we want to combine it with Netem. I first tried to configure DummyNet in FreeBSD and everything went fine. As soon as I try the same configuration under linux, there is a problem. It seems the one_pass option (ipfw disable one_pass) has no effect. We want to combine pipes to simulate a multihop line, but with any configuration we've tried, the first rule is processed and then the traffic is released to the network or the operating system. Is this a known bug? And is there a way to fix it? I hope you guys can help us.  Thank you in anticipation, r0b

---

