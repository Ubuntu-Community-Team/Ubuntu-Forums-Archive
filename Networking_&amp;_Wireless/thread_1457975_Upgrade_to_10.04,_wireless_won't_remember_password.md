---
title: "Upgrade to 10.04, wireless won't remember passwords"
date: 2010-04-19
forum: Networking &amp; Wireless
---

### Post by CMOT-Weasel on 2010-04-19
Hey.

New on here, but I can't find a fix for this.. it's probably pretty simple.

Was running Ubuntu 9.10 on an IBM ThinkPad X41T, upgraded to 10.04 beta 2, but for some reason now NetworkManager is refusing to remember any of my passwords (Either saved networks or pptp VPN conncetions.)

It works fine, I just need to input the password every time I try to connect or reconnect to a wireless network.

Any suggestions?

Cheers guys,

Weasel

---

### Post by eltonw on 2010-04-19
> **CMOT-Weasel said:**
> Hey.

New on here, but I can't find a fix for this.. it's probably pretty simple.

Was running Ubuntu 9.10 on an IBM ThinkPad X41T, upgraded to 10.04 beta 2, but for some reason now NetworkManager is refusing to remember any of my passwords (Either saved networks or pptp VPN conncetions.)

It works fine, I just need to input the password every time I try to connect or reconnect to a wireless network.

Any suggestions?

Cheers guys,

Weasel

FYI: BETA code is for testing only. [COLOR="Red"]It's not[-X a good idea to "upgrade" with such code.[/COLOR] There ***are*** connection problems with the current beta, and the following thread will update you on the current situation:
[http://ubuntuforums.org/showthread.php?p=9140633#post9140633]("http://ubuntuforums.org/showthread.php?p=9140633#post9140633")

---

### Post by CMOT-Weasel on 2010-04-19
> **eltonw said:**
> FYI: BETA code is for testing only. [COLOR="Red"]It's not a good idea to "upgrade" with such code.[/COLOR] There ***are*** connection problems with the current beta 

It's not a connection problem as such, it connects fine but NetworkManager needs me to enter the password each time. (I know it's not a stable release. ;-) )

---

### Post by spiky001 on 2010-04-19
when you put the wpa code in then a box comes up are you sure it,s not for keyring password

---

### Post by eltonw on 2010-04-19
> **spiky001 said:**
> when you put the wpa code in then a box comes up are you sure it,s not for keyring password

That is what I said (in slightly *different words*), when I wrote my original post:
[http://ubuntuforums.org/showthread.php?t=1438175]("http://ubuntuforums.org/showthread.php?t=1438175")

/BEGIN QUOTE

"...keeps trying and sending me back to the Authentication dialog when I run the Lucid beta..."

/END QUOTE

Authentication dialog =  "box comes up" :lolflag:

---

### Post by CMOT-Weasel on 2010-04-20
> **spiky001 said:**
> when you put the wpa code in then a box comes up are you sure it,s not for keyring passwordVery sure. ;-)

Odly, for some reason the problem appears to have fixed itself. O.o

Not sure what it was or why, checking logs now. Cheers for the help guys. :-)

Weasel

---

### Post by Rebootkid on 2010-05-03
Well, now I'm running the full version, and it's not remembering the wireless passwords (or email passwords for that matter)

Any suggestions?

---

### Post by tarator on 2010-05-04
Same problem here.

KNetworkManager doesn't remember WPA-Password.
It also doesn't ask to save it in KWallet.

---

### Post by bagpussnz on 2010-05-05
I am running a fresh install of 10.04 on my laptop.
When I login, it always asks for my wireless password. Everything works fine when I enter the password - it just won't remember it.

Regards,
Ian

---

### Post by chadmerkert on 2010-05-06
I am also having this problem. I can connect to the wireless fine, but if it is a network with a password, I have to type the password in each time I connect! It isn't a huge problem, but it is an inconvenience.

I am running 10.04 64-bit.

I would very much like to find a solution to this.

---

### Post by djmm on 2010-05-08
Same problem here.

---

### Post by DeanSchneider on 2010-05-17
Same problem here.

Lucid 10.04 (upgrade from 9.10), Gnome
HP Pavillion dv2750ei

