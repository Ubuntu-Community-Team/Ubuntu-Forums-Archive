---
title: "advice on the current state of setting up tv out on nvidia"
date: 2008-07-19
forum: Multimedia Software
---

### Post by McQuaid on 2008-07-19
My friend got a new nvidia card and wants me to help him set up tv out (analog via s-video to an older tv).

He got a relatively new nvidia card, but on the lower end (an 8400gs I think).  

Anyway, I'm wondering how easy (or difficult) tv out is now to set up.  Can it all be done now by nvidia-settings or is major tweaking of xorg still required?

I have a nvidia card myself but I don't have a tv hooked up to it, so can't play around with the second display settings.

It's been years since I last tried myself to setup tv-out so here are some questions I have.

1) What's the maximum resolution output via s-video?  800x600, 640x480?

2a)My friend primarily wants to play videos to his tv.  Is clone the best option?  I believe I recall you can send a seperate screen to the tv.  Is that difficult to set up?

2b) Concerning issues with clone or setting up a seperate screen, I remember years ago the 2nd screen couldn't have vsync with opengl (or xv as well? can't recall), that won't do for playing video.  Is this only an issue in clone mode, or is it also an issue when tvout is a seperate screen?  If this is still an issue, what's the workaround?  Make the tv out the primary screen? Is there a way to force vsync on tv out?

3) if clone has to be used, how is that handled when his monitor is widescreen (ob. using a widescreen res) and of course a tv uses 4:3 res?  Do you have to drop the monitor to 800x600, 640x480?  Not sure if this involves xorg.conf juggling but my friend wouldn't really be comfortable with that, so ideally it would be set it up and leave it if possible.

Any suggestions would be great.  Again, mainly the tv out would be for playing video via xv, or probably opengl (like say xbmc) so I'd like to dodge vsync issues if possible.


edit:

Just read a little in the nvidia readme.  As I understand there are three video out modes, clone, twinview (def don't want that) and two independant X screens.

It says this here:

[ftp://download.nvidia.com/XFree86/Linux-x86/1.0-8174/README/32bit_html/appendix-p.html](ftp://download.nvidia.com/XFree86/Linux-x86/1.0-8174/README/32bit_html/appendix-p.html)
"
While there are several disadvantages to this approach as compared to TwinView (e.g.: windows cannot be dragged between X screens, hardware accelerated OpenGL cannot span the two X screens), it does offer several advantages over TwinView:

#

If each display device is a separate X screen, then properties that may vary between X screens may vary between displays (e.g.: depth, root window size, etc).
#

Hardware that can only be used on one display at a time (e.g.: video overlays, hardware accelerated RGB overlays), and which consequently cannot be used at all when in TwinView, can be exposed on the first X screen when each display is a separate X screen."


So it seems the opengl xv hardware issue still exists unless this part of the readme hasn't been updated for newer cards.  If one wanted to get around this, I guess they would use the basic clone option but then I assume they would be forced to drop their monitor res to a tv out res correct?  If one did want to go the separate X screen route, it seems one would make the tv out the first X screen so it has hardware opengl xv.

---

