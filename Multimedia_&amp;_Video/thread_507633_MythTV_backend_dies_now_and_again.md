---
title: "MythTV backend dies now and again"
date: 2007-07-23
forum: Multimedia &amp; Video
---

### Post by timefortea on 2007-07-23
Hi,
I have got MythTV up and running ok on my machine. I connect to it via MythWeb and it records for me - most of the time. It seems though, that now and again the backend dies with no explanation. This could be in a couple of days, hours or minutes time - and it could be during recording or when it is just sitting there. There is nothing unusual in the log:

```
2007-07-23 10:47:34.377 Scheduled 2 items in 0.1 = 0.06 match + 0.01 place
2007-07-23 10:48:56.751 DVBSignalMonitor(0)::constructor(3,Warning, can not count Uncorrected Blocks): Operation not supported
2007-07-23 10:48:56.784 EITScanner: Now looking for EIT data on multiplex of channel 701
2007-07-23 14:00:49.650 Using runtime prefix = /usr
2007-07-23 14:00:49.814 New DB connection, total: 1
2007-07-23 14:00:49.846 Connected to database 'mythconverg' at host: localhost
```

2pm is the time I restarted the backend when I discovered it was down. The messages logged at 10:48 were logged lots of other times during the time the application was up, so i have assumed they are ok. No programmes were scheduled until 12 noon.

I am running Feisty Fawn, apt says the MythTV package is mythtv_0.20-svn20070122-0.0ubuntu6_all.deb.
The TV card is a Nebula PCI, running in an Athlon XP 2200 / Abit KX7-333 motherboard.

Any ideas? The setup is great but if I can't trust it to record anything, its not much use...

---

### Post by MrHippocampus on 2007-07-23
Well, since the last thing in the log is related to scanning for EIT data, I would suggest that you turn this feature off (you should be able to get the channel listings from other sources). I know on the card that I have (Nova 500) there is a problem where the card can sometimes disconnect itself when you do an EIT scan, this may be a similar problem.

---

### Post by timefortea on 2007-07-25
I'll keep an eye out to see if it keeps dying when it does the scan - is there a better/as good source for channel data in the UK?

Thanks.

---

### Post by MrHippocampus on 2007-07-25
[This]("http://parker1.co.uk/mythtv_id.php") page has some information on getting channel data from the internet, I havent tried this myself so I wish you the best of luck :)

---

### Post by timefortea on 2007-07-26
Thanks for the info, I might just have to try it out, it had died again this morning, although for the first time I got a stack trace:

```
07-07-26 05:24:05.307 EITScanner: Now looking for EIT data on multiplex of channel 11
*** glibc detected *** /usr/bin/mythbackend: free(): invalid next size (fast): 0xabd246f8 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb5a717cd]
/lib/tls/i686/cmov/libc.so.6(cfree+0x90)[0xb5a74e30]
/usr/lib/libstdc++.so.6(_ZdlPv+0x21)[0xb5c32d11]
/usr/lib/libmythtv-0.20.so.0(_ZN4QMapIiiED1Ev+0x4f)[0xb7915709]
/usr/lib/libqt-mt.so.3(_ZN13QRegExpEngine5StateD1Ev+0x51)[0xb64ed5c1]
/usr/lib/libqt-mt.so.3(_ZN10QPtrVectorIN13QRegExpEngine5StateEE10deleteItemEPv+0x34)[0xb64ed614]
/usr/lib/libqt-mt.so.3(_ZN8QGVector5clearEv+0x65)[0xb64d9937]
/usr/lib/libqt-mt.so.3(_ZN10QPtrVectorIN13QRegExpEngine5StateEE5clearEv+0x1d)[0xb64edaa3]
/usr/lib/libqt-mt.so.3(_ZN10QPtrVectorIN13QRegExpEngine5StateEED1Ev+0x2b)[0xb64edb25]
/usr/lib/libqt-mt.so.3(_ZN13QRegExpEngineD1Ev+0xa4)[0xb64e515e]
/usr/lib/libqt-mt.so.3[0xb64eb628]
/usr/lib/libqt-mt.so.3(_ZN7QRegExp16invalidateEngineEv+0x52)[0xb64eb696]
/usr/lib/libqt-mt.so.3(_ZN7QRegExpD1Ev+0x1d)[0xb64eb9ed]
/usr/lib/libqt-mt.so.3(_ZN7QString7replaceERK7QRegExpRKS_+0x5e7)[0xb64f78d7]
/usr/lib/libmythtv-0.20.so.0(_ZNK8EITFixUp5FixUKER7DBEvent+0x131)[0xb7b4801d]
/usr/lib/libmythtv-0.20.so.0(_ZNK8EITFixUp3FixER7DBEvent+0x110)[0xb7b4aeb6]
/usr/lib/libmythtv-0.20.so.0(_ZN9EITHelper13ProcessEventsEv+0xc5)[0xb7b3a831]
/usr/lib/libmythtv-0.20.so.0(_ZN10EITScanner12RunEventLoopEv+0xe2)[0xb7b451a4]
/usr/lib/libmythtv-0.20.so.0(_ZN10EITScanner14SpawnEventLoopEPv+0x322)[0xb7b45e7e]
/lib/tls/i686/cmov/libpthread.so.0[0xb5c6e31b]
/lib/tls/i686/cmov/libc.so.6(clone+0x5e)[0xb5ad957e]
======= Memory map: ========

```

