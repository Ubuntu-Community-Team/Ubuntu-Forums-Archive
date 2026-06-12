---
title: "Having issues accessing mediatomb via XBMC"
date: 2010-06-30
forum: Multimedia Software
---

### Post by jfmanamtr on 2010-06-30
Ok. I will explain the setup first. What I have is two computers; one is my media server running Ubuntu Server 10.04 LTS, using mediatomb for UPNP streaming, & the other is a media center computer that I built running Linux Mint 9, using XBMC. I just recently setup the media server & was told that mediatomb is the best UPNP server ever (I think a friend of mine is a bit biased). 

So, I installed it from the Ubuntu repos & have been trying to get it working, but for the life of me can't figure it out. I have media tomb setup using the defaults & set to share 2 folders located on the media server (one for videos & one for music). The thing is that mediatomb says that it is running on the server, but when I check the media center, XBMC shows no UPNP shares. I also have samba sharing the folders & can see those if I tell XBMC to look using smb. I am just not sure why it can't see the mediatomb share. Any ideas on what I need to check? 

~JFM

---

### Post by jfmanamtr on 2010-06-30
Ok. I need to learn to read logs. I had mediatomb setup to bind to an IP address that wasn't in my subnet. That is the issue & all is well. Sorry for the noob mistake.

~JFM

---

