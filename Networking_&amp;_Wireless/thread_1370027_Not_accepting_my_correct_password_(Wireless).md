---
title: "Not accepting my correct password? (Wireless)"
date: 2010-01-01
forum: Networking &amp; Wireless
---

### Post by mikerpiker on 2010-01-01
Hi all,

Before I installed Ubuntu, I was having the following problem on Windows XP: 

My computer would try to connect to the wireless network at my parents house, but when I tried to enter the password (it's WEP protected, I think) it wouldn't accept it -- it would try to connect again for a little while, and then would ask me for the password again.

After I installed Ubuntu, but before I upgraded to 9.10 (on the two distributions before it) I could connect to the network just fine.

Now that I'm on 9.10 I'm having the same problem I had when I was on Windows XP -- it doesn't seem to be accepting my password.

I have tried all the different dropbox options -- WEP 40/128 bit key, WEP 128-bit passphrase, LEAP, and Dynamic WEP -- but none have worked.\

Any ideas?  This is driving me crazy!

I have an Acer Aspire 5500Z.

Network controller: Intel PRO/Wireless 2200BG [Calexico2] Network Connection (rev 05)

---

### Post by mikerpiker on 2010-01-01
My ethernet controller is: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02) -- I'm not sure if that's important.

---

### Post by als123 on 2010-01-09
I recently ubuntu 9.1 about 5 days ago and was able to access my wireless network which is WEP protect. I just installed numerous updates and now I can't get on my wireless.  It keeps asking me for my WEP password.

The only thing I saw was my router password is 64 bit encrypted. That is not one of the options offered as stated in mikerpiker's first post above.

I hope someone can offer some help.  If not, I guess I may have to start from scratch with the original installation disc, not a pleasant thought.

I also have XP

Thanks

---

### Post by bkratz on 2010-01-09
> **als123 said:**
> I recently ubuntu 9.1 about 5 days ago and was able to access my wireless network which is WEP protect. I just installed numerous updates and now I can't get on my wireless.  It keeps asking me for my WEP password.

The only thing I saw was my router password is 64 bit encrypted. That is not one of the options offered as stated in mikerpiker's first post above.

I hope someone can offer some help.  If not, I guess I may have to start from scratch with the original installation disc, not a pleasant thought.

I also have XP

Thanks

According to wikipedia

Standard 64-bit WEP uses a 40 bit key (also known as WEP-40), which is concatenated with a 24-bit initialization vector (IV) to form the RC4 traffic key. At the time that the original WEP standard was being drafted, U.S. Government export restrictions on cryptographic technology limited the key size. Once the restrictions were lifted, all of the major manufacturers eventually implemented an extended 128-bit WEP protocol using a 104-bit key size (WEP-104).

So 40 and 64 are really the same.

---

### Post by llawwehttam on 2010-01-09
broadcom and linux have never worked very well together. WPA2 seems to work fine but I have heared of a lot of problems with WEP.

My temporary solution is to remove the password and set up MAC address filtering.

---

### Post by bkratz on 2010-01-09
> **llawwehttam said:**
> broadcom and linux have never worked very well together. WPA2 seems to work fine but I have heared of a lot of problems with WEP.

My temporary solution is to remove the password and set up MAC address filtering.



The original poster has an

Network controller: Intel PRO/Wireless 2200BG [Calexico2] Network Connection (rev 05)

Intel wireless card.

---

### Post by lisati on 2010-01-09
Suggestion: Go to preferences->network connections and see if you have multiple entries for your networks on the Wireless tab.

---

### Post by als123 on 2010-01-09
How do I do a MAC filtering?

---

### Post by als123 on 2010-01-09
I only have the one network in the wireless connections

---

### Post by als123 on 2010-01-11
Ok All, This is an offical DUH moment.  I had accidently pushed the physical wireless network disconnect button on the front of my laptop, thereby creating all the above problems.  
 
Hopefully, someone else will read this first and not have egg on their face like I do.

---

### Post by martinr on 2011-06-25
Dear Mikerpiker or anyone else, did you ever find a solution to the problem?

I have a similar/same problem: 
Ubuntu 10.04 has a hard time connecting wirelessly using WEP encryption with a 64 bit/40 bit passkey (hidden network). It scans for ages and sometimes asks for a password, but only connects occasionally. When it finally does make a connection, then after a little while of use it suddenly drops the connection and the misery starts all over again. An interesting detail is that the notification area says that the connection was lost, while it actually still works for a few seconds after that message. Previously I ran Ubuntu 8.04 (Hardy), which worked like a charm out of the box with the same hardware and wireless router (the setting haven't changed)?

Laptop: Aces Aspire 5500Z
Wireless Card: [device] WM3B2200BG, [IC] 1000M-B2200BG
Wireless Driver: [messages] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.2kmprq

---

