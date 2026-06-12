---
title: "help with Ubuntu  internet connections (I am giving UP)"
date: 2011-07-01
forum: Networking &amp; Wireless
---

### Post by moisea on 2011-07-01
hello i am trying to use Ubuntu for the second time (tried 10 years ago got headaches and no help went back to windows) but I am having  headaches connecting to the internet using a wireless dongle which works without a problem with windows XP (I have a dual boot PC Dell Optiplex gx280) but no connection with Ubuntu. Installed and re-installed many times no success. Need help or I might go back to Windows for good. i would like to use Ubuntu but gets sometimes tricky and easy to understand help is hard to get. Suppose to connect to the internet after installation automatically but NO and even after manually setting it up.
Many Thanks.

---

### Post by tommpogg on 2011-07-01
Could you provide more information about how you are trying to connect to your wireless network?
I suppose you are using the graphical interface. Can you find your wireless network from your PC? Is it a DSL connection?

There are lots of thread on this topic. Have you already taken a look at them?

---

### Post by moisea on 2011-07-01
thanks tommpogg, for your reply. yes I am using the graphical interface and it is a DSL connection from virgin media. yeah i did look at some of the threads but did not help.

---

### Post by regala on 2011-07-01
> **moisea said:**
> thanks tommpogg, for your reply. yes I am using the graphical interface and it is a DSL connection from virgin media. yeah i did look at some of the threads but did not help.

well, what is the type of wifi network ? open, wep, wpa ? do you select the correct authentication method if wpa ? are you sure of the password ?

br,

Mathieu

---

### Post by moisea on 2011-07-01
yes did all that wpa2 authentication ssid but nothing works

---

### Post by collisionystm on 2011-07-01
So assumingly you can see your wireless network. And it has a WPA2 authentication.

Ubuntu is famous for problems with authenticating with anything other than WEP. It all comes down to the driver being used on the wifi card.

I suggest changing your security type on the router to something else.

Although, its a bit ironic that WEP works the best with ubuntu, but ubuntu makes it so easy to hack  into someone elses WEP enabled network lol.

---

### Post by MooPi on 2011-07-01
We will probably need more than whether or not your trying to configure wep or wpa. How about some info on your device so we can narrow down the problem correctly.
Try these commands from a terminal. 
```
lsusb
```
```
lsmod
```
```
iwconfig
```
If you could please post the results of each of those commands

---

### Post by georgelab on 2011-07-01
> **collisionystm said:**
> So assumingly you can see your wireless network. And it has a WPA2 authentication.

Ubuntu is famous for problems with authenticating with anything other than WEP. It all comes down to the driver being used on the wifi card.

I suggest changing your security type on the router to something else.

Although, its a bit ironic that WEP works the best with ubuntu, but ubuntu makes it so easy to hack  into someone elses WEP enabled network lol.

Since I started using Ubuntu (my first flavor was Dapper Drake) I had no problems with wireless authentications, including wpa and wpa2... It works fine for me in my Dell notebook, my desktop workstation and my Acer netbook, all of them with different wireless cards.

I never had to set up wep authentication in my router to fix connection issues. Maybe I am just lucky but I think that Ubuntu wifi problems are easily fixed by using the right driver and the right configuration.

Regards,

---

### Post by moisea on 2011-12-28
Hi back again with a another approach. Bought the Tenda w322p pci wireless adapter installed it works fine on xp without any problem HOWEVER with Ubuntu 10.04 it shows that there is connection BUT cannot browse the internet (even though it says connected to the network).
How do i fix this new Issue please. thanks.

---

### Post by zuerston on 2011-12-28
> **moisea said:**
> Hi back again with a another approach. Bought the Tenda w322p pci wireless adapter installed it works fine on xp without any problem HOWEVER with Ubuntu 10.04 it shows that there is connection BUT cannot browse the internet (even though it says connected to the network).
How do i fix this new Issue please. thanks.


**EXACT SAME** problem I am having!!  I have never been able to connect **THIS **computer with **USB WIFI using Ubuntu!**
see my thread I just posted today [http://ubuntuforums.org/showthread.php?p=11571236#post11571236](http://ubuntuforums.org/showthread.php?p=11571236#post11571236)

I have been here at the forum before trying to fix this but no answers!  I was boored today so I thought I would try it again but.....................?
I once ordered a PCI USB adapter to try on Ebay but the Chinese dealer never sent it so I forgot that too!  But my USB ports work fine with everything else,so I just don't know, not hard to give up on this one is it?  No idea what it could be at all, I have never had any problems with WIFI before with other computers.

---

