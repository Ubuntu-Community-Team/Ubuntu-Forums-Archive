---
title: "Tearing Windows and Video Playback"
date: 2011-05-07
forum: Multimedia Software
---

### Post by debd on 2011-05-07
I have a problem with the display while it is in motion, i.e. while the fps rate is higher.
Like, when I move a window on my screen , the moving -window gets teared. 
The same happens with video playback., when the frame rate is higher during the playback, it gets teared. (please take a look at the attachments)
But there's no problem with 3D rendering in games.

I think the problem is  inconsistent windows due to partial updates in the frame buffer of X.org server (?). Or is it some other problem?

Am facing this problem after installing the nvidia driver (260.19.36) for my GPU- GeForce7025.  There was no problem when VESA driver was in use. 

For your information, the same happened with other Linux distros I have tried. (i.e. No problem with VESA & same scenario with nvidia)

_(*this info may be of some hint*)_
 One more problem I have with the nvidia driver is that-- I have the 1360x768 res. option instead of 1366x768 which is used as default in windows(with the driver installed)  But I cant use 1360x768 in Linux yet, as it gets the display out of the screen. Currently 'am using 1280x800  -- and may be for this reason I dont get a proper/appropriate font display. Its a bit hazy.
With VESA, I had the 1366x768 res. option and it would be set as default; but about 0.5cm would be left blank on the right side.

Is there a way to solve this problem other than switching back to vesa(which I dont want :( ) ?

Tell me if any info is needed.
Thanks.

---

### Post by Paddy Landau on 2011-05-07
This is clearly a driver problem. When you move the window, the graphics cannot keep up properly.

Either don't move your window while playing back, or change back to Vesa. Sorry.

---

### Post by debd on 2011-05-08
> Either don't move your window while playing back

 I dont have to move the window while playback. It just gets teared if the fps is little high.

>  Sorry.

no reason to be sorry! but you might want to know that natty users are facing the same problem. 
[http://ubuntuforums.org/showthread.php?t=1742643](http://ubuntuforums.org/showthread.php?t=1742643)

thanks.

---

