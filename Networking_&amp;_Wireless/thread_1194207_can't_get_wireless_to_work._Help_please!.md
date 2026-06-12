---
title: "can't get wireless to work. Help please!"
date: 2009-06-22
forum: Networking &amp; Wireless
---

### Post by makesmewanna on 2009-06-22
Hi,

I am using Ubuntu 9.04 on t61. I don't know very much about linux.
after installing the OS, it keeps giving me wireless discovery disabled. 
The wireless keeps getting disconnected and after a few disconnection, the wireless still detects the wifi with 90%, however, it just can not connect to it.

I tried the following website, but it does not work: 

[http://www.thinkwiki.org/wiki/Installing_Ubuntu_9.04_(Jaunty_Jackalope)_on_a_ThinkPad_T61#Fixing_Atheros_Ath5K_Stability_Issues]("http://www.thinkwiki.org/wiki/Installing_Ubuntu_9.04_%28Jaunty_Jackalope%29_on_a_ThinkPad_T61#Fixing_Atheros_Ath5K_Stability_Issues")

Can someone please help me on this?

Thank you very much!!

---

### Post by tmht on 2009-06-23
What output do you get when you run the following command?

```
sudo apt-get install linux-backports-modules-jaunty
```

---

### Post by drrdf2 on 2009-06-24
I had the same problem with Ubuntu 8.10 and the current release, using a wireless card.  It is a common problem with Ububtu, iincluding the latest release. After wasting an inordinate amount of time I put together a clear detailed procedure which should work with most if not all wireless cards. I have posted it on this forum under **Ubuntu 8.10 stated menu options missing. **Strangely I have now discovered that some of these menu options only appear after you have installed ndisgtk! Weird that.

---

