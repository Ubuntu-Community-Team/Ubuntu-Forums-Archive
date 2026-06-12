---
title: "Ubuntu 9.04 Jaunty Jackalope DSL/PPPoE problem"
date: 2009-05-03
forum: Networking &amp; Wireless
---

### Post by ayonkhan on 2009-05-03
After I setup my Internet on Ubuntu 9.04 Jaunty Jackalope via Network Manager (GUI)/Terminal(sudo pppoeconf), my Internet works like a charm, but after I reboot my computer, I cannot connect to Internet further. Even using sudo pppoeconf in terminal again. Please note that, on Ubuntu 8.10 Intrepid Ibex, I haven't faced this problem.

---

### Post by mikhail_lem on 2009-05-03
Same problem here. I type "sudo pon" and i get a message saying "Unrecognized option /dev/modem"

Helpppp!!!

---

### Post by ayonkhan on 2009-05-05
Firewall!!! :P
How to disable firewall? Let's try this way.

---

### Post by NorthernForest on 2009-05-05
> **mikhail_lem said:**
> Same problem here. I type "sudo pon" and i get a message saying "Unrecognized option /dev/modem"

Helpppp!!!

If you want to connect to an dsl-connection, you have to type "sudo pon dsl-provider". Nonetheless it's strange why jaunty doesn't connect automatically during boot-time anymore.

---

### Post by tarntow on 2009-05-06
> **NorthernForest said:**
> If you want to connect to an dsl-connection, you have to type "sudo pon dsl-provider". Nonetheless it's strange why jaunty doesn't connect automatically during boot-time anymore.

