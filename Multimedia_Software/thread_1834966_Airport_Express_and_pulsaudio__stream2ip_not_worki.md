---
title: "Airport Express and pulsaudio / stream2ip not working"
date: 2011-08-28
forum: Multimedia Software
---

### Post by midden on 2011-08-28
My Airport Express historically worked using the setup described [{here}]("http://www.makeuseof.com/tag/apples-airtunes-ubuntulinux/"). The problems were mainly that when audio stopped, the connection (and high traffic) to the AEX remained. Although not ideal, this was OK because at least it worked.

For a while now (the last six months or so) the AEX does not show up on the sound preferences. Or if it does, it appears as two or three entries but does not work. I tried stream2ip, when it connects the AEX appears in the sound prefs for about five seconds and then disappears (but stream2ip still shows a connection). Only local sound plays. The stream2ip manual is not clear on how to set this up, so perhaps I am doing something wrong.

Does anyone have a suggestion or alternative approach to get audio to play? Ideally I will use the MPoD iphone app to control music playing on mpd server.

I am running Ubuntu Maverick (64bit, pulseaudio 0.9.21-63-gd3efa-dirty). The AEX works fine for iTunes / iPhone play.

Thanks for the help.

---

### Post by Takkat on 2011-08-29
From release > 0.3.0[ stream2ip ]("https://launchpad.net/stream2ip") checks for the presence of your Airport Express's IP on estalishing a connection, disconnects to the previous audio sink when the connection is lost, and tries to reconnect when the AEX comes back. For reconnecting to become possible the stream from your **audio player needs to be stopped first**. If the player is supported (selectable in preferences) stream2ip will do that for you.

There is a myriad of possible causes when you lose your AEX that are hard to debug when this happens. In the best possible case your AEX will be discovered by the Avahi service to appear in sound preferences. One drawback in this setup is that there is no update when the connection is intermittently lost (as it may be the case in a bad WiFi environment). To overcome these Avahi issues you may be successful by using stream2ip that makes use of the IP to stream (independent of Avahi name resolution).

To get it running I suggest you go through the following:

- Optimize WiFi connection (change location, other channel)
- Reset the AEX (by power off)
- Reset Pulseaudio (by stream2ip "Reset" or ressetting using **pulseaudio -k** in a terminal)

---

