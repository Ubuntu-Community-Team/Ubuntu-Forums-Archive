---
title: "Refreshing the IP address"
date: 2006-06-14
forum: Networking &amp; Wireless
---

### Post by matjaz_pirnovar on 2006-06-14
Internet connection stopped working (ethernet).

Internet connection is searching for web sites but then it says "time has expired, try later".

I'm using ethernet connection, no router.

I asked the technical support of my service provider (NTL in UK) and they said it's probably because IP address needs to be refreshed (or rebooting computer).
Unfortunatelly they don't offer support to linux systems, only Windows  :(

My question is, how do you refresh IP address in Ubuntu 6.06?

I believe this problem started when I turned on the computer yesterday and there was a note that Ubuntu was not root-mounted (or smth similar) again after 30 times of using it. So Ubuntu did it automatically. I'm not familiar with what it says. Is it possible that I need to refresh the IP address or it could be something else?

Thanks very much.

Matjaz:p

---

### Post by superjet on 2006-06-14
[QUOTE=matjaz_pirnovar]Internet connection stopped working (ethernet).

Internet connection is searching for web sites but then it says "time has expired, try later".

I'm using ethernet connection, no router.

I asked the technical support of my service provider (NTL in UK) and they said it's probably because IP address needs to be refreshed (or rebooting computer).
Unfortunatelly they don't offer support to linux systems, only Windows  :(

My question is, how do you refresh IP address in Ubuntu 6.06?

I believe this problem started when I turned on the computer yesterday and there was a not that Ubuntu was not root-mounted (or smth similar) again after 30 times of using it. I'm not familiar with what it says. Is it possible that I ned to refresh the IP address or it could be something else?

Thans very much.

Matjaz:p[/QUOTE]


 Hi Matjaz,
 I am sitting at a Windoze box in training, so bear with me I don't have the exact paths infront of me.
 You can go to Administrator, network, and click on your network card and deactivate the network card. Then reactivate it and you should be good to go.
 If you perfer command line, try "sudo ifconfig eth0 down" (assuming your network card is eth0 here) then "sudo ifconfig eth0 up"

 If that doesn't work, please run ifconfig and post the results.


 Good luck,
 Jamie

---

### Post by 5-HT on 2006-06-14
Is your IP static or dynamic?

To check your IP:
```
 ifconfig 
``` Are you pulling a 169.x.x.x address? 

a) If you do need to refresh your IP, one way would be to just reboot.
I would suggest a full power-cycle on the modem to be safe.

1. Shutdown the computer
2. Unplug the modem
3. Wait ~15 seconds and plug the modem back in
4. Wait until the modem has block sync (you can tell by the lights), or just wait   ~ 20-30 seconds.
5. Turn on the computer

b) If you want to manually refresh your IP:

1. You need to find out what Ubuntu is recognizing your NIC as (e.g., eth0). The output from 'ifconfig' should have an entry for 'lo' and an additional one(s) for any NIC(s). Usually the first network card is 'eth0'.

2. To deactivate the NIC (use the appropriate device if not eth0)```
 sudo ifdown eth0 
``` 
3. To activate the NIC```
 sudo ifup eth0 
``` 
4. To request an IP from a DHCP server (may be needed if using DHCP)
```
sudo dhclient eth0 
``` 

HTH.

*EDIT: too slow, and superjet provided a walkthrough for doing the same from the GUI (system -> administration -> networking).

*EDIT2: that message you received about Ubuntu needing to check the filesystems after 30 mounts is perfectly normal, and is a default setting. It may be just a coincidence that both things occured at the same time. It's unlikely, but possible, that the two are related.

---

### Post by rccharles on 2006-06-14
[QUOTE=matjaz_pirnovar]Internet connection stopped working (ethernet).
I asked the technical support of my service provider (NTL in UK) and they said it's probably because IP address needs to be refreshed (or rebooting computer).
[/QUOTE]
Many technical support centers personnel read from prepared scripts.  They may not be correct.
[QUOTE=matjaz_pirnovar]
I believe this problem started when I turned on the computer yesterday and there was a note that Ubuntu was not root-mounted (or smth similar) again after 30 times of using it. So Ubuntu did it automatically. [/QUOTE]
This may be your real problem.

re-boot

You could look in the log.
:?:/var/syslog
:?:dmesg
:?: some system log viewer




Robert

---

### Post by matjaz_pirnovar on 2006-06-15
Thanks very much guys.

I will try to implemet suggested today. Will post results.

BTW: I did fully re-start the computer and the broadband modem, waited in between etc. Problem remains.

I use dynamic IP address.

(Not sure I know which ethernet card you're refering to. Probably you mean the card that must be installed in the comput. harware - otherwise I don't use any external ethernet cards (only cable broadband modem without router).)


Matjaz

---

### Post by matjaz_pirnovar on 2006-06-16
Hi Guys,

I have done all you suggested. I was able to renew-refresh IP address, either in terminal or through GUI networking. Reply in terminal was positive - IP address renewed. Also I rebooted computer as instructed. But I still didn't get the connection.

The problem was in my service provider NTL in United Kingdom. They disconnected me due to some unpayed bills which prove as a mistake. So...service provider's fault... ;)  BTW, I'm a bit dissapointed on their informing system, didn't have a clue it could be such a reason, I would have expected to receive a note from service provider...so I wouldn't have to go through detailed examination of computer's configuration etc.
(which is excellent for learning though ;)  )

Looks like refreshing the IP address wasn't the case so simultaneous disconnection and root-mountaing (hope I named it right) after 30 start-ups were not linked.

Many thanks again for your support.  I will keep an eye in forum and hopefully be able to help someone in similar situation.

;) 

Matjaz

---

### Post by 5-HT on 2006-06-16
[quote=matjaz_pirnovar]

Many thanks again for your support.  I will keep an eye in forum and hopefully be able to help someone in similar situation.

;) Matjaz[/quote]

Glad you got it working! 
Must be frustrating that your ISP's left hand didn't know what their right hand was doing, but at least you now know a few ways to release/renew your IP should the need arise.

---

