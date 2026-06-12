---
title: "Intermittent wireless?"
date: 2010-04-01
forum: Networking &amp; Wireless
---

### Post by a mad pigeon on 2010-04-01
Hey everybody!
Recently been having issues with Ubuntu 9.10 on my laptop. Works great all the time, but now I'm having wireless issues. I'm using 9.10 64 bit with a built in wireless card. I dual boot with Windows 7, wireless works fine on that, no issues and great range. However, on Ubuntu, the wireless will work for 5-10 seconds at a time and will cut out most of the time. Then it disconnects after about 10 minutes, sometimes sooner. I've ruled out that it is the laptop, my other PC and iPhone work fine. I'm using wireless G only on channel 1, no other interference. I live out in the country, so there's no other wireless points around me. Any help please? :D I'm guessing it's the default Ubuntu drivers, but what can I do?

Thank you.

---

### Post by adam814 on 2010-04-01
Well, it's pretty hard to give any advice without more specific information.  Important things to know would be the wireless card you have and which driver it's using.  Post the output from these commands to give us a better picture of what you have:

```
iwconfig
sudo lshw -C network
sudo lspci
```
Also it would be useful to know what type of encryption you're using (WEP v WPA/WPA2).

---

