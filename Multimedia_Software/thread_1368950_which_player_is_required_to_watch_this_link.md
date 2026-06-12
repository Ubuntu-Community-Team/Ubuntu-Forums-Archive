---
title: "which player is required to watch this link"
date: 2009-12-31
forum: Multimedia Software
---

### Post by tapas_mishra on 2009-12-31
I use Ubuntu and do not have any thing else on my laptop
came across a link [http://www.shrisaibabasansthan.org/onlinedarshan/onlinedarshan1.htm](http://www.shrisaibabasansthan.org/onlinedarshan/onlinedarshan1.htm)
a video is available to be watched but they have given in requirements windows media player and clicking on the links in mozilla I was not clear as to where should I look in.

---

### Post by howefield on 2009-12-31
Click on the flashing link above the image in the centre of the page.

Should then open up another page with the video player, you might need to press the play button and after a few minutes buffering the video will start.

If it doesn't start, you need some codecs, which will be easy enough to track down. Let us know if you are able to view the stream as it is.

---

### Post by tapas_mishra on 2009-12-31
> **howefield said:**
> Click on the flashing link above the image in the centre of the page.

Should then open up another page 
Well another page came here is the link
[http://www.shrisaibabasansthan.org/shirdilivedarshan1.htm](http://www.shrisaibabasansthan.org/shirdilivedarshan1.htm)

> **howefield said:**
>  with the video player, you might need to press the play button and after a few minutes buffering the video will start.

If it doesn't start, you need some codecs, which will be easy enough to track down. Let us know if you are able to view the stream as it is.
I have mplayer installed in this laptop tell me what codecs you are talking about because no video player etc came to be opened on which I could play any thing.
Is there any way I can attach a snapshot here to show what is it appearing at my system.

---

### Post by howefield on 2009-12-31
> **tapas_mishra said:**
> Is there any way I can attach a snapshot here to show what is it appearing at my system.

When clicking on the link, this is what I see on the page, (click on the thumbnail to view full size). See the video player in the middle of the page.

[[IMG]http://i157.photobucket.com/albums/t51/howefield/th_Screenshot-ShriSaibabaSamadhiMandir.png[/IMG]](http://s157.photobucket.com/albums/t51/howefield/?action=view&current=Screenshot-ShriSaibabaSamadhiMandir.png)

---

### Post by mutex023 on 2009-12-31
You need to install the gstreamer codecs or plugins.
Just search for gstreamer in Synaptic package manager, and install all the plugins. (gstreamer-plugins-xxxx).
Restart your browser, the video should now play.

---

### Post by howefield on 2009-12-31
Probably just w32codecs. (w64codecs for 64 bit)

---

### Post by tapas_mishra on 2009-12-31
> **howefield said:**
> When clicking on the link, this is what I see on the page, (click on the thumbnail to view full size). See the video player in the middle of the page.

[[IMG]http://i157.photobucket.com/albums/t51/howefield/th_Screenshot-ShriSaibabaSamadhiMandir.png[/IMG]]("http://s157.photobucket.com/albums/t51/howefield/?action=view&current=Screenshot-ShriSaibabaSamadhiMandir.png")
No this is not  in my case.
After installing gstreamer plugins also it did not worked.
this is what I see [IMG]http://i743.photobucket.com/albums/xx75/tapas_ubuntu/ubuntuvideo.png[/IMG][IMG]http://s743.photobucket.com/albums/xx75/tapas_ubuntu/[/IMG]

---

### Post by mc4man on 2009-12-31
> No this is not in my case.

Atm I see what I think you're seeing ( empty boxes with a 'back'

Note this is on both ubuntu and vista

Because it's a live stream maybe it's a time thing - says 4 am to 11:45 pm.
Figuring it's about 12:30 am right now (i think

---

### Post by tapas_mishra on 2010-01-01
> **mc4man said:**
> 
Because it's a live stream maybe it's a time thing - says 4 am to 11:45 pm.
Figuring it's about 12:30 am right now (i think
Can you check now.

---

### Post by mutex023 on 2010-01-01
All right, the video is playing now, but I've to say sorry first.
Initially I checked in google chrome and it was playing, but now I checked in firefox and its not . Chrome is using a VLC player plugin, which plays the video but not firefox.
Does anyone know how to enable this in firefox ?

So @tapas_mishra you could install google chrome and vlc player and then try watching the video, it should work.

---

### Post by howefield on 2010-01-01
> **tapas_mishra said:**
> Can you check now.

Try installing the w32codecs from medibuntu.

Go here and download the w32codecs package, (if you are using 64 bit, you'll want the w64codecs package instead) double click the downloaded file to start the install. Then try again.

[http://packages.medibuntu.org/karmic/index.html](http://packages.medibuntu.org/karmic/index.html)

---

### Post by tapas_mishra on 2010-01-01
Right now it is late night and by the time all the replies came live telecast may be closed I will do as all the replies are suggesting and then get back here.

---

### Post by tapas_mishra on 2010-02-08
Well after doing all that mentioned it is still not working.

---

