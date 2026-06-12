---
title: "Suddenly I couldn't connect internet the LAN way"
date: 2010-07-23
forum: Networking &amp; Wireless
---

### Post by DiegoTc on 2010-07-23
Hi 
Well I will tell you which was my problem.
I was on internet last night, all was good.
I left my laptop on stand by and today on the morning I could wake up my laptop so I turn it of the manua way. When I start again, I notice there is something going wrong

It said to me I don't have internet. I check the modem and yes I have internet, I check the lan cable and it looks it works fine. So I thought it was the ethernet card that was bad. So I restar again and enter with Windows 7, and yes I have internet. So it made be one problem of my Ubuntu.

I did an ifconfig and got the following
> 
lo        Link encap:Bucle local  
          Direc. inet:127.0.0.1  Másc:255.0.0.0
          Dirección inet6: ::1/128 Alcance:Anfitrión
          ACTIVO BUCLE FUNCIONANDO  MTU:16436  Métrica:1
          Paquetes RX:364 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:364 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:0 
          Bytes RX:26928 (26.9 KB)  TX bytes:26928 (26.9 KB)


It doesn,t detects the ethernet connection :(

---

### Post by Iowan on 2010-07-23
Some updates Disable NM. Right-click the applet and verify "Networking Enabled" is checked.
[Here]("http://ubuntuforums.org/showthread.php?t=1505217") is another thread that might be helpful.

---

### Post by DiegoTc on 2010-07-23
Thanks
That was the problem I don't who it got disable. But its fine
Thanks

---

### Post by Iowan on 2010-07-23
\\:D/ Woohoo!
Tag it [[SOLVED]]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads")  :D

---

