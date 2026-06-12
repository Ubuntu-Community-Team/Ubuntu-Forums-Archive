---
title: "Can't connect to my university network"
date: 2012-10-13
forum: Networking &amp; Wireless
---

### Post by llamas612 on 2012-10-13
As the title states, I'm trying to connect to my university's network, but I'm having authentication issues. I tried contacting IT help but they "don't support linux" so they were of no use. At first, i thought that maybe there was some special type of authentication neccesary to connect (when on Windows, you're required to download a program just to connect to the network), but it seems as though on Android and older versions of OSX, one simply needs to choose the right settings in order to connect.

[Here]("http://www.cumc.columbia.edu/it/howto/wireless/leopard.html") is a link to the instructions on how to connect using OSX 10.5 and 10.6. From that, i figured that I could simply create a network connection in Ubuntu, and choose WPA2 Enterprise, TTLS and PAP for the authentication settings. Then I would enter in my user credentials and connect. However it still isn't working, and I have no idea how to get around it. 

Any Ideas?

---

### Post by llamas612 on 2012-10-13
anyone?

---

### Post by Doug S on 2012-10-15
The only observation I have is that the link you gave refers to "WPA Enterprise" and your text says you tried "WPA2 Enterprise".
Sorry, I can not be of more help.

---

### Post by llamas612 on 2012-10-15
As the title states, I'm trying to connect to my university's network, but I'm having authentication issues. I tried contacting IT help but they "don't support linux" so they were of no use. At first, i thought that maybe there was some special type of authentication necessary to connect (when on Windows, you're required to download a program just to connect to the network), but it seems as though on Android and older versions of OSX, one simply needs to choose the right settings in order to connect.

[Here]("http://www.cumc.columbia.edu/it/howto/wireless/leopard.html") is a link to the instructions on how to connect using OSX 10.5 and 10.6. From that, i figured that I could simply create a network connection in Ubuntu, and choose WPA&WPA2 Enterprise, TTLS and PAP for the authentication settings. Then I would enter in my user credentials and connect. However it still isn't working, and I have no idea how to get around it. 

Any Ideas?

---

### Post by Polydorus on 2012-10-15
Perhaps it's just me, but I don't see any link?

---

### Post by llamas612 on 2012-10-15
Hah, you are correct. My mistake. I have fixed the link

---

### Post by Polydorus on 2012-10-17
I have far to little experience with Linux to answer your question but two suggestions:

Have you tried contacting other students at your school who use Ubuntu?

Post more details, the release of Ubuntu you are using, what you have tried to make a connection, etc.

---

### Post by lmm5247 on 2012-10-17
> **llamas612 said:**
> As the title states, I'm trying to connect to my university's network, but I'm having authentication issues. I tried contacting IT help but they "don't support linux" so they were of no use. At first, i thought that maybe there was some special type of authentication necessary to connect (when on Windows, you're required to download a program just to connect to the network), but it seems as though on Android and older versions of OSX, one simply needs to choose the right settings in order to connect.

[Here]("http://www.cumc.columbia.edu/it/howto/wireless/leopard.html") is a link to the instructions on how to connect using OSX 10.5 and 10.6. From that, i figured that I could simply create a network connection in Ubuntu, and choose WPA&WPA2 Enterprise, TTLS and PAP for the authentication settings. Then I would enter in my user credentials and connect. However it still isn't working, and I have no idea how to get around it. 

Any Ideas?
Just for the hell of it, instead of choosing WPA/WPA2 Enterpise, did you try choosing 802.1X? I'm running Mint 12.04, but I assume it's the same in Ubuntu..

---

### Post by llamas612 on 2012-10-21
> **Polydorus said:**
> I have far to little experience with Linux to answer your question but two suggestions:

Have you tried contacting other students at your school who use Ubuntu?

Post more details, the release of Ubuntu you are using, what you have tried to make a connection, etc.

Hah! I wish i knew somebody who used Ubuntu. Unfortunately there are none around here (or they're hiding).

I'm using Ubuntu 12.04 and I've tried whatever I could to make a connection. I tried using all of the different types of inner authentication methods, (CHAP, MSCHAP, etc). 

Also, from the website I linked to, you'll see that there are different instructions for newer Mac users. I downloaded the file that those users need, and inside found what looked like kind of CA certificate. I copied that info and made a certificate file and used that. That didn't work either. To be honest, I know absolutely nothing about Wireless Security, and really don't even know what a CA certificate is, so I'm quite sure my attempt at that was pointless. Also, there's no need for any type of certificate if you're using an Android phone, so I doubt I need one.

Thanks for the response though. I'm still working on it, but at some point I might just be resigned to sticking to Windows.

Man, the world makes it pretty difficult to be a linux user.

---

### Post by llamas612 on 2012-10-25
Well I seem to have sort of solved it. I tried out the latest nightly (10/22) of ElementaryOS Luna, and my connection worked perfectly! This leads me to think that there might be some sort of weird driver issue. When I googled my issue, I found a few users complaining about these problems who claimed that Ubuntu was somewhat finnicky with some WPA connections, although I cant vouch for the validity of that. What even more curious is that Luna is based off of Ubuntu 12.04, so you would think they would work similarly in this situation.

---

### Post by dino99 on 2012-10-25
on ubuntu, networkmanager is sometimes a real pain, but wicd works smoothly with all network types.

---

### Post by llamas612 on 2012-10-26
You know, I tried wicd, but I was having trouble with it. The specific settings I need are WPA2 Enterprise, TTLS, and the Inner Auth as PAP. I couldn't seem to find that combination in wicd.

---

### Post by howefield on 2012-10-26
If the owners of the network won't help, why would you expect help here in circumventing their policies.

Thread closed.

---

