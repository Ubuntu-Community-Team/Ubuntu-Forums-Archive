---
title: "Cisco Linksys e-1500"
date: 2012-11-21
forum: Networking &amp; Wireless
---

### Post by KegHead on 2012-11-21
Hi!

I'm trying to set up wep/wpa.

I have a Cisco Linksys e-1500.

I'm on a desktop w/12.10 (Xubuntu) and trying to setup three android tablets and an Ubuntu laptop.

Is there a guide/docs to follow?

I must be having a mental block.

Thanks!

KegHead

---

### Post by CharlesA on 2012-11-21
Are you trying to set it up on the router itself, or on the devices?

---

### Post by KegHead on 2012-11-21
Hi!

Which is best?

KegHead

---

### Post by CharlesA on 2012-11-21
WPA2 would be best unless your devices do not support it (and all newer devices do).

The documentation for the router can be found here:
[http://homesupport.cisco.com/en-us/support/routers/E1500](http://homesupport.cisco.com/en-us/support/routers/E1500)

Basically you just need to login to the web interface and go to the wireless security tab and set it up, if it isn't set up yet.

As for the Android devices, they should have a wireless networks link in the settings area.

---

### Post by KegHead on 2012-11-21
Hi!

Thanks!

I'll give a try!

KegHead

---

### Post by chili555 on 2012-11-21
> Hi!

Which is best?

KegHeadBasically,you are going to, I hope, set up the router to use WPA2 and set a strong password. Then when your computers, tablets. etc. try to log in, they will be asked for the password. They will supply it and connect. Those hackers next door who don't know the strong password won't log in.

CharlesA is right on target, as usual. I'll subscribe and chime in if needed, which I doubt.

We now return you to our regularly scheduled penguin.

---

### Post by KegHead on 2012-11-21
Hi!

CharlesA  and chilli555 it worked!

You've restored my faith in the Ubuntu forums!

KegHead

---

### Post by chili555 on 2012-11-21
I'm glad it's working. Now I know I can call on CharlesA when I get stuck!

Have fun!

---

### Post by KegHead on 2012-11-21
Hi!

Follow up question.

Do I need a hardware and software firewall?

Thanks!

KegHead

---

### Post by chili555 on 2012-11-21
> **KegHead said:**
> Hi!

Follow up question.

Do I need a hardware and software firewall?

Thanks!

KegHeadCharlesA will probably chime in here. I recommend both. Your router is undoubtedly a hardware firewall. Generally, the firewall is set to ON by default, but you might poke around in the administration pages and the manual of the router just to confirm it.

The firewall in Ubuntu is configured easily with ufw:```
man ufw
```At a minimum, I'd suggest:```
sudo ufw enable
```

---

### Post by KegHead on 2012-11-21
Hi!

I've done both.

Thanks!

KegHead

---

### Post by CharlesA on 2012-11-21
> **chili555 said:**
> CharlesA will probably chime in here. I recommend both. Your router is undoubtedly a hardware firewall. Generally, the firewall is set to ON by default, but you might poke around in the administration pages and the manual of the router just to confirm it.

What they said. ^

You should already have one on your router, but it doesn't hurt to run one on the machine itself.

---

### Post by KegHead on 2012-12-06
Hi!

Just a quick follow question:

I have soft and hard firewalls.

I have wpa2 protection.

Do I need to use a VPN at home or just on the road?

Thanks in advance.

KegHead

---

### Post by chili555 on 2012-12-06
More security is always better than less, however, I feel very secure at home with no VPN and a strong WPA2 password. A strong password is, in my opinion, more than the shortest eight characters, not a part of your name, address, etc. and not likely to be in a crackers dictionary; obviously not 'password,' 'supervisor,' etc. On the road, I avoid, if at all possible, logging in to sites where I must give my bank or credit card details. A cheap motel in Flagstaff is no place to check my investment portfolio!

---

### Post by KegHead on 2012-12-06
Hi!

Thanks for your reply!

I feel pretty safe now.

LOL copy the Flagstaff!

KegHead

---

### Post by chili555 on 2012-12-06
> **KegHead said:**
> Hi!

Thanks for your reply!

I feel pretty safe now.

LOL copy the Flagstaff!

KegHeadA few months ago, we rented a vacation cabin where the wireless encryption was WEP and the password was the *_phone number_* ! That meant anybody could join the network that had access to a local telephone directory! I changed it to WPA2 and a strong password immediately and then changed it back before we left at the end of the vacation. Sometimes a geek has got to take matters into his own hands.

---

### Post by KegHead on 2012-12-06
Yup!

a friend works for a "major" league company.

they had a demo comparing wpa /wpa2.

someone hacked the wpa within two minutes!

demo was onsite, hacker was someone-somewhere.

wpa2 seems to be the de facto standard.

KegHead

---

### Post by KegHead on 2012-12-07
Hi!

Follow, follow up!

I use an N7 remotely in my house, wifi analyzer shows me channels 12,13 & 14 are a better fit, rather than channel 1.

What gives?

KegHead

---

### Post by CharlesA on 2012-12-07
Depends on what wireless traffic is around you.

Most of the routers I have seen have a setting that lets it pick the best channel. I know DDWRT does this.

---

### Post by KegHead on 2012-12-07
Hi!

I have a choice of 11 channels.

I'm on "1".

Are there any routers w/channels 12, 13 & 14?

KegHead

---

### Post by CharlesA on 2012-12-07
Yes, but they aren't allowed to be used in America.
[http://en.wikipedia.org/wiki/List_of_WLAN_channels](http://en.wikipedia.org/wiki/List_of_WLAN_channels)

---

### Post by chili555 on 2012-12-07
> Are there any routers w/channels 12, 13 & 14?Sure, in Japan. And in Europe, there are channels 12 and 13. But here in the USA, we are limited to channels 1-11 by FCC regulation. They set channels for all kinds of devices to prevent interference, although that only sort of works. We ideally don't want buzz from your wireless on our cordless or cellular phones and we sure don't want a 747 landing in our driveway because it thought your radio beacon was LAX.

Taking your laptop or iPad to Japan? Have fun! Moving with your laptop and router to France? Have fun! Buying a used router from Europe? Have fun!

A fascinating subject, by the way.

---

### Post by KegHead on 2012-12-07
Hi!

I'm just curious as I set up my router w/wpa2 I've been learning a lot!

KegHead

---

