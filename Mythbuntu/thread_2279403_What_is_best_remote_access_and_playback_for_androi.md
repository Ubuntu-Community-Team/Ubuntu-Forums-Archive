---
title: "What is best remote access and playback for android?"
date: 2015-05-23
forum: Mythbuntu
---

### Post by afremont on 2015-05-23
Hello,

I'm migrating from WMC to MythTV as the backend for a home DVR/media center machine.  Currently I use Remote Potato (WMC) and Remote Media Center (Android) to access my media center remotely and impress people.  ;)  I'm looking for something similar for MythTV that will allow me to watch recordings (and maybe live TV) as well as view the program guide and schedule recordings.  Accessing pictures and music is secondary.

I have mythmote installed for remote control.  I've glanced at Mythling and MythTV Player, but they didn't work out of the box.  Before dedicating a bunch of time and effort into getting them to work, does anyone have a suggestion as to which way I should go?  I also see that there is one called MythTV Go, but I haven't even installed that one yet.

Remote Potato and RMC would let me instantly stream recordings without having to wait for transcoding.  Is that possible with any of these remote Myth apps?  I have an HDHomerun tuner that is used to make my recordings.  I also have an extensive library (2TB) of TV recordings that were made using WMC.  Any way to get that stuff into MythTV as recordings, or am I stuck adding them as Videos?  Right now, I use OpenELEC on a RPi2 to as the front-end for all of this.  Any suggestions for an external video player on the remote Android device?

Thanks for any advice.

---

### Post by SeijiSensei on 2015-05-23
On Android, I use BubbleUPnP for DLNA connections and MXPlayer for video.  Both work well together to stream video from a miniDLNA server.

---

### Post by afremont on 2015-05-24
Ok, thank you.  I will look into that, but isn't DLNA only for local networks?  I want to access my box from outside my home network.  Thank you for your input.

---

### Post by SeijiSensei on 2015-05-24
Yes.  You'll still want mxplayer though.

You'd be better off copying the files you want to use to your phone than trying to stream over the Internet.  I use an SD card for that.

---

### Post by afremont on 2015-05-25
Ok, thank you very much.  I do want to be able to stream though.  I'll keep poking at it.  Right now I'm off on another adventure trying to migrate all my WMC recordings to MythTV as recordings, not videos.  It's looking like I'm going to have to hack together some code to make that work.  That's cool though, I haven't written anything new for a while.

---

### Post by uteck on 2015-05-26
There is a plugin for Plex that will connect it to your Myth server, then you can use the Plex website or a client.  
There is also MythWeb, but it exposes all the controls for your server and not just recordings.  I used a VPN to connect to my house then used MythWeb to stream.

---

### Post by afremont on 2015-05-27
I don't mind the controls being exposed, that's fine with me.  I don't know anything about Plex, I guess it's time for me to learn.  I keep hearing about it, but I've not looked into it.  How do you get MythWeb to play videos on the Androd?  Are you just using the Chrome browser, or is there some Android client that I don't know about?

---

### Post by philip7 on 2015-07-24
When I went on holiday the other month I just used Mythweb to direct download the recordings via my Android tablet, the video files are saved using the episode number/title so easy to read from the device at a later date.

The filesize might be an issue for some people but I wasn't too bothered and just deleted after watching so no fuss.

I think Mythtv player is the app that is in development at the moment, I had a quick look and very interested in the Chromecast support, if they can get that to work you wouldn't need a dedicated frontend in each tv just cast from the phone/tablet to the TV, I do this with NowTV now and its really simple/easy.

---

### Post by ian95 on 2015-08-20
I'm just going through the exact same as you, but coming from mediaportal rather than WMC.  I am largely a TV/EPG/recordings user as well, with hdhomerun. I hit on Kodi almost straightaway as a front end and it worked first time. Same front end on Android and windows, both worked out of the box talking to the myth backend.

---

### Post by afremont on 2015-08-24
Ian95, are you running kodi on your phone?  When away from home, don't you run into bandwidth problems?

---

