---
title: "Atheros AR9285 trouble with HP G60-536NR"
date: 2009-12-20
forum: Networking &amp; Wireless
---

### Post by archer007 on 2009-12-20
I cannot get my Atheros AR9285 card in Ubuntu 9.10 on my HP G60-536NR laptop working.

I tried "sudo apt-get install linux-backports-modules-jaunty". That didn't work. I [_successfully installed the latest Linux wireless drivers_]("https://help.ubuntu.com/community/WifiDocs/Device/Atheros/AR9285") (version compat-wireless-2.6.33-rc1.tar.bz2) without success. I restarted each time. Ideas?

---

### Post by drpjkurian on 2009-12-20
> **archer007 said:**
> I cannot get my Atheros AR9285 card in Ubuntu 9.10 on my HP G60-536NR laptop working.

I tried "sudo apt-get install linux-backports-modules-jaunty". That didn't work. I [_successfully installed the latest Linux wireless drivers_]("https://help.ubuntu.com/community/WifiDocs/Device/Atheros/AR9285") (version compat-wireless-2.6.33-rc1.tar.bz2) without success. I restarted each time. Ideas?

Hi Archer
Your card appears to be atheros,
Why cant you give a try to my thread.
The url is [http://ubuntuforums.org/showthread.php?t=1240781](http://ubuntuforums.org/showthread.php?t=1240781)

Best of luck
Dr Kurian

---

### Post by archer007 on 2009-12-20
Now I cant even see the card using ifconfig after following those directions :(

Should I try them again?

---

### Post by drpjkurian on 2009-12-20
Hi
what is the output of
```
iwconfig
```
Dr Kurian

---

### Post by archer007 on 2009-12-20
```
lo        no wireless extensions.

eth0      no wireless extensions.


```

I also compiled and installed the bleeding edge ath9k Linux wireless drivers unsuccessfully.

---

### Post by archer007 on 2009-12-20
Bizarrely, when I boot into the Ubuntu 9.10 LiveCD, the wifi works perfectly.

EDIT: I just realized that my wifi might be off. However, I can't turn it on, as when I press the hardware wifi button, it stays off. When I boot into the LiveCD, it works perfectly (turns on and off via the hardware switch as expected).

---

### Post by archer007 on 2009-12-20
I solved this issue. I reinstalled Ubuntu and then found out I could use the hardware wifi switch to turn on the Atheros adapter at the login screen. Works fine now. Thanks, drpjkurian!

---

### Post by drpjkurian on 2009-12-21
Hi
Thats great. I am happy to know that your card is back to life again.

Well please note that in earlier instance your driver was installed properly because the command iwconfig should also give you 'ath0'. which was not seen in your output.

With regards
dr kurian

---

