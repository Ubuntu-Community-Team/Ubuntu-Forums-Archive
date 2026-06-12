---
title: "Android 2.2 Hotspot HTC Legend Kubuntu 11.04"
date: 2011-06-24
forum: Networking &amp; Wireless
---

### Post by dochegal on 2011-06-24
Hello!

I'm desperately trying to connect my ASUS UL30A with a Atheros (AR9285) chip to my HTC Legend with Android 2.2 so I can access the Internet over my phone.
Each time I try to connect i get invalid password from wicd (I already removed the network manager, hoping i would work with wicd). I also tried installing some debs (kernel 3, headers, init-tools-3.13) but no luck so far. All the other wireless connections are working properly only the Android hotspot does not.
Noticed that this is not a new problem, but [B]is there a solution yet?
[/B] It would be acceptable if there is a way to connect the Phone via USB and then use it to access the Internet.

greetings

---

### Post by dozycat on 2011-06-24
try barnacle, it uses the wifi works great with windows  xp and ubuntu 10.04.
However there is something...... your android must be rooted.

---

### Post by dochegal on 2011-06-24
Seriously? Thought ubuntu (especially 11.04) is the problem here. The hotspot function came along with Android 2.2 and I can't imagine that there is something wrong.

---

### Post by CaptainMark on 2011-06-24
are you using the wireless hotspot function on the andriod, i have and htc desire and use this feature, double check the settings in the phones menu, you can set any password, it creates a wireless network just as a home router would do, can you access normal wireless networks from your kubuntu pc?

---

### Post by dochegal on 2011-06-24
Yes, it is the function that came with android 2.2. The laptop was able to access all other access points / routers I had the password and IP-settings for. Only with the phone's hotspot I have to face those troubles. I'm sure all the settings are correct. Tried it with and without dhcp set on both devices. As far as I can tell - mostly from researching the web - it is a 11.04 related issue, apparently older versions work.
It is the authentication that takes forever and then fails - wicd says wrong password, network manager just kept asking for it again and again and...

---

