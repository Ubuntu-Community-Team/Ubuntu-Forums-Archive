---
title: "Compiling hostapd 0.7.3 for Ubuntu, problems"
date: 2011-04-02
forum: Networking &amp; Wireless
---

### Post by BkkBonanza on 2011-04-02
I've been trying to compile and use the newer version of hostapd rather than the one in the repos. This is because the one in the repos won't let me go into [HT40] mode. It keeps failing. The new version does.

However, when I build the new hostapd and run it my station only ever sees WEP auth and won't auth with WPA. But I have hostapd.conf set for WPA/WPA2 and this works fine with version 0.6.10. I haven't changed my conf file and I can't find any reason why hostapd wants to do WEP instead of WPA.

I got the Debian .config to use for the build so I should have the same build options. 

It seems there is a config change between versions that causes WEP to override WPA.

Anyone have some success with this? 

Thanks for any expert input.

---

