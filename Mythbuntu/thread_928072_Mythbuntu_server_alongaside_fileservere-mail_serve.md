---
title: "Mythbuntu server alongaside fileserver/e-mail server etc.?"
date: 2008-09-23
forum: Mythbuntu
---

### Post by Tuskan360 on 2008-09-23
I want to create a server that would act a an e-mail server, a file server (including remote access, ftp) and possibly a web server.

I also want the same server to act as a media server/centre.  I would like to put a twin digital tuner in it and use it as a PVR.  I would then access videos on it using other computers over the network.  I would also like to be able to connect a screen up to it directly and watch the TV live or recordings.  The other computers would mostly run windows XP/vista.

Is mythbuntu going to do everything I need or are there going to be problems with this setup:

1xShuttle KPC K45 Barebone, 1xCorsair 512MB DDR667, 1xIntel Celeron E1200, 2xSamsung 750GB SATA2, 1xMythbuntu Hardy, 1xNova-T 500 Dual,

---

### Post by mrand on 2008-09-23
> **Tuskan360 said:**
> I want to create a server that would act a an e-mail server, a file server (including remote access, ftp) and possibly a web server.

I also want the same server to act as a media server/centre.  I would like to put a twin digital tuner in it and use it as a PVR.  I would then access videos on it using other computers over the network.  I would also like to be able to connect a screen up to it directly and watch the TV live or recordings.  The other computers would mostly run windows XP/vista.

Is mythbuntu going to do everything I need or are there going to be problems with this setup:

1xShuttle KPC K45 Barebone, 1xCorsair 512MB DDR667, 1xIntel Celeron E1200, 2xSamsung 750GB SATA2, 1xMythbuntu Hardy, 1xNova-T 500 Dual,

Assuming you are talking about doing very light email / web / file server activity for just a couple of casual users at home, I think the CPU would probably keep up, but I'd personally put at least a gigabyte of memory (so all programs can stay resident and not be swapped, and still have some memory left over for web and disk cache and such).  2 G was so cheap, that is what I went with, but otherwise my setup is pretty much what you describe, PLUS I use the machine with vnc or nx as my desktop sometimes (Firefox has 400 MB of memory used up currently, in addition to the Myth components [front+back+sql] using 200 MB).

Have fun,

[INDENT]   Marc[/INDENT]

---

### Post by volkswagner on 2008-09-23
I had asked a similar question a while back.  One comment stuck in my head from the following response.
[QUOTE=hermanAB]
However, you may be trying to do too much on a single machine. The issue is not just processor load, but ease of maintenance.[/QUOTE]

As mrand mentioned, it depends on web usage.  Folks are often tweaking their home theater setup.  A web server you want to set it and forget it.  

If it is truly limited to a casual web site go ahead.  Mythweb is already running on apache if you enable it.

Mine and hermaAB's 2cents

---

### Post by Tuskan360 on 2008-09-24
Thanks guys, it is really just a couple of casual users, me mostly plus my family occasionaly so it sounds like this should work.

---

### Post by volkswagner on 2008-09-24
I never did virtual hosting with mythweb.  You may need to run your website or Mythweb on a different port than the default port :80, not sure.  Let us know how it works out.

---

### Post by anonymousdog on 2008-09-24
It works fine...non-php websites and such.

---

### Post by Quazza on 2009-02-20
I would like to try this maybe I might have a go at adding some more use to my server and see what happens.

Quazza

---

### Post by ian dobson on 2009-02-21
Hi,

I'm doing that at the moment. My backend (Quad Q6600, 8Gb Ram 4Tb RAID array, 3 Tuners) runs ubuntu server with the myth-backend package. The frontend runs a straight MythBuntu.

On my backend I run:-

1) Web server   - apache2
2) Email server - xmail
3) SQL server   - Mysql
4) Myth         - Mythbackend

If you going to run a dedicated server, I'd recommend you use the server install rather than the full ubuntu desktop with X-server etc.

Regards
Ian Dobson

---

