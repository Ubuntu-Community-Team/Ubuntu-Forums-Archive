---
title: "Help with Bluetooth Dial-up Networking"
date: 2011-04-21
forum: Networking &amp; Wireless
---

### Post by princeofthecity on 2011-04-21
i use bluetooth dial-up networking with the same phone as i use on my other windows xp machine all the time.  i got as far as pairing and connecting the two devices but i cant seem to get the dial-up networking started.

im using blueman bluetooth manager but when i pair, connect, and right-click the device all i can "connect" to is SSP1.  but also all i can "disconnect" to is Dial-up Networking, which leads me to think that its already "connected" to the Dial-up Networking service.  but when i click my browser to test it isnt connected.  also i can tell when i am connected by looking at my phone - the data arrows will be displayed on the phone screen.

further i get a system message pop open after successfully pairing and connecting that "...Dial-up Networking DUN is available through Network Manager..." im a little confused by this message.

a few caps:

[IMG]http://i207.photobucket.com/albums/bb260/joshtridge/bt1.png[/IMG]

[IMG]http://i207.photobucket.com/albums/bb260/joshtridge/bt2.png[/IMG]

thanks for reading and thanks in advance for any help.

---

### Post by frytek on 2012-03-22
This worked perfectly in 10.4 and 10.10. Recently I upgraded to 11.10 and I have exactly the same problem. It seems to be working only half-way. Blueman can pair and set up a dial-up connetcion. Then, you can  right-click the Network Manager to modify the connections and to add a mobile connection, using a wizard for country / mobile operator. 

But this connection is not available in Network Manager. In 10.4 / 10.10 the new connection was visible in available networks, next to wifi and cable connections every time blueman was paired and DUN-ed. 

I am really considering downgrading to 10.4 if 12.4 does not solve this bug. Ubuntu 10.4 will be supported till 2013...

:(

---

### Post by frytek on 2012-03-22
I just found a solution here: 
[http://ubuntuforums.org/showthread.php?t=1597732&highlight=blueman+network+manager+dial](http://ubuntuforums.org/showthread.php?t=1597732&highlight=blueman+network+manager+dial)

It does not work for me, though. I'm using xubuntu...

---

