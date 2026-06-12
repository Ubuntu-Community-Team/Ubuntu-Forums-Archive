---
title: "XBMC running real slow in 9.10"
date: 2010-05-18
forum: Multimedia Software
---

### Post by Infamshxr on 2010-05-18
Ok, exactly what the title says. Here's my specs:

AMD Semprom 1.8Ghz
512 MB RAM
Nvidia TNT2 M64 @ 32 MB

I know it's old lol but probably better than the onboard graphics. The computer is a Compaq  Presario sr1403wm. I checked proprietary drivers and there are none available. The graphics run smooth on the desktop and I don't have Compiz enabled. Any ideas or is the graphics card just too old for XBMC? Weird thing is, I also have the same problem in Ubuntu on my good desktop when it's connected to my TV. Just using a normal VGA cable. If I have it connected to my computer monitor using a DVI cable, there's no problem. The only thing I thought of was maybe the resolution was too high, but that made no difference with either computer. If this computer is too old for XBMC, what would be second best in line? MythTV? Doesn't need TV capabilities. Just to watch what's already on the computer. I just really like the XBMC interface and the fact that I can boot right into the interface and of course all the cool plugins and whatnot.
Thanks in advance.

---

### Post by disturbed1 on 2010-05-18
Xbmc's UI is pretty GPU intensive. You either have no 3d rendering (Vesa, NV) or very poor/incomplete 3d rendering (nouveau). Not only that, but the TNT 2 is a pretty weak card to begin with. MythTV is extreme overkill for just watching a bunch of videos already on the PC.

Use a player like Totem, Mplayer, VLC, Kaffeine ... Enable thumbnail previews in your file manager and increase the size of the thumbnails.

Nvidia has PCI versions of the 8400 graphics card available. Not only will you have the chance to use 3d rendering, but also [VDPAU](http://en.wikipedia.org/wiki/VDPAU).

---

### Post by Infamshxr on 2010-05-18
So my assumptions are right. I do have a 128mb ATI card laying around. I think its a 9200 or 9250. It might have died, I'm not sure. I do know its a lot newer than the tnt2 card that's in there now. If it isn't dead, you think it would be powerful enough? Anywho if I can't use either, there isn't any other media center programs that are good and would run good on it? I don't like totem/mplayer (seems the same thing to me.) I've had problems playing videos and the video quality sucks in my experience. I never used kaffiene, so idk anything about that one. I do like vlc, because of the options I have for videos, the only thing I don't like is the interface. I currently use vlc because of how well it plays videos. Is there any way to change the interface in vlc? The other media players I have used are kmplayer, which seems to play videos a tad better than totem/mplayer, and I have used xine, which plays videos very well but I hate the settings cuz they are too confusing to me and I really hate the interface.

---

### Post by Infamshxr on 2010-05-21
Well, I got some good news and bad news. The bad news is xbmc is still running slow and that 128mb card I had was indeed dead. The good news is I found a 64mb ati card and used that and now compiz enabled itself and a few more media center programs I'm trying run good. Myth tv was overkill, but thought I'd give it a shot. It runs faster than xbmc, but still slow. So far I really like the look and feel or enna and freevo, but found out that I have to edit text files to change their settings. That sucks... Big time. But, I kinda got it figured out. Does anyone know of anywhere I could get a good walk through/tutorial on either of these programs? I found some help on the wiki's but got slightly confused. Other than that, moovida looked promisng, but hate the layout. Can you change the theme in it? If so, that would probably be best for me because of all the nice video/audio streaming plugins it has. Last good news is I found out how to chnage the vlc skin and found one I like, so I always have that to fall back on. :)

---

