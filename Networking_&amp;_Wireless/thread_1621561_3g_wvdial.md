---
title: "3g wvdial"
date: 2010-11-14
forum: Networking &amp; Wireless
---

### Post by lhdror on 2010-11-14
k i successfuly got online using wvdial and zte mf636/mf637 (i have two) 

```

[Dialer Defaults]
Modem = /dev/ttyUSB2
Modem Type = Analog Modem
ISDN = 0
Baud = 460800
Dial Attempts = 1
Username = guest
Password = guest
Init1 = AT+CGDCONT=1,"IP","uinternet"
Phone = *99#
Stupid Mode = 1

```

but i would like to force the zte card to use only 3g or higher how do i do that? 

(not gprs - yes umts and higher)

i was using network-manager but its no good with zte`s makes
trouble and "wvdial" seams like the real thing regardless 

thanks in advance

---

### Post by lhdror on 2010-11-15
if not a soluion doz anyone know a good manual fo at commands in wvdial ???

---

### Post by alexfish on 2010-11-16
Hi

Have a look here

[How To : Mobile Broadband Connections [ Ubuntu 10.10 : 10.04 : 9.10 ]]("http://ubuntuforums.org/showthread.php?t=1466490") 

With Reference Post  to post  #[**8**]("http://ubuntuforums.org/showpost.php?p=9268456&postcount=8")  (use at own risk)

alexfish

---

### Post by lhdror on 2010-11-16
thanks a million 

got it

AT+ZSNT=0,0,0 (Auto) - Default 
AT+ZSNT=1,0,0 GPRS Only 
AT+ZSNT=2,0,0 3G Only 
AT+ZSNT=0,0,1 GPRS Preferred 
AT+ZSNT=0,0,2 3G Preferred 

its for sure good with zte mf636 didnt test mf637

---

