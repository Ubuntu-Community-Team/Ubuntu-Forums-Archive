---
title: "is flv the best format for web videos?"
date: 2010-12-03
forum: Multimedia Software
---

### Post by bistro on 2010-12-03
Hi

I've installed winff. I've been looking around the web for the best format in which to create videos to put on web pages. I'm slightly confused! As I understand it:
Ogg - the open-source option but IE users won't be able to play it;
flv - almost universal but becoming less so
mp4 - no good for firefox users

What is best one to use?

Thanks

Dave

---

### Post by lovinglinux on 2010-12-03
You should use [webm]("http://www.webmproject.org/") format/encoder and a web player capable of falling back to flash if the browser doesn't have capability of playing the html5 video. See the free open source [VideoJS]("http://videojs.com"). Read the "Getting Started" section on their site. It is very informative, even if you are not considering using their player.

The demo video on that site works perfectly on Chrome, Firefox, Opera and IE. However, they embed multiple video formats to allow fall back in unsupported browsers. Included formats are webm, mp4 and ogv. Firefox 4.0, Chrome 7 and Opera 11 can all play webm natively. Firefox 3.6 requires the ogv file for regular html5 playback and IE <9 requires the mp4 for flash playback. 

I know, this is not very convenient, but if you want to use a web standard  format, then you should choose webm whenever possible. Flash is convenient and will play in most browsers, but performance in Linux is really bad and since it is a proprietary format, it should be avoided. 

For webm and mp4 encoding, see [http://ubuntuforums.org/showpost.php?p=9441742&postcount=2](http://ubuntuforums.org/showpost.php?p=9441742&postcount=2)

---

