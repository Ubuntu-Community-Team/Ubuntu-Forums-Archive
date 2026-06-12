---
title: "Is mythweb HMTL 5 compliant?"
date: 2012-10-13
forum: Mythbuntu
---

### Post by nhtrader on 2012-10-13
Just looking to learn if it is possible to use the new HTML 5 "video" tag?

In particular, I'd like to modify the HTML code to use this new "video" tag so that webbrowsers  will "autoplay" all *.m4v, *.webm *.mp4 videos.

I'm interested in doing this b/c I can't get any of these webbrowsers (FF, Opera, IE9, Chrome) to "autoplay" these formats.

If anyone has any ideas, please advise.


BTW, in an effort to get my webbrowsers to play these formats, I have modified two files:
/usr/share/mythtv/mythweb/mythweb.conf.apache
/etc/apache2/sites-avilable/mythweb.conf

added:
AddType video/m4v .m4v
AddType video/webm .webm
AddType video/mp4 .mp4

I also checked this file: /etc/mime.types
these 3 entries exist:

video/m4v .m4v
video/webm .webm
video/mp4 .mp4

Lastly, current HTML code from MythWeb just provides a hyperlink:
[http://localhost/mythweb/data/video/MyMovie-PG.m4v](http://localhost/mythweb/data/video/MyMovie-PG.m4v)


So I'd like to change this so that I can stream a movie to any device whether it be an iPad, iPhone, Android based device, or to a PC based Webbrowser. 

Here's an example of what I like to see Mythweb Video contain in the HTML source code:
```

<video width="720" height="352" controls autoplay>
  <source src="mymovie.mp4"  type="video/mp4; codecs=avc1.42E01E, mp4a.40.2">
  <source src="mymovie.webm" type="video/webm; codecs=vp8, vorbis">
  <source src="mymovie.m4v"  type="video/m4v; codecs=h264, aac, ac3">
</video>

```

If this new HTML 5 code could be inserted into Mythweb Video, it could stream movies to any device and they would "autoplay". And yes, I plan to have multiple copies of the same movie in the various formats so that any device can stream the movie.

---

### Post by nickrout on 2012-10-14
> **nhtrader said:**
> Just looking to learn if it is possible to use the new HTML 5 "video" tag?

In particular, I'd like to modify the HTML code to use this new "video" tag so that webbrowsers  will "autoplay" all *.m4v, *.webm *.mp4 videos.

I'm interested in doing this b/c I can't get any of these webbrowsers (FF, Opera, IE9, Chrome) to "autoplay" these formats.

If anyone has any ideas, please advise.


BTW, in an effort to get my webbrowsers to play these formats, I have modified two files:
/usr/share/mythtv/mythweb/mythweb.conf.apache
/etc/apache2/sites-avilable/mythweb.conf

added:
AddType video/m4v .m4v
AddType video/webm .webm
AddType video/mp4 .mp4

I also checked this file: /etc/mime.types
these 3 entries exist:

video/m4v .m4v
video/webm .webm
video/mp4 .mp4

Lastly, current HTML code from MythWeb just provides a hyperlink:
[http://localhost/mythweb/data/video/MyMovie-PG.m4v](http://localhost/mythweb/data/video/MyMovie-PG.m4v)


So I'd like to change this so that I can stream a movie to any device whether it be an iPad, iPhone, Android based device, or to a PC based Webbrowser. 

Here's an example of what I like to see Mythweb Video contain in the HTML source code:
```

<video width="720" height="352" controls autoplay>
  <source src="mymovie.mp4"  type="video/mp4; codecs=avc1.42E01E, mp4a.40.2">
  <source src="mymovie.webm" type="video/webm; codecs=vp8, vorbis">
  <source src="mymovie.m4v"  type="video/m4v; codecs=h264, aac, ac3">
</video>

```

If this new HTML 5 code could be inserted into Mythweb Video, it could stream movies to any device and they would "autoplay". And yes, I plan to have multiple copies of the same movie in the various formats so that any device can stream the movie.

You should look at the services api stuff which was introduced in 0.25.

---

### Post by nhtrader on 2012-10-14
> **nickrout said:**
> You should look at the services api stuff which was introduced in 0.25.

While this is an interesting new dimension to MythTV, this didn't answer the question.

I did find the answer - NO. 

Currently, MythWeb still is HTML 4.01 compliant and therefore the use of the new HTML 5 video tag is not applicable.

So the next question is, does the next version of MythTV (v0.26) implement/use HTML 5?

---

### Post by nickrout on 2012-10-14
> **nhtrader said:**
> While this is an interesting new dimension to MythTV, this didn't answer the question.

I did find the answer - NO. 

Currently, MythWeb still is HTML 4.01 compliant and therefore the use of the new HTML 5 video tag is not applicable.

So the next question is, does the next version of MythTV (v0.26) implement/use HTML 5?Have a look at the release notes on the mythtv wiki, or at the source code at github.

---

### Post by thatguruguy on 2012-10-15
> **nhtrader said:**
> 
So I'd like to change this so that I can stream a movie to any device whether it be an iPad, iPhone, Android based device, or to a PC based Webbrowser. 

...

If this new HTML 5 code could be inserted into Mythweb Video, it could stream movies to any device and they would "autoplay". 

No, they wouldn't. Android devices, iPads and iPhones don't support autoplay.

---

### Post by nhtrader on 2012-10-18
> **thatguruguy said:**
> No, they wouldn't. Android devices, iPads and iPhones don't support autoplay.

Thank you. I'm been hunting for this clear and definitive answer.

I'm glad to learn that "autoplay" isn't supported by these devices, but I'm confused. Apparently, it must have been supported in the past b/c I've seen many examples on the web of HTML 5.0 code specifically designed to make a website iPad and Android video friendly. 

Do you when support for "autoplay" for these devices was discontinue/disabled?

All I know is that flash was "pulled" from Android 4.1 Aug 15 2012.

---

