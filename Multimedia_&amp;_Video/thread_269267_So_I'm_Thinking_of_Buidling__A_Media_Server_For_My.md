---
title: "So I'm Thinking of Buidling  A Media Server For My House, Anyone got advice?"
date: 2006-10-01
forum: Multimedia &amp; Video
---

### Post by steve k on 2006-10-01
So,

I have an old wireless router and an old desktop computer that I'm not doing too much with and I've also got some low power radio transmitters lying around the house so what I was thinking I'd do was:

- Connect the computer to the router and the radio transmitter to the back of the computer so that I could select and play music from a large library of MP3s and OGGs on the computer anywhere in my house, controlled by my laptop or some other similar device.  

Ideally, I'd be using something like a regular playlist managing tool from my desktop to do this.  Like amarok or something (even though I use gnome I prefer amarok to listen or other such gnome players..), I'd also like to be able to rip cds right into it, with some element of control over how each one is tagged and filed, using something like grip, or something that presents the features of grip.  I'm not too hung up on user interface, if this all goes down in Ncurses or something it'd be fine with me, so long as when i control it from my laptop it's no more bother than looking at a little icon in my system tray or something.  

So I'm looking for advice, has anyone done this?

One way of doing it I thought of would be to login remotely to the desktop on the desk computer through the network, i see that GDM has all these remote login options, has anyone ever done that? that seems very very cumbersome.

ideally, i'd be able to log in through some kind of music playing application on my computer that would know to play remote media from the remote source and local media through the laptop's speakers, not simultaneously, but if they were after eachother in a playlist or something...

is this weird/dumb?

---

### Post by skymt on 2006-10-01
Have you looked into [MPD](http://www.musicpd.org/)?

---

### Post by water on 2006-10-05
You might want to have a look at Slimserver from Slimdevices - it's gpl and works perfectly with or without Slimdevices' hardware players.

[http://www.slimdevices.com/pi_features.html](http://www.slimdevices.com/pi_features.html)

:water

---

### Post by jfdill_2 on 2006-10-05
I set up [Subsonic]("http://subsonic.sourceforge.net/index.html") running via JBoss and even my wife was impressed :) It's JSP based, so you need a Tomcat server, I'm just using the one in JBoss.  Subsonic is a streaming server using a Java implementation of shoutcast.  It seems to work best for me with Amarok on Linux and Winamp on Windows.

---

### Post by dannyboy79 on 2006-10-05
i previously had run cabling from my room to all my receivers in my house, the cable was the one that has a headphone jack on one end and rca plugs on the other. i then turned on my desktop (ubuntu) and turned on my wireless laptop, did a remote desktop using xvncviewer and was able to control what i was listening to when I was downstairs using my laptop screen to control what I played thru my ubuntu desktop. i used xmms, it was really cool cause my friends aren't like me all into computers and stuff, so they were all like, dude this is so awesome. i was just glad that i didn't have friends going in and out of my room to select what they wanted to play from my 5 gb of mp3's!!!

---

