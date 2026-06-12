---
title: "Problems with .avi files in VLC"
date: 2008-04-02
forum: Multimedia &amp; Video
---

### Post by net wrek on 2008-04-02
Hey, I have not been using Ubuntu for very long, but thus far have much preferred it over windows xp. Anyhow this is so far the only problem I have not been able to solve on my own. When I am watching videos in VLC Player, the colour of all my .avi files is really distorted and screwed up. 

Here is an .avi file.

[IMG]http://i40.photobucket.com/albums/e226/ima_cartoon/Screenshot-4.png[/IMG]

The colour is really screwed and there is a green bar at the top, it does this with all my .avi files, and makes movies and other videos unbearable to watch.

This is a divx file

[IMG]http://i40.photobucket.com/albums/e226/ima_cartoon/Screenshot-4-1.png[/IMG]

Colour is good, and no green bar. So I was wondering if there is a simple way to fix this. I have no idea why or how it happened, it just kind of happened out of the blue any help would be greatly useful to me.

---

### Post by gsmanners on 2008-04-03
Does it do that discoloration with anything else? I get the feeling that twbb is a rip of a screener, so maybe it's just that file.

---

### Post by aeiah on 2008-04-03
does this happen in other video players?

---

### Post by net wrek on 2008-04-03
> **gsmanners said:**
> Does it do that discoloration with anything else? I get the feeling that twbb is a rip of a screener, so maybe it's just that file.

Yes it does it with all my avi files, and it didn't do it before.

> **aeiah said:**
> does this happen in other video players?

I just got Totem and all the files in that work just fine, but I still prefer the interface and style of VLC.

---

### Post by lswest on 2008-04-03
2 options:
a)  It has something to do with the dark theme you're using, if you changed it recently, try using a different theme

b) try deleting your vlc configuration files (probably in like ~/.vlc) so that when you start it again, it will rebuild the configuration.  might solve the problem.

just my $0.02

---

### Post by net wrek on 2008-04-03
> **lswest said:**
> 2 options:
a)  It has something to do with the dark theme you're using, if you changed it recently, try using a different theme

b) try deleting your vlc configuration files (probably in like ~/.vlc) so that when you start it again, it will rebuild the configuration.  might solve the problem.

just my $0.02

Nah, I've had he dark theme for a long time and only recently has VLC been all screwed up, and I'll try the configuration files idea.

---

### Post by Splat on 2008-04-03
I have a very similar problem, also with There Will Be Blood incidentally. Although for me it's not a horizontal green bar at the top but rather a vertical green bar (can still make out the image underneath, it's just tinted green) of about the same width located about a quarter of the screen's width from the left as well as the same kind of discolorations in the entire image as the OP.

Happens with all media players I've tried but only with that one file. All other files work perfectly in all players (though I usually use MPlayer). Pretty sure there's nothing wrong with the file though because it seems to work fine for everyone else.

Totem reports the video codec to be "DivX MPEG-4 Version 5" @ 24fps. I have another file with the same codec / framerate that works flawlessly. According to supplied info, this file is supposed to be XviD @ 23.976fps though... maybe that has something to do with it? Kind of doubt it though...


EDIT:

Just tried VLC (dont know why I hadn't tried before) and it plays it fine. There's still a very thin (about 1-2 pixels, only noticeable in fullscreen) horizontal green line at the bottom, but no discoloration of the entire image like with the other players. Still weird though, there must be a reason it works in VLC and not in the other players... output is set to default in VLC so I'm assuming it uses Xv (I have compiz running, so I don't think any of the others would work correctly) just like MPlayer and Totem... very strange.

---

### Post by cor2y on 2008-04-03
It looks like a decoder issue.
Have these files played before in previous versions of vlc?
I remember i had a similiar problem with some avi files in vlc but in addition to the green bits the image was upside down as well.
Changing to x11 output in vlc  until i updated the ati drivers fixed the problem temporarily.
Settings->Video->xshm from auto.
Another thing that might cause this as well is old versions of the xvid codec that the video was encoded with.
Your best bet is to find another media player that can sometimes correctly render the older version of the codec like mplayer.

---

### Post by Eastisle on 2008-04-04
I used to have the same issue, go to Video>Deinterlace at the top of VLC. Play around with one of the options, I don't remember which one I chose to fix it (I think I set it to X).

---

### Post by prince_niceguy on 2008-05-17
I too have same kind of problem. Not sure what the issue is... If i choose the output mode as X11 the green bar goes but video plays very slowly and cpu usage becomes very high. any idea what the issue is?

---

