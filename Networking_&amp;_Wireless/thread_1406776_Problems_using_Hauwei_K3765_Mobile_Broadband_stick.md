---
title: "Problems using Hauwei K3765 Mobile Broadband stick on Ubuntu"
date: 2010-02-14
forum: Networking &amp; Wireless
---

### Post by paulgreen35 on 2010-02-14
[SIZE=3][FONT=Verdana]I have a Hauwei K3765 [/FONT]Mobile Broadband stick and would like to use it on my Ubuntu 9.10 operating system[/SIZE].

[FONT=Verdana][SIZE=3]I've tried downloading the vodafone-mobile-connect_2.15.01-2_all.deb package, but I recive the following error message[/SIZE][/FONT][FONT=Verdana][SIZE=3]:-[/SIZE][/FONT]

[FONT=Verdana][SIZE=3]/tmp/vodafone-mobile-connect_2.15.01-2_all.deb could not be opened, because the associated helper application does not exist. Change the association in your preferences.

Does anyone know what this means and how I could install the package?
[/SIZE][/FONT]

---

### Post by razvandudu on 2010-02-18
1. Go to 
[https://forge.betavine.net/frs/?group_id=12](https://forge.betavine.net/frs/?group_id=12)
Download:
ozerocdoff_0.4-2_i386.deb
([https://forge.betavine.net/frs/download.php/538/ozerocdoff_0.4-2_i386.deb](https://forge.betavine.net/frs/download.php/538/ozerocdoff_0.4-2_i386.deb))
usb-modeswitch_0.9.7_i386.deb
([https://forge.betavine.net/frs/download.php/490/usb-modeswitch_0.9.7_i386.deb](https://forge.betavine.net/frs/download.php/490/usb-modeswitch_0.9.7_i386.deb))
vodafone-mobile-connect_2.20.01-1_all.deb
 ([https://forge.betavine.net/frs/download.php/591/vodafone-mobile-connect_2.20.01-1_all.deb](https://forge.betavine.net/frs/download.php/591/vodafone-mobile-connect_2.20.01-1_all.deb))

2. Install in this order (to avoid dependency problems):
sudo dpkg -i ozerocdoff_0.4-2_i386.deb
sudo dpkg -i usb-modeswitch_0.9.7_i386.deb
sudo dpkg -i vodafone-mobile-connect_2.20.01-1_all.deb

3. fix group, group membership, permissions:
sudo chmod 0660 /etc/ppp/pap-secrets
sudo chmod 0660 /etc/ppp/chap-secrets
sudo groupadd -f dip
sudo usermod -a -G dip <your_username>

The "dip" stuff was asked for by "vodafone-mobile-connect..." when launched one of first times... the above commands solved the complaints ;)

4. Reboot.

5. After reboot connect your modem... It should be automatically recognized and installed, then a connection wizard should pop up. This wizard had the proper settings predefined for Vodafone Romania (I've seen Orange too), so if you're on a major network you shouldn't have any problems.

The "vodafone-mobile-connect-card-driver-for-linux" application can be launched from terminal or from the "Applications/Network" menu, but this application is useful mainly for it's traffic reports and for sending SMS... You can connect without it too.

Post your results, please.

---

### Post by eski037 on 2010-04-30
how do you download that if your modem isn't working?

---

### Post by alexfish on 2010-04-30
Hi

Before Trying VMC try to get the modem working, as there can Be problems geting VMC to work with ubuntu

Follow this post , if you need to download usb_modeswitch   use computer with Internet access and use the Debian link and save the file to a usb stick , when in Ubuntu the file will self install


[http://ubuntuforums.org/showthread.php?t=1465557](http://ubuntuforums.org/showthread.php?t=1465557)

regards

alexfish

---

### Post by shawnerz on 2011-04-05
I just wanted to say that this worked for me. :D 
I did everything down to the 'dip' portion because I don't understand what "dip" means.
I also do not have a username and password.  I only have a 4 digit PIN.
I'm using a K3765 on a prepaid plan, in Italy, on Vodafone (UMTS).
Yay! :)

---

### Post by cobalote on 2012-04-07
Great post from razvandudu (#2). The solution described there solved my problem.
Many thanks.

---

### Post by cobalote on 2012-04-07
@[eski037]("http://ubuntuforums.org/member.php?u=360156"): Man ... what kind of question is that ? How could access this forum with you hadn't internet access ?

---

### Post by coffeecat on 2012-04-07
Old thread - closed.

---

