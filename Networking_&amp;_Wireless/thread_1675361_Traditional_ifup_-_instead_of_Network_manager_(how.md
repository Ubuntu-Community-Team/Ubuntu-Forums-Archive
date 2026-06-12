---
title: "Traditional ifup - instead of Network manager (how is it done?)"
date: 2011-01-25
forum: Networking &amp; Wireless
---

### Post by smudgy on 2011-01-25
**How does one get**** Ubuntu to use traditional ifup** instead of network manager? .... I have been asking myself this question for a long long time!

**Would someone be able to share this secret knowledge and impart it to me and thereby posterity.... ;-}**

I have been trying for ages but apart from being told to configure  interfaces in /etc/networks there seems to be little intelligible  guidance on this that I can find...

tubasoldier seemed to use it in an old post but unfortunately (grrr....) he has not indicated how... in addition to his rant ...! 

Anyone using traditional ifup instead of network manage that can tell me how?  :idea:

---

### Post by spiky001 on 2011-01-25
Prehaps you could explain what you want to do abit better if it's turn wireless off

---

### Post by smudgy on 2011-01-25
> **spiky001 said:**
> Prehaps you could explain what you want to do abit better if it's turn wireless off

Hi Spiky

I don't use wireless much. But I do use suspend/hibernate a lot and there is a conflict between suspend/hibernate and network manager that I only know how to resolve by using traditional ifup. Other wise when I resume although network manage reports eth0 as being connected nothing happens and disconnecting/reconnecting nothing happens.

In openSUSE they have a gui they call Network Tools in Yast that lets you change from having Network Manager control things to using Traditional ifup. That does the trick. I don;t yet know how to automate suspend/resume to run sudo /sbin/ifdown eth0 and the reverse on resume but I have a couple of easy quick launchers in my menu that quickly do the job when I resume.

Alas for Ubuntu I have to reboot as Suspend/Hibernate involve loss of internet connection which I don;t know how to solve. The easiest thing would be to use traditional ifup as explained how suse does it.

Hope that explains enough! Also hope you know the answer to how I can switch to Traditional ifup in Ubuntu!

;)

.

---

### Post by spiky001 on 2011-01-25
```
sudo ifconfig wlan0 up
``````
sudo ifconfig wlan0 down
``` All done in terminal, I had the same problem going from Ubuntu to Open suse they are different

---

### Post by smudgy on 2011-01-25
> **spiky001 said:**
> ```
sudo ifconfig wlan0 up
``````
sudo ifconfig wlan0 down
``` All done in terminal, I had the same problem going from Ubuntu to Open suse they are different

wlan0: ERROR while getting interface flags: No such device

I thought it couldn't be that simple ;)

Went into interfaces and added to the eth0 interface I had already configured (although it didn't seem right somehow)

```
auto eth0
iface eth0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
```Anything you have forgotten to tell me?  Maybe I should add I am a bit of a newbie as far as linux goes so the less left unsaid the better  ;).

---

### Post by smudgy on 2011-01-25
I should add that I tried ```
sudo ifconfig eth0 down
``` and that did take the network down alright without an error message or any message. However ```
sudo ifconfig eth0 up
``` did nothing so I had to admit defeat again and reboot into openSUSE ... am still none the wiser.

PS: remember I don't have a wireless connection. It's wired ethernet.

.

---

### Post by Iowan on 2011-01-25
Some suggest that Network Manager must be completely removed (as opposed to simply disabled). I haven't been brave enough to try...

---

### Post by smudgy on 2011-01-26
> **Iowan said:**
> Some suggest that Network Manager must be completely removed (as opposed to simply disabled). I haven't been brave enough to try...

I have removed NM but elected to keep the files. I was afraid that if I reinstalled it later I would lose the configuration I got during installation. Since there doesn't seem to be an ifup gui configuration package out there for ubuntu. Maybe I don't need such a package and configuration is easy enough providing NM is fully cleansed from the system?

I suppose I could try it out on a spare linux partition....

Thanks for the input.

---

