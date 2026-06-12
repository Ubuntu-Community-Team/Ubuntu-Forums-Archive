---
title: "Blue Tinted Display?"
date: 2009-07-13
forum: Multimedia Software
---

### Post by Zinmaster on 2009-07-13
I'm guessing this would go here..
well I've been at this for a few days now and finally got just about everything fixed and running on my displays....except one thing....the colour on the TV...it's still blue...one thing is when I take a screen shot it shows up "normal" on the comp monitor...I've adjusted just about every colour setting available. does any one have any ideas? I'm using one card, it's an Nvidia 8300 GS, the computer monitor is connected via VGA and the TV, which is a 32" LCD, is connected via what looks to be a S-Video to Component connection...If any one has ANY idea's I'm open and looking for any sugestions. I can give you any additional info if needed, and up some pics if wanted. Please help me out...so far I have had no help. And the screen is driving me NUTS. Thanks in advance -Robert

---

### Post by squaregoldfish on 2009-07-13
It should really be in Hardware & Laptops ;)

Anyway, your problem is almost certainly with the connection between the computer and the TV. Since you say you're using a component input, it's likely that one of the colour channels isn't being connected properly. There's a number of possible causes:


[LIST]
[*]Cable isn't corrected properly - try unplugging it and reconnecting (both ends!)
[*]Faulty cable - try a different one
[*]Faulty connectors on the PC and/or TV - this could be expensive
[/LIST]

Steve

---

### Post by Zinmaster on 2009-07-13
> **squaregoldfish said:**
> It should really be in Hardware & Laptops ;)

Anyway, your problem is almost certainly with the connection between the computer and the TV. Since you say you're using a component input, it's likely that one of the colour channels isn't being connected properly. There's a number of possible causes:


[LIST]
[*]Cable isn't corrected properly - try unplugging it and reconnecting (both ends!)
[*]Faulty cable - try a different one
[*]Faulty connectors on the PC and/or TV - this could be expensive
[/LIST]

Steve

The only thing wrong with that is the fact that before I got it set up properly and would run in "low graphics mode I had no issuse with colour...what so ever...and when I boot it's in colour just after I log in does it change to the blue tinted fun...
So with that said is it still possible that it could be the "adapter" that I have for the Video card? Should I call the comapny and try and get a replacement sent?

---

### Post by xyphur on 2009-07-13
It's not the cable. I have had the same issue on a number of "HDTV-enabled" nvidia boards with the 7-pin S-video connection on them. I have the same "s-video-to-component" cable you mention. In my experience the blue tint issues are Linux-specific.

I believe it happens because the TVs we're using are expecting YPrPb (also known as YCrCb, and/or component HDTV) color coding.

The problem is that once under Linux driver control, the boards are being put into RGB mode for that connection. Some televisions are capable of receiving RGB video over component cables, but as far as my research goes these are few and far between. The vast majority of HDTVs with component video expect YPrPb, so we need to find a way to tell our nvidia drivers (likely by way of a modeline in xorg.conf) to switch back to that mode.

Under windows, the last few revisions of the Nvidia ForceWare drivers have a software switch in the Nvidia Control Panel applet that allows you to switch between RGB and YPrPb modes for the svideo-to-component connection (a setting you wouldn't have unless the board detects this special cable as being connected to the board and terminated on the other end by component cables on a TV, same as with older s-video- or component-only boards that wouldn't show settings for those connection unless you had a corresponding cable attached to a device. My old TNT2 with s-vid in & out comes to mind.)

As I don't use Ubuntu on a machine connected to a TV, I can't test the latest drivers for this software switch in the Nvidia settings panel, but I fear this is likely the only way forward, save for the modeline shenanigans.

For my XBMC machine (which is based on Ubuntu), I've just stuck with a really good quality S-video cable for the time being. When I upgrade my TV, I'll be moving to HDMI anyway...

---

### Post by soffer12 on 2009-12-17
I am having the GeForce 8300 GS , and well I am using HDMI cable. it is still bluish.
if i remove the Nvida driver , all works well ( the generic Ubuntu driver is in use) , but this is not helping with  with the 3D accelerator. 
I am going to try the new 190 driver from Nvida, see if that works.

---

