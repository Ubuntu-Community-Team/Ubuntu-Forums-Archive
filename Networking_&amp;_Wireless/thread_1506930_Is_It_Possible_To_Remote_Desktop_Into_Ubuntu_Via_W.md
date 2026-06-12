---
title: "Is It Possible To Remote Desktop Into Ubuntu Via WAN"
date: 2010-06-10
forum: Networking &amp; Wireless
---

### Post by hayhursm on 2010-06-10
[SIZE=3]In my quest to find the answer to this question I have found that others suggest using a VNC viewer on their Windows PC and setup X11vnc on their Ubuntu PC.  My only complaint is that this method is very slow when connecting to my Ubuntu machine but when I use Remote Desktop to connect to my Windows machine the speed is great.  I see Ubuntu 10.04 has RDP protocol built into the Terminal Server Client; so with that said is there some way I could RDP from Windows default Remote Desktop program into Ubuntu over the internet?  I heard that RDP protocol was proprietary to M$ but how can this be when it is clearly installed on Ubuntu?  I just want to see if there is anyway to avoid VNC.[/SIZE]

---

### Post by hayhursm on 2010-06-14
Bump

---

### Post by Peter09 on 2010-06-14
Yes,
ssh is the simple command line type interface, but you can pull up application GUI's across the WAN withit. However the best one that I have found is FREENX. Look it up on the internet, it will give you a excellent desktop experience.
 
The other option is something like X11VNC which can also sent compressed data across the WAN, I use it to support a couple of friends.

---

### Post by hayhursm on 2010-06-14
> **Peter09 said:**
> Yes,
ssh is the simple command line type interface, but you can pull up application GUI's across the WAN withit. However the best one that I have found is FREENX. Look it up on the internet, it will give you a excellent desktop experience.
 
The other option is something like X11VNC which can also sent compressed data across the WAN, I use it to support a couple of friends.
 
 
[COLOR=black][FONT=Verdana]I have looked into FREENX and I think it would work very well for me except I am unable to install any kind of client program on my work PC (IS Dept. restricts this).  The only client program I have access to is Windows Remote Desktop (the one under "Start", "All Programs" and then "Accessories").  That's why I was wondering if there was a host server I could install on my home PC running Ubuntu that could successfully communicate with the Window's Remote Desktop program?[/FONT][/COLOR]

---

### Post by krunge on 2010-06-15
> ... except I am unable to install any kind of client program on my work PC (IS Dept. restricts this).  The only client program I have access to is Windows Remote Desktop (the one under "Start", "All Programs" and then "Accessories").
One possibility with x11vnc is the '-http' or '-http_ssl -ssl ...' option that serves a java enabled VNC client (SSL encrypted in the 2nd case.) Then on the client side one only needs a java enabled web browser.

---

### Post by hayhursm on 2010-06-15
> **krunge said:**
> One possibility with x11vnc is the '-http' or '-http_ssl -ssl ...' option that serves a java enabled VNC client (SSL encrypted in the 2nd case.) Then on the client side one only needs a java enabled web browser.
 
