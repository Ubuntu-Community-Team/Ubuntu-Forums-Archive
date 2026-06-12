---
title: "HOWTO/trouble broadcasting ogg stream w/vlc"
date: 2008-07-03
forum: Multimedia Software
---

### Post by nonstopCM on 2008-07-03
I'm sorry I'm such an idiot about this stuff. After days of video card trouble, I managed to get vlc to broadcast a live mic recording coming from sound recorder. That was great, but since I couldn't get my video card to play nice I reinstalled Ubuntu (hardy) and then Ubuntu Studio. I'm currently running 2.6.24-19-rt. 

Much to my dismay, the method of streaming from my mic does not work now that I've reinstalled.

I'm specifically trying to stream meetings to an icecast2 server. I'm streaming to an HTML location in ogg format. 

It's been weeks since I've been trying to get this to work and I've tried to find/follow every piece of information I can with no luck - if what I need to do is out there I'm either too stupid to find it or to stupid to do it right. 

I've also installed a myriad of packages to no avail. This is what I get in the VLC messages: 

main error: Cannot resolve http port 8080 : Name or service not known
main error: cannot create socket(s) for HTTP host
access_output_http error: cannot listen on http:8080
stream_out_standard error: no suitable sout access module for `http/ts://http://source@rad10:listen.antiochians.org:8000'

I believe what I need to do is configure the shoutcast or icecast module, but I don't understand how to do that at all. Please help me. I'm going crazy. I need instructions for idiots.

---

### Post by Peyton on 2008-07-25
I don't know much about VLC, although it looks like you're trying to use "http" as the hostname. What command did you use to produce the above error?

---

### Post by nonstopCM on 2008-08-09
I open Audio Recorder, then VLC. I choose "open file" from the VLC menu and find the file that Audio Recorder is recording to. I check the "stream/save" box and then choose "settings" and it brings up a menu. From there, I am able to choose from a variety of methods of streaming out. I choose "http" and enter the webpage that it should stream to. I include a username and password in that line because it's required - I got it to work like this, as I said before, prior to reinstalling Ubuntu. 

I'm not sure if I need to configure icecast or what. I also can't figure out how to use darkice/darksnow - seems it's a client, but I can't find it after I install the package.

---

