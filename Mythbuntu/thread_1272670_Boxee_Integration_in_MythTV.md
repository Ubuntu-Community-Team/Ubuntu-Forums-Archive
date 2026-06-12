---
title: "Boxee Integration in MythTV"
date: 2009-09-22
forum: Mythbuntu
---

### Post by bsntech on 2009-09-22
Hello all,

I have finished setting up Boxee on a second PC that I will use as a front end.  The main MythTV box doesn't seem to work with Boxee - when I load Boxee, it just goes to a black screen and does nothing.  Even waiting over an hour, nothing still came on the screen.  I believe it is related to my SiS Xabre 330 video card since it doesn't support OpenGL.

Anyways, I have successfully set Boxee up on the second box with the GeForce MX4000 video card.

Boxee integration works fantastic and getting the remote to work took a bit of time.  The only place I read that you needed the lircmap.xml file was in the ~/.boxee/UserData folder - when you actually also need to place the same file in the /opt/boxee/UserData folder.  That is when the remote finally started working.

Anyways, I am quite happy to see how Boxee works and the integration it has with several online streams from Hulu, YouTube, CBS, MTV, Discovery, Comedy Central, and countless others.

IMO, MythStream will be a goner when Boxee is officially "integrated" in with MythTV.  The ShoutCast Streams and Apple Movie Trailers are also in Boxee as well.

If anyone would like help getting Boxee integrated so that it appears in a MythTV menu and also would like to have their remote work with Boxee, see my link with my full MythTV setup guide (kept there so I have record when I re-do the main PC).

The Boxee setup guide is down fully at the bottom.

[http://www.bsntech.com/content/view/591/281/]("http://www.bsntech.com/content/view/591/281/")

---

### Post by williammanda on 2009-09-22
Yes I agree your problems are your video card. There are several of us that have intergrated boxee into mythtv:

[http://ubuntuforums.org/showthread.php?t=1262401]("http://ubuntuforums.org/showthread.php?t=1262401")

Also the lircmap.xml only needs to be in /opt/boxee/system to function correctly.

---

