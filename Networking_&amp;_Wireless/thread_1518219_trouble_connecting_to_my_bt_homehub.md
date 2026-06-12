---
title: "trouble connecting to my bt homehub"
date: 2010-06-26
forum: Networking &amp; Wireless
---

### Post by MCL34NS on 2010-06-26
i got ubuntu 10.04 this week but i am having trouble connecting to my homehub. I am on vista right now and am connecting fine.

Network manager does not have an option for 64 bit hex wep keys so i cant do it that way.

i have tried using the command line but it says that there was no dhcp offers recieved.

i am new to ubuntu and linux so any help would be welcome. if you need any info i wil be happy to try and find it out for you to fix my problem

---

### Post by MCL34NS on 2010-06-27
bump

i think ubuntu could potentially pretty good but i cant really use it unless i can go on the internet with it. i really don't know how to sort  it:confused: i might be missing something obvious

---

### Post by grahammechanical on 2010-06-27
Left click on the network manager icon. You should see a list of available networks. Do you see your BT homehub listed there? Select it. You will be asked for the network security key or pass-phrase. I am quoting from an instruction tract provided by my ISP plusnet. It says: "use the WPA-PSK key on the bottom of your modem. The WPA-PSK key is ten characters long and the letters are CAPITALISED."

I was also provided with a sticker that had information on it. From this I have worked out that the WPA-PSK key is also called the WIRELESS KEY. On my modem this ten character key is exactly the same as the WEP (hex) ten character code that is on the bottom of the modem or hub in your case.

Once you have entered this code network manager should remember it and connect to the modem/hub.

I hope this helps. I am new to all this myself. So, don't treat me as an expert.

Regards.

---

### Post by MCL34NS on 2010-06-27
thanks for your advice but Network manager does allow you to select the option for wpa keys. if you go in via  network connection menu it does not even try to connect. If i am doing something wrong please say.

---

### Post by MCL34NS on 2010-06-28
bump

---

### Post by MCL34NS on 2010-06-29
bump

---

### Post by MCL34NS on 2010-06-29
bump

---

### Post by MCL34NS on 2010-06-30
bump

---

### Post by pedro_orange on 2010-06-30
> **MCL34NS said:**
> thanks for your advice but Network manager does allow you to select the option for wpa keys. if you go in via  network connection menu it does not even try to connect. If i am doing something wrong please say.

Hey.

Does this mean you can or can't see your network in the list provided by network manager?

```
iwlist scan
```

If you can't see any networks, are you sure your network device has actually been detected / installed? 

```
lshw -C network
```

If you can see it, is there something strange about your WPA key? Because certain characters need to be escaped with the "\" character. 

Have you tried removing the security on the wireless connection and determining if you can connect to it in this way?

---

### Post by MCL34NS on 2010-06-30
yes i can see my network. I've got a WEP key rather than a WPA key. will that make any difference

---

### Post by pedro_orange on 2010-07-01
Yes the type of network authentication makes a difference. Try using different authentication methods and see what works and what doesn't. Then use the most secure authentication method that works.

---

### Post by brunogirin on 2010-11-29
I just managed to connect using Ubuntu 10.10 so here is what I did.

By default, the BT Home Hub comes with WPA-PSK using an hexadecimal key, rather than an alphanumeric one. Network Manager, as installed on Ubuntu, doesn't have an option to use hexadecimal WPA-PSK keys, it expects an alphanumeric key. In order to fix this, connect to the home hub with a cable, go to the admin web interface ([http://bthomehub.home](http://bthomehub.home)), go to settings -> wireless and change the key to an alphanumeric one. You should be able to connect wirelessly after that.

---

