---
title: "vlc streaming how to??"
date: 2009-04-27
forum: Multimedia Software
---

### Post by element_G on 2009-04-27
I know that VLC is a much talked about program on these forums but I haven't been able to google  a how to on the internet or one in this forum. So here goes:

Does anyone know how to stream videos on my server at home to a remote laptop? I think this is probably vlc's webui but as stated I can't seem to find any docs/how tos/forum posts.

Thanks

---

### Post by Sin@Sin-Sacrifice on 2009-04-27
Couldn't you just open the file location since you're already networked? Unless you're trying to view it on more than one computer simultaniously... then network stream options under File in VLC has that option. I think you would just open the file and then press play on the host but my network is down because one PC crapped out... it's replacement is in the mail... or I'd test it for you.

---

### Post by element_G on 2009-04-27
I think I need to explain my request better, sorry:

At home I have a file server that has file sharing through samba which I can use to watch videos etc on my desktop and laptop on my local (home) network.

I travel for work often and right now, I am away from home and am wondering if there is a way of getting vlc to stream a video to this remote laptop.

---

### Post by Sin@Sin-Sacrifice on 2009-04-27
Yeah... but I'm sure you'd have to use ssh or remote desktop etc... Not sure of the details but I've been trying to do the same thing with my G1. I was successful when I had a wireless intranet but using the internet I've had no success. I would say just ssh to the pc at home and use local software to open the media. Streaming is beyond me... sorry I cant be of more help.

---

### Post by Sin@Sin-Sacrifice on 2009-04-27
This might help even though it's using windows version. [http://www.engadget.com/2005/11/29/how-to-stream-almost-anything-using-vlc/](http://www.engadget.com/2005/11/29/how-to-stream-almost-anything-using-vlc/)

---

### Post by element_G on 2009-04-28
Thanks for your responses, Sin@Sin-Sacrifice

I can ssh into my server and have vnc running so I can do the admin tasks I need to with vlc. VNC is definitely not a solution for streaming a video file over the internet though.

I have played around with vlc a bit more and gotten the webui working. I noticed a "web interface with flash output" link and decided to give that a try. When I tried to play something I found I had to install xubuntu-restricted-extras b/c there was an error about a missing mpeg encoder. However I am just fumbling about in this interface, I'm not able to play anything ?? 

Does anyone know the proper way to use the vlc web ui with flash output, or is there a better way?

---

