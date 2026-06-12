---
title: "Injection working but Freeze when connecting to Network"
date: 2011-05-30
forum: Networking &amp; Wireless
---

### Post by menguin on 2011-05-30
Hi Guys i'm having a quite strange problem:
I am currently playing around with aircrack-ng on my Asus Eee Pc 901, OS is Ubuntu 10.10 i386 Netbook Edition.
The Netbook has a built in WLAN interface (wlan0), i think its a Ralink but i dont use this one. (Everything is working with that interface, even injection which i find a bit surprising, but of course the sensitivity is weak)

The Interface that bothers me is a TP-Link WN-422G USB Stick (wlan1).. It is important to mention that i possess version 2.3 of this Stick, version 1 requires the zd1211rw driver, the second version needs the ath9k_htc instead.. I needed days to realize that >_>

Out of the box the stick worked with Ubuntu 10.10, i was able to connect to wireless networks, monitor mode worked as well, but packet injection with aireplay didnt work.
So i downloaded compat wireless 2011-05-11, extracted it, applied the "channel-negative-one-maxim.patch" patch (Had to do it by hand, and i dont even know if this patch is actually even nessecary) compiled and installed it. No errors, everything went well, i also put the htc_9271.fw firmware in the /lib/firmware directory.
I also typed this in my shell before installation:
CONFIG_ATH_COMMON=m
CONFIG_ATH9K_HW=m
CONFIG_ATH9K_COMMON=m
CONFIG_ATH9K_HTC=m
because this site: [http://wireless.kernel.org/en/users/Drivers/ath9k_htc](http://wireless.kernel.org/en/users/Drivers/ath9k_htc) tells me to so (or do i need to enter it somwhere else o.o ? )

Now injection was working fine and i was able to crack my own AP Wink

BUT, here it comes:

I can detect all networks normaly but if i want to connect to one with this stick the system freezes. Completely. No matter if the network is encrypted or not.. No matter if i do it right after starup or if i had the stick in monitor mode before.
I tired to do it manually:
"iwconfig wlan1 essid SkyNet" - this step worked
"ifconfig wlan1 192.168.1.8 netmask 255.255.255.0" - at this point the system freezes. HDD Led stays dark, WLAN Stick LED stays on, no mouse movement possible, nothing.

Of course the same happens if i try to connect using the network manager..
Syslog doesnt show anything strange (to me), here the last few lines before the system crashes:
[http://pastebin.com/1PE3s9Dq](http://pastebin.com/1PE3s9Dq)

For some reason this country regulation thing says CN, Canada? Actually i'm living in Austria, could this be the Problem?
What coud cause that? I could of course use the second interface but i dont want to because its insensitive and i wont allow the USB interface not to work!  Grin
Can i somehow load the original driver that came with Ubuntu 10.10, ath9k_htc as well i think, if i want to connect to a network?
Or how can i make both injection and managed mode working?

Almost forgot to mention another important thing: the exact same freeze occours on my normal desktop PC with Backtrack 4 R2 and this stick! I THINK (im can no longer remember^^) i also used the same compat wireless version, the same patch and firmware! Additionaly if Backtrack freezes the Capslock, Numlock and Roll LED on my Keyboard start blinking!

Do you need additional logs or information to help me?
Thank you guys! And please spare me for any spelling/writing/whatever errors :>

---

