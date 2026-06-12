---
title: "Help Connecting To Internet"
date: 2006-04-12
forum: Networking &amp; Wireless
---

### Post by sdannenberg3 on 2006-04-12
Hey, yes, i am a newbie, but my friend told me t come here because everyone is so friendly and helpful. So, here it goes. I have been using windows for 10 years now :( and i finally had enough of its crap. I have both windows and Ubuntu installed. When i am in windows, i can get the intetrnet through DHCP just fine. BUT! in ubuntu, i cant. I try to connect through ubuntu, and it seems like it works, but when i go into firefox, it says something like "Could not fidn page ...." or when i try to logonn to my linksys router.. "The connection was refused by host" So whats up!???!!?!? I even tried manually setting the IP. Same message. So, ANY suggestions? imso lost. Can I do something like ipconfig in windows? to check to see if i am recieving packets? I dont know how to do stuff like that yet because im so new. So, if anyone could, please tell me how, or send me a link that would give me info to solve this annoying problem. All i want to do is use its stability, and so far, well, i cant really sue it.

---

### Post by mips on 2006-04-12
In the firefox address/URL space type    "about:config"    , scroll down to    **network.dns.disableIPV6 = false**    ,double click this line to change it to **true**.
In the above do NOT type in any quotes.

The above will most probably help for Firefox but not your other applications. Test with Synaptic, GAIM and other stuff using the net and if they dont work try the following:

Open a terminal and enter:
**sudo gedit /etc/modprobe.d/aliases**

Look for the line that reads:
**alias net-pf-10 ipv6**

Change it to:
**alias net-pf-10 off #ipv6**

**Save and reboot your PC**.

If you want to stop the module from loading then:
```
sudo mv /lib/modules/$(uname -r)/kernel/net/ipv6/ipv6.ko /lib/modules/$(uname -r)/kernel/net/ipv6/ipv6.ko.bak
sudo depmod -a
```

---

