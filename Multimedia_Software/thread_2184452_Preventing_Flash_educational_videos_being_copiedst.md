---
title: "Preventing Flash educational videos being copied/stolen"
date: 2013-10-29
forum: Multimedia Software
---

### Post by 9k0aefbmMtuJ on 2013-10-29
An associate needs a website set up that will contain many relatively small educational videos that she has created. These are all (flv) flash files.
Please does anyone know how copying of these videos may be prevented?

---

### Post by tgalati4 on 2013-10-29
You can make it difficult, but not impossible to prevent copying the videos.  Many content providers use a proprietary player to stream the videos (written in Java, for instance) which does not expose the flash file to copying.

You would have to add DRM--digital rights management--to the videos and encode them in a proprietary format to make them more difficult to copy.  But in linux there are no tools that I know of to do that.

Perhaps describe the Use Case in more detail:

How does a user access the site?  Does it require a paid subscription to access content?  If the videos are truly educational, then why is content protection needed?  Perhaps there is another business model that will work?  If the videos are released under Creative Commons, you have a lot more flexibility on how you license and handle the content.

[http://creativecommons.org/](http://creativecommons.org/)

---

### Post by TheFu on 2013-10-29
If they can be viewed, then they can be copied - period.  Very high quality copies can be made - even from copy-protected DRM sources like netflix using proprietary hardware like a Roku3 (which only has HDMI w/ HDCP output) with a small, relatively cheap, hardware investment. Too much DRM just pisses off potential clients.  Look up "video game recording" to learn more. Nobody really talks about the other abilities that these devices allow ... but that doesn't prevent them from working at 1080p er .... so I hear.

I'd recommend building good will and making other parts of the total educational experience value proposition more useful so that clients will pay.  Some of the Ruby-on-Rails people have done this. At least that is how it appears to me.

BTW, "stolen" implies that someone else can't also make use or purchase the content, which is not the situation. Copyright infringement does fit, however.

With all that said, the best answer is probably to get a business account on vimeo or some similar service and let them handle the video protection.  A Roku channel perhaps?

Allowing a computer to directly access the videos is asking for trouble.  Just sayin'.

---

### Post by Rawit on 2013-10-30
It's perhaps best to figure out the whole copyright/legal stuff concerning the video's beforehand. Also embedding the website as a watermark into the video prevents a lot of copying.

---

### Post by TheFu on 2013-10-30
> **Rawit said:**
> It's perhaps best to figure out the whole copyright/legal stuff concerning the video's beforehand. Also embedding the website as a watermark into the video prevents a lot of copying.

Good point. There are 2 types of copies - locally downloaded for personal use and downloaded to be shared either via torrent or reused on paid sites elsewhere.  The watermark can be useful for the lazy infringers, but those can be masked with some video editing tools.  Search for "avidemux delogo"

---

