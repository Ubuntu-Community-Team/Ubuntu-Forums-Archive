---
title: "MythTV on HTML"
date: 2012-06-29
forum: Mythbuntu
---

### Post by ketan16may on 2012-06-29
Hi All,

I am very new to Ubuntu as well as to MythTV.
After several trials I could watch Live TV on Ubuntu 12.04 using MythTV and "Technotrend TT-Connect S2-3600" USB adaptor.

Need help to embed the tv tuner video into an HTML page with which the Live TV could be watched along with additional data on page.

I am not sure if mythtv can be used as HTML plugin or else VLC can be used or any other way.

Please help.

Thanks
Ketan.

---

### Post by nickrout on 2012-06-30
> **ketan16may said:**
> Hi All,

I am very new to Ubuntu as well as to MythTV.
After several trials I could watch Live TV on Ubuntu 12.04 using MythTV and "Technotrend TT-Connect S2-3600" USB adaptor.

Need help to embed the tv tuner video into an HTML page with which the Live TV could be watched along with additional data on page.

I am not sure if mythtv can be used as HTML plugin or else VLC can be used or any other way.

Please help.

Thanks
Ketan.

That is not what mythtv is all about. However VLC or Kaffeine should be able to view livetv in from a dvb card, without any help from mythtv.

---

### Post by MrMic on 2012-07-01
Have you tried the mythweb application that runs on apache.It will be part of mythbuntu install.You may have to enable it via the myth control panel.You can access it via [http://address_of_your_master_backend/mythweb](http://address_of_your_master_backend/mythweb)

---

### Post by nickrout on 2012-07-01
> **MrMic said:**
> Have you tried the mythweb application that runs on apache.It will be part of mythbuntu install.You may have to enable it via the myth control panel.You can access it via [http://address_of_your_master_backend/mythweb](http://address_of_your_master_backend/mythweb)

what has that got to do with live tv?

---

### Post by ketan16may on 2012-07-03
Yes, after trying a lot i came to know that Mythtv is not a solution to my problem, so i tried vlc plugin and it worked.

But now with vlc streaming i can play a network url or local file and not the tv tuner.

Can you help me playing the dvb-s channel on vlc.

---

### Post by nickrout on 2012-07-03
> **ketan16may said:**
> Yes, after trying a lot i came to know that Mythtv is not a solution to my problem, so i tried vlc plugin and it worked.

But now with vlc streaming i can play a network url or local file and not the tv tuner.

Can you help me playing the dvb-s channel on vlc.

You are confusing me. Are you trying to play TV from the dvb-s card, or are you trying to stream the output of the dvb-s card over your network?

In either case open vlc and choose Media|Open Capture device

In the dialog box that comes up choose TV (Digital). Fill in the blanks and then choose "Play" or "Stream" at the bottom, if you  choose stream, another dialog will come up with streaming options.

My description is from vlc 2.0.1, the dialogs were, I think, slightly different on earlier versions. But the above should hopefully assist.

---

### Post by anonymousdog on 2012-07-03
I think he's trying for a SlingBox alternative with a web frontend.

---

### Post by ketan16may on 2012-07-03
> **nickrout said:**
> You are confusing me. Are you trying to play TV from the dvb-s card, or are you trying to stream the output of the dvb-s card over your network?

In either case open vlc and choose Media|Open Capture device

In the dialog box that comes up choose TV (Digital). Fill in the blanks and then choose "Play" or "Stream" at the bottom, if you  choose stream, another dialog will come up with streaming options.

My description is from vlc 2.0.1, the dialogs were, I think, slightly different on earlier versions. But the above should hopefully assist.

Sorry to confuse you. 
My ultimate goal is to play the live stream in html page, which i couldn't do it easily.
As a second option i though of playing the dvb-s live channel using vlc and then stream it to a http destination, which finally could be embedded to html.

Now as per your suggestion i tried to play the dvb-s channel using "Open capture card" but always getting the MRL error. I will post the exact error and snapshot soon.
Thanks for your till time support.

Ketan

---

### Post by nickrout on 2012-07-03
> **ketan16may said:**
> Sorry to confuse you. 
My ultimate goal is to play the live stream in html page, which i couldn't do it easily.
As a second option i though of playing the dvb-s live channel using vlc and then stream it to a http destination, which finally could be embedded to html.

Now as per your suggestion i tried to play the dvb-s channel using "Open capture card" but always getting the MRL error. I will post the exact error and snapshot soon.
Thanks for your till time support.

Ketan

I think you are very confused.

---

### Post by azmyth on 2012-07-03
I haven't tried it with livetv so I don't know if it works.

[http://en.wikipedia.org/wiki/HTTP_Live_Streaming](http://en.wikipedia.org/wiki/HTTP_Live_Streaming)

---

### Post by anonymousdog on 2012-07-03
It does not (with LiveTV).

---

### Post by nickrout on 2012-07-03
> **azmyth said:**
> I haven't tried it with livetv so I don't know if it works.

[http://en.wikipedia.org/wiki/HTTP_Live_Streaming](http://en.wikipedia.org/wiki/HTTP_Live_Streaming)

no it doesn't work with livetv.

---

### Post by ketan16may on 2012-07-12
[URL="http://ubuntuforums.org/member.php?u=253067"][ATTACH]221111[/ATTACH]

[ATTACH]221112[/ATTACH]

[ATTACH]221113[/ATTACH][/URL]

[nickrout]("http://ubuntuforums.org/member.php?u=253067"),

Probably I am not able to put into words well.
When I am trying to play any channel using vlc , I am getting MRL error.
The vlc debug logs are attached if u can help.

Thanks

---

### Post by nickrout on 2012-07-12
> **ketan16may said:**
> [URL="http://ubuntuforums.org/member.php?u=253067"][ATTACH]221111[/ATTACH]

[ATTACH]221112[/ATTACH]

[ATTACH]221113[/ATTACH][/URL]

[nickrout]("http://ubuntuforums.org/member.php?u=253067"),

Probably I am not able to put into words well.
When I am trying to play any channel using vlc , I am getting MRL error.
The vlc debug logs are attached if u can help.

Thanks

I suggest you find a forum that supports vlc.

---

### Post by ijumpship on 2012-07-13
The mere suggestion of placing TV programs on HTML leaves so much questions.

Just to inform this is what the web interface of mythtv does

Let You See a guide of what's on tv, schedule recordings and manage shows that you've already recorded. 

You will have the following choices:
Program Listing
Special Searches
Upcoming Recordings
Recording Schedules
Schedule Manually
Custom Schedule
Recorded Programs


Live-TV can be watch via a number of front-end options.
Recorded programs is possible via mythweb but its experimental.

I hope You are not suggesting to place the contents on any  channel of your Major TV  Network on a website that the public can view.(legal Problems)

If so abandon this idea.

I would suggest you look at PLEX if you want to watch TV when you are away from home and have a few programs recorded.

---

