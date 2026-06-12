---
title: "Can't install Intel Wifi Link 1000 / iwlwifi"
date: 2010-07-17
forum: Networking &amp; Wireless
---

### Post by kuckunniwi on 2010-07-17
Hi,

I'm I complete noob. Have been using Ubuntu Desktop Amd64 for 6months, on a dual boot alongside Vista64. Since first installing the OS, I have switched over to Ubuntu & use Windows only for heavy multimedia edition & the occasional gaming.

I just bought a netbook and installed Ubuntu 10.04 LTS NBR. Works great, except for wlan. No propriety drivers available for my Intel Wifi Link 1000BGN. 

I've spent hours trying to install iwlwifi, but the process is somewhat complicted for a noob such as myself.

After much reading and trying, I've managed to download and install iwlwifi-1000-ucode-128.50.3.1.tgz, (following the [http://intellinuxwireless.org/?p=iwlwifi&n=howto-iwlwifi]("http://intellinuxwireless.org/?p=iwlwifi&n=howto-iwlwifi") instructions)
and am now working on installing the mac80211 subsystem (following the [http://intellinuxwireless.org/?p=mac80211&n=howto-mac80211]("http://intellinuxwireless.org/?p=mac80211&n=howto-mac80211") instructions)

When running 

```
% wget \
  intellinuxwireless.org/mac80211/downloads/mac80211-10.0.4.tgz[/url]
% tar xvf mac80211-10.0.4.tgz
mac80211-10.0.4/origin/GIT 
mac80211-10.0.4/origin/net/mac80211/Makefile
```

I get: 
mac80211-10.0.4/origin/GIT
bash: mac80211-10.0.4/origin/GIT: Permission denied

I found this [http://www.linuxquestions.org/questions/linux-newbie-8/permission-denied-662567/]("http://www.linuxquestions.org/questions/linux-newbie-8/permission-denied-662567/")and did a chmod 755, and when later try to execute the code again, I get a "command not found error".

Here is where I learned there's no way around changing my kernel, which is where things get too hairy for me. I'm well aware that there's plenty of documentation out there on how to do this, but studying+working, I've already spent more time than I had trying to solve this issue. All I need the netbook for is using openoffice & wifi. I'd much rather run Ubuntu, but as I said, I need the thing up and running, and though I'd love to become fluent in Ubuntu usage, I'm the kind of user who can't afford to spend days at a time trying to figure things out, and may very well end up switching over to Windows (thanks a bunch, Intel! This kind of issue must translate into quite a profitable relationship with Microsoft for them...).

Are there any alternatives to changing the kernel? How long/how many OS reinstalls do you guys think it'll take a newbie like myself to change it and get iwlwifi running? I despise having to resort to Windows, but may have to, for the time being, until a more newbie-friendly option becomes available...

Thanks in advance!!!

---

### Post by Buffalo Soldier on 2010-07-19
I think Intel Wifi 1000BGN is well supported in Linux. Their driver is completely opensource.

---

### Post by kuckunniwi on 2010-07-19
> **Buffalo Soldier said:**
> I think Intel Wifi 1000BGN is well supported in Linux. Their driver is completely opensource.

Actually, aside the option mentioned in my post, I know of no other. I get a wired connection, and have checked for propriety drivers & update system to no avail. I've tried Ubuntu 10.04 NBR, 10.04 Desktop, 9.04 NBR, EasyPeasy, Eeebuntu & Moblin & none of them detect the card at all.

iwconfig reports:

> 
lo        no wireless extensions.

eth0      no wireless extensions.

Anything a complete noob can do to solve this?

---

