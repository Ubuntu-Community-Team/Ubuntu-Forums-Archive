---
title: "Ubuntu 10.10 can't connect to wireless network"
date: 2011-04-03
forum: Networking &amp; Wireless
---

### Post by Cromwell_Linux on 2011-04-03
Hi everyone !

I'm having a little issue here with my laptop. I've installed Ubuntu 10.10 Maverick/Meerckat on my Lenovo Thinkpad T61p about 3 hours ago and it can't seem to connect to the wireless network... I've had the same problem when I moved from Windows to Ubuntu on my desktop but I've been able to fix it completely. The thing is I can't remember how I fixed it :S So, I updated my system, downloaded the additional drivers. Also, I cna connect to the ethernet network. To fix my desktop, I used some command lines that someone posted in a thread about the wireless keeping disconnecting... I just can't find that post though :S What I remember about the post was that there was someone who had posted a thing with like a parabolic thing around he wireless adapter (LOL). Maybe you guys have any clue ?

---

### Post by Cromwell_Linux on 2011-04-03
Up ! Please :confused:

---

### Post by matt_symes on 2011-04-03
Hi

A word to the wise. It's frowned upon to write and bump a thread more than once in 24 hours. ([SIZE="1"]/whisper/ someone might say something /whisper/[/SIZE])

I am soon off to bed but to help others i suggest you open a terminal and post the output of (case sensitive)

```
sudo lshw -C network
lspci -nnk | grep Network
ifconfig
iwconfig
```

Enter your password. It will not be echoed to the screen.

Please post the output between code tag as it's easier to read. To do this highlight the text to put between code tags and hit the # button above where you are tying your reply.

Kind regards

---

