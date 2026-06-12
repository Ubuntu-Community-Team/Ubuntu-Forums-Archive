---
title: "IP Camera Video Streaming"
date: 2010-04-06
forum: Multimedia Software
---

### Post by Rhiknow on 2010-04-06
My local priest has asked me if I can use my computer skills to stream church services live for people who can't make it to church.

I said, sure thing! I thought it would be simple, but the deeper I look into it, the more lost I have become!

Here's the tech requirements:

- A camera with good optical zoom and focused on the altar (the camera will be stationed at an unobtrusive point at the back of the church on the choir balcony)
- Everything must be wireless (power is available on choir balcony to power the camera). 
- Sound should be synchronised perfectly with the video (have access to the church PA system - located behind altar)
- the internet connection should be able to upload the stream to a virtual server (i.e. with root access) that's accessible to the web with ease. What upload speed would I need? Would 256k be enough? HD video is not required - youtube quality would be great. We can upgrade to HD at a later point in time!
- What bandwidth requirement would my server need if say 1000 users were connected? Seeing as they would most likely be locals, would just one stream be sent to the local exchange and that exchange would send out the stream to the 1,000 users, or would each user have to have a dedicated connection to the server?
- Say I bought a camcorder with HDMI output, what kind of processing power would I need to convert this to compressed video? (I've got an old Pentium 4 and an AMD64 2.0GHz lying idle in my bedroom and it would be great to make use of 'em instead of chucking 'em on the skip)
- I'd like all this to be done so that HTML5 browsers can access the video, resorting to flash if necessary
- I'd also like to be able to power down all the hardware with ease: i.e. set a timer. I'm sure ubuntu can do this with ease? What about configuring the camera to zoom in every time it is powered on? Can linux control the zoom on a camcorder?
- Am I totally nuts?

Any insight from you guys would be much appreciated.

Pax.

---

### Post by allenck on 2010-04-12
Sounds like an interesting and worthwhile project. I just setup a webcam on my server and used the Yawcam webcam software. I don't know about the need to control the zoom but Yawcam should enable you to broadcast the video. I'm not an expert on this but you might be able to find more help in the Yawcam forum.

---

### Post by casedog21 on 2010-04-13
I too am working on this project.  I have a local "For Fun" sports group and are wanting to broadcast their events on the camera.  

What I have used in the past for internet DJ was Icecast2.
I have that same setup and from what I can tell I can use it to push NSV video to it. I just cant get the VLC encoder to login into the Icecast part and create a mount.  

If there is a better way I am all for it. This is one of those cases so far that I have found is way easier in Ms. You can use MS encoder9 and set it to server the stream or relay it to a MS server. 

My server with the big internet pipe is of course... ubuntu server

Any help here would be welcomed with a smile..
:)

Casey

---

