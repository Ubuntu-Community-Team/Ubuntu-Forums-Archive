---
title: "Bug in Karmic's Network Manager?"
date: 2009-11-03
forum: Networking &amp; Wireless
---

### Post by ausmuso on 2009-11-03
I had something weird going on with Karmic's network manager. It steadfastly refused to recognise the password for the keyring. First I thought I had been sloppy in my typing somewhere. I reinstalled from scratch, being very careful with my typing but the same thing happened again. Has anybody else run into this?
Luckily my Karmic is running on a desktop so I always log in to the one wireless server.
The simple solution for me was to do away with the network manager altogether and use wicd instead. Now my wireless network gets up and running at boottime, very convenient.

---

### Post by Phyxiis on 2009-11-03
I might have had the same problem.

When ever I start up Ubuntu 9.10, the network manager comes up asking me for the Network key. I enter it and the Keyring Manager pops up and if I put in a password and check the automatically unlock and click OK, it pops up again. I do the same thing and it keeps popping up. I have my Network Manager to automatically connect to the Internet but it keeps asking me for the Network key.

How do I get it to automatically accept the connection without the keyring popping up?

---

### Post by ausmuso on 2009-11-03
> **Phyxiis said:**
> I might have had the same problem.

When ever I start up Ubuntu 9.10, the network manager comes up asking me for the Network key. I enter it and the Keyring Manager pops up and if I put in a password and check the automatically unlock and click OK, it pops up again. I do the same thing and it keeps popping up. I have my Network Manager to automatically connect to the Internet but it keeps asking me for the Network key.

How do I get it to automatically accept the connection without the keyring popping up?


You may like to try Wicd. Visit this link:
[http://wicd.sourceforge.net/moinmoin/Wicd%20on%20Ubuntu](http://wicd.sourceforge.net/moinmoin/Wicd%20on%20Ubuntu)

Good luck!

---

### Post by ugashia on 2009-11-04
I seem to be having the same problem as Phyxiis. It keep asking for the network key over and over. I know the key is correct and have tested it on another system. Wicd doesn't appear to be working either. Any suggestions?

---

### Post by angelus13 on 2009-11-04
Howzit guys,

this is insane...i just had a similar problem..
i was surfing the net normally and torrents were running, then all of a sudden..popup for keyring password auth. and then twice, maybe about 10 times. I am using mobile 3g modem so initially I thought it was a problem with the provider. Called them and they were doing some upgrades, so I waited an hour and still nothing, So I rebooted into windows and tried and everything is working alright. 

In karmic I can now connect without any problem, ie the keyring is not coming up all the time, but the net is not working. Funny thing is that the torrents are responding and are downloading. I cannot access my mailserver, nothing else is working other than my torrents.


Can someone please help me!!!!!!!!

---

### Post by jkmonto on 2009-12-05
same problem here, 
it keeps asking for the WEP key, I triple checked the key... sometimes, but not lately, it used to getting online after puting in the ke a few times, but lately it just tries and tries and I can't get to the network...
I tried to switch to WICD but it just doesnt recognizes my wireless card, I don't know if it is because I use ndiswrapper, but the deal is that my pc does not see any available network, I went back to network manager but everything was the same, however, it has to be related to the program that stores the keyring or the passwords, because I have a non protected wifi network and it gets acces to this network without any problem... I need some help guys... I'm really desperated! please!

---

### Post by uncaspi on 2009-12-05
Will you post /etc/network/interfaces

---

