---
title: "MLBaseball Radio and Gutsy a No Go?"
date: 2008-02-28
forum: Multimedia &amp; Video
---

### Post by NoVista on 2008-02-28
I have s subscription to MLB 2008 radio for the year.
Now this year, MLB has a new interface for the radio player.
And it didn't work here. No audio, and some of the links wouldn't display as a link.
Luckily, I saw a link on the new interface, asking you if you wanted to return to the older "original" interface. And that got me the audio back.
I use Firefox 2.0.0.12.

Anyone else notice the change?
Does the new interface work on your system?

---

### Post by crossface on 2008-02-28
I have the same problems with mlb baseball video.  The only way it work is using the "old player", also nascar scanner audio works only intermittently. Looks like multimedia will be with ms for awhile. Use swiftfox .12 which essentially firefox .12. Nothing in the future firefox 3 that will help us.

---

### Post by gregalynch on 2008-03-30
I'm having the same problem.  Where do you find the option to return to the old interface?

---

### Post by lefthand on 2008-03-31
Looks like the option to use the old player is gone. Now that the season has started they only let you use the 'new' player. I'm thinking of asking for my money back, using virtualbox just to listen to an audio stream is unappealing.

---

### Post by lefthand on 2008-03-31
I found the link for the classic player. In XP I had to install both Silverlight AND flash before it appears. The link comes up right after you login. I haven't found a way to get the link to appear in Ubuntu though :(

Hopefully they'll get this fixed soon. There always seems to be bugs on opening day, so I'll give them a chance.

---

### Post by drs305 on 2008-04-02
I have been unable to access MLB audio during the regualr 2008 season so far. I get to the links page displaying the day's games. When I click on the specific radio station link, nothing happens. I have never seen a link to the old or new media players. (I can access the audio via windows.)

Hopefully someone will post a solution on this forum.

I have registered my displeasure with MLB support, have you?

---

### Post by lefthand on 2008-04-03
Ironically, I tried to leave them feedback but that form was broken too. I know they were having lots of issues on opening day, so I'll try it again now.

Here is the link to leave feedback if anyone else wants to chime in: [http://mlb.mlb.com/mlb/help/contact_us.jsp](http://mlb.mlb.com/mlb/help/contact_us.jsp)

---

### Post by drs305 on 2008-04-04
There is now a workaround for both MLB audio and video. It entails installing the firebug addon to Firefox/Swiftweasel to cull the feed's url. I have used it successfully to listen to MLB audio using Swiftweasel/firebug/VLC. 

Here is the link to the entire thread:
[http://www.linuxquestions.org/questions/fedora-35/mlb.tv-in-linux-432479/](http://www.linuxquestions.org/questions/fedora-35/mlb.tv-in-linux-432479/)

---

### Post by lefthand on 2008-04-04
Works for me. Thanks for the link.

---

### Post by NoVista on 2008-04-05
Great, can't wait to try it.
I have resorted to running my XP virtual machine in order to listen to the games.
Hope the fix works for me.

---

### Post by drs305 on 2008-04-05
The link I referenced is getting pretty lengthy. For MLB audio, here are the steps. 

1. Install the firebug add-on to firefox/swiftweasel and restart.
1a.  Make sure popups are not blocked (Edit, Prefs, Content). Also, you most likely will get a "onTabClosed" message and no mURL if you have AdBlock Plus enabled.
2. Sign onto the MLB web site with your username/password.
3. Go to the media page with the game you are interested in.
4. Click on the game you wish to listen to.
5. When the new page/window opens, select F12. This will open firebug in the lower half of the page. With the console tab selected, you will see an address that starts with mURL:
Copy this address, remove the "mURL:" so it starts with "http://web.servicebureau.net/conf....."
6. Enter this into a player that will play streaming audio (e.g. VLC).

Note: You don't need or want to click on the Listen button in the new page to select the feed you desire.  You already did this on the media links page. If you do so on the new pop-up page, you won't see the url and will not see the correct address.

If this doesn't work for you, go to the link in my previous post. There is more information there as well as scripts for simplifying video playback.

---

### Post by oaksterdam on 2008-04-09
good g-d that was convoluted.  but it does work.  sheesh.  probably won't be buying the audio package next year....

---

### Post by NoVista on 2008-04-09
Thank you drs305.

Works perfectly !

---

### Post by llc1985 on 2008-04-17
Here is what i got to work for my fathers machine for gameday audio

1. Install grease monkey

2. install this script [http://userscripts.org/scripts/show/24731](http://userscripts.org/scripts/show/24731)

3. install mozilla-mplayer 

terminal

sudo apt-get install mozilla-mplayer

4. restart firefox

gameday audio should load in a mplayer tab once you select a stream.

---

### Post by Detonate on 2008-04-22
Hmmm, did not get to try the Greasemonkey Script.  I upgraded to Hardy yesterday, and FF 3, and lo and behold, MLB audio opened in mplayer just fine.  I don't know if it was the upgrade that did it or the nasty letter I wrote to MLB to which I never got a reply. :-)  

Listening to Braves and Nats as I type, Smoltz should reach 3000 K tonight.

---

### Post by NoVista on 2008-04-22
As of today, the MLB player was back  working again for radio broadcasts without any user intervention other than selecting what broadcast you want.

---

### Post by Detonate on 2008-04-24
As of today 4/24/08, it's not working again.  I want my money back!!

I'll try the Greasemonkey Script and see what happens, I'll report back.

---

### Post by Detonate on 2008-04-24
The Greasemonkey Script does not work for me.  For those of you who really need your baseball fix, here is a great alternative, and it's free.

[http://www.freebaseballradio.com/](http://www.freebaseballradio.com/)

---

### Post by drs305 on 2008-04-25
> **Detonate said:**
> As of today 4/24/08, it's not working again. 

I just installed Hardy and flash. MLB audio works fine for me without using greasemonkey or the vlc-plugin. A 'no video' message appears in the new window but the audio starts in about 30 seconds and seems to be working without any special efforts on my part.

---

### Post by drs305 on 2008-04-26
This thread may be a little old to get read much, but since we don't see MLB posts very often:

Does anyone running linux have an app which will allow you to skip forward during playback of an archived MLB game? With windows media player (windows), you can start a game and use the slider to move to any point of the archived game. You can advance a couple of minutes (between innings) or even use the slider to start listening at the 2 hour point (or anywhere else in the broadcast); and as often as you like.

The only thing I have found in linux is VLC, which will allow me one (1) advance, usually for about 25 minutes. If I try a second time the program crashes. Some linux apps appear to have the capability to advance (smplayer, for instance) but they don't seem to work with archived games.

Anyone know of an app that has this capability?  Thanks.

---

### Post by trippinnik on 2008-05-01
check out this python script for getting the games.  I haven't gotten seeking to work yet, but it's a lot better than what I was doing before (booting windows or using a VM): [http://www.eds.org/~straycat/mlblinux.php](http://www.eds.org/~straycat/mlblinux.php)

---

### Post by twolaw on 2008-05-06
Year after year it's a struggle to get Gameday Audio working under Linux. You'd think mlb.com wouldn't want to alienate its customers...

---

### Post by NoVista on 2008-05-07
Today, May 7,2008, MLB Gameday Audio is back on its own under Gutsy. Mplayer opens up in its own window. Even the volume control for it worked.

---

