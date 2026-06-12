---
title: "Keeps asking for password"
date: 2010-11-09
forum: Networking &amp; Wireless
---

### Post by werr300 on 2010-11-09
I try to connect to a wireless network under Ubuntu 9.10, but every time it just keeps on loading for about a minute and than asks for the password again. No matter how many time I enter it, it cannot connect, but keeps requesting the key. 
At first I thought it might be because of the encription type, but I checked and it is open.
 
Any ideas?

---

### Post by uncaspi on 2010-11-09
Possible bug in the distro. Try upgrade to 10.04 and NOT 10.10

---

### Post by werr300 on 2010-11-10
The thing is that I do not wish to update. Isn´t there a possible patch for this? Is it even a known bug?

---

### Post by grahammechanical on 2010-11-10
I have found that when you enter the wrong password it takes the system a few seconds to check to see if it can connect to the modem. When this fails you do not get a "wrong password" error message, just the same dialog box requesting authentication. Are you putting in your login password? I have made that mistake. It is the password for the modem/router. It is called the wireless key or WPA-PSK. It should be printed on a label stuck on the bottom of the modem. Once you get the right password it will be remembered by the system. 

If you go to Edit connections and select your wireless network and look under the wireless security tab you can check what the actual password is. You will need to put a check mark against Show password to see what the password actually is.

Regards.

Regards.

---

### Post by werr300 on 2010-11-16
I really wish the problem was just a mistype, but alas, it ain't. I verified, quite a few times, that I am indeed using the correct key, so that cannot be the issue.

---

### Post by Peter09 on 2010-11-16
As I understand there is a problem in the current kernels with some drivers. I found that a work around for me was to delete the actual network by
 
Right click on network manager -> edit connections -> wireless (delete any reference to the network you want to connect to). Y
 
ou should get a network disconnect message. The try selecting the network again and logging in.
 
Not sure this will work for all cards though.
 
I do wish they would resolve this - its hurting a lot of people and is a severe regression.

---

### Post by deconstrained on 2010-11-16
It's also quite possible you're simply using the wrong type of wireless encryption (change this under the 'security' tab of the connection-editing dialogue in network-manager). It has to be the same type as used by the router, and a mis-match is common. Yet another possibility (less likely) is that the wireless encryption being used by the router isn't supported.

---

### Post by theozzlives on 2010-11-16
Whenever I access my Windows 7 machine from one of my machines, I get a password dialogue and just simply hit cancel. I then have access.

---

### Post by grahammechanical on 2010-11-16
You say > I checked and it is open then it should not need a password. If I switch off my modem/router then network manager will automatically connect me to the nearest unsecured wireless network. Perhaps the problem is not so much the password being rejected but failure to connect because of incorrect settings. This is the location of the wireless trouble shooting guide

[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide/Connections](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide/Connections)

Regards.

---

### Post by Peter09 on 2010-11-22
Think you will find there are a lot of people with this problem, it is unlikely to be just finger trouble - although you never know.

---

### Post by werr300 on 2010-11-24
@grahammechanical:
Do you think I enter a 26 digits password just for fun? It is obviously not an unsecured network. And I am pretty sure my settings are correct.
 
@deconstrained:
That is what I thought at first as well, but I am certain I am using the correct encryption type and that the settings match the router's.
 
@theozzlives:
That would work if the network is not password protected. Besides, Win 7 and Ubuntu have little to do with each other.
 
I´ll try the suggestions and see how it goes.

---

### Post by tmratwork on 2011-05-18
> **Peter09 said:**
> 
 
Right click on network manager -> edit connections -> wireless (delete any reference to the network you want to connect to). You should get a network disconnect message. The try selecting the network again and logging in.
 

peter's solution worked for me :)  thanks peter!

i tried lots of other solutions first, spent hours on this, nothing worked.  deleted the wireless connection per peter's post, then wireless worked again.

background:
wireless working fine, then one day boot up and it does not work.  ubuntu 11.04 keeps asking for wireless password.  other computers on same network with same password working good.  this computer on different networks running into same 'keeps asking for password' error.  now after above fix, error is fixed.

---

