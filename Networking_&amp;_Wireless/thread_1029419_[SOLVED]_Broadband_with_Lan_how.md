---
title: "[SOLVED] Broadband with Lan how ?"
date: 2009-01-03
forum: Networking &amp; Wireless
---

### Post by Dimitree on 2009-01-03
Hello i have the latest Ubuntu, and i'm trying to configure my Internet connection.

Under windows, all i do is Setup New Network connection, then click next next, then chose manual setup, then next and then chose the Broadband option followed by 3 next clicks.
Then i simply enter my Username and Password and click on Dial and i'm connected.
It's trough a Lan cable.

Where can i make the same settings in Ubuntu ?
I tryed the PPPoeconf but all it says is connection terminated after i use my user and pass to connect ?

Please help :) if this is confusing i will post screenshots in windows.

---

### Post by ieee488 on 2009-01-03
I have Verizon DSL. Ubuntu 8.10 found my Ethernet card. And I didn't have to do anything special. Automatically connected when I boot up.

---

### Post by melojo on 2009-01-03
You need to give us more info.

You must have DSL if you are using ppoe so what brand is your modem/model #
also are you using a router?

Can you give us specs about your computer?

---

### Post by Dimitree on 2009-01-04
Ok i will try to provide more info.

I have a network cable LAN in my network card on the PC.
With previous ISP i had to manually type in my IP, Mask, Gateway, DNS1, DNS2.And that's how it worked.

Now with this new ISP, nothing is changed.
I still have Lan cable plugged in my network card,
but ....

Now instead of typing my IP, Mask, Gw, DNS1, DNS2
i just do this :
New network connection wizard -> Connect to the internet -> setup my connection manually -> connect using a broadband connection that requires username and password (this is a high speed connection using either DSL or cable modem, your ISP may refer to this connection as PPPoE -> type Isp name -> type user and pass -> finish.

The result is this :

[IMG]http://i43.tinypic.com/2wf96ax.jpg[/IMG]

[IMG]http://i42.tinypic.com/30ij4zq.jpg[/IMG]

So whenever i want to connect, I double click an icon on the desktop, and click on Dial.

I don't have a Modem, just network card and Lan cable in it, no router.

---

### Post by Dimitree on 2009-01-04
Never mind .... it seams i typed my username with 1 upper case letter and that's why it didn't connect with pppoeconf ... SORRY !!! :)

---

