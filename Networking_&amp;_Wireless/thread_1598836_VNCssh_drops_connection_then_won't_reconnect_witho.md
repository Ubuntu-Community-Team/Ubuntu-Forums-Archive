---
title: "VNC/ssh drops connection then won't reconnect without reboot"
date: 2010-10-17
forum: Networking &amp; Wireless
---

### Post by mb_webguy on 2010-10-17
I'm using my netbook to connect to my headless media server using VNC over ssh, using the following in a script.```
ssh -f -L 5900:localhost:5900 matt@$xxx.xxx.xxx.xxx x11vnc -safer -localhost -nopw \
  -env X11VNC_WATCH_DX_DY=1 -once -xkb -display :0 \
  && sleep 5 \
  && vinagre --vnc-scale --display=:0 localhost
```Both computers are running 10.10, though the netbook is running UNE.

Generally, this setup works just fine, but occasionally the connection is dropped, and I can't reconnect without rebooting the media server.  I was thinking that the problem was due to either with x11vnc or vinagre, since when I reboot the media server I do so through ssh in the terminal.  But it happened just a minute ago while I was watching a movie streaming from the media server (using PS3 Media Server) to my PS3, and the PS3 lost the connection with the media server at the same time as my netbook lost the VNC connection.

I'm not sure what the specific problem is, or even where to start looking to identify it.  Any ideas?

---

### Post by krunge on 2010-10-17
You may want to add "-rfbport 5900" to the x11vnc cmdline to force use of port 5900, otherwise if 5900 is taken (by another x11vnc or something else) the new x11vnc will autoprobe to find a free port (e.g. 5901) that your ssh does not redirect to.

You may also want to use the -o log.txt on the cmdline to capture the x11vnc messages.  If you cannot understand them, post them here for a failure case.

Anyway, when it fails I suggest ssh-ing into the box and running "ps", "top", and similar tools to see which programs are running and/or consuming high CPU. Look for the X server and x11vnc processes.

Finally, there is a serious bug in the Xorg X server that was released in the recent ubuntu that can be triggered by x11vnc's default mode of operation. Basically the Xorg X server goes into an infinite loop.  The workaround is to supply the "-noxrecord" option to x11vnc.  See this thread for more info:

[INDENT][http://ubuntuforums.org/showthread.php?t=1585973](http://ubuntuforums.org/showthread.php?t=1585973)[/INDENT]

---

### Post by mb_webguy on 2010-10-17
> **krunge said:**
> You may want to add "-rfbport 5900" to the x11vnc cmdline to force use of port 5900, otherwise if 5900 is taken (by another x11vnc or something else) the new x11vnc will autoprobe to find a free port (e.g. 5901) that your ssh does not redirect to.
Hrm... except that the PS3 lost connection to the media server at the same time as I lost the VNC connection, I'd say that this might be the problem.  I had a similar issue previously in which closing vinagre wasn't killing x11vnc, and successive connection attempts couldn't grab display 0.  I solved this by adding a launcher to the media server's panel to "killall x11vnc" to end my VNC session rather than simply closing Vinagre.  I'd think that this would also release the port, but... *shrug*

> **krunge said:**
> Finally, there is a serious bug in the Xorg X server that was released in the recent ubuntu that can be triggered by x11vnc's default mode of operation. Basically the Xorg X server goes into an infinite loop.  The workaround is to supply the "-noxrecord" option to x11vnc.  See this thread for more info:

[INDENT][http://ubuntuforums.org/showthread.php?t=1585973](http://ubuntuforums.org/showthread.php?t=1585973)[/INDENT]
I can see how this might be a problem.  And it could very well be *my* problem, since until yesterday (when I finally decided to drop some money on an HDMI cable to connect the media server to the tv) the VNC connection from my netbook was the only way I could see whether the X server was running correctly.  I can't really think how this would affect the connection to the PS3, since I have PS3 Media Server set to run as an init process, but that could have been coincidence.

Thanks for the suggestions.  I've added all of them to my script, and will keep an eye on things (particularly the log file).

---

### Post by krunge on 2010-10-17
OK.  I don't really know what a media server or PS3 is so I can't help you out with that or their networking issues.  But if you have any x11vnc questions feel free to ask.

---

### Post by mb_webguy on 2010-10-17
> **krunge said:**
> OK.  I don't really know what a media server or PS3 is so I can't help you out with that or their networking issues.  But if you have any x11vnc questions feel free to ask.
PS3 = PlayStation 3
media server = [UPnP media server]("http://en.wikipedia.org/wiki/UPnP_AV_media_server")

As I said, though, it could have just been coincidence that I lost the VNC connection and the PS3's connection to the media server at the same time.  I haven't noticed this happening other times I've lost the VNC connection (though I also don't think I've been in the middle of watching a movie when I've lost the VNC connection before, either).

But your suggestions might be working.  I've been doing a lot of work on the media server today, and so far I haven't had any problems with the VNC connection.

I'm going to wait a few days before marking the thread solved though, especially since I haven't actually diagnosed the problem.

---

### Post by krunge on 2010-10-18
[QUOTE=mb_webguy;9988056]
But your suggestions might be working.  I've been doing a lot of work on the media server today, and so far I haven't had any problems with the VNC connection.
/QUOTE]
So you are using "-noxrecord" on the x11vnc cmdline now?

---

