---
title: "Error connecting shoutcast server"
date: 2010-12-29
forum: Multimedia Software
---

### Post by btrajesh on 2010-12-29
Hello friends, 
I have been using Ubuntu for almost one year or so. I use to have a good experience with it. But, since last few days I have been experiencing something nuance with my Ubuntu and most particularly the Exaile player. 

It use to connect to the Shoutcast server fine. But, these days I can't connect it. 

Everytime I try to connect it; it shows the message, "Error connecting shoutcast server". 

Can you please let me know some simple suggestion which I can use to fix it?

I have tried reinstalling it along with the normal plugins that use to work fine. But nothing seems working .

Any suggestions?

Looking forward to your kind suggestion and help. 

Sincere regards, 
Rajesh

---

### Post by DapperMe17 on 2010-12-31
Rajesh,

About a week ago, Shoutcast changed it's API, or the way it sends data information. Since then, most players such as Exaile, Listen, Rhythymbox, etc...have been unable to populate Shoutcast streams into their interface, like they had up to about a week ago. 

It appears that those players only need to update their plugins. It's only a matter of time. 

I've read that Rhythymbox has since updated their plugin, so that it can again receive streams. 

Alternatively, you can temp listen to your favorite streams with your browser, or by manually pasting in the stream address to your player.

I hope this helps you!
Good luck

---

### Post by RedRat on 2011-01-04
> **DapperMe17 said:**
> Rajesh,

About a week ago, Shoutcast changed it's API, or the way it sends data information. Since then, most players such as Exaile, Listen, Rhythymbox, etc...have been unable to populate Shoutcast streams into their interface, like they had up to about a week ago. 

It appears that those players only need to update their plugins. It's only a matter of time. 

I've read that Rhythymbox has since updated their plugin, so that it can again receive streams. 

Alternatively, you can temp listen to your favorite streams with your browser, or by manually pasting in the stream address to your player.

I hope this helps you!
Good luck
I have tried using the browser mode, Firefox 3, but the connection is terrible with almost continuous dropouts at 128k. If I can find the radio station from its own browser page, I can get realplay to replay the same stream very well, no drop outs. What ever plugin is put in Firefox does not appear to work very well.

---

### Post by tjones00 on 2011-01-06
I was messing with radio tray in crunchbang 10 (debian base) last night it is a simple tray based shoutcast player.

To get it working with debian 5 I had to enable gstreamer0.10-plugins-base, gstreamer0.10-plugins-good, gstreamer0.10-plugins-ugly. It could not connect without all 3 of those.

Perhaps it's the same with Ubuntu and your player.

---

### Post by RedRat on 2011-01-06
> **tjones00 said:**
> I was messing with radio tray in crunchbang 10 (debian base) last night it is a simple tray based shoutcast player.

To get it working with debian 5 I had to enable gstreamer0.10-plugins-base, gstreamer0.10-plugins-good, gstreamer0.10-plugins-ugly. It could not connect without all 3 of those.

Perhaps it's the same with Ubuntu and your player.
I have all of these gstreamer enabled in my installation. I have alternatives for getting to my favorite radio stations via totem, realplayer, and others. Right now, I hope that eventually Amarok will come around to the new shoutcast API.

Thanks!

---

### Post by Tekmbster on 2011-01-06
Hello as I am new to the forum and a converted Ubuntu User!  I run a Shoutcast Radio Network for an IRC Network that I am a Net Administrator.  For my server, I run Ubuntu 10.04 with WineTricks.  With WineTricks, I use an older version of Winamp (5.5), the Shoutcast DSP 1.9 for Windows and the Shoutcast DNAS 1.9.8 for Linux.  This combination allows me to stream and broadcast live.  I can also listen to streams with Winamp via WineTricks.  

I hope this helps a little bit.

---

### Post by RedRat on 2011-01-07
> **Tekmbster said:**
> Hello as I am new to the forum and a converted Ubuntu User!  I run a Shoutcast Radio Network for an IRC Network that I am a Net Administrator.  For my server, I run Ubuntu 10.04 with WineTricks.  With WineTricks, I use an older version of Winamp (5.5), the Shoutcast DSP 1.9 for Windows and the Shoutcast DNAS 1.9.8 for Linux.  This combination allows me to stream and broadcast live.  I can also listen to streams with Winamp via WineTricks.  

I hope this helps a little bit.
I have also Winamp too, but here is my problem with it, I run it under Wine, it resolves on my screen into too small an application, very tiny print. Hey, I am over 70 and the eyesight isn't what it used to be. I have found that if if I can find the url for the particular radio station I am interested in, I can paste that into RealPlay and get good reception. I just found that the plugin for Firefox AND Google Chrome and Opera suffer from the same problem of cut-outs and drops. Also Totem Player also works very well. It is clear that the problem lies in all of these browser's software and how the encoding is implemented. Perhaps the browser just consume far too much overhead. 

Thanks for your insight, I might go and give Winamp a new try. I used to use it exclusively when I was running Windows.

---

### Post by btrajesh on 2011-04-16
Thank you friends, for your kind concern. I have been using shoutcast server and listen to the online radio through browser, as you all have suggested. It works fine with it. 

But, I think, we still have to wait for few more months or even years till Ubuntu 11 will come into being. 

Lets have our finger crossed and hope for the good news to come. 

Have a wonderful time everybody. And, thanks a lot once again for your pronto reply. 

Take care, and keep posting helps and suggestions like this. 

God bless you all. 

Regards,
Rajesh

---

