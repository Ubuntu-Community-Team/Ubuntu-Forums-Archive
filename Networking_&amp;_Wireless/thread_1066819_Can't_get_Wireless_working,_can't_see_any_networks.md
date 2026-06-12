---
title: "Can't get Wireless working, can't see any networks."
date: 2009-02-11
forum: Networking &amp; Wireless
---

### Post by LGP7 on 2009-02-11
Sorry if this is a dumb question or i'm just doing something wrong.  I've never used linux before so i'm just having a little difficulty troubleshooting routine things!

Anyway,  I just installed Ubuntu on my lapttop.  I have a Dell m90 with a Intel Corp PRO/Wireless 3945ABG (rev02) wireless card.  I checked intels site for drivers, but they said it's built in to the kernel(2.6.24) i'm using so i figured it should just be working out of the box.

So when i tried to connect, i just entered in all my network information and figured it would connect right up.  It didn't...then i noticed, it's not even picking up an other networks.  I have the computer at work right now and there should  be around 6 different access points it should see.  It doesn't see any.  In the gui nothing comes up and when i type iwlist scan in the terminal, wlan0 just says No scan Results.

I'm not sure if i'm doing something wrong or what....but any help would be appreciated. 

thanks.

---

### Post by oponto on 2009-02-11
Get you wireless card's name and google it "wlan card xyz ubuntu/linux driver".

---

### Post by LGP7 on 2009-02-11
So upgrading to 8.10 is the solution?  that's really the only thing i could find out of that.

---

### Post by Fire_Chief on 2009-02-11
What version did you install?
Does the Dell have a hardware switch for the wireless card?
You may want to verify that Ubuntu is seeing the wireless card
```
lspci
```
If it does see it, do you have wireless enabled in NetworkManager? (two screens icon in the panel). Right click on it and make sure the Enable Wireless option is checked. Then left click to see detected wireless networks.

Cheers!

---

### Post by superprash2003 on 2009-02-11
also post output of the following commands from the terminal
1)lshw -C network
2)iwlist scanning
3)iwconfig

---

### Post by LGP7 on 2009-02-11
I'm using 8.04.1  I installed it back in november, i just haven't got around to messing around with anything till now.

No, there is no physical switch on the laptop.  The OS does see the wireless card, when i run that command it is the last entry to come up.  That's actually how i found out what card i had in the first place.

yeah i have network manager and wireless is enabled.  When i left click it shows wireless networks but there is nothing underneath it.  


As for posting the results from those commands, i'm on a different computer so i can't cut and paste...so i'll type in what i can

iwlist scanning

lo - doesn't support scanning
eth0 - " "
wmaster0 - " "
wlan0 - no scan results

iwconfig

lo - No wireless extensions
eth0 - " "
wmaster - " "
wlan0 IEE 802.11g ESSID:" " Nickname" " 
      Mode:manged Frequency: 2.412 ghz AP: Not-Associated
      TX-Power = 27 dbm
      Retry min limit: 7   RTS thr:0ff  Fragment thr=2246B
      power management: off
      Link Qaulity: 0 Signal level:0 Noise Level: 0
      Rx invalid nwid:0  Rx invalid crypt: 0 Rx Invalid frag: 0
      Tx excessive retries:0 Invalid misc: 0 missed beacon: 0

---

### Post by Fire_Chief on 2009-02-11
I have the same card in a Lenovo T60 using the iwl3945 driver running 8.10 and it does work out of the box. I was previously running 8.04 and it also worked fine. :confused:

When you did the ```
lshw -C network
```
what module did it say was loaded for the wireless card?

---

### Post by LGP7 on 2009-02-11
module = iwl3945  driver= iwl3945  broadcast: yes

---

