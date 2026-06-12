---
title: "connect Onkyo receiver to mythbackend"
date: 2013-01-07
forum: Multimedia Software
---

### Post by x-wolf on 2013-01-07
I am using Mythtv 0.25 on Mythbuntu and I am currently trying to get the an Onkyo receiver connected to my mythbackend box. It works partly via the DLNA setup, but:
1. music only shows all music and all albums (no artists etc.)
2. video gives an error and I can't see any movie

What can this be? I found one post on the internet for someone who also had this problem (with different frontend), but unfortunately without a solution. On my Iphone I have an app which can find the video's, so the backend can't be configured totally wrong.

Does anyone have a clue?
thanks!

---

### Post by BicyclerBoy on 2013-01-07
DLNA is a failed std & broken inter-operability.

So your AVR is a video renderer (DMR) ?

Maybe the AVR does not like the video format..run mediainfo on the video files & check the AVR manual..

Could use DMC on phone/tablet (BubbleUpnp) to control/route audio to amp (DMR) & video to DLNA TV (DMR).
This requires your amp & TV to be DMRs.

The HLS features are another possibility or an "app" on TV & use ARC to feed audio back to amp.

---

### Post by x-wolf on 2013-01-08
Good idea to check with an upnp player on my iphone, this gives some new info.
My Onkyo receiver is a TX-NR609, which should be able to handle video from DLNA server.
With my Iphone i do see the videos and music, but for music i still only see all music and all albums. What could that be?

---

### Post by x-wolf on 2013-01-08
Okay, just found out that this Onkyo can't handle video streaming, only music streaming.....
But still, why do I only see "all music" and "all albums" in the music section?

---

### Post by BicyclerBoy on 2013-01-08
Your amp is network capable but that does not mean it is a video DMR.
Lots of TVs & BD players are.
If your amp must be connected by HDMI cable (from PC) then use myth app on iProduct (TORC?) or mythmote etc.

BubbleUpnp can work as a controller, not just a server or client/renderer..
This means you use tablet/phone as remote control between any server & any client (these don't have to be separate devices).

If you have iProduct then airplay/RAOP is a good option with mythtv.
Mythtv supports push rendering with airplay.

MythTV DLNA server does not support folders/hierarchical browsing. You recordings/music/pictures are displayed as a flat mess.
Mythlink can be used to make human readable recording names.
 
I believe myth devs are looking to better solns as DLNA is closed std & broken.
Airplay/Fairplay/Mirobridge/WiFiDirect.

---

### Post by x-wolf on 2013-01-10
Mmm, I did not know they stopped supporting (or development) on DLNA in Myth.

Well, main reason that I wanted to use the DLNA function of my receiver, is the LCD screen on my receiver. As I have myth running in a case with LCD screen, I used to select music on that LCD screen (Antec Veris Fusion). Unfortunately selecting music on the LCD screen is not possible anymore in Mythmusic in version 0.25 and higher. That is my main reason to look for other solutions. Now I have to put on my tv to select music, which I don't like. The mythbox is connected with HDMI cable to my receiver, but Mythbox and Receiver are also both connected via UTP to internet.

Do you see any other option to select music without putting on my tv? I already have TORC installed on my iphone, but unfortunately TORC does not support mythmusic (the services API of Mythtv does not support it).

---

### Post by BicyclerBoy on 2013-01-10
I assumed TORC would support mythmusic...

Music:
- You could run remote control app on tablet/phone, controlling backend player (myth). But I have not seen any with visual feedback.

- use some other music player with remote control. I think RhymthmBox/pulseaudio/mpd/MPRIS can do this.

Squeezeboxlite ?

---

