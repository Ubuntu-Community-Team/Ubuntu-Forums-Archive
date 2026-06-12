---
title: "Cycling.tv in Ubuntu?  what I have so far"
date: 2009-03-08
forum: Multimedia Software
---

### Post by brian.t on 2009-03-08
I am trying to watch Cycling.tv using ubuntu 8.10
I can easily watch it if I run Windows xp in vmware then use firefox and the windows media player plug-in.  I don't want this  method, it is too easy and I really don't want to use windows for many reasons that I am sure you can understand but we won't get into now.

What happens when I use firefox in unbuntu for this URL [http://www.cycling.tv/newMediaPlayer/consolewmp.htm?type=vod&SPID=&DB_MENU_ID=&CLIP_FILE_ID=383174&SPSID=&id=383174&DB_OEM_ID=20300&CLIP_ID=376475&oemid=20300]("http://www.cycling.tv/newMediaPlayer/consolewmp.htm?type=vod&SPID=&DB_MENU_ID=&CLIP_FILE_ID=383174&SPSID=&id=383174&DB_OEM_ID=20300&CLIP_ID=376475&oemid=20300")
Is I get "Your wmp is an old version you need to download  and install the new version." 
I never get to the link that I can use to see video.
What I did do was run streamsniffer and then vmware, xp and firefox to sniff out what urls I can. 
Now I have a list of urls that I can use in ubuntu to watch my cycling and I am 1/2 happy.
What I really want to figure out is how to trick the website into thinking that I do have wmp (windows media player) installed and get the link and just play it in mplayer or what ever.
Does any one know how to get the javascript to give up the url?

I ultimately want to sign up and get the subscription to the paid tv, but why would I if I can't easily watch it?  I asked their tech support and they said that it was made for windows media player.  I call that a challenge!

Anyone able to help?  I am going to keep working on this.  

If I start at this url[http://www.cycling.tv/club/std/ViewCategory.dbml]("http://www.cycling.tv/club/std/ViewCategory.dbml")
And choose free2view
I pick one of the links and see this javascript:openOnDemandViewer('372974', '378817')
then this will give
HTTP: [http://objects.tremormedia.com/embed/swf/AdManagerProxy.swf?connectionNum=9354](http://objects.tremormedia.com/embed/swf/AdManagerProxy.swf?connectionNum=9354)

HTTP: [http://www.cycling.tv//onDemand/OnDemandVideo.wvx?CID=372974&CFLID=378817&DB_OEM_ID=20300](http://www.cycling.tv//onDemand/OnDemandVideo.wvx?CID=372974&CFLID=378817&DB_OEM_ID=20300)

HTTP: [http://ad.doubleclick.net/adx/jtvs.20300.cyclingtv/videoplayer;oem=20300;sz=320x240;lan=en;pos=;dcopt=null;sec=videoplayer;u=con%3Djtvs.20300.cyclingtv%2Fvideoplayer%7Csize%3D320x240;gen=videoplayer;c_cou=us;c_reg=north_america;s_sec=;c_type=VOD;s_type=none;c_content=free;tile=1;ord=337334013?](http://ad.doubleclick.net/adx/jtvs.20300.cyclingtv/videoplayer;oem=20300;sz=320x240;lan=en;pos=;dcopt=null;sec=videoplayer;u=con%3Djtvs.20300.cyclingtv%2Fvideoplayer%7Csize%3D320x240;gen=videoplayer;c_cou=us;c_reg=north_america;s_sec=;c_type=VOD;s_type=none;c_content=free;tile=1;ord=337334013?)
    : ca;s_sec=;c_type=VOD;s_type=none;c_content=free;tile=1;ord=337334013?

RTSP: rtsp://www.xosn.com.edgestreams.net/video90/WMGLTKWCGQSUTVJ.20090216143444.wmv 

Which ultimately translates to this url
[www.cycling.tv/video90/WMGLTKWCGQSUTVJ.20090216143444.wmv](www.cycling.tv/video90/WMGLTKWCGQSUTVJ.20090216143444.wmv)


That is what I can figure out, I would like a script that i can run that will ultimately give the url that it equals , then I have to figure out how to pass it information when I do choose to subscribe and then see the pay urls.

This is fun,
Brian

---

