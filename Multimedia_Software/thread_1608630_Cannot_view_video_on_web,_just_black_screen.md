---
title: "Cannot view video on web, just black screen"
date: 2010-10-29
forum: Multimedia Software
---

### Post by rdh61 on 2010-10-29
Hi,

I am having great difficulty viewing a series of educational videos (MMS streams) in Ubuntu 10.04, which view perfectly in Windows XP.

All I get is a black screen. No matter whether I use Firefox or Chrome or Opera, No matter whether with MPlayer, Totem or VLC.

I have tried everything I could find by googling (basically trying different media players and plugins) but nothing works.

This is my final attempt! Anyone have any ideas, or similar problems?

Many thanks.

---

### Post by jeremyswalker on 2010-10-29
Do you have the gstreamer0.10-plugins-bad and gstreamer0.10-plugins-ugly packages installed?

---

### Post by rdh61 on 2010-10-29
Yes.

---

### Post by cchhrriiss121212 on 2010-10-29
Could you post a link?

---

### Post by rdh61 on 2010-10-29
The link won't be much help to you I don't think as I have to log on with my university password to access it. Once I've successfully logged on all I get on my viewer is a black screen, while the bottom bar of the browser perpetually flashes "Waiting for (source)" at me.

However, the url is: [http://teleuned.uned.es/teleuned2001/directo.asp?ID=931&Tipo=A](http://teleuned.uned.es/teleuned2001/directo.asp?ID=931&Tipo=A)
The MMS stream is: mms://cemav.uned.es/datos/Psicologia/psico-20092010/psicosalud/psico-psicopatologia-salud-20100508.wmv

---

### Post by jeremyswalker on 2010-10-29
Well, I can view the mms link on my computer. I viewed it using totem.

---

### Post by jeremyswalker on 2010-10-29
Do you have ubuntu-restricted-extras and w32codecs installed?

---

### Post by rdh61 on 2010-10-29
Good news that you can view it - gives me hope!

Yes, I do have w32codecs and ubuntu-restricted-extras installed.

---

### Post by rdh61 on 2010-11-30
Still no joy, if anyone has any other suggestions.

Thanks.

---

### Post by xc3RnbFO8P on 2010-11-30
Try to start firefox in Terminal:
> export XLIB_SKIP_ARGB_VISUALS=1 firefox

---

### Post by rdh61 on 2010-11-30
Hi, I don't understand what the following is for:

export XLIB_SKIP_ARGB_VISUALS=1 firefox

However, if I start firefox from a terminal and try to watch the video, I get the following on the terminal:

robert@robert-laptop:~$ firefox
NPP_New called
Using player backend of ''
DBUS connection created
Listening to path /control/54792
ARG: type = audio/x-pn-realaudio-plugin
ARG: name = RealPlayerNS
ARG: id = RealPlayerNS2
ARG: controls = HomeCtrl
ARG: height = 0
ARG: width = 0
URL Notify url = ''
reason = 1

/control/54792
URL Notify result is Network Error
NPP_New called
Using player backend of ''
DBUS connection created
Listening to path /control/2999
ARG: type = audio/x-pn-realaudio-plugin
ARG: name = RealPlayerNS
ARG: id = RealPlayerNS2
ARG: controls = HomeCtrl
ARG: height = 0
ARG: width = 0
URL Notify url = ''
reason = 1


/control/2999
URL Notify result is Network Error
NPP_New called
Using player backend of ''
DBUS connection created
Listening to path /control/23552
ARG: type = video/x-ms-asf-plugin
ARG: src = mms://cemav.uned.es/datos/Psicologia/psico-20092010/psicosalud/psico-psicopatologia-salud-20100507.wmv
ARG: name = Reproductor
ARG: mute = 0
ARG: showcaptioning = 0
ARG: showcontrols = 1
ARG: showaudiocontrols = 0
ARG: showdisplay = 0
ARG: showtracker = 0
ARG: showstatusbar = 1
ARG: autosize = 0
ARG: animationatstart = 0
ARG: showgotobar = 0
ARG: pluginspage = [http://www.microsoft.com/Windows/Downloads/Contents/Products/MediaPlayer/](http://www.microsoft.com/Windows/Downloads/Contents/Products/MediaPlayer/)
ARG: height = 205
ARG: width = 249
Window resized
Sending Open mms://cemav.uned.es/datos/Psicologia/psico-20092010/psicosalud/psico-psicopatologia-salud-20100507.wmv to connection 0xb24c6350
item->hrefid = 0 item->src = mms://cemav.uned.es/datos/Psicologia/psico-20092010/psicosalud/psico-psicopatologia-salud-20100507.wmv
Window resized
media size = 0 x 0
media size = 0 x 0
media size = 0 x 0
media size = 249 x 168
media size = 249 x 168
media size = 249 x 168
media size = 249 x 168

---

### Post by runeh76 on 2010-11-30
What ur fox says, when type ```
about:plugins
``` to address bar..u see flash enabled?
hmm it sounds flash-problem, not sure..

---

### Post by rdh61 on 2010-11-30
Shockwave Flash is enabled.

---

### Post by runeh76 on 2010-11-30
Okey becouse mms stream is windows stuff i dont want to think that too much, so i just give u a link that might help u a bit.
[http://linuxers.org/howto/how-download-mms-streaming-videos-ubuntu](http://linuxers.org/howto/how-download-mms-streaming-videos-ubuntu)

Cheers

---

### Post by rdh61 on 2010-12-02
Thanks anyway. The main suggestion on that page is to download and use mimms. I did, but it cannot connect to the mms stream. So, no further on...

---

### Post by pianomans on 2010-12-06
Yes "YEREMYSWALKER"..... Yas, it solve my problem. Now i can see MMS. Thanks again "YEREMYSWALKER.

---

