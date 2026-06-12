---
title: "Networking not working after Wubi Install on HP Mini"
date: 2011-10-25
forum: Networking &amp; Wireless
---

### Post by jetmakerbrit on 2011-10-25
I just installed Ubuntu 11.10 on a HP Mini 311-1025NR running Win7 using Wubi and unfortunately neither wired nor wireless networking is operational. The wifi I'm not surprised by and assume I need to download and install the Broadcom card drivers but this is tough without any networking (other than within Win7). Please can anyone advise how to get networking operational in Ubuntu?

I have used Ubuntu before but not for a few years or on this machine. It's fair to consider me a newb for the purposes of this thread.

Many thanks in advance for any help,

---

### Post by varunendra on 2011-10-26
Please post the output of:
```
sudo lshw -C network
```

Once we know exactly the models of your network interfaces, we should be able to download the suitable drivers on windows and then install them on Ubuntu.

---

### Post by jetmakerbrit on 2011-11-11
The output from the command specified is contained in the attached text file.

Many thanks,

---

