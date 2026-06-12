---
title: "internet connection sharing HELP PLEASE"
date: 2009-05-06
forum: Networking &amp; Wireless
---

### Post by ssj3g0ku on 2009-05-06
hello
i have 2 pcs
1 with ubuntu 8.10 with 2 network cards
1 with windows xp pro sp 2 with 1 network card

ubuntu is connected to the internet tru eth1 with pppoe
the other eth2 is connected with other pc windows xp

i tryed to share the internet connection with "firestarter"
and even manualy from this [http://ubuntuforums.org/showthread.php?t=91370](http://ubuntuforums.org/showthread.php?t=91370) link
but no use :(

can you guys tell me what can i do ?
or tell me a program that can do the work for me or a script..

Thanks :guitar:

---

### Post by ssj3g0ku on 2009-05-07
any help please ?

---

### Post by SHENGTON on 2009-05-07
Hello ssj3g0ku, good evening. :)

You don't need to install the "firestarter".

I assumed that you have two cards:
1. The first network card is = Realtek
2. The second netword card is = Marvell

You connected the cable from modem to the Realtek network card.

**First Method:**
1. Right-click on the network icon and click "Edit Connections".
2. In "Wired" tab, select the Marvell network card and click Edit.
3. In &#8220;IPv4 Settings&#8221; tab, select &#8220;Shared to other computers&#8221; and click OK.
4. Now, plug the cable to your Ubuntu computer to Windows XP computer.
5. In Ubuntu computer, click on the nm-applet or network icon and select Marvel network card you have just created. In few seconds, a popup balloon message from the nm-applet or network icon says "Connection is established".

**Second Method:**
1. Right-click on the network icon and click "Edit Connections".
2. In "Wired" tab, click "Add" button.
3. In "Connection name" type "ICS" or any name what you want.
4. Uncheck "Connect automatically".
5. In &#8220;IPv4 Settings&#8221; tab, select &#8220;Shared to other computers&#8221; and click OK.
6. Now, plug the cable to your Ubuntu computer to Windows XP computer.
7. In Ubuntu computer, click on the nm-applet or network icon and select "ICS" you have just created. In few seconds, a popup balloon message from the nm-applet or network icon says "Connection is established".

Take care and God bless. :)

---

### Post by Iowan on 2009-05-07
[Here]("https://help.ubuntu.com/community/Internet/ConnectionSharing") is a help page for ICS.

---

### Post by ssj3g0ku on 2009-05-07
> **SHENGTON said:**
> Hello ssj3g0ku, good evening. :)

You don't need to install the "firestarter".

I assumed that you have two cards:
1. The first network card is = Realtek
2. The second netword card is = Marvell

You connected the cable from modem to the Realtek network card.

**First Method:**
1. Right-click on the network icon and click "Edit Connections".
2. In "Wired" tab, select the Marvell network card and click Edit.
3. In “IPv4 Settings” tab, select “Shared to other computers” and click OK.
4. Now, plug the cable to your Ubuntu computer to Windows XP computer.
5. In Ubuntu computer, click on the nm-applet or network icon and select Marvel network card you have just created. In few seconds, a popup balloon message from the nm-applet or network icon says "Connection is established".

**Second Method:**
1. Right-click on the network icon and click "Edit Connections".
2. In "Wired" tab, click "Add" button.
3. In "Connection name" type "ICS" or any name what you want.
4. Uncheck "Connect automatically".
5. In “IPv4 Settings” tab, select “Shared to other computers” and click OK.
6. Now, plug the cable to your Ubuntu computer to Windows XP computer.
7. In Ubuntu computer, click on the nm-applet or network icon and select "ICS" you have just created. In few seconds, a popup balloon message from the nm-applet or network icon says "Connection is established".

Take care and God bless. :)


thanks ill try :D

---

### Post by SHENGTON on 2009-05-07
Hello ssj3g0ku, good morning. :)

Remember that if you need to refresh the network card of your Windows XP refresh it by right-clicking it and refresh. Because in my Windows Vista I need to refresh before it will connect to the internet.

You don't need the "firestarter or [this]("https://help.ubuntu.com/community/Internet/ConnectionSharing") Internet Connection Sharing from Ubuntu documentation.

Take care and God bless. :)

---

### Post by ssj3g0ku on 2009-05-08
> **SHENGTON said:**
> Hello ssj3g0ku, good morning. :)

Remember that if you need to refresh the network card of your Windows XP refresh it by right-clicking it and refresh. Because in my Windows Vista I need to refresh before it will connect to the internet.

You don't need the "firestarter or [this]("https://help.ubuntu.com/community/Internet/ConnectionSharing") Internet Connection Sharing from Ubuntu documentation.

Take care and God bless. :)

it did not work :(
crap...

---

### Post by superprash2003 on 2009-05-09
you said you tried the manual method in the first step.. you would have needed to replace ethX with eth1 or eth0 depending on your network. so could you post all the commands you typed to get ICS working.. and also mention which interface ( eth0 or eth1 ) connects to your router and which one connects to the xp

---

### Post by ssj3g0ku on 2009-05-09
> **superprash2003 said:**
> you said you tried the manual method in the first step.. you would have needed to replace ethX with eth1 or eth0 depending on your network. so could you post all the commands you typed to get ICS working.. and also mention which interface ( eth0 or eth1 ) connects to your router and which one connects to the xp

I did it exactly as in tutorial but it does not work.
Mabe a user or you can connect to my pc tru ssh and help me out ?

:(

---