About to download about 80mb of updates (funnily enough, I haven't been prompted to update since installing 10.04) so will let you know if that changes anything.

EDIT: Installed all latest updates - no change to this problem - it still exists.

---

### Post by chadmerkert on 2010-05-18
Hello Everyone, lets try to narrow down the problem a little bit. If everyone could give some more information about their setup, it might help us determin where the problem is.

I am running a Fresh install of 10.04 64-bit on an HP TX2500z

My Wireless card (as listed from command lspci) is: Broadcom Corporation BCM4322 802.11a/b/g/n Wireless LAN Controller (rev 01)

If everyone posts this information as well, we may be able to find out what the problem is with.

Thanks for your help!

---

### Post by ParliamentFunkadelic on 2010-05-19
I have been having the same issue whenever cold booting or waking up my netbook. What I did to fix it was right-click on the network-manager icon and go to Edit Connections. Then go to the Wireless tab > Edit > Wireless Security > Check "Available to all users" at the bottom of the box. This setting seemed to take care of the issue, after verifying it with a quick log out/in. Hope this helps you guys.

---

### Post by berman56 on 2010-05-20
> **ParliamentFunkadelic said:**
> I have been having the same issue whenever cold booting or waking up my netbook. What I did to fix it was right-click on the network-manager icon and go to Edit Connections. Then go to the Wireless tab > Edit > Wireless Security > Check "Available to all users" at the bottom of the box. This setting seemed to take care of the issue, after verifying it with a quick log out/in. Hope this helps you guys.

ParliamentFunkadelic's suggestion worked for me!  Thanks.

---

### Post by lautarop on 2010-05-23
> **ParliamentFunkadelic said:**
> I have been having the same issue whenever cold booting or waking up my netbook. What I did to fix it was right-click on the network-manager icon and go to Edit Connections. Then go to the Wireless tab > Edit > Wireless Security > Check "Available to all users" at the bottom of the box. This setting seemed to take care of the issue, after verifying it with a quick log out/in. Hope this helps you guys.


Hey, I tried that, but it just doesn't remember the "available to all suers box"

And it has to do with the fact that it doesnt pop ups the "enter your password" thing, and there's not a "unlock" button.

am I missing something?

---

### Post by Kaihaku on 2010-06-13
Same here.

No problems before I upgraded to 10.04 LTS 64-Bit, but now asks for wireless login everytime I open admin account. Oddly, other less privileged accounts get wireless as normal.

*Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express)*

I wonder, could the conflict be with the router?

---

### Post by chocobanana on 2010-08-14
Hi everyone

I hope I'm still on time to provide the solution to the problem. I just did a clean install of Ubuntu 10.04 and have the exact same problem - which basically is that the Gnome Keyring Manager is not creating a login Password Keyring, it instead creates one named default which is acting weird by not remembering any password. Why it does it I don't know and among half dozen installs this is the only installation where the keyring manager misbehaved. 

Here's how to solve the issue:

1) Go to the Applications menu > Accessories > Keyring manager
2) Click the File menu > New
3) Select the Password Keyring
4) Name it "login" without the quotes (the normal behavior would have created this keyring automatically)
5) Right click on the login keyring and click Set as default
6) Close the Keyring Manager
7) Open your home folder in the Nautilus browser
8 ) Press Ctrl+h to show hidden files
9) Open the .gnome2 folder and then the keyrings folder
10) Delete all files except "default" and "login.keyring"
11) Reboot the computer
12) It will ask for the Wireless password for the last time
13) Reboot again to test if you wish

Enjoy!

Greetings

---

### Post by mutsa on 2010-09-12
Thanks chocobanana worked for me

---

### Post by holy.zarquon on 2010-11-02
This also works if you want to bypass the Keyring password request every time you turn on your computer.  For example, I had to enter my password to login to Ubuntu, and then enter a separate password for the Keyring so that it would remember my wireless password.  Now I only have to enter the Ubuntu password.

---

### Post by DeweyDL on 2010-11-18
I fixed it on my Ubuntu 10.04 Lucid Lynx..  I right clicked the wireless antenna and chose edit connections.  Chose the wireless tab.  Chose my wireless connection.  Clicked Edit.  Put a check mark in the Available to All users check box.  Now I automatically connect to my wireless network... Yippee

---