Yes, I tried that with some success other than it "lagged" very bad.  Of course that could have just been some settings that needed tweaked.  Thank you for all your help but I believe I found my answer:
[http://ubuntuwiki.net/index.php/Xrdp,_installing](http://ubuntuwiki.net/index.php/Xrdp,_installing)

---

### Post by krunge on 2010-06-15
> **hayhursm said:**
> Yes, I tried that with some success other than it "lagged" very bad.
Could you describe which activities are slow and quantify by how much time they are lagged?

I ask this because there is a bug with the Xorg server that causes lagginess and it can be worked around with an x11vnc cmdline option to some degree.

---

### Post by hayhursm on 2010-06-16
> **krunge said:**
> Could you describe which activities are slow and quantify by how much time they are lagged?
 
I ask this because there is a bug with the Xorg server that causes lagginess and it can be worked around with an x11vnc cmdline option to some degree.
 
[COLOR=black][FONT=Verdana]I tested this for you this morning (as I was still unsuccessful in getting Xrdp to work).  I uninstalled Vino (I'm running Ubuntu Lucid) and then installed X11vnc via Synaptics.  Now to your question, there is probably a 3-4 second gap between the time I input a keyboard stroke or click the mouse before I see the outcome on my client monitor; I tested this with VNC Viewer instead of the Java setup.  Now to the Xrdp, I was only able to successfully get the Xrdp login screen to appear (the one where you can select your login preferences) but when I clicked ok I got a protocol error (even following the Wiki tutorial).  In the midst of my frustrations, I decided to try VNC Viewer with Vino (instead of going through Remote Desktop) and surprisingly it worked.  When I woke up this morning and tried it again I could get no response from the keyboard strokes and mouse clicks on the client PC. That’s when I uninstalled Vino and installed X11vnc to test and now I’m back to square one.  Right now I’m stumped and have wasted countless hours on something that should be very simple (at least it is in Windows).  I would really like to get this working through Windows Remote Desktop client.  Also, is there a known issue with using Windows 7 X64 Remote Desktop client to connect to Xrdp?  Thanks for the help![/FONT][/COLOR]

---

### Post by krunge on 2010-06-16
I think you should try it with x11vnc's "-noxdamage" option:
```
x11vnc -noxdamage ... (your other options)
```
to work around an Xorg bug in its DAMAGE extension. Let me know if that makes a difference.

BTW, which video drivers are you using?

---

### Post by hayhursm on 2010-06-16
> **krunge said:**
> I think you should try it with x11vnc's "-noxdamage" option:
```
x11vnc -noxdamage ... (your other options)
```to work around an Xorg bug in its DAMAGE extension. Let me know if that makes a difference.

BTW, which video drivers are you using?

I decided to install Kubuntu 10.04 and I must say I like it a lot  better than GNOME.  Anyways, I disabled the -noxdamage in X11vnc.  I  went through the interface it has instead of using the terminal (I hope  that is acceptable).  I noticed a definite speed improvement but would  it still be faster going through Xrdp?  I'm in a hurry so I didn't setup  up an SSH yet but if I did would that possibly help with speed (on top  of security of course)?  Also, since I was able to get X11vnc to work  with VNCviewer would that mean Xrdp would work?  Xrdp just links to a  VNCserver and X11vnc is a VNCserver correct?

Using ATI/AMD  Proprietary FGLRX graphics driver on host PC

---

### Post by krunge on 2010-06-17
> **hayhursm said:**
> Anyways, I disabled the -noxdamage in X11vnc.  I  went through the interface it has instead of using the terminal (I hope  that is acceptable).
Which interface are you referring to?  A GUI?
> I noticed a definite speed improvement

How long are the activities that you said took 3-4 seconds taking now with -noxdamage?
> but would  it still be faster going through Xrdp?  

I don't know; I've never used Xrdp.
> Also, since I was able to get X11vnc to work  with VNCviewer would that mean Xrdp would work?  Xrdp just links to a  VNCserver and X11vnc is a VNCserver correct?

That sounds like what I have heard about how Xrpd works.  Sorry I can't help you get it working.

---

### Post by YesWeCan on 2010-06-17
> **hayhursm said:**
> [SIZE=3]In my quest to find the answer to this question I have found that others suggest using a VNC viewer on their Windows PC and setup X11vnc on their Ubuntu PC.  My only complaint is that this method is very slow when connecting to my Ubuntu machine but when I use Remote Desktop to connect to my Windows machine the speed is great.  I see Ubuntu 10.04 has RDP protocol built into the Terminal Server Client; so with that said is there some way I could RDP from Windows default Remote Desktop program into Ubuntu over the internet?  I heard that RDP protocol was proprietary to M$ but how can this be when it is clearly installed on Ubuntu?  I just want to see if there is anyway to avoid VNC.[/SIZE]

I am not sure I can help you with the specific issues you seem to be having but I thought I'd give you a benchmark to compare. I run a remote desktop on my Ubuntu PC from a Ubuntu server located 3000 miles away. I am running Xtightvnc over there and vinagre here. I tunnel the connection using OpenVPN. Even with the VPN overhead the keystroke response time is less than half a second. It is extremely usable and reliable. I would have trouble watching a video but for everything else I do it is excellent.

So I suppose I'm saying it can work well and you may need to examine your set-up to see why it is performing so badly.

Good luck. 8)

---

### Post by Peter09 on 2010-06-18
One of the things to remeber is that the outgoing speed of broadband is significantly less that the incoming. 
 
I have a friend who I support using x11vnc, he has a 2MB broadband link and the response is really not good. I normally ask him to drive the mouse because of the response time because his 'up' speed is so bad.

---

### Post by YesWeCan on 2010-06-18
Good point, Peter.
My local connection has download/upload speeds of 4Mbps / 500kbps
The remote server has 20Mbps / 2Mbps
bps = bits per second
Brian

---

### Post by Peter09 on 2010-06-18
Yes - the thing to remember is that that is a maximum, ideal, speed, given no contention and a good connection. Having said that I would have thought you should be able to get a reasonable connection.
 
If you get a reasonable connection on the LAN then it is all to do with WAN speeds and quality of service.

---

### Post by Peter09 on 2010-06-18
Note: I also suspect that x11vnc does not do compression by default, at a quick glance it was not very clear how to enable it.

---

### Post by krunge on 2010-06-18
> **Peter09 said:**
> Note: I also suspect that x11vnc does not do compression by default, at a quick glance it was not very clear how to enable it.
It does enable compression by default.  Look for lines in the output like this:
```

18/06/2010 10:26:31 Pixel format for client 10.0.2.1:
18/06/2010 10:26:31   16 bpp, depth 16, little endian
18/06/2010 10:26:31   true colour: max r 31 g 63 b 31, shift r 11 g 5 b 0
18/06/2010 10:26:32 Using compression level 1 for client 10.0.2.1
18/06/2010 10:26:32 Using image quality level 9 for client 10.0.2.1
18/06/2010 10:26:32 Enabling X-style cursor updates for client 10.0.2.1
18/06/2010 10:26:32 Enabling full-color cursor updates for client 10.0.2.1
18/06/2010 10:26:32 Enabling cursor position updates for client 10.0.2.1
18/06/2010 10:26:32 Enabling LastRect protocol extension for client 10.0.2.1
18/06/2010 10:26:32 Enabling NewFBSize protocol extension for client 10.0.2.1
18/06/2010 10:26:32 Using tight encoding for client 10.0.2.1

```
"tight" encoding is pretty good, so is "zrle".  If it negotiates "hextile" that would be OK on a LAN but probably not a good choice on broadband.

If it negotiates "raw" encoding (no compression), something is really wrong and the updates will be very slow.

Sometimes (for older tightvncviewer) an SSH tunnel can confuse the viewer to think the connection is to localhost (same machine) and so it requests "raw" encoding.

I suggest the OP paste the above part of the x11vnc output (or all of it) to this thread so I can have a look at it.

BTW, it pays to have a simple desktop (e.g. solid background, window decorations  without color gradients, etc.)  There are some tips here:
[indent][http://www.karlrunge.com/x11vnc/faq.html#faq-slow-link](http://www.karlrunge.com/x11vnc/faq.html#faq-slow-link)[/indent]

---

### Post by hayhursm on 2010-06-18
> **krunge said:**
> Which interface are you referring to? A GUI?
 
How long are the activities that you said took 3-4 seconds taking now with -noxdamage?
 
I don't know; I've never used Xrdp.
 
That sounds like what I have heard about how Xrpd works. Sorry I can't help you get it working.
 
Yes the GUI that X11VNC has, that's what I used.
 
The activities are probably down to 1 - 1.5 seconds

---

### Post by krunge on 2010-06-18
> **hayhursm said:**
> 
The activities are probably down to 1 - 1.5 seconds
You mentioned earlier this was for keystrokes to appear and simple mouse click results.  1-1.5 secs is still too long for that (OTOH, exposing a large web browser window with complex images could easily take that long.)

I wonder what is wrong with your setup...  I have an x11vnc I keep open on the west coast (I'm on the US east coast) and for me to see keystrokes to appear in the VNC viewer is very fast, maybe 0.1-0.3 secs (the ping time is about 120ms)

---

### Post by hayhursm on 2010-06-21
> **krunge said:**
> You mentioned earlier this was for keystrokes to appear and simple mouse click results.  1-1.5 secs is still too long for that (OTOH, exposing a large web browser window with complex images could easily take that long.)

I wonder what is wrong with your setup...  I have an x11vnc I keep open on the west coast (I'm on the US east coast) and for me to see keystrokes to appear in the VNC viewer is very fast, maybe 0.1-0.3 secs (the ping time is about 120ms)

That could possibly be causing the lag.  You said you manage a system on the west coast, does it have a GUI?  If so, did you do anything to the background or colors to improve speed?

---

### Post by krunge on 2010-06-21
> You said you manage a system on the west coast, does it have a GUI?  
Yes; I meant to imply I export that GUI via x11vnc.
> If so, did you do anything to the background or colors to improve speed?
x11vnc has the '-solid' option that will try to make the background solid when viewers are connected.  

Unfortunately kde and gnome often break their interfaces and '-solid' might not work anymore in your environment.  If it doesn't work, you would have to change it manually to a solid background when you connect (or just leave it that way.)

There are some general speedup ideas here:
[INDENT][http://www.karlrunge.com/x11vnc/faq.html#faq-slow-link](http://www.karlrunge.com/x11vnc/faq.html#faq-slow-link)[/INDENT]

There is also an experimental client-side-caching scheme (-ncache option) described here:
[INDENT][http://www.karlrunge.com/x11vnc/faq.html#faq-client-caching](http://www.karlrunge.com/x11vnc/faq.html#faq-client-caching)[/INDENT]
I actually use this method (-ncache) on that west coast machine: I use a full photo image jpeg background and it works great (because the background image is cached on the viewer side.)

But be careful, as the FAQ above discusses, the client side caching may confuse you.

---

### Post by hayhursm on 2010-06-22
> **krunge said:**
> Yes; I meant to imply I export that GUI via x11vnc.

x11vnc has the '-solid' option that will try to make the background solid when viewers are connected.  

Unfortunately kde and gnome often break their interfaces and '-solid' might not work anymore in your environment.  If it doesn't work, you would have to change it manually to a solid background when you connect (or just leave it that way.)

There are some general speedup ideas here:[INDENT][http://www.karlrunge.com/x11vnc/faq.html#faq-slow-link](http://www.karlrunge.com/x11vnc/faq.html#faq-slow-link)[/INDENT]There is also an experimental client-side-caching scheme (-ncache option) described here:[INDENT][http://www.karlrunge.com/x11vnc/faq.html#faq-client-caching](http://www.karlrunge.com/x11vnc/faq.html#faq-client-caching)[/INDENT]I actually use this method (-ncache) on that west coast machine: I use a full photo image jpeg background and it works great (because the background image is cached on the viewer side.)

But be careful, as the FAQ above discusses, the client side caching may confuse you.

This is all very good information...thank you.  I do have some good news, I was able to successfully install FreeNX and also get the NoMachine client working on my work PC.  Have you messed with the FreeNX much?  Just curious as to what your thoughts are on it?

---

### Post by coskierken on 2010-06-22
Well, I switched over to Teamviewer for Ubuntu and Windoze.  They have a version for both.  I don't know if this may help you, but it did the trick for me.  I can view a Win machine and the Win can view me if I let it.  Of course there are slight delays, but that is more of a function of my internet speed, which is DSL and not too fast.

---

