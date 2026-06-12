---
title: "karmic 9.10 &amp; Intel 3945ABG"
date: 2009-11-11
forum: Networking &amp; Wireless
---

### Post by Hell_Rico on 2009-11-11
Hi everybody.
I am newbie, I installed Karmic on my HP compaq 6510b and everything is ok, expect for the wireless connection. As soon as I turn it on the wireless card takes 100% of the CPU and after a while ubuntu freezes and I cannot do anything. I don't want to go back to windows...I really appreciate all your help.

Thanks

---

### Post by fargle on 2009-11-11
What does "top" show as using the most CPU when it's at 100%?

I have a Dell XPS M1330 with a 3945ABG in it and have never had an issue.

---

### Post by Hell_Rico on 2009-11-11
the top command shows that iwl3945 takes 100% of the cpu

---

### Post by fargle on 2009-11-11
Interesting.  Can you see if anything is being logged in /var/log/syslog by Network Manager relating to this?  If so, attach it here.

---

### Post by Hell_Rico on 2009-11-11
I have found something, I hope it can help

---

### Post by fargle on 2009-11-11
Hmm.  I see lots of reboots, and I see eth0 coming active as well - do you have a network cable plugged into the Ethernet jack?  Does iwl3945 take up lots of CPU even when the wifi is not active and the Ethernet is plugged in?

Other than that I don't see anything that points to the problem in this log.

---

### Post by Hell_Rico on 2009-11-11
I have to reboot my system every time I try to turn on the wireless, it freezes my ubuntu. Anyway if I switch off the wireless the CPU usage is about 4-5% in total, depending on what program I am running.

---

### Post by fargle on 2009-11-11
Okay, thanks.  Think I'm in over my head on this one then, I don't see network manager logging anything, and I don't think it will do any good to have you look at dmesg kernel output if your system freezes when it's on.

I hate to say it, because I have a 3945ABG card and I love it, but one fairly quick way to get rid of this would be to replace that card - it's likely on a MiniPCI card under a panel on the bottom of the computer, and you could look for a replacement on Ebay, they're usually pretty cheap.

Otherwise, perhaps a Google to see if anyone else is having that problem with your specific machine and card and Karmic.

---

### Post by slakkie on 2009-11-11
You have this card?
0c:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)


Too figure that out, run this command:
```

lspci | grep -i wire

```

If so, could you please post/attach the output of:

```

grep iwl /var/log/*

```

That should report anything for your card in your log files. 

I have the same card and no issues at all.

---

### Post by fargle on 2009-11-12
Same one I have as well, no issues.

---

### Post by Hell_Rico on 2009-11-12
I have forgotten some details, I don't know if they are important. I am running Ubuntu in dual boot with Windows XP and in the latter os I can use the wireless, even if it takes a lot of time to find the network (more than 20 minutes) and to connect. So I don't know if replacing the card can help. I am going to try.

Thanks

---

