---
title: "How Do I Get the Extenal iSight to Work?"
date: 2006-09-05
forum: Multimedia &amp; Video
---

### Post by I922sParkCir on 2006-09-05
How Do I Get the External iSight to Work?

This is one of the last things I need to in order to convert my girlfriend to linux. She has been having several problems with her 15in iBook G4 (ppc)under OSX so I feel Ubuntu will work better for her.

I can get the wireless, suspend, and the trackpad scroll to work. This iSight nonsense is the lasting I need.

Thank you all.

---

### Post by I922sParkCir on 2006-09-05
Quess nobody wants to help me.

---

### Post by I922sParkCir on 2006-09-06
I am so happy I am not a new user and know how great the Ubuntu community is, or else this could be a bad experience. Thank you for always coming to the rescue before ubuntu community.

---

### Post by Lord Illidan on 2006-09-06
There is no call to be snide. We don't know everything.
After a google search, I found this, scroll down the page :
[http://en.wikipedia.org/wiki/ISight](http://en.wikipedia.org/wiki/ISight)

---

### Post by I922sParkCir on 2006-09-06
> **Lord Illidan said:**
> There is no call to be snide. We don't know everything.

I wasn't being snide, I was earnest. Thank you for your help.

---

### Post by oswaldkelso on 2007-05-12
> **I922sParkCir said:**
> How Do I Get the External iSight to Work?

This is one of the last things I need to in order to convert my girlfriend to linux. She has been having several problems with her 15in iBook G4 (ppc)under OSX so I feel Ubuntu will work better for her.

I can get the wireless, suspend, and the trackpad scroll to work. This iSight nonsense is the lasting I need.

Thank you all.

I'm running debian etch but got external isight running though only as root see link

[link]("http://www.my2bits.org/?p=62")

I just checked my senaptic history and below is everything I installed following a reinstall ( I messed up my permissions)


coriander (1.0.1-3.1+b1)
ftplib3 (3.1-1-6)
gdk-imlib11 (1.9.14-31)
gnome-bin (1.4.2-34)
gnome-libs-data (1.4.2-34)
imlib-base (1.9.14-31)
libart2 (1.4.2-34)
libdb3 (3.2.9+dfsg-0.1)
libdc1394-13 (1.1.0-3+b1)
libgdk-pixbuf2 (0.22.0-11)
libglib1.2 (1.2.10-17)
libgnome32 (1.4.2-34)
libgnomesupport0 (1.4.2-34)
libgnomeui32 (1.4.2-34)
libgnorba27 (1.4.2-34)
libgnorbagtk0 (1.4.2-34)
libgtk1.2 (1.2.10-18)
libgtk1.2-common (1.2.10-18)
liborbit0 (0.5.17-11.1)
libpt-plugins-dc (1.10.2-2)
libungif4g (4.1.4-4)

I had to change permissions for /dev/raw1394 to my user name.
  Ive not played around much with permissions so am not to sure if Ive done the right thing but it does work!! as a normal user but if Ive screwed other permissions I'm not sure. It was set to disk?

---

### Post by alexvd on 2007-05-12
Hi does this work with the mic on the iSight as well?  What is the maximum resolution you can capture?

---

### Post by oswaldkelso on 2007-05-13
> **alexvd said:**
> Hi does this work with the mic on the iSight as well?  What is the maximum resolution you can capture?

I have an external usb headset so dont know if the isight mic will work? When I was getting it to work there was an echo.  I thought it was from another mic but if it was from the isight mic or built in I have no idea. I do know the internal mic on my emac works, but use my andrea usb nc 7100 as the sound quality is better and you dont get specker echo.

When running in ekiga I just get a small window I dont know what size. If I check the resolution in coriander I get 320x240 at an option for 30fps or 640x480 an option for 30fps though I just noticed the actual frame rate shows as 15fps. If that can be setup for ekiga I dont know. 

Sorry I couldn't offer more help.

---

