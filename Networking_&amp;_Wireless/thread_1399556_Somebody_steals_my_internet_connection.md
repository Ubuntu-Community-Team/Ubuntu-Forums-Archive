---
title: "Somebody steals my internet connection"
date: 2010-02-05
forum: Networking &amp; Wireless
---

### Post by zgembo on 2010-02-05
Hi everybody,
I have one computer with Ubuntu 8.10 and router connected to it (wired). Another computer is Win XP and it is connected to router wireless. My concern is that somebody from my neighbourhood steals my connection because I see that  my internet usage is very large, much larger then before when I didn't have any router.
How can I set security options for the router in order to prevent other people using my connection? 
I found on google something but I can not even start my network-manager](*,)
What I tried didn't work.
When I go to System->Administration I don't see Network.:-k
Where is it?

---

### Post by mushwars on 2010-02-05
you need to enable encryption with a key for your wireless. go on your windows xp computer and type in your df gateway ip address and log into your router, then go to wireless settings and turn on wpa/psk encryption.

---

### Post by Robster2 on 2010-02-05
The problem you have is not in Ubuntu it is in your Wireless  Modem router.

You must have setup information that came with your Wireless Modem.

What you are looking for is setting up WPA (WEP is much weaker but better than nothing) and you must set up a password.

You must setup the password on the every computer that uses your WiFi.

One final thing make the password some thing good don't use some thing like "Password"

---

### Post by zgembo on 2010-02-05
Thank you, I will try that.
How about network-manager , how can I start it?

---

### Post by 2hot6ft2 on 2010-02-05
> **zgembo said:**
> Thank you, I will try that.
How about network-manager , how can I start it?
On Ubuntu network-manager is in the top right panel near the clock you can left click or right click, each giving you different options.
See pic below...yours may look a little different due to themes and other things running but I drew an arrow to it on mine.

If you want to generate some good strong WPA keys so it will take them a long long time to try and crack it you should check out this page:
[http://help.ubuntu.com/community/StrongPasswords](http://help.ubuntu.com/community/StrongPasswords)

You can go 63 characters long for WPA so see the part that discusses it.

---

### Post by 2hot6ft2 on 2010-02-05
Change the routers login user name and password as well. Otherwise they can figure out what router you have and log onto it and change things locking you out of it as well as connecting to your service.

Like has already been said don't use WEP it can be cracked in just a few minutes WPA Personal or WPA 2 Personal will be enough to make them go elsewhere.

63 character WPA will secure it good enough to keep most people out. Use the link I gave you since it's a pain to try and count 63 characters let alone making it real strong at the same time.

Save it somewhere so you can copy and paste it in where you need it.

---

### Post by Psumi on 2010-02-05
> **2hot6ft2 said:**
> Like has already been said don't use WEP it can be cracked in just a few minutes

Most devices like printers/ etc. require WEP though (especially the PSP.)

---

### Post by mushwars on 2010-02-05
looks like to start network-manager you cant just /etc/init.d/network-manager start you have to do sudo service network-manager start. then if you still dont see it do ALT + F2 and type nm-applet that should start the network manager applet.

---

### Post by 2hot6ft2 on 2010-02-05
> **Psumi said:**
> Most devices like printers/ etc. require WEP though (especially the PSP.)
Our printer uses WPA 2 Personal. I know I had to manually enter it...what a pain.
I don't have a PSP and the OP didn't mention one. But if I did and it did require WEP I would create another network for it in the router and lock it's MAC to that network and seriously restrict it's access.

Or use a second router connected to the first one and unplug it when not in use as well as restricting that routers access to just what the PSP had to have and assigning an IP to it's MAC address.

Either that or I would throw it away.
:popcorn:

---

### Post by Psumi on 2010-02-05
> **2hot6ft2 said:**
> Our printer uses WPA 2 Personal. I know I had to manually enter it...what a pain.
I don't have a PSP and the OP didn't mention one. But if I did and it did require WEP I would create another network for it in the router and lock it's MAC to that network and seriously restrict it's access.

Or use a second router connected to the first one and unplug it when not in use as well as restricting that routers access to just what the PSP had to have and assigning an IP to it's MAC address.

Either that or I would throw it away.
:popcorn:

And I just learned my HP 6500 Wireless printer takes WPA2 passphrases, yay.

But yeah, the original PSP design (1000, 2000, 3000) all require WEP, and I think the Go might as well.

The PS3 however, as odd as it may be, can use WPA if I recall. This also is the same for Nintendo DS and wii:

The DS can't use WPA, only WEP; and the Wii is restricted to use WPA2 AES (can't can't use Tkips or whatever the heck it is.)

---

### Post by 2hot6ft2 on 2010-02-05
> **Psumi said:**
> And I just learned my HP 6500 Wireless printer takes WPA2 passphrases, yay.

But yeah, the original PSP design (1000, 2000, 3000) all require WEP, and I think the Go might as well.

The PS3 however, as odd as it may be, can use WPA if I recall. This also is the same for Nintendo DS and wii:

The DS can't use WPA, only WEP; and the Wii is restricted to use WPA2 AES (can't can't use Tkips or whatever the heck it is.)
There you go ours is a HP DeskJet 6400 series.

Forgot to mention **WPA Personal AES should be used NOT TKIP** since it is more secure than TKIP and if you wnt to use N band and get good speeds then it has to be AES.

Choosing a good router makes a difference since I load up DD-WRT on mine so I have more options like creating more than 1 network.

---

### Post by zgembo on 2010-02-06
Thank you all for your help.

---

### Post by mushwars on 2010-02-06
sure, we are here to help you
if you could mark this thread as resolved :D


come back if you need more help.

---

### Post by zgembo on 2010-02-07
I believe everything is OK now but just to make it sure I want to ask one more question. 
I have changed password for router (so nobody can not take control of it and lock me out), and I made encryption WPA with new passport (12 letters) so everything should be ok. My question is when I turn on the computer with WinXP is it supposed to connect automatically without asking me for password to connect to internet, or I need to type the password every time?
Right now it doesn't ask me for password.

---

### Post by Shark_AtK12 on 2010-04-29
Im sure you already answered your question since this is a few months old but yes, it stores the key will connect automatically until the key changes.

---