### Post by Fire_Chief on 2009-02-11
Ok, so it appears you were onto the best track earlier when you mentioned changing to Ubuntu 8.10.
See this [http://support.uakron.edu/wiki/index.php/Wireless_Setup_on_Ubuntu_8.04_(Hardy_Heron)_with_Intel_3945/4965]("http://support.uakron.edu/wiki/index.php/Wireless_Setup_on_Ubuntu_8.04_(Hardy_Heron)_with_Intel_3945/4965")

But if you really want to stay on 8.04 there is a way to probably make it work.
[http://linuxtechie.wordpress.com/2008/04/24/making-intel-wireless-3945abg-work-better-on-ubuntu-hardy/]("http://linuxtechie.wordpress.com/2008/04/24/making-intel-wireless-3945abg-work-better-on-ubuntu-hardy/")


Cheers!

---

### Post by ussndmac on 2009-02-11
I've been fighting same issue with the 3945 on my dell XPS1530 for forever.

Take a look at the dmesg and see if you notice any messages about failing being associated.

I don't know what it means I noticed that on mine last night.

Everything else shows up as being ok, modprobe, lspci, etc.

But, when my PC came from Dell it did work. It has not ever since I cleaned the HD and put on conanical Ubuntu (8.04 or 8.10) and Ubuntustudio (8.04, 8.10 both 64 bit)

No one has been able to tell me what Dell did to make it work.

---

### Post by LGP7 on 2009-02-11
> **Fire_Chief said:**
> Ok, so it appears you were onto the best track earlier when you mentioned changing to Ubuntu 8.10.
See this [http://support.uakron.edu/wiki/index.php/Wireless_Setup_on_Ubuntu_8.04_(Hardy_Heron)_with_Intel_3945/4965]("http://support.uakron.edu/wiki/index.php/Wireless_Setup_on_Ubuntu_8.04_(Hardy_Heron)_with_Intel_3945/4965")

But if you really want to stay on 8.04 there is a way to probably make it work.
[http://linuxtechie.wordpress.com/2008/04/24/making-intel-wireless-3945abg-work-better-on-ubuntu-hardy/]("http://linuxtechie.wordpress.com/2008/04/24/making-intel-wireless-3945abg-work-better-on-ubuntu-hardy/")


Cheers!


nice!  i gave the second option a try before i upgraded the whole os.  It wokred!  thanks alot....atleast some people are helpful unlike that yahoo that posted first.

---

### Post by LGP7 on 2009-02-12
> **Fire_Chief said:**
> Ok, so it appears you were onto the best track earlier when you mentioned changing to Ubuntu 8.10.
See this [http://support.uakron.edu/wiki/index.php/Wireless_Setup_on_Ubuntu_8.04_(Hardy_Heron)_with_Intel_3945/4965]("http://support.uakron.edu/wiki/index.php/Wireless_Setup_on_Ubuntu_8.04_(Hardy_Heron)_with_Intel_3945/4965")

But if you really want to stay on 8.04 there is a way to probably make it work.
[http://linuxtechie.wordpress.com/2008/04/24/making-intel-wireless-3945abg-work-better-on-ubuntu-hardy/]("http://linuxtechie.wordpress.com/2008/04/24/making-intel-wireless-3945abg-work-better-on-ubuntu-hardy/")


Cheers!

Ok so everything was working, then installed VLC, the game frozen bubble and wine.  All of a sudden this morning my sound isn't working and it's like i don't even have a wireless card.  So i re ran this method again and my wireless is working again...sound still doesn't.   My question is...(im not exactly sure what's going on when i do this fix) but it seems like it's using old files for the os, so when i install stuff does it update to new modules and screw up the old ones??  Am i going to have to do this method every time i make a change??

---

### Post by Fire_Chief on 2009-02-12
You mentioned that you upgraded from Hardy. Did you specifically do a clean install or an actual distribution upgrade? I would recommend a clean install as it will prevent any quirky files or configs from Hardy sneaking into the new system.

---

### Post by LGP7 on 2009-02-12
> **Fire_Chief said:**
> You mentioned that you upgraded from Hardy. Did you specifically do a clean install or an actual distribution upgrade? I would recommend a clean install as it will prevent any quirky files or configs from Hardy sneaking into the new system.

No, i didn't do the upgrade to hardy.  I used the second method there which was a way to get wireless working in hardy.

---

### Post by Fire_Chief on 2009-02-12
You may want to try using Wicd in place of NetworkManager as some of the posts on that page suggested.

---

