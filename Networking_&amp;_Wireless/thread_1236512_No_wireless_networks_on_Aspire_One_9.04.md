---
title: "No wireless networks on Aspire One 9.04"
date: 2009-08-10
forum: Networking &amp; Wireless
---

### Post by xtremesupremacy3 on 2009-08-10
Hey there people,

I'm kinda on wits end now.
I purchased an Aspire One (Linpus version), some time ago now and my brother used it on Ubuntu Netbook Remix, since I use this laptop on Ubuntu anyway.
Now I'm running into bother constantly.
The wireless is nicely there and installed, when I check it out its recognised as Atheros AR242X 802.11abg Adapter. It's using the kernel driver ath5k_pci modules ath_pci, ath5k.
So as you can see, it IS installed.
Problem is, when I click on network manager, it shows NO networks under the 'Wireless Networks' option...even attempting to sign on as hidden network goes with no luck. Wired works fine.
I tried installing the propretiery (how do ya spell it?), and then the thing stops showing up all together.
I tried the madwifi approach but my terminal lets me know nicely that it can't resolve the host 'snapshot.madwifi.org'...so that won't help.

Anybody got any ideas what I can do?

Thanks
Arthur

---

### Post by LowSky on 2009-08-10
[https://help.ubuntu.com/community/AspireOne](https://help.ubuntu.com/community/AspireOne)


add blacklist acer_wmi to /etc/modprobe.d/blacklist for wifi to work

---

### Post by xtremesupremacy3 on 2009-08-10
Thank you for the reply, this has also been done to no avail.

EDIT: Just to let you know, I have gone through the walkthrough and searched Google endlessly

---

### Post by DustDiesel on 2009-08-11
Im new, pardon my ignorance. I have a similar problem. I am on a Acer Aspire One and I have found I have an Atheros wireless card. I have tried both the madwifi driver and the standard one enabled, rebooted a few times.

 I cannot seem to find any of the wireless networks in my area (I have 5-8 in range). When I goto edit connections and select wireless there is nothing there. I can click add and essentially manual intput information, that cant be how I connect, can it?

 Again, Im new, just downloaded the pocket guide. 

 How do I " add blacklist acer_wmi to /etc/modprobe.d/blacklist " ?

 I have tried typing that at terminal and everything else I could think of, Ive been messing with it for several hours but havent had any luck.

---

### Post by DustDiesel on 2009-08-11
Im new, pardon my ignorance. I have a similar problem. I am on a Acer Aspire One and I have found I have an Atheros wireless card. I have tried both the madwifi driver and the standard one enabled, rebooted a few times.

 I cannot seem to find any of the wireless networks in my area (I have 5-8 in range). When I goto edit connections and select wireless there is nothing there. I can click add and essentially manual intput information, that cant be how I connect, can it?

 Again, Im new, just downloaded the pocket guide. 

 How do I " add blacklist acer_wmi to /etc/modprobe.d/blacklist " ?

 I have tried typing that at terminal and everything else I could think of, Ive been messing with it for several hours but havent had any luck.

---

### Post by DustDiesel on 2009-08-12
I have figured out how to navigate the file system to /etc/modprobe.d/blacklist.conf? I can open this file with the text editor and add the blacklist acer_wmi to the lines. However it does not allow me to save. It says I do not have the permissions, am I missing something here?

 also, upon reading the guide it asks to make sure that the wireless is turned on. My wireless switch is not responsive in ubuntu so I am unsure if it is active, this may even be the problem. 

 Any tips?

---

### Post by xtremesupremacy3 on 2009-08-16
Hey there friend.

Sorry for the late reply, it's been a while since i been here.
Anyway, NEVER apologise for being new, we all start somewhere and we're glad to help where we can.

In linux, for safety reasons, any alterations outside of the folders you have permissions in (/home), you need administrative rights.

In Ubuntu we call this sudo. To apply this you basically put the word 'sudo' before the rest of the command, for instance:
You want to gedit /etc/modprobe.d/blacklist.conf. You do this by:

```
sudo gedit /etc/modprobe.d/blacklist.conf
```

After this you will be prompted for a password, once that has been entered you can simply change and save. Easy :-)

Welcome to Ubuntu

---

### Post by DustDiesel on 2009-08-16
I see. Well I was able to save it. Still no luck with the connection to the wireless. I was able to gain a connect when I connect it to the router with a ethernet cable.

 Ive messed with it so much that I think I'm going to have to revert back to XP or check to see if it is something only in the netbook remix.

---

