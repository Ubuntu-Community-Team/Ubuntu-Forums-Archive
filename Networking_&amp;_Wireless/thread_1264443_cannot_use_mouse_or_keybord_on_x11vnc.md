---
title: "cannot use mouse or keybord on x11vnc"
date: 2009-09-12
forum: Networking &amp; Wireless
---

### Post by 78ufzniyE4 on 2009-09-12
Helo people i rarely use ubuntufourms but this time i realy have a problem i cannot use my mouse or my keybord through an x11vnc connection i dont know why or how if its just a settings problem im very sorry for disturbing your day but this is realy a bumer :( im all mixed up about ssh :confused: so i cant use that and other vnc clients are sick they are totaly useless thank you for your time









Linuxbrother11...

---

### Post by krunge on 2009-09-12
> **linuxbrother11 said:**
> Helo people i rarely use ubuntufourms but this time i realy have a problem i cannot use my mouse or my keybord through an x11vnc connection i dont know why or how if its just a settings problem 
Are you using the x11vnc supplied by ubuntu or one you compiled yourself from the source tarball?

Sometimes people compiling it themselves hit this missing libxtst-dev problem:
[INDENT][http://www.karlrunge.com/x11vnc/faq.html#faq-missing-xtest](http://www.karlrunge.com/x11vnc/faq.html#faq-missing-xtest)[/INDENT]
which sounds like your description.

---

### Post by 78ufzniyE4 on 2009-09-13
no i oppened a terminal and typped in sudo aptitude or apt-get install x11vnc

and subcomandante a person in the #yafaray irc x11vnced on mine and he could use the mouse and keyboard

:(:confused:

---

### Post by krunge on 2009-09-13
> **linuxbrother11 said:**
> no i oppened a terminal and typped in sudo aptitude or apt-get install x11vnc

When you connect can you *move* the mouse, but cannot click or type?  Or can't you even move it?
> and subcomandante a person in the #yafaray irc x11vnced on mine and he could use the mouse and keyboard :(:confused:
She connected to the same x11vnc you set up on your system?

What VNC viewer are you using and on what OS/distro/version?  Ditto for subcomandante?

Does your VNC viewer have some 'viewonly' setting toggled on?

---

### Post by 78ufzniyE4 on 2009-09-19
ok ill have to tell you how i vnc ok i oppen a terminal and type x11vnc -rfbauth /home/aaronvarghese/.vnc/passwd and then it oppens up and it tells you the port and you can get your ip from whatismyip.com or type in ifconfig and it should tell you ur ip address 
:lolflag: everyone should know that any way so subcomandante which is a HE typped in vncviewer <IP>:5900 and then he hits enter and it preforms the rfb authorisation and then i tell him my passwd and he gets inside and helps me out with some programs problems and bugs but when i try to help someone by typping vncviewer <IP>:5900 it connects but no clicks or taps working on the keybord and mouse and no i did not choose viewonly.:guitar::guitar::guitar::P

---

### Post by krunge on 2009-09-19
> **linuxbrother11 said:**
> any way so subcomandante which is a HE typped in vncviewer <IP>:5900 and then he hits enter and it preforms the rfb authorisation and then i tell him my passwd and he gets inside and helps me out with some programs problems and bugs but when i try to help someone by typping vncviewer <IP>:5900 it connects but no clicks or taps working on the keybord and mouse and no i did not choose viewonly.
So you see the screen?  Can you move the mouse (but not click)?
  
When you try to help someone, what VNC server are they running at their machine?

Is it x11vnc or something else?  If it is x11vnc, add the logfile option to it:
```
x11vnc ... -o /tmp/x.log
```  Then try it all again and either attach /tmp/x.log to this thread or send it to me in PM.

---

### Post by 78ufzniyE4 on 2009-09-21
> **krunge said:**
> So you see the screen?  Can you move the mouse (but not click)?
  
When you try to help someone, what VNC server are they running at their machine?

Is it x11vnc or something else?  If it is x11vnc, add the logfile option to it:
```
x11vnc ... -o /tmp/x.log
```  Then try it all again and either attach /tmp/x.log to this thread or send it to me in PM. 

yes i can move my mouse i experimented on local (on aaronvarghese and dub) and i noticed that the updating only lasts few seconds then it freezes but the mouse can be moved and while there is updating you can click i havent tried typping and while typing the code that u gave do i have to type '...' or x11vnc -0 /tmp/x.log thanks

Linuxbrother11...

---

### Post by krunge on 2009-09-22
> **linuxbrother11 said:**
> yes i can move my mouse i experimented on local (on aaronvarghese and dub) and i noticed that the updating only lasts few seconds then it freezes but the mouse can be moved and while there is updating you can click i havent tried typping and while typing the code that u gave do i have to type '...' or x11vnc -0 /tmp/x.log thanks
Maybe you need the "-noxdamage" option or disable compiz?  Search these forums for "noxdamage" for more info on that workaround for a Xorg/compiz bug.

---

### Post by irvin on 2009-09-23
Right Mouse-Click won't work sometimes

Hallo

I have a similar Problem. I made a VM (Ubuntu 9.04-32bit) in virtualbox (Host is 9.04 - 64-bit). I installed X11VNC 0.9.3 and also tried 0.9.8-2 debian package which I found.

When I now connect to the VM from my windows PC via putty+tightvnc viewer sometimes the right mouse click won't work anymore. Sometimes after a few days, sometimes directly from the start. I can do anyhing with the mouse, only the right mouse click is gone :-(

With older Versions of Ubuntu 7.04. 8.04 I dont' have this Problem, only with the new Ubuntu 9.04

Any Ideas where the Problem is ?
Thanx

---

### Post by krunge on 2009-09-24
> When I now connect to the VM from my windows PC via putty+tightvnc viewer sometimes the right mouse click won't work anymore. Sometimes after a few days, sometimes directly from the start. I can do anyhing with the mouse, only the right mouse click is gone :-(

With older Versions of Ubuntu 7.04. 8.04 I dont' have this Problem, only with the new Ubuntu 9.04

Any Ideas where the Problem is ?
Since this is only for button3 I think it is a different root cause.

You can add the '-dp' option to x11vnc and get verbose debugging printout for the pointer.  So you will see if x11vnc receives the Button3 click from the viewer and how it responds. 

I'm wondering if the problem is due to some sort of 'accessibility' tool in gnome (or even kde...) Maybe an accessibility (or other desktop) daemon is intecepting all user input and messing up somehow.

---

### Post by irvin on 2009-09-25
many Thanks for the answer, but this does not work.
After changing these two files:
/etc/gdm/Init/Default
/etc/gdm/PreSession/Default

with this line
/usr/bin/x11vnc -rfbauth /etc/x11vnc.pass -o /tmp/x11vnc.log -forever -bg -rfbport 5900 -xrandr

to

/usr/bin/x11vnc -rfbauth /etc/x11vnc.pass -o /tmp/x11vnc.log -forever -bg -rfbport 5900 -xrandr -dp

After Reboot i have no gnome login Screen anymore.
After changing the first file:
/etc/gdm/Init/Default

back without the -dp I had a login screen but after login it's blank again. And then I changing the second file back to the original line everything worked again.
Isn't this strange ?

Edit:
I can't connect via putty+tightvncviewer anymore. Login with putty works, but when I try to login via vncviewer
i get the info "Connection closed".

I reinstalled x11vnc and watched in all the files, but everything ist fine in the files but it won't work anymore.

Edit 2:
Only the first login with VNC crashes. When I login directly on the Host machine with Virtualbox and then connect via putty+vnc i see the desktop and everything works.

Here's the logfile, may it helps.

25/09/2009 16:54:08 passing arg to libvncserver: -rfbauth
25/09/2009 16:54:08 passing arg to libvncserver: /etc/x11vnc.pass
25/09/2009 16:54:08 passing arg to libvncserver: -rfbport
25/09/2009 16:54:08 passing arg to libvncserver: 5900
25/09/2009 16:54:08 x11vnc version: 0.9.8 lastmod: 2009-06-14
25/09/2009 16:54:08 Using X display :0
25/09/2009 16:54:08 rootwin: 0x100 reswin: 0x400001 dpy: 0x8464360
25/09/2009 16:54:08 
25/09/2009 16:54:08 ------------------ USEFUL INFORMATION ------------------
25/09/2009 16:54:08 X DAMAGE available on display, using it for polling hints.
25/09/2009 16:54:08   To disable this behavior use: '-noxdamage'
25/09/2009 16:54:08 
25/09/2009 16:54:08   Most compositing window managers like 'compiz' or 'beryl'
25/09/2009 16:54:08   cause X DAMAGE to fail, and so you may not see any screen
25/09/2009 16:54:08   updates via VNC.  Either disable 'compiz' (recommended) or
25/09/2009 16:54:08   supply the x11vnc '-noxdamage' command line option.
25/09/2009 16:54:08 
25/09/2009 16:54:08 Wireframing: -wireframe mode is in effect for window moves.
25/09/2009 16:54:08   If this yields undesired behavior (poor response, painting
25/09/2009 16:54:08   errors, etc) it may be disabled:
25/09/2009 16:54:08    - use '-nowf' to disable wireframing completely.
25/09/2009 16:54:08    - use '-nowcr' to disable the Copy Rectangle after the
25/09/2009 16:54:08      moved window is released in the new position.
25/09/2009 16:54:08   Also see the -help entry for tuning parameters.
25/09/2009 16:54:08   You can press 3 Alt_L's (Left "Alt" key) in a row to 
25/09/2009 16:54:08   repaint the screen, also see the -fixscreen option for
25/09/2009 16:54:08   periodic repaints.
25/09/2009 16:54:08 
25/09/2009 16:54:08 XFIXES available on display, resetting cursor mode
25/09/2009 16:54:08   to: '-cursor most'.
25/09/2009 16:54:08   to disable this behavior use: '-cursor arrow'
25/09/2009 16:54:08   or '-noxfixes'.
25/09/2009 16:54:08 using XFIXES for cursor drawing.
25/09/2009 16:54:08 GrabServer control via XTEST.
25/09/2009 16:54:08 
25/09/2009 16:54:08 Scroll Detection: -scrollcopyrect mode is in effect to
25/09/2009 16:54:08   use RECORD extension to try to detect scrolling windows
25/09/2009 16:54:08   (induced by either user keystroke or mouse input).
25/09/2009 16:54:08   If this yields undesired behavior (poor response, painting
25/09/2009 16:54:08   errors, etc) it may be disabled via: '-noscr'
25/09/2009 16:54:08   Also see the -help entry for tuning parameters.
25/09/2009 16:54:08   You can press 3 Alt_L's (Left "Alt" key) in a row to 
25/09/2009 16:54:08   repaint the screen, also see the -fixscreen option for
25/09/2009 16:54:08   periodic repaints.
25/09/2009 16:54:08 
25/09/2009 16:54:08 XKEYBOARD:
25/09/2009 16:54:08 Switching to -xkb mode to recover these keysyms:
25/09/2009 16:54:08    xkb  noxkb   Keysym  ("X" means present)
25/09/2009 16:54:08    ---  -----   -----------------------------
25/09/2009 16:54:08     X           0x40  at
25/09/2009 16:54:08     X           0x5b  bracketleft
25/09/2009 16:54:08     X           0x5d  bracketright
25/09/2009 16:54:08     X           0x7b  braceleft
25/09/2009 16:54:08     X           0x7d  braceright
25/09/2009 16:54:08     X           0x7c  bar
25/09/2009 16:54:08     X           0x5c  backslash
25/09/2009 16:54:08 
25/09/2009 16:54:08   If this makes the key mapping worse you can
25/09/2009 16:54:08   disable it with the "-noxkb" option.
25/09/2009 16:54:08 
25/09/2009 16:54:08 X FBPM extension not supported.
25/09/2009 16:54:08 X display is capable of DPMS.
25/09/2009 16:54:08 --------------------------------------------------------
25/09/2009 16:54:08 
25/09/2009 16:54:08 Default visual ID: 0x21
25/09/2009 16:54:09 Read initial data from X display into framebuffer.
25/09/2009 16:54:09 initialize_screen: fb_depth/fb_bpp/fb_Bpl 24/32/4096
25/09/2009 16:54:09 
25/09/2009 16:54:09 X display :0.0 is 32bpp depth=24 true color
25/09/2009 16:54:09 
25/09/2009 16:54:09 Listening for VNC connections on TCP port 5900
25/09/2009 16:54:09 
25/09/2009 16:54:09 Xinerama is present and active (e.g. multi-head).
25/09/2009 16:54:09 fb read rate: 9 MB/sec
25/09/2009 16:54:09 screen setup finished.
25/09/2009 16:54:09 

The VNC desktop is:      DEXTER:0

******************************************************************************
Have you tried the x11vnc '-ncache' VNC client-side pixel caching feature yet?

The scheme stores pixel data offscreen on the VNC viewer side for faster
retrieval.  It should work with any VNC viewer.  Try it by running:

    x11vnc -ncache 10 ...

One can also add -ncache_cr for smooth 'copyrect' window motion.
More info: [http://www.karlrunge.com/x11vnc/faq.html#faq-client-caching](http://www.karlrunge.com/x11vnc/faq.html#faq-client-caching)

25/09/2009 16:58:12 Got connection from client 77.237.243.21
25/09/2009 16:58:12   other clients:
25/09/2009 16:58:12 Disabled X server key autorepeat.
25/09/2009 16:58:12   to force back on run: 'xset r on' (3 times)
25/09/2009 16:58:12 incr accepted_client for 77.237.243.21:39835.
25/09/2009 16:58:12 Client Protocol Version 3.8
25/09/2009 16:58:12 Protocol version sent 3.8, using 3.8
25/09/2009 16:58:12 rfbProcessClientSecurityType: executing handler for type 2
25/09/2009 16:58:12 created xdamage object: 0x400025
25/09/2009 16:58:14 Pixel format for client 77.237.243.21:
25/09/2009 16:58:14   32 bpp, depth 24, little endian
25/09/2009 16:58:14   true colour: max r 255 g 255 b 255, shift r 16 g 8 b 0
25/09/2009 16:58:14 no translation needed
25/09/2009 16:58:14 rfbProcessClientNormalMessage: ignoring unsupported encoding type zlibhex
25/09/2009 16:58:14 Enabling X-style cursor updates for client 77.237.243.21
25/09/2009 16:58:14 Enabling full-color cursor updates for client 77.237.243.21
25/09/2009 16:58:14 Enabling cursor position updates for client 77.237.243.21
25/09/2009 16:58:14 Using image quality level 6 for client 77.237.243.21
25/09/2009 16:58:14 Enabling LastRect protocol extension for client 77.237.243.21
25/09/2009 16:58:14 Enabling NewFBSize protocol extension for client 77.237.243.21
25/09/2009 16:58:14 Using tight encoding for client 77.237.243.21
25/09/2009 16:58:15 client_set_net: 77.237.243.21  0.1513
25/09/2009 16:58:15 copy_tiles: allocating first_line at size 33
25/09/2009 16:58:22 client 1 network rate 51.9 KB/sec (2281.1 eff KB/sec)
25/09/2009 16:58:22 client 1 latency:  12.8 ms
25/09/2009 16:58:22 dt1: 0.0610, dt2: 0.8308 dt3: 0.0128 bytes: 45985
25/09/2009 16:58:22 link_rate: LR_BROADBAND - 12 ms, 51 KB/s

---

### Post by krunge on 2009-09-25
> **irvin said:**
> 
/etc/gdm/Init/Default
/etc/gdm/PreSession/Default

Do you really need to add it to both? I only use /etc/gdm/Init/Default.

BTW, did you put the KillInitClients=false in gdm.conf and/or gdm.conf-custom?  Search for 'x11vnc killinitclients' for more info.
> 
/usr/bin/x11vnc -rfbauth /etc/x11vnc.pass -o /tmp/x11vnc.log -forever -bg -rfbport 5900 -xrandr -dp

back without the -dp I had a login screen but after login it's blank again. And then I changing the second file back to the original line everything worked again.
Isn't this strange ?

Oh, you have found a bug.  Get rid of the '-bg' and put '&' at the very end of the line.
> 
Edit 2:
Only the first login with VNC crashes. When I login directly on the Host machine with Virtualbox and then connect via putty+vnc i see the desktop and everything works.
Maybe this is the lack of changing KillInitClients=false?  Did you do it?

---

### Post by irvin on 2009-09-26
Thanks, as for using x11vnc i had to only do this 2 changes for versions of ubuntu until 8.04

- sudo gedit /etc/gdm/Init/Default

and add this line to the file:

/usr/bin/x11vnc -rfbauth /etc/x11vnc.pass -o /tmp/x11vnc.log -forever -bg -rfbport 5900 -xrandr

sudo gedit /etc/gdm/gdm.conf
Search for this
#KillInitClients=true

And change it to this:

KillInitClients=false

That was it.

Starting with 8.10 and 90.4 now I had to to this, you told me this. Because after the first login after reboot the vnc closes.
So i had to do this to make it happen:

- sudo gedit /etc/gdm/Init/Default

and add this line to the file:

/usr/bin/x11vnc -rfbauth /etc/x11vnc.pass -o /tmp/x11vnc.log -forever -bg -rfbport 5900 -xrandr

- sudo gedit /etc/gdm/PreSession/Default

and add this line to the file:

/usr/bin/x11vnc -rfbauth /etc/x11vnc.pass -o /tmp/x11vnc.log -forever -bg -rfbport 5900 -xrandr

sudo gedit /etc/gdm/gdm.conf

now search for this:

#KillInitClients=true

And change it to this:

KillInitClients=true

sudo gedit /etc/gdm/gdm.conf-custom

add this in the DAEMON Section:
KillInitClients=true

That's it !
But as you see, the "KillInitClients=true" stays "true" from 8.10 on.

As I get rid of (-bg) should the line just look like this ?

/usr/bin/x11vnc -rfbauth /etc/x11vnc.pass -o /tmp/x11vnc.log -forever -bg -rfbport 5900 -xrandr &

Thanks again

---

### Post by 78ufzniyE4 on 2009-09-26
Ahhh... I cant solve the problem :confused:. And btw Noxdamage does not do anything. Perhaps x11vnc is not the right thing for me. :( . Any further ideas im going to put this link on the irc #ubuntu and see if i can get Live help. If anyone has anymore solutions please post them here. OH and also i turned Compiz off.:(

---

### Post by krunge on 2009-09-26
> **irvin said:**
> 
So i had to do this to make it happen:
..
- sudo gedit /etc/gdm/PreSession/Default

Now I see what you are doing.

However I believe your old way (KillInitClients=false) should work on recent ubuntu if you put this x11vnc option```
-noxfixes
```  This works around a recent Xorg crash bug.  Search for 'x11vnc noxfixes' and you will find discussion of it.

But your post (unrelated to the original post BTW) talked about Button3 not working.  I didn't know you had the other problem.  Anyway try "-noxfixes" for the login one.
> 
As I get rid of (-bg) should the line just look like this ?

/usr/bin/x11vnc -rfbauth /etc/x11vnc.pass -o /tmp/x11vnc.log -forever -bg -rfbport 5900 -xrandr &

Yes, that looks good.  Except you haven't removed the "-bg" yet.

---

### Post by krunge on 2009-09-26
> **linuxbrother11 said:**
> Ahhh... I cant solve the problem :confused:. And btw Noxdamage does not do anything.

linuxbrother11:  run x11vnc with "-o /tmp/x11vnc.log".  Connect to it via VNC  viewer and make sure the problem is still happening.  Then attach the **full** /tmp/x11vnc.log to this thread (please don't paste it in to thread, it is too big).  Then I will have a look.

---

### Post by 78ufzniyE4 on 2009-10-02
Ok ive tried noxdamage but no diffrence! I think there is no other solution!:( Ill turn the thread to solved

or one of you please tell me what you think. should i solve it or leave it

---

### Post by krunge on 2009-10-02
> **linuxbrother11 said:**
> 
or one of you please tell me what you think. should i solve it or leave it
Where's the full log file I asked for? Or do you prefer to play 20 questions? ;-)

---

### Post by irvin on 2009-10-06
Hallo

Here's my logfile after putting the "&" Option.
I put this option in both files:
/etc/gdm/Init/Default
and
/etc/gdm/PreSession/Default

Hope that helps with my "no right mouse click" Problem.

Also I tried your option -noxfixes with the old config for ubuntu 7.04. This works but I don't have the normal mouse cursor. Now there's a big Cross or X. Can I get the normal cursor back with any option ?

---

### Post by krunge on 2009-10-06
> **irvin said:**
> 
Hope that helps with my "no right mouse click" Problem.

Nothing jumps out to me.  I was expecting you to use the "-dp" debug pointer option I suggested.  Then you will get lots of lines printed out; several for **every** pointer movement or click.  Then, with the "-dp" output being captured, you would do some "right mouse clicks".  Then we would at least know if x11vnc was receiving those right mouse clicks from the viewer.  Once received x11vnc would very likely inject them into the desktop.  If we saw all that, I would begin to suspect something on your desktop preventing the clicks from having effect.  If they never got to x11vnc, that suggests a problem with the viewer-side desktop.
> 
Also I tried your option -noxfixes with the old config for ubuntu 7.04. This works but I don't have the normal mouse cursor. Now there's a big Cross or X. Can I get the normal cursor back with any option ?
Yes, the XFIXES feature is what allows x11vnc to retrieve the current mouse cursor shape from the X server.  If we disable XFIXES (i.e. to avoid Xorg crashing) then you only get some "canned" cursor shapes.

The Xorg crash seems to only happen at startup with x11vnc doing some xfixes activities.  I suspect some "pointer device" is null at that point and that is why Xorg crashes.

Anyway, x11vnc has a little known "remote control" feature.  So once you login and are in your desktop via VNC you can try to re-enable XFIXES by typing this *additional* x11vnc cmd in a shell on the desktop:
```
x11vnc -R xfixes
```
This will return immediately with, hopefully, the original x11vnc now in xfixes mode and the Xorg server not crashing.

You may need to also re-enable cursor shapes via 
```
x11vnc -R cursor=most
```

---

### Post by irvin on 2009-10-06
Sorry, but if I use the -dp option which I just did again i'll get a blank ubuntu screen and the system doesn't work anymore. So I have to do an new installation again. I could't fix this.

That's what I did in both files:
/usr/bin/x11vnc -rfbauth /etc/x11vnc.pass -o /tmp/x11vnc.log -forever -bg -rfbport 5900 -xrandr -dp

---

### Post by krunge on 2009-10-06
> **irvin said:**
> Sorry, but if I use the -dp option which I just did again i'll get a blank ubuntu screen and the system doesn't work anymore. So I have to do an new installation again. I could't fix this.

That's what I did in both files:
/usr/bin/x11vnc -rfbauth /etc/x11vnc.pass -o /tmp/x11vnc.log -forever -bg -rfbport 5900 -xrandr -dp
Earlier I believe I suggested this:
```

/usr/bin/x11vnc -rfbauth /etc/x11vnc.pass -o /tmp/x11vnc.log -forever -rfbport 5900 -xrandr -dp &

```

---

### Post by irvin on 2009-10-07
Hi

OK, was my mistake :-(
Now I did it with the "-dp &" an get a result. I did the option in both config files. Hope this helps.

---

### Post by krunge on 2009-10-07
> 
Now I did it with the "-dp &" an get a result. I did the option in both config files. Hope this helps.
OK, looking at the log I see you pressing button 3 (the right mouse button), for example:
```

07/10/2009 08:37:17 pointer(): mask change: mask: 0x0 -> 0x4 button: 3
07/10/2009 08:37:17 pointer(): sending button 3 down (event 1)
07/10/2009 08:37:17 calling XTestFakeButtonEvent(3, 1)  300.5550
07/10/2009 08:37:17 # pointer(mask: 0x0, x: 805, y: 678) dx:   0 dy:   0 dt: 0.0662 t: 300.6198
07/10/2009 08:37:17 pointer(): mask change: mask: 0x4 -> 0x0 button: 3
07/10/2009 08:37:17 pointer(): sending button 3 up (event 1)
07/10/2009 08:37:17 calling XTestFakeButtonEvent(3, 0)  300.6199
07/10/2009 08:37:17 # pointer(mask: 0x0, x: 805, y: 677) dx:   0 dy:  -1 dt: 0.1487 t: 300.7685
07/10/2009 08:37:17 XQueryPointer:     x: 805, y: 677)
07/10/2009 08:37:17 # pointer(mask: 0x4, x: 805, y: 677) dx:   0 dy:   0 dt: 0.1030 t: 300.8715

```
So x11vnc injected this button 3 click into the X server.  Did the click not appear on the desktop?

---

### Post by irvin on 2009-10-07
No, nothing happens when I press the right Mouse Button.

Maybe, I'm not sure, it has something to do with the Virtualbox guest additions ? But as I said, in the "old" Ubuntu's everything works. Only in the newer 8.10, 9.04 and 9.10 it isn't working. Sometimes from beginning, sometimes after a few minutes, hours, days ...

---

### Post by krunge on 2009-10-07
> **irvin said:**
> No, nothing happens when I press the right Mouse Button.

So for the most recent '-dp' log you posted, the right mouse button was not working at all (i.e. causing no effects on the desktop) for all of those clicks?
> 
Maybe, I'm not sure, it has something to do with the Virtualbox guest additions?

Could be.  I also wonder about an accessibility daemon trapping things somehow...

---

### Post by irvin on 2009-10-08
> **krunge said:**
> So for the most recent '-dp' log you posted, the right mouse button was not working at all (i.e. causing no effects on the desktop) for all of those clicks?

Could be.  I also wonder about an accessibility daemon trapping things somehow...

Yes, all the clicks with the right mouse button had absolutely no effect. I tried a lot :-)

I'll make a test without the guest additions, but I think I had trouble before without them too.

---

### Post by krunge on 2009-10-08
> **irvin said:**
> Yes, all the clicks with the right mouse button had absolutely no effect. I tried a lot :-)

Yes, as the log shows x11vnc did its job by calling XTestFakeButtonEvent() for the right button (i.e. button 3).  So the problem seems to be downstream of that.

A couple thoughts:

[INDENT]Try all of this in a failsafe session (i.e. no gnome, kde, etc.)  Also try it in a simpler window manager (e.g. blackblox or xfce.)  Trying to narrow it down to which desktop.

Try running xev(1) and putting the mouse in its window and clicking.  It prints out all events received.  See if it is receiving the button3 clicks or not.  You should also use xev in the failsafe test too.[/INDENT]

---

