---
title: "Wireless problem, BC 4315"
date: 2010-10-06
forum: Networking &amp; Wireless
---

### Post by gonzaga on 2010-10-06
Hello, 

I know this is probably a very rookie problem but that suits my knowledge of Linux right now...

I installed ubuntu netbook on my netbook yesterday by using wubi.

Immediately I realized that i was having trouble with the wireless and plugged in an ethernet cord, and realized i needed the drivers for my wireless card.... which i determined was a broadcom type 4315

After a little research I ran the 

sudo apt-get install b43-fwcutter

get command... and I was excited because now I could see available wireless networks.

When I connected to my home network it requested the authentication key, but after I put it in it wouldn't connect. It would try but would never actually form a connection.

So then I tried my school network, and again I entered my log on and I still could not connect.

Then I tried my schools guest network, which doesn't require a key but requires an email authentication web page, which you get redirected to when you attempt to access the internet. AND this worked!

So I went back home and tried by home network with my key thinking that maybe a restart had fixed it but it still wouldn't connect, it just tries forever and occasionally asks for the network password.

Anything in here im missing? also note i am using network manager

W

---

### Post by gordintoronto on 2010-10-06
You're doing great!

What type of encryption is used on your home network? Did you tick the "show password" box, so you could see what you were typing?

---

### Post by gonzaga on 2010-10-06
WPA is used on both the encrypted school and home network.

Thank you for the vote of confidence :)

W

---

### Post by gordintoronto on 2010-10-07
There are two type of WPA, any chance you're specifying the wrong one?

I've had better success by right-clicking on the network icon, selecting "edit connections," then the wireless tab and "add". Doesn't mean it will work for you...

---

