---
title: "Static IP on 9.10 wireless"
date: 2009-11-16
forum: Networking &amp; Wireless
---

### Post by 3m_g33k on 2009-11-16
Hello,

I've been trying to get a static IP going on my laptop across my wireless connection to my router. Ive found a couple of threads that mention editing /etc/network/interfaces file. All the examples I've seen people have their files properly populated with loads of information goodies whereas mine is like below:

```

auto lo
iface lo inet loopback

```

Ive also read I need to uninstall the network manager that comes with 9.10 but again I'm a bit hesitant and would really appreciate a step by step walkthrough!

Many thanks in advance!!

---

### Post by The Funkbomb on 2009-11-16
First thing you want to do is get your info.  This is what you need to know:

Your desired IP address on your local network.  Usually something like 192.168.1.X

Your Netmask.  You can find this out by typing into terminal:
```
ifconfig
```

Your gateway.  Usually it's 192.168.1.1 but your router might be different.

Your DNS servers:

```
sudo cat /etc/resolv.conf
```

Now we can start plugging it in.

System>Preferences>Network Connections

Click Wireless and select your router.  Now press edit.

Click on IPv4 settings.  Put the drop down bar to manual.

Fill in all the information.  Your router will probably drop your connection and you will reconnect.

---

### Post by 3m_g33k on 2009-11-16
Thanks for the speedy reply Funkbomb!

I've done all that and have come to the stage now of just saving the settings but the "Apply" button is greyed out and I cannot save the new config settings? Thanks for your help again mate!

> **The Funkbomb said:**
> First thing you want to do is get your info.  This is what you need to know:

Your desired IP address on your local network.  Usually something like 192.168.1.X

Your Netmask.  You can find this out by typing into terminal:
```
ifconfig
```

Your gateway.  Usually it's 192.168.1.1 but your router might be different.

Your DNS servers:

```
sudo cat /etc/resolv.conf
```

Now we can start plugging it in.

System>Preferences>Network Connections

Click Wireless and select your router.  Now press edit.

Click on IPv4 settings.  Put the drop down bar to manual.

Fill in all the information.  Your router will probably drop your connection and you will reconnect.

---

### Post by The Funkbomb on 2009-11-16
Weird.

What wireless card are you using?  Have you tried setting a static IP through your router before?

Very weird.

---

### Post by 3m_g33k on 2009-11-16
I know, rather baffling !:confused:

I have one of those dreaded Atheros cards which are a real pain to get working with Ubuntu. I managed to get a static IP going with Hardy Heron but ever since Jaunty and Koala I haven't been able to get it working and I need it to get Mediatomb working!

I've seen a few fixes for Jaunty which involved editing the interfaces file etc but as I mentioned in the OP I don't have the greatest confidence editing that!

---

### Post by idef1x on 2009-11-16
Why not configure your network settings via the networkmanager itself? Works just fine.
To be honest, i installed wicd instead of the standard network manager, because i like it better.
It has a gui frontend which starts automaticaly at boot and if not try to start wicd-client....

---

### Post by 3m_g33k on 2009-11-16
Hey there mate, cheers for the reply. I'm afraid you are going to have to dumb that down a bit for me lol. Isn't Network Connections the Network Manager? if not, where do I find it? Or we could go for that wicd you were talking about?

---

### Post by Iowan on 2009-11-16
System>Preferences>Network Connections *should* stash information in the same place as Network Manager - but I've had a couple of times (other releases) where one will let me save data, and one won't. As I recall, Network Manager let me edit the connection.

---

### Post by idef1x on 2009-11-17
> **3m_g33k said:**
> Hey there mate, cheers for the reply. I'm afraid you are going to have to dumb that down a bit for me lol. Isn't Network Connections the Network Manager? if not, where do I find it? Or we could go for that wicd you were talking about?
With Network Manager you MANAGE the Network connections, so is not the same ;)
Anyway there should allready be a network manager icon in your status bar, where you can see your current settings. Here you can also select "manage connections"...that's the one you need to set it to static and fill in your network details.

---

