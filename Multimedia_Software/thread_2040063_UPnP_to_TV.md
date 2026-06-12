---
title: "UPnP to TV?"
date: 2012-08-10
forum: Multimedia Software
---

### Post by Statia on 2012-08-10
Hi,

Is it possible to select my TV as mediarenderer from Linux? I can do something like that on my Android phone with BubbleUPnp: select a video file and then select the renderer: local (the phone's screen) or remote, my TV. TV will show up automatically as a renderer selection when it's switched on. I've been trying Google and the forum's search, but since I'm not sure how to phrase this in a few keywords, I haven't found what I'm looking for. All I find is using Linux as a mediaserver. Does anyone know of a program that can do this?

---

### Post by Statia on 2012-08-13
Bump?

---

### Post by Statia on 2012-08-31
Bump?

---

### Post by Statia on 2012-09-22
Is this really not possible?

---

### Post by BicyclerBoy on 2012-09-22
What you are asking is:
DLNA "push" support to UPnP Media Renderers

Most DLNA soln to date (on PC) have been "pull" not push..

And you want the linux PC to push to a TV renderer..

Not sure..have to study this one..

---

### Post by Statia on 2012-09-23
Thanks! At least you gave me a better keyword to Google.
I found this:

[http://www.serviio.org/download](http://www.serviio.org/download)

Will try it out.

---

### Post by BicyclerBoy on 2012-09-23
BubbleUPnP is avail across multiple platforms..

The most limiting factor in this arrangement (TV as renderer) is the TV.
I haven't read of anyone "pushing" to TV DMR.
This could make a good soln.
- backend server (in a cupboard etc)
- control tablet (scheduling, prog details, remote control)
- TV DMR

VLC, MythTV & XBMC seem to be able to work as renderer & server using many protocols including RAOP/AirPlay but only an iProduct TV (or open source firmware TV) is going to support AirPlay..
The AirPlay functionality was likely developed to take advantage of shiny tablets.
I believe RAOP/AirPLay etc is an encrypted form of DLNA protocol.

---

### Post by Statia on 2012-09-23
Thanks for your reply.
My TV can handle "being pushed", it is a Philips 37PFL7606.
I have pushed content that is stored on my NAS to the TV by using BubbleUPnP on my Android phone. This works nice, as the TV's own media server is not too great. (I have my hopes up for XBMC on the Ouya!). I did not know Bubble UPnP is also available for Linux, I'll give that a spin as well. Serviio did not work for me, it looks like it doesn't find my Java.

---

### Post by BicyclerBoy on 2012-09-24
Could be wrong..
But there is an Ubuntu ppa..
[http://www.bubblesoftapps.com/bubbleupnpserver/](http://www.bubblesoftapps.com/bubbleupnpserver/)

Android apps like this are cross-compiled/developed on other systems. Android (& target systems) suit consumption not development. This one could have used linux & netbeans etc..
This app makes heavy use of other open source linux stuff like ffmpeg.

---

### Post by jtgd on 2012-11-30
Did you try minidlna?

---

### Post by BicyclerBoy on 2012-12-01
It "just" looks to be a server..(guessing).
Doesn't exactly sell itself does it ?
There is no documentation to help explain its features/support..

---

### Post by jtgd on 2012-12-02
I've been using minidlna for a few months now and it works wonderfully.
It will index the directories I specify and serve the video and audio to my TV and other devices. It works better than any other server I've tried.

You should try it before you judge it.

---

### Post by BicyclerBoy on 2012-12-02
My judgements were limited to what can be observed from the website.

You might like to comment on the OP requirement seems how you have tried it..
Little point trying miniDLNA when does not appear to do what is required.

Does miniDLNA serve a flat file list of all your media or structured ?

---

### Post by jtgd on 2012-12-02
DLNA has Clients (like his TV), Servers and Control Points.  What the OP seems to want is a CP.  I think "push" is perhaps not a descriptive term, rather the CP tells the Client to pull from the Server.

My first post was in response to others that were suggesting servers.  I find minidlna to be the best server.

I came to this thread searching for a Linux CP myself.  I may try the Bubble thing to see if that works as a CP, but of the many others I've tried only 2 worked with Kinsky being the best and eezUPnP also workable.

I didn't see where the OP was asking to serve "flat" files.  Do you mean like a simple file server?  I did discover djmount and it does work, but not what I need since the files are on my Linux machine to begin with.

---

