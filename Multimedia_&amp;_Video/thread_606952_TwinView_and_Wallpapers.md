---
title: "TwinView and Wallpapers"
date: 2007-11-08
forum: Multimedia &amp; Video
---

### Post by cluaps on 2007-11-08
Hi All,

Wondering if someone could help me solve this problem? What I'm trying to do is get my wallpaper to display on only 1 of my two twinview monitors and just have solid colour on the other.

I can't figure this out, but it must be possible as the screensaver runs independently on both screens.

Any ideas?

Cheers
cluaps

---

### Post by carlinuxlearner on 2007-11-10
This is not possible, unless you can find some program on the net that will do it.

C@RL

---

### Post by rsambuca on 2007-11-10
It is very simple to create this with gimp.  Just make an image that is the size of both desktops put together, and insert an image on one side and leave the other side any colour you choose.

---

### Post by phub4r on 2008-05-03
I had the same problem (my dual screen setup consists of two samsung syncMaster 226BW's with nvidia card and ubuntu Hardy Heron v8.04.)

After searching the following solutions came up:

Solution1
You can us GIMP plugin pandora, see [http://www.linuxjournal.com/article/7295](http://www.linuxjournal.com/article/7295) for more info. Problem, I could not get it to work, probably because I'm too stupid to get the whole GIMP plugin idea so I opted for solution 2, see below.

Solution2
Also GIMP (version 2.4.5) but by hand. To explain how read the step by step instruction below.


STEPS

[step 01] Get screen resolution of your monitor
- Goto: System>Preferences>Screen resolution
- Here you see window with a example twin view screen with big letters "Cloned output." Below it is a listbox with the resolution, in my case 3360x1050 (width x height). Twin view ofcourse means both screens so your monitor = (width / 2 x height). So my monitor resolution is 1680x1050.

[step 02] Goto to wallpaper website and download two images, one for left & one for right monitor.
- I used the website [http://www.mandolux.com/](http://www.mandolux.com/)
Download the images which apply for your monitor, so in this case for me this means two wallpaper images both with resolution of 1680x1050 (see step 1 why). 

[step 03] Open GIMP, I used version 2.4.5
If you do not have it installed then open terminal and type 
"sudo apt-get install gimp" this will install the latest GIMP version.

[step 04] Within GIMP, create a new image with correct resolution
- Goto, File > New 
- Width: fill in twin view width (not monitor width), so in my case this is 3360
- Height: fill in twin view height, so in my case this is 1050
- Click 'Advanced Options' and select Fill with: Transparency

[step 05] Within GIMP, open wallpaper images as layers
- Goto, File > open as layers: select the right monitor wallpaper first and click open button.
- Then again goto, File > open as layers: select the left monitor wallpaper.

[step 06] Drag & drop layers
- Goto, Tools > Transform Tools > Move (now you can drag&drop layers)
- Try to Align layers by hand. You can get a little help by selecting:Image > Align available Layers.
- When two layers are correctly juxtaposed (always wanted to use that word in a sentence ;-)) play around with with Layer > Layer to image size and Layer > auto crop layer until it seems about right.

[step 07] Flatten image
- Goto, Image > flatten image

Now save image and try to set as wallpaper. It should be equally distributed over your monitors, by this I mean. The 'left' part of the wallpaper image should only be visible on your left monitor and the 'right' part of the same wallpaper should only be visible the right part of your monitor.
If the wallpaper positioning is not exactly as you wanted, you can go back in GIMP and do control+z (undo) until you are back at the separate layers again so you can tweak a little more. Or begin from step 1 and try again.

It took me several times for a good result but now I'm there. 
Hope you found this useful, I've also attatched my wallpaper result just for reference.

---

