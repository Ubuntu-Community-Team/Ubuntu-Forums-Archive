---
title: "Please help????"
date: 2011-01-21
forum: Networking &amp; Wireless
---

### Post by moonrise333 on 2011-01-21
Ok, so I'm a total noob when it comes to computers so if you please speak english, I'd be really grateful! I run a HP G60-127NR laptop and my wireless was working beautifully as of 30 minutes ago. But my finger accidently hit the wireless button and the wireless was disabled. I've tried everything from network tools to hitting the wireless icon on the top toolbar. However, when I right click the icon, the option for enabling wireless is blacked out. I've also tried frantically hitting the wireless button on my laptop over and over again to no avail. Please help!!! :'(

---

### Post by dheerajrav on 2011-01-21
Go to System->Administration->Additional Drivers and see if the wireless propriety driver is enabled

---

### Post by moonrise333 on 2011-01-21
It said "no proprietary drivers are in use on this system."

---

### Post by Rubi1200 on 2011-01-22
Did you try restarting?

Also, when you do run this command in the terminal (Applications > Accessories > Terminal):

```
ifconfig
```

---

### Post by moonrise333 on 2011-01-22
I've tried restarting numerous times and I just typed in that code. I'm on my phone right now and don't have any computers running internet. I'm desperate. what do I do next?

---

### Post by moonrise333 on 2011-01-22
Bump

---

### Post by moonrise333 on 2011-01-22
I've been googling around and it said to type in "iwconfig" and I got 
Lo: no wireless extensions
Eth0: no wireless extensions
Wlan0: IEEE 802.llabgn ESSID: off/any
              Mode:managed access point:not-associated tx-power = off
              Retry long limit:7 RTS thr: off Fragment thr: off
              Power management: off
then I typed in "sudo ifconfig wlan0 up" and it said "operation not possible due to RF-kill"

Does that help at all??

---

### Post by TBABill on 2011-01-22
Can you try ```
sudo rfkill unblock all
```

---

### Post by moonrise333 on 2011-01-22
Just tried it and it didn't work.

---

### Post by TBABill on 2011-01-22
There has to be a way to turn the wireless device back on again. The output of iwconfig shows it as off. Do you have a Fn (function) key combo that turns it back on? Do you have a book to look that up in if it's not easy to identify on the keyboard? My Dell, for example, just requires you to hit F2 and it turns it on and off.

---

### Post by moonrise333 on 2011-01-22
I accidently hit the wireless toggle button before this stuff started happening and it turned amber, indicating that it was off. I tried posing it again but it won't turn back on. I do have an fn key and I tried holding that and pushing the button and it still wouldn't turn on. :,(

---

### Post by moonrise333 on 2011-01-23
Bump

---

### Post by lisati on 2011-01-23
According to the [manual]("http://h10032.www1.hp.com/ctg/Manual/c01540485.pdf") for your laptop the wireless button can be used to turn the wireless on or off, no mention of using it with the Fn key. Does it change colour when you press it?

Edit: Do you still have a copy of Windows on your machine so you can test the wireless?

---

### Post by moonrise333 on 2011-01-23
It does not change color when I press it.
And I no longer have windows on the machine.

---

