---
title: "Firewire and tuner question"
date: 2009-05-05
forum: Mythbuntu
---

### Post by WrathofthePenguin on 2009-05-05
I'll be getting Fios in the near future, and I plan on having a set top box that I can use the firewire connection with. If I understand things correctly, I'll only be able to record one channel from that set top box. I'll also have two front ends on two other televisions. I plan to connect with gigabit ethernet.

So I guess my question falls along the lines of design/operation. If I connect my backend to the set top box via firewire and have a separate tuner plugged in to the coax, I should be able to record HD via firewire and clear qam via the coax connection, correct? Is there any way to set priority? What I want to avoid is some darnfool situation where I can't record an HD program because the firewire connection already was recording something that could have been recorded on the clear qam connection.

Thanks in advance!

---

### Post by newlinux on 2009-05-06
Yes, that setup allows you to record as you specified. The scheduler is smart enough to know when two scheduled recordings occur at the same time and one of them is only available on one video source to use the tuner with that source and schedule the other recording on the other tuner with a different video source. You'll probably want to setup one video source for firewire (with one set of channels) and another for your QAM. Also, you can set manual priorities for tuners as well - i.e. when you are scheduling a recording you can specify which tuner you want it to "prefer" and you can setup priorities when there are conflicts.

Before you run into any disappointments, have checked to see what channels will be available via firewire and unencrypted QAM from your provider in your area?

---

### Post by WrathofthePenguin on 2009-05-06
> **newlinux said:**
> Yes, that setup allows you to record as you specified. The scheduler is smart enough to know when two scheduled recordings occur at the same time and one of them is only available on one video source to use the tuner with that source and schedule the other recording on the other tuner with a different video source. You'll probably want to setup one video source for firewire (with one set of channels) and another for your QAM. Also, you can set manual priorities for tuners as well - i.e. when you are scheduling a recording you can specify which tuner you want it to "prefer" and you can setup priorities when there are conflicts.

Before you run into any disappointments, have checked to see what channels will be available via firewire and unencrypted QAM from your provider in your area?

This is good news (and no phenom-bashing in this post!). I've checked and found that there are quite a few channels available in clear qam. Right now I have a Tivo which can't record HD content at all, and it can only record one channel at a time. Even a limited set of secondary tuner channels would be an improvement.

---

