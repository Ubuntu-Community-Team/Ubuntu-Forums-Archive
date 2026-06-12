---
title: "how to connect ubuntu 10.10 with MTS modem(wireless) internet"
date: 2011-10-29
forum: Networking &amp; Wireless
---

### Post by summii on 2011-10-29
I am using Ubuntu 10.10, and I can't seem to connect to my home wireless network. I click the wireless icon and select my MTSblaze connection1 and Ubuntu starts trying to connect but then it just tells me that the Network connection is disabled and I am offline. I am using a sony Eseries laptoop and Ubuntu is in a dual-boot with Windows 7 (which was originally the only OS on it.). I installed wvdial and ndiswrapper but nothing happened. 

I know this probably isn't enough, are there any commands I can use to get more information?

I am a beginner "absolute beginner" so please provide me with detail when answering my question. Thanks.

---

### Post by LinuxTrix on 2011-10-29
Hi Summii,

Have you tried activating the STA broadcom via additional drivers?
I had the same problem, and all I had to do was go to:
-system
-additional drivers
-select the broadcom STA driver & click "activate"

Tell me if it works.:)

Welcome to the forum, by the way.

---

