---
title: "MYTHTV - Live TV no channel lock"
date: 2008-03-15
forum: Multimedia &amp; Video
---

### Post by Boexli on 2008-03-15
Hi all,


I have successfully installed my Terratec PCI Cinergy C card. I can watch DVB with Kaffeine or Mplayer without any issues (except HD does not work - will have to address this issue a bit later).

In MYTHTV I have successfully imported the channels.conf which I created using scan. However when trying to watch LIVE TV I allways get the message that there is no channel lock. 

Does anyone know what needs to be done to get this solved. It is espesially annoying since the card works perfectly with any other player.

Thanks a lot for any feedback / Nick

---

### Post by reesje on 2008-04-02
Hi Nick

Just to let you know, I have the exact same problem. The backend searches and finds the channel, no problem, but in the frontend it says no lock and I can see in the bottom of the screen that the signal level is 0% But it still shows what show is running (set up for EIT, so it is getting the info via the DVB signal somehow). I have asked the same question over at mythtvtalk, but it seems like no one knows the answer. I too can watch DVB via kaffeine and other application. I wonder if I can make the conclusion that the DVB HW is fine and I should look for my problem elsewhere or that there still may be a HW incompatability problem.

I have an MSI TV@nywhere cardbus TV tuner.

Can you do a search of the channels without using the channels.conf file? When you search, does the backend indicate that you have a signal?

BR,
René

---

### Post by Boexli on 2008-04-12
Hi Rene

thanks for your reply. yes i can scan the channels directly using the MYTHV scan function. Maybe someone else knows how to get it fixed? cheers Nick

---

### Post by The-Wappy-One on 2008-04-21
Hi there

I have this exact same problem! fine in mplayer.. but no lock in Myth (a Partial on radio stations)

From the days of searching what i've come across is apparently its a bug in version 20.2?

If you revert to earlier version 0.18 - 0.19 and then input the channels and then UPGRADE TO 0.20.2.  it will work?

but i havent been able to test yet still trying to find a older version lol ... but im hoping one of you lot might be able to try if you havent had any luck yet.. if i do get a copyof a older version i will let you guys know!

Wappy

---

### Post by Boexli on 2008-05-04
This is the bug - fixing it manually channel by channel is a cumbersome exercise but works - there is a perl scribt but have not tried it yet. Cheers Nick 
----------------

If its a DVB-C device, you may be affected by the following bug:

[http://svn.mythtv.org/trac/ticket/3640](http://svn.mythtv.org/trac/ticket/3640)

Without the little haxie you could have incorrect multiplex
information in MythTV. Check over the frequencies in the database and
compare with your channels.conf.

---

