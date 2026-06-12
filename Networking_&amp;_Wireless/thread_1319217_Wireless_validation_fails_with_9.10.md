---
title: "Wireless validation fails with 9.10"
date: 2009-11-08
forum: Networking &amp; Wireless
---

### Post by greencarpet on 2009-11-08
Hi,
I have a problem using my wireless connection since upgrading from 9.04 to 9.10. I am using a wireless USB adaptor (VIGOR N61) which sees the wireless networks around but is unable to connect, stopping a validating authentiation (Using WPA2). After reading some other threads I installed Wicd but the problem persists. I have also tried reducing the security to WEP which will then validate but doesn't obtain an IP address. 
What could be preventing the handshakes from working properly? All my other computers are able to connect seamlessly it is just the 9.10 machine that is failing - should I downgrade?
Thanks.

---

### Post by GreenEU on 2009-11-08
I'm pretty new to Ubuntu so can't help - but I have run Mint 7 and 9.04 on this computer as dual boot with Windows vista and now Windows 7, and agree - there seem to be huge issues with the networking connection in 9.10. I suggest you go scout through some of the threads on here. I'll say this - I've used some of the solutions but the problem comes back again when I log in. So far, only abandoning the wireless and using ethernet worked. Not a good place to be!

---

### Post by greencarpet on 2009-11-08
Thanks for the reply, I've had a read around and can't seem to find much in the way of a solution which is a real shame. I think that I'll downgrade and wait for 9.10 to bed in a bit more.

---

### Post by iponeverything on 2009-11-08
> **greencarpet said:**
> Thanks for the reply, I've had a read around and can't seem to find much in the way of a solution which is a real shame. I think that I'll downgrade and wait for 9.10 to bed in a bit more.

You might try removing and reinstalling network-manager.. 

I think it's:
```
dpkg --purge -e network-manager
```

You will need to have the debs saved locally on the machine to reinstall them..

---

### Post by greencarpet on 2009-11-08
Hi,
I have removed and reinstalled network manager but without success. The problem occurs with both wicd and network manager :(

---

### Post by greencarpet on 2009-11-08
Here's an update.
I restarted this machine, pressed escape in grub and selected the older version of the kernel (2.6.28-14 if I remember correctly) which allowed me to connect wirelessly but killed the trackpad. I am not worried about the trackpad because I am sure I am getting on the right track. Can anyone tell me which if there is a way of disabling the newest drivers in the kernel?

---

### Post by dclark16 on 2009-11-09
I'm having a similar problem, except mines stranger. If I connect to my wireless downstairs it works fine, if i go upstairs it stays connect but the internet doesn't work, and eventually drops out altogether, the signal strength is at about 70%. If i try to connect upstairs (using wicd) it says "failed to connect, unable to obtain ip address". And its not limited to my wireless router, if i go to my mates house same issue. It seems that unless i have 100% wireless signal i cannot connect. I've googled it around but no one seems to be having the same problem, some people are just unable to connect full stop, but i can (when im downstairs, kinda defeats the object of wireless and a laptop if you have to be in one room), ive reinstalled 9.10 twice, Ive tried various wireless utilities and fixes and none of them seem to have any affect. I have spoken to my Linux tutor and he says he's never come across anything like it. i would really appreciate any help.

edit wired works fine btw

---

### Post by iponeverything on 2009-11-10
try fixing the rate at 10 Mb to see if helps.

---

### Post by dclark16 on 2009-11-10
I cant seem to fix the rate at 10M, not quite sure if im using the right command or not:

sudo iwconfig wlan0 rate 10M

Is that the right command?

Thanks

---

### Post by cespinal on 2009-11-18
bump.... there is a lot of people downgrading to jaunty because of this...

---

### Post by rmccardal on 2010-08-20
I too have this issue with a Vigor N61 dongle.

---