---

### Post by timefortea on 2007-08-04
Time for a quick update on this: I didn't have much luck with the XMLTV method, although I didn't try all that hard. Instead I created a script which is called from crontab every minute, to check that the mythbackend is still running, and if not it restarts it. I know this isn't perfect, if it gets restarted half way through a recording, I think it will overwrite what was recorded before the crash with what is recorded after it.

Does anyone know of a way to contol the EIT scanner, to say only scan once a day? Not sure if its even possible but who knows.

---

### Post by Scorpuk on 2007-08-04
woah I have the exact same problem. I thougth it was something to do with my install.

But I get the exact same problem in that my backend can stop working for no apparent reason.

If I run mythfrontend from a terminal then exit and then try and stop the backend I get a whole lot of text whizzing by.


Next time this happens I'll try and copy n paste into a post.


Oh and the other thing that I get, and is why I thought it was down to my install, is that my computer also drops from my network meaning I also cant get to it through mythweb. :(


Anywho upgrade coming to backend only mdia server sometime soon :D

---

### Post by mabovo on 2007-08-04
Hello, Need help installing MythTV

Do I need to install all these packages in order to have MythTV running on my PC ?

marcos@linux-ubuntu:~$ sudo apt-get install mythtv
[sudo] password for marcos:
Lendo lista de pacotes... Pronto
Construindo árvore de dependências       
Reading state information... Pronto 
Os pacotes extra a seguir serão instalados:
  gawk libdbd-mysql-perl libdbi-perl libfame-0.9 libmysqlclient15off
  libmyth-0.20 libnet-daemon-perl libplrpc-perl libpvm3 libqt3-mt-mysql
  mysql-client mysql-client-5.0 mysql-common mysql-server mysql-server-5.0
  mythtv-backend mythtv-common mythtv-database mythtv-frontend
  mythtv-transcode-utils ntp pwgen transcode
Pacotes sugeridos:
  dbishell libcompress-zlib-perl mysql-doc-5.0 tinyca mythweb mythmusic
  mythweather mythgallery mythdvd mythvideo mythgame mytharchive ntp-doc
  libdvdcss xvid4conf
Pacotes recomendados:
  pvm mailx mythtv-doc mythtv-themes xmltv-util sox mjpegtools toolame
  transcode-doc
Os NOVOS pacotes a seguir serão instalados:
  gawk libdbd-mysql-perl libdbi-perl libfame-0.9 libmysqlclient15off
  libmyth-0.20 libnet-daemon-perl libplrpc-perl libpvm3 libqt3-mt-mysql
  mysql-client mysql-client-5.0 mysql-common mysql-server mysql-server-5.0
  mythtv mythtv-backend mythtv-common mythtv-database mythtv-frontend
  mythtv-transcode-utils ntp pwgen transcode
0 pacotes atualizados, 24 pacotes novos instalados, 0 a serem removidos e 0 não atualizados.
É preciso fazer o download de 55,9MB de arquivos.
Depois de desempacotar, 158MB adicionais de espaço em disco serão usados.
Quer continuar [S/n]? 

Translating: Do you want to continue ?

---

### Post by timefortea on 2007-08-05
mabovo, I would say yes they are all needed. 

Scorpuk, about 2/3rds down [this]("http://parker1.co.uk/blog/?page_id=25") page, there is a suggested simple script to restart the backend if it dies. I did something similar - the only thing I would like to do now is change the EIT scan so that it happens less frequently but I don't know if that is possible. MrHippocampus posted a link a few posts up, on how to get the XMLTV stuff working instead (it pulls the programme data from the Radio Times, rather than over the air) but I had various problems with it and settled on the restart solution for now.

---

### Post by Scorpuk on 2007-08-27
Update:

I am now VNC'ing into my machine every 3 days to switch EIT on, to get new listings, and then off once updated.


So far my machine has been up for 11 solid days with no problems.



Deff need to look into internet listings as an alternative. :)

---

### Post by parker13 on 2008-04-03
I don't have a Nova-T 500 card myself, but I've been trying to help someone who does and is having the same problem as you guys. It seems that he's made some progress:

> Thought I'd give  you a little update on the crashes I was experiencing. Turns out if I delay the time the system should wait for a tuner to be idle before doing an eit scan to the maximum the system doesnt crash as often. And the times it does seem to be at times of extremely poor signal, due to rain etc. But this is where your workaround script saves the day. Well I ran the restart command manually today and it worked so I have setup the cron now so let's see if it ever crashes again.

Sohail Anwar 	

Hope it helps.
Garry.

---

### Post by MrHippocampus on 2008-04-05
On the issue of the nova 500 disconnects, thats (hopefully) now been fixed, turns out it was a bug in the usb stuff kernel which was causing the problems. The patch is apparently in Hardy's kernel already :)

---

