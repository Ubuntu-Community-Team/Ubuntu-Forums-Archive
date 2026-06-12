---
title: "Configuring the Huawei E220 modem"
date: 2009-08-23
forum: Networking &amp; Wireless
---

### Post by ExtremeCoolSha on 2009-08-23
Hello Everybody!

This is my 1st post in the Ubuntu Forum. If this is a usual question:Excuse me!!

I want to configure the Huawei E220 modem I recently bought in Ubuntu. I read lot of detail documents in the internet. All were interesting and explaining the wvdial.conf file. The problem I have is that, the file asks for the phone # to dial, username & a password. I don't have these informations since my ISP didn't provide those.
It works perfectly in Windows, in which above informations are not needed, because when plugged in Windows, a software installation launches, which does the job to connect to the internet.
So, is there a way to configure the modem to connect to the internet without those informations. Because my ISP refuses to provide those, when I called there customer services.

---

### Post by GeorgeVita on 2009-08-24
Hi **ExtremeCoolSha**,
with newer versions of Ubuntu most people is using network manager which includes a list of providers to choose and all the setup needed.

For your info, most times phone# is *99# (GPRS/3G) or #777 (CDMA) and any username any password. The most important is APN (name of service from provider) which usually is "internet" but some providers have more than one. Choosing the wrong one may COST you A LOT of money! As you are the "customer" they must provide you info to keep working. Did they sold you also the Operating System?

Actions: Check if you can use network manager and setup properly. Ask again all info (APN, username, password). Post here your /etc/wvdial.conf file. Post info about country, provider, type of connection (prepaid internet, contract, etc) if more than one from the same provider.

Regards,
George

---

### Post by ExtremeCoolSha on 2009-08-24
Thanks Goerge for your info. I didn't sold me the OS. First I'll try to work through your step & if fails I'll try to contact the ISP for the info again & come back to you for further clarifications.

---

### Post by ExtremeCoolSha on 2009-08-25
My service provider is Dialog GSM in Sri Lanka. I found the APN as well. But still I don't have the username and the password. As you stated in you post I used a username and password as my wish. But still I coudn't connect. The Network Manager request some further data as well, such as Network etc. What about that? I used both *99# and #777 as the phone #, but no result yet.

---

### Post by GeorgeVita on 2009-08-25
Hi, **ExtremeCoolSha**, searching ubuntuforums for 'Dialog GSM Huawei E220' found your [2nd thread]("http://ubuntuforums.org/showthread.php?t=1248538") about the same subject.

I am posting there to have a better summary: [http://ubuntuforums.org/showthread.php?t=1248538](http://ubuntuforums.org/showthread.php?t=1248538)

---

