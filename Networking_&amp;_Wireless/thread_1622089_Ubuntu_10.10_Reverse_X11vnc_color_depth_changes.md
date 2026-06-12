---
title: "Ubuntu 10.10 Reverse X11vnc color depth changes"
date: 2010-11-15
forum: Networking &amp; Wireless
---

### Post by Ynothna on 2010-11-15
Hey,

I have looked around and haven't had a lot of luck finding any information on this. I could be blind...but I'm not sure, haha.

I do a lot of remote support for my clients (I do PC repairs and training). I have recently starting suggesting to some of my basic users that they give Ubuntu a try. So far it has been very well received and they are loving it. The problem I am running into is that some of them use laptops in multiple places, and some use routers that are not easily configured. In each case it makes port forwarding a large pain in the behind to allow for remote access. 

I have started using the X11vnc reverse connection and it has been working well, except for the fact that it is using high quality color depth (24bit I think?). I know when starting the connection from my end I can set the color depth, but is there any way to set the depth of a reverse connection?

Also, I understand that using just vnc over the Internet is not secure. I need to look into a decent guide to set up SSH tunneling for this. I don't suppose anyone knows of a good guide for 10.04 and 10.10?

Any information is hugely appreciated! Thanks.

Ynothna

---

### Post by krunge on 2010-11-15
> **Ynothna said:**
> 
I have started using the X11vnc reverse connection and it has been working well, except for the fact that it is using high quality color depth (24bit I think?). I know when starting the connection from my end I can set the color depth, but is there any way to set the depth of a reverse connection?


It should work for reverse connection. In the VNC protocol is is the VNC VIEWER that selects what color depth and pixel format.  By default your VNC viewer will normally choose it to match the screen it is displaying on. Most VNC viewers have a setting for 8bpp color depth (and sometimes even 6 and 3 bit color.)

SSVNC (companion viewer to x11vnc) on Unix and MacOSX supports these low colors as well as a 16bpp mode (and all work for reverse connections as well.)  I can't remember what Windows VNC viewers do WRT color for reverse connections...
> 
Also, I understand that using just vnc over the Internet is not secure. I need to look into a decent guide to set up SSH tunneling for this. I don't suppose anyone knows of a good guide for 10.04 and 10.10?

SSH is a good choice. The x11vnc website has some info on how to do this (see also its -ssh and -proxy options.) x11vnc also supports SSL and VeNCrypt (which is basically SSL.) The SSVNC viewer can set up SSH or SSL tunnels automatically, even for reverse connections.

---

### Post by Ynothna on 2010-11-15
Thanks very much :) it's a relief to know it is possible, now I just need to figure out the details.

I have been using the pre-installed "Remote Desktop Viewer" that came with Ubuntu and it doesn't look like the GUI provides any way to change the settings on a reverse connection.

Is there a different one that would work better? Or a terminal command I should use instead to open Remote Desktop Viewer?

I mostly work with servers, so I'm still a little behind when it comes to using GUIs in Linux.

Thanks again,
Ynothna

---

### Post by krunge on 2010-11-15
> **Ynothna said:**
> 
I have been using the pre-installed "Remote Desktop Viewer" that came with Ubuntu and it doesn't look like the GUI provides any way to change the settings on a reverse connection.

What is the real name of this program? (perhaps try an 'About' button.)  vinagre or something else?
> 
Is there a different one that would work better? Or a terminal command I should use instead to open Remote Desktop Viewer?

Well SSVNC is a hack that I wrote, most people think it is too ugly & etc, but it will do all of this on Unix and MacOSX.  You can also change the color depth dynamically with it (F8 menu).

BTW, are you certain color depth is slowing you down significantly?

---

### Post by Ynothna on 2010-11-15
Silly me, I missed the "Vinagre" right under the big bold "Remote Desktop Viewer".

I'm not picky about how it looks, function is the important part.

I'm not positive how much of a difference it is making so I want to test and find out. A couple of my clients don't have a very fast connection, so any bit helps.

One main problem I have run into is the wallpaper. One client has an alternating one so I have to disable it to do any work. I don't suppose there is a script or daemon that can be watching for remote connections and disable/enable the wallpaper?

Thanks,
Ynothna

---

### Post by krunge on 2010-11-15
> **Ynothna said:**
> 
I'm not picky about how it looks, function is the important part.

SSVNC will do quite a lot for you; e.g. the color depth and encryption.  It is in the ubuntu/debian repositories. I can help you with it here in this thread if you need any.
> 
I'm not positive how much of a difference it is making so I want to test and find out. A couple of my clients don't have a very fast connection, so any bit helps.

Yes I have seen this.  Also with asymmetric links like cable-modem or DSL on both sides, the pixel traffic is going to hit one of the slow directions no matter what.
> 
One main problem I have run into is the wallpaper. One client has an alternating one so I have to disable it to do any work. I don't suppose there is a script or daemon that can be watching for remote connections and disable/enable the wallpaper?

x11vnc has its '-solid' option for doing this.  Sadly it no longer works on KDE.  I think it still works on GNOME...
[INDENT][http://www.karlrunge.com/x11vnc/x11vnc_opts.html#opt-solid](http://www.karlrunge.com/x11vnc/x11vnc_opts.html#opt-solid)[/INDENT]
If you find scripts that do this for the various desktops please let me know.

There is also an experimental x11vnc option called '-ncache' that tries to cache pixel data on the viewer side.  It works well with SSVNC. After the initial download of the background it will try to cache it for better response.  But the caching is heuristic and so it can miss opportunities. If you try out -ncache please report here if it improved things for you or not.

---

### Post by Ynothna on 2010-11-15
Awesome :) Thanks very much.

I will hopefully get to testing all of this in the next couple days and I will be sure to let you know how it goes. I'm having to give support for my Windows clients far more then my Linux clients, haha, so they keep me busy.

Ynothna

---

### Post by krunge on 2010-11-15
> **Ynothna said:**
> 
I will hopefully get to testing all of this in the next couple days and I will be sure to let you know how it goes. I'm having to give support for my Windows clients far more then my Linux clients, haha, so they keep me busy.

There was one fellow about a year or two ago who had a business similar to yours where he supported Linux and Windows machines. He made a lot of useful suggestions for feature enhancements and bugfixes to SSVNC. One of them that might be of use to you is "multilisten". More later.

---

### Post by Ynothna on 2010-11-15
I took a look at the website and so far it looks like exactly what I am looking for :)

The only problem I have run into so far is after downloading it I tried to run the startup script but got the error "exec: 3: wish: not found".

I took a look at installing wish with apt-get, but I wasn't sure if that is what it was looking for, so I didn't go ahead with anything.

Multilisten will be a very useful option to have. I don't have many Linux users at the moment, but with Windows I often have 3-4 computers open at a time.

Thanks,
Ynothna

---

### Post by krunge on 2010-11-16
> **Ynothna said:**
> 
The only problem I have run into so far is after downloading it I tried to run the startup script but got the error "exec: 3: wish: not found".

I took a look at installing wish with apt-get, but I wasn't sure if that is what it was looking for, so I didn't go ahead with anything.

You'll find a list of its dependences here:
[INDENT][http://packages.debian.org/squeeze/ssvnc](http://packages.debian.org/squeeze/ssvnc)[/INDENT]
The 'tk' one there will give you the 'wish' program. You might also need openssh-client, openssl, stunnel4 and perhaps a few others if they are not installed yet.

It might be simpler for you to just use the debian ssvnc.  Just type 'apt-get install ssvnc' and I think it will work.  That version will be older than the one on the ssvnc website, but you probably won't notice the difference.

Good luck.

---

