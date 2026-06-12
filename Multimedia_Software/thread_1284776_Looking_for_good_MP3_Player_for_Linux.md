---
title: "Looking for good MP3 Player for Linux"
date: 2009-10-07
forum: Multimedia Software
---

### Post by Capt. Blackwood on 2009-10-07
Well, the reason why i'm lookin is, My Zune died. I'm looking something that'll sync with ubuntu, without any hassles.

I'm thinking about an iPod, but I want to hear what you folks have to say :). 

I've punched the term "iPod" through the app data base on my install and it came up with pretty interesting apps, including one i've already got...Rythem Box Music Player. I want to hear about the pluses and minuses...and your experiances before I make a move.

---

### Post by mastermindg on 2009-10-07
If you're looking for a simple, full-featured app for Ubuntu that will sync an Ipod then it's GTKPod. It allows import/export/playlists/photos... and is really easy to use.

If you're looking for an app that's got a bunch of features but is not as friendly, that would be Amarok. Unfortunately the current version in the distro is 2.2 which doesn't have iPod supoort, but you can downgrade to 1.4 by removing the current version, adding the following to your sources:

## amarok 1.4 
deb [http://ppa.launchpad.net/bogdanb/ppa/ubuntu](http://ppa.launchpad.net/bogdanb/ppa/ubuntu) jaunty main
deb-src [http://ppa.launchpad.net/bogdanb/ppa/ubuntu](http://ppa.launchpad.net/bogdanb/ppa/ubuntu) jaunty main

and installing amarok14 - apt-get install amarok14.

It works with ipod-convenience and has a lot of cool functions like Lyrics and Album Cover managers.

Personally I'm using Ubuntu for it's power in command-line so I've automated the process of managing my iPod Touch by using gnupod. It's not for everybody; but if you're a geek like me who enjoys simplicity, then it's perfect.

In summary:

GTKPod - simple, sync's an iPod, not a great player
Amarok - not so simple, sync's an iPod, great player
GNUPod - advanced, sync's an iPod, not a player

---

### Post by Capt. Blackwood on 2009-10-07
Found this :)

[http://www.bestbuy.com/site/olspage.jsp?skuId=8771929&type=product&id=1204332254016](http://www.bestbuy.com/site/olspage.jsp?skuId=8771929&type=product&id=1204332254016)

---

### Post by mastermindg on 2009-10-08
Not bad though I'm more of a fan of the Touch because of the apps.

---

### Post by Capt. Blackwood on 2009-10-08
Ok so i figured out how to get it set up and music on
 
I've only got enough to get me through the day
 
How do i get Video on this thing, properly sorted...movies, music videos, tv shows...stuff like that. I know what to convert my videos to. But when adding them they show up under my music videos.
 
 
It's a 6th Generation iPod Classic 160GB
 
I read somewhere i need to format it in windows first...is there alot i need to do?

---

### Post by mastermindg on 2009-10-12
gtkPod and Amarok 1.4 both support 6th Gen iPod Video. Transferring video is just like transferring music. You only have to get the format/dimensions right.

---

### Post by Capt. Blackwood on 2009-10-12
gtkPod wouldn't recognize the video files...the app does look promising.

Armarok, i didn't like too much though

---

### Post by Lan on 2009-10-13
I still have yet to find a good mp3 player that I like. I liked the older Amarok on Hardy. I'm using Songbird now. Got rid of the other stuff like exaile, ryhthmbox etc.
I like visual stuff, so I want my mp3 player to look like it's actually playing like winamp,wmp, instead of just a library...

I'd have to admit that WMP11 is great. Not only it's got alot of visuals, settings, plugins, it also sounds great!
I play the same track on WMP11,then I switch over to Songbird/Amarok/etc., but the sound just can't compare to WMP.
Any pointers is appreciated!
Thanks.


On - Jaunty Jackalope -

---

### Post by xpoff on 2009-10-13
Capt. Blackwood,
I'm down with Lan ,try out the songbird for music ,they have a Ipod connect device
My favorite music player hand's down!

---

