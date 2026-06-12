---
title: "ADSL with wireless"
date: 2009-07-02
forum: Networking &amp; Wireless
---

### Post by surajullas on 2009-07-02
Hi frnds
i have a desktop and laptop
i want to connect to wireless ADSL but though i can see it on my laptop i am unable to connect as it always ends in an disconnectd message

i think i have to enter my username and password for the broadband connection for acessing the wireless but don't know how plz help me

---

### Post by computer13137 on 2009-07-03
OK, I think the reason nobody answered your question is because it doesn't make sense.  I'm kind of confused by what you mean too. :|

That being said, I'm going to subscribe to this thread in case I can help you further, but first I need a few things cleared up.

1) When you say "wireless ADSL" do you mean your friend has ADSL and a wireless router, and you are trying to connect to the router?  There is no such thing as "wireless ADSL".

2) If the wireless network is encrypted, it may need a WEP or WPA key to gain access.  Your friend should know this because they would need to use it to gain access to the network too.  However, the wireless router has nothing to do with the credentials for the ADSL.  The access code is quite likely a different password.

-Kirk

---

### Post by superprash2003 on 2009-07-03
post output of
1)sudo iwlist scan
2)iwconfig

does it give any error when you try to connect?

---

### Post by surajullas on 2009-07-04
> **computer13137 said:**
> OK, I think the reason nobody answered your question is because it doesn't make sense.  I'm kind of confused by what you mean too. :|

That being said, I'm going to subscribe to this thread in case I can help you further, but first I need a few things cleared up.

1) When you say "wireless ADSL" do you mean your friend has ADSL and a wireless router, and you are trying to connect to the router?  There is no such thing as "wireless ADSL".

2) If the wireless network is encrypted, it may need a WEP or WPA key to gain access.  Your friend should know this because they would need to use it to gain access to the network too.  However, the wireless router has nothing to do with the credentials for the ADSL.  The access code is quite likely a different password.

-Kirk
hi computer13137
1)
i will explain more so that u can help me
i have a ADSL modem/router that is i have both wired and wireless
it is connected to my desktop (win XP) through the wired connection
i want to connect it to my laptop with ubuntu9.04 through the wireless connection 

2)
i am a complete newbie to ubuntu in terms of connecting to internet but have used it earlier for multimedia purposes

i have a username and password which i don't know where to give for this wireless connection

when i boot my laptop and switch on my wireless i see my wireless connection but i am unable to connect to internet bcoz of the obvious reason that i have to give the username and password but i don't know where

can u plz help me step by step???

---

### Post by surajullas on 2009-07-04
> **superprash2003 said:**
> post output of
1)sudo iwlist scan
2)iwconfig

does it give any error when you try to connect?
1)
suraj@surajs-DELL:~$ sudo iwlist scan
[sudo] password for suraj: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:1B:DA:49:44:BD
                    ESSID:"UTStarcom"
                    Mode:Master
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=100/100  Signal level:-34 dBm  Noise level=-87 dBm
                    Encryption key:off
                    IE: Unknown: 0009555453746172636F6D
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD090010180200F4000000
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:tsf=0000000042bc6183
                    Extra: Last beacon: 48ms ago

pan0      Interface doesn't support scanning.
2)

suraj@surajs-DELL:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:"UTStarcom"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Tx-Power=15 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.



no there is no error message as such just that after trying to connect i get the reply disconnected

---

### Post by computer13137 on 2009-07-04
I think you will find this easy to follow:  [https://help.ubuntu.com/8.04/internet/C/wireless-connecting.html](https://help.ubuntu.com/8.04/internet/C/wireless-connecting.html)

Cheers,
Kirk

---

### Post by surajullas on 2009-07-05
> **computer13137 said:**
> I think you will find this easy to follow:  [https://help.ubuntu.com/8.04/internet/C/wireless-connecting.html](https://help.ubuntu.com/8.04/internet/C/wireless-connecting.html)

Cheers,
Kirk
i tried it out but i am not sure what type of security is in use first of all.
what i know is i have a username and password i tried leap in all the other security i can't see a place to enter my username and password

also i am not sure if 8.04 and 9.04 has the same network manager

---

### Post by computer13137 on 2009-07-05
Sorry, my bad for linking you to the wrong page.

[https://help.ubuntu.com/9.04/internet/C/connecting-wireless.html](https://help.ubuntu.com/9.04/internet/C/connecting-wireless.html)

Additionally, your ADSL password will not work.  My guess is you have WEP.  I've never seen any routers that use LEAP.

If you go to your router's wireless configuration page you can configure security settings.

-Kirk

---

### Post by surajullas on 2009-07-06
> **computer13137 said:**
> Sorry, my bad for linking you to the wrong page.

[https://help.ubuntu.com/9.04/internet/C/connecting-wireless.html](https://help.ubuntu.com/9.04/internet/C/connecting-wireless.html)

Additionally, your ADSL password will not work.  My guess is you have WEP.  I've never seen any routers that use LEAP.

If you go to your router's wireless configuration page you can configure security settings.

-Kirk
can u plz tell me how to find my routers wireless configuration page

i have already tried 192.168.1.1, 192.168.1.0

but both has no reply


ok i will get back soon

---

### Post by computer13137 on 2009-07-06
Could you paste the results of the following command so we can see how your network is setup?

```
ifconfig
```

Cheers,
Kirk

---

### Post by surajullas on 2009-07-10
thank you

i have atlast connected to wireless through ubuntu

it is working well

what i did was

1) Resetted the modem
2) Got into the configuration page to change my connection from bridge to PPOE by giving my usename and password in the modem (sorry but i didnt knew it until recently)
 but i have one question

1)is there some way that the modem is connected in bridge mode itself and still i can connect to it through wireless itself???

---

