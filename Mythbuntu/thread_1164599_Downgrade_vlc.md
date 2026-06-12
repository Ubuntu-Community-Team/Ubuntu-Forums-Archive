---
title: "Downgrade vlc?"
date: 2009-05-19
forum: Mythbuntu
---

### Post by elgordo123 on 2009-05-19
I have a script that will stream live tv, videos, dvd's etc over vlc.  (I ssh into my box and run it, then connect from video client).   They have taken out ALOT of the essential things I need.   
How do I downgrade vlc?  I've tried removing vlc, vlc-nox, libvlc2, vlc-data libvlc0 (or something like that).  I then tried to use the vlc 8.6 from Hardy, but got stuck in dependency hell and stopped. 
Can someone point me in the right direction to downgrade vlc?  I am aware of security issues, etc of old versions. 
Here is an example of one of the commands that USED to work:

vlc -I http --http-host=:8002  --sout-transcode-fps=15 --sout-transcode-deinterlace /myth/video/somevideo.mp4 ":sout=#transcode{vcodec=DIV3,acodec=mpga,vb=192,ab=64,scale=.5}:std{access=http{user='',pwd='',mime=video/x-ms-asf},mux=asf,url=:8001}"

I keep getting the SocketBindError (permission denied).  I've tried to run it as sudo and also as vlc-wrapper and sudo vlc-wrapper.  

EDIT -SOLVED, was crashing into my port 8080 I used for apache.  Hours for a stupid thing I should have caught right away.. duh!   I dont know how to delete a post... 


Any ideas?

---