yes, same here, now i have to type 'pon dsl-provider' just like windows, no more automatic internet connection! :(

---

### Post by wiznillyp on 2009-05-06
> **tarntow said:**
> yes, same here, now i have to type 'pon dsl-provider' just like windows, no more automatic internet connection! :(Couldn't you just add that to your startup script?

---

### Post by Mugsy323 on 2009-05-07
Same problem here. I connected once, then never again. :(

I've tried configuring "DSL" under "Network Connections". I've tried "pon dsl-provider". Even "sudo pppoeconfig" doesn't work anymore. I'm stumped (I had everything working just fine under Hardy, so I'm none too pleased with Jaunty right now.

My setup:
DSL direct connected. Not wireless. Installed 9 clean (reformat), not an upgrade.
Using XP to type this from same computer, so hardware is working.

---

### Post by ayonkhan on 2009-05-08
> **wiznillyp said:**
> Couldn't you just add that to your startup script?

How to add?

---

### Post by ayonkhan on 2009-05-12
```
option rfc3442-classless-static-routes code 121 = array of unsigned integer 8;
```
```
rfc3442-classless-static-routes, ntp-servers;
```

I have removed above lines from **/etc/dhcp3/dhclient.conf** & my internet is working well. I did this because I don't find those lines in Felicia. But finally my internet is working. I don't know how long it will work. One more thing I don't know is this a solution or not! So if anyone can then please let me confirm.

---

### Post by shazoor on 2009-05-12
Try this:

click NteworkManager Applet > VPN connections > Configure VPN.
Under DSL tab select your connection and click Edit.
Under IPv4 settings tab select some other method [Automatic (PPPoE)].

Hope this would work.

---

### Post by ayonkhan on 2009-05-13
Automatic (PPPoE) - already set by default.

---

### Post by R3M3 on 2009-05-13
Take this with a grain of salt, as I am a clueless noob when it comes to networking, but you might want to try using the network-admin program from the gnome-network-admin package to set up your networking instead of NetworkManager. (After install it would be found as System->Administration->Networking in Gnome, or Applications->System->Network in xcfe)

I had a similar issue with my Jaunty upgrade, and found that changing eth0 from "roaming mode" to "dhcp" fixed it. Your mileage will vary, though, based on your system configuration and what DSL modem you're using.

---

### Post by alan sawyer on 2009-05-14
I had the same problem and found connecting was automatic only if I used the login window. It's a little easier entering a user name and password than opening a terminal, entering sudo pon dsl-provider and then entering a password. I prefer the automatic login, but will live with this solution until a fix is found.

---

### Post by mickeld on 2009-05-14
I am using Xubuntu 9.04 and I can access the internet from XP but not from Xubuntu. The network manager shows me as being connected but I cannot access the internet. Also my volume does not work. It seems to me as Ubuntu/Xubuntu has some pretty major flaws it needs to address before it can be considered "usable" by the abso-friekin-lute noob like me! ANYONE know how to DOWNGRADE to 8.10 without erasing Xubuntu? I do not wish to lose my music etc.

---

### Post by Prelude203 on 2009-05-28
i dont know how to "fix" the problem here but i do know how to get you guys online.

heres what i did...

i removed the packages:

network-manager

and 

network-manager-gnome

THEN:

(If you havent already, make a new pppoe connection by doing sudo pppoeconf)


then go to terminal and do 

sudo poff dsl-provider

then 

sudo pon dsl-provider



YOU WILL HAVE TO DO THESE TWO COMMANDS EVERY TIME YOU LOGIN AFTER YOU RESTART YOUR COMPUTER... (sudo poff dsl-provider  and   sudo pon dsl-provider)



NOTE: i dont know if you had to remove the network manager packages but thats how i did it...also i dont know if it was too smart to remove them becasue when the developers make an update to fix this you probably wont get the update for network manager..but thats how im getting my connection to work..hope it works for you guys. :D

---

### Post by jfbilodeau on 2009-05-28
Hope this helps someone. I spend three hours trying to make sure that PPPoE started at boot time on my mothers computer.

Turns out, I had to change:
```
iface eth0 inet manual
```
to
```
iface eth0 inet **dhcp**
```
in /etc/network/interfaces

Works like a charm! :guitar:

J-F

---

### Post by ayonkhan on 2009-05-29
May be a Kernel bug.

---

### Post by Chris_no on 2009-05-29
If you want to have your commands started at boot just add them to the
/etc/rc.local file. Then every time you start ubuntu your command will run.

---

### Post by Habboblob on 2009-05-29
This is very weird. Ever since the release of Ubuntu 9.04 J I have seen many internet connecting problems. I myself had experienced that shortly after I installed 9.04 J that my wireless was no longer working, until now it is magicly working! I haven't done anything, it just started working by it's self!

---

### Post by FishyFantasy on 2009-05-29
I've heard that (launchpad.net) if you use pppoeconf in Ubuntu 9.04 Jaunty, you cannot connect to the internet. You must use Network Manager ONLY to configure your internet settings. 

Try this:

```
sudo apt-get --purge remove pppoeconf
```

I've tried it and it works. I can connect to the internet now. 


Hope this helps and sorry for my bad english =/

---

### Post by ayonkhan on 2009-06-28
Updating Kernel fixed this issue for me.

---

### Post by ario on 2009-07-15
Please don't do like this. I had the same problem as you, Then I road your post and then upgraded my kernel. But this was not solved my problem.
So now you have writen "It solved my problem so somebody there in canonical company may think that this big problem is solved and no need to work on it.
I will report a bug. Because I've installed ubuntu and can not make my linux to connect my LAN connection (Wiered connection) at boot time.
By the way thank you.

---

### Post by ario on 2009-07-15
Thank you "jfbilodeau"
Your Solution solved my problem. I entered Alt+F2 and then "gksudo nautilus" then my password, Then opened a file manager windows there I searched for "/etc/network/interfaces" opened it by default text editor and then changed "manual" to "dhcp" as you said.
It worked for me too like a charm;)

---

### Post by ZhuaSD on 2009-07-21
Hi thanks to the posters here, I also found that the system changed somehow after installing, I configured the pppoe and then restarted, restarting changed everything and pppoe was not working.

Anyway, I followed jfbilodeau's advice, and now everything works, but its a little messed up.

When I start up, plog returns nothing at all, no data.  And then I just need to 
```
sudo poff dsl-provider
```

and then 
```
sudo pon dsl-provider
```

and everything will work.  

So its starting  but somehow not available to me until I re-start it.

This is pretty buggy actually.  <b>My network icon on the desktop has a red x in it, as if telling me a cable is unplugged, and if I go into the dialog there is no connection listed at all. Nothing in any of the columns.</b>

But the connection is fine...

All I can say is if plog gives you nothing then try this fix.  Remember, I already did jfbilodeau's fix from this thread. Other than that, I haven't done anything but run pppoeconf (like 15 times ;-)

[Note: My pppoe connection was buggy before, on 8.04]

---

### Post by ubu-lemon on 2009-08-25
I did :  System-->Preferences--->Startup applications and there removed Network manager from the list.
Since I'm only a happy user and no Linux wizard I don't know if that's a good thing, but it did work for me. (if anyone can tell me if this is a good or a bad thing, be welcome)

---

