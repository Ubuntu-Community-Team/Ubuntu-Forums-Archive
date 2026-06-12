---
title: "Calling Network Manager from a script?"
date: 2009-09-25
forum: Networking &amp; Wireless
---

### Post by ninja123 on 2009-09-25
Hi All,

I am using ubuntu 9.04.

I use network Manager to connect to my wireless. Since I had get static IPs working(eth0 and an alias eth0:1) and the network manager would not get this IP alias to work, I decided to retain NM for wireless and included my eth in /etc/network/interfaces file. Works good.

However what bothers me is, if I include wlan0 details into the /etc/network/interfaces, wlan0 doesnt work :(

But that is still ok as now wlan does work with NM.


I have some scripts that disconnect network using ifconfig, iwconfig commands. Somehow, wlan although gets turned off using this script does not get turned on at all.

I was wondering if you could use some command in this script to called NM to do this.

Is that even possible??

Now what I do is, after the script turns wlan down, i manually  connect wlan using NM on menubar :( :(  which is not the desired way.




Thanks a lot

---

### Post by kay-man on 2009-09-25
I think it's probably more worthwile to have another go at trying to control everything from /etc/network/interfaces.

It took some doing, but I managed to get rid of network manager altogether.

I use a ralink RT2500 card, and connect to my WPA protected wireless network using wpa_supplicant.

I think NetworkManager is only useful on laptops. What kind of pc are we talking about, anyway?

---

### Post by ninja123 on 2009-09-25
I am using a DELL laptop.

Yes, I guess using the /etc/network/interfaces is a better idea.

But I haven't been able to get that working.

In my file I added:

auto wlan0
iface wlan0 inet dhcp


And after I restarted network. I used iwconfig to give essid, key etc and used 

ifconfig wlan0 up 

followed by

dhclient wlan0


But it would simply not get associated with the router :(

It works perfectly with NM though..

---

### Post by kay-man on 2009-09-25
Have you tried

```
iwconfig wlan0 ap <access point MAC>
```

to see if you can connect? Normally it should be able to find an acceess point, but this will direct your interface to a specific access point

---

### Post by ninja123 on 2009-09-25
I tried it but it doesnt work either.

I had a look at my dmesg which shows that although my wlan0 gets associated, immediately it gets dissociated.


Any idea?

---

### Post by kay-man on 2009-09-25
What kind of adapter do you have? Is it one that should word, or one with known issues, such as mine used to have? :)

If network manager can do it, it must be possible.

Also, what kind of encryption does you wifi setup use?

Have you tried to disable that and see if you can connect then?

---

### Post by ninja123 on 2009-09-25
I have this broadcom b43. At the moment no encrytion. Once it works I thought of going for WAP.

---

### Post by kay-man on 2009-09-25
Did you see this?

[http://ubuntuforums.org/showthread.php?t=949198&highlight=broadcom+b43]("http://ubuntuforums.org/showthread.php?t=949198&highlight=broadcom+b43")

---

### Post by shredder12 on 2009-09-25
> **ninja123 said:**
> 
In my file I added:

auto wlan0
iface wlan0 inet dhcp


And after I restarted network. I used iwconfig to give essid, key etc and used 

ifconfig wlan0 up 

followed by

dhclient wlan0


But it would simply not get associated with the router :(

It works perfectly with NM though..

Did you try providing the essid and key in the interfaces file itself..

If you are using WEP then try something like this
```
auto wlan0
iface wlan0 inet dhcp
wireless-essid essidname
wireless-key1 key_value
```

If you are using WPA then you may try

```
auto wlan0
iface wlan0 inet dhcp
wpa-ssid essidname
wpa-psk hex_pass_key
```

I am not sure about WPA bcoz.. i don't use it.. but since you are running without enryption now... i guess the first one should work for you..without the "wireless-key" line..or you  may try leaving the key_value field blank.
     I am not sure about the correct way here.. I jst hope some trick works for you..

---

