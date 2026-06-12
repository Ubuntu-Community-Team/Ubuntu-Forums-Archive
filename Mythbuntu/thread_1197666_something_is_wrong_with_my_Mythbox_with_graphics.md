---
title: "something is wrong with my Mythbox with graphics"
date: 2009-06-26
forum: Mythbuntu
---

### Post by TravisEvans on 2009-06-26
Hi I am extremely new to this and am looking for help.
Yes I do have an ATI graphics card its a radeon something with 256 ram and 256 bit
anyway I'm trying to do this Mythbox setup and I can't get anywhere, all i get is a black screen with an outlined Grey beveled rectangle and thats it. If i hit a lot on the arrow keys i then get a different outline and i can move a box up and down to make a choice. But i see no text at all with anything. so if i hit escape and then chose the lower option i finally get the desktop. I get the same thing when i try to configure it like i need to. and I tried disabling all the theams to see if some odd default would work but no luck. here is a log file that i was able to make, again i just want to record tv with this computer and then watch it here and there. I have it coming in from an intenna and I know it all went to digital but with this same cord i can plug it into a tv in my room and watch tv just fine, an old crt tv, the antenna is really really big on top of our house and i live in the city so...

here can anybody just help me i don't even know how to create a new thread in this thing or a post. I have never used forms really ever.
I'm 19 I've been puttzing with computers for a long time and i have built six for firends and family.

man this is odd I hope that error log made it on here as an attachment.

Ok well I hope i can get help here and there I am just gonna post this everywhere and hope i can get some help set up.

Travis Evans

It says to put this link somewhere?
[http://mythbuntu.pastebin.com/f3633a24](http://mythbuntu.pastebin.com/f3633a24)
Yeah this link works it show you my comp set up if you can read all that code!


I have posted that above message here and there hoping for help
I have a leadtec tv tunner card. please check that link above it will tell you all the specs of my comp. but real quick 1gb ram, 60gb hd, Pentium 4 3.2 single core or 32 bit, I'm using the problem computer right now to type this and I don't understand it because my desktop envionment is nice and works fast but... idk I can't even set up the card for the tv or scan channels or anything i just get the black screen with what i said above. 

I am using mythbuntu 9.04 32 bit stright from the site.

Thanks for helping me I am sorry for the poor typing but i'm in a rush i have to go to work now...

---

### Post by uncle hammy on 2009-06-26
[http://ubuntuforums.org/showthread.php?t=1163714&highlight=outline](http://ubuntuforums.org/showthread.php?t=1163714&highlight=outline)
[http://ubuntuforums.org/showthread.php?t=1155163&highlight=outline](http://ubuntuforums.org/showthread.php?t=1155163&highlight=outline)

---

### Post by TravisEvans on 2009-06-26
Hey thanks, but I'm reading it and i don't see what i have to do to fix my problem...


what do i type and where?


Thanks

Travis

---

### Post by ktmom on 2009-06-26
I think you are being told that you are being affected by the change in Xorg drivers that cause problems with ATI cards.  The first thing you might try is to start the myth front end from a terminal using;
> XLIB_SKIP_ARGB_VISUALS="1" mythfrontend

If that helps, then look at the link (already supplied) [http://ubuntuforums.org/showthread.php?t=1163714&highlight=outline]("http://ubuntuforums.org/showthread.php?t=1163714") post #3

Else, the second link provided above, discusses turning off the DRI in the xorg.conf.  Edit your /ect/X11/xorg.conf file (back it up first) and add;
> Option "DRI" "off" as described in Bon's [Launchpad post]("https://bugs.launchpad.net/ubuntu/jaunty/+source/mesa/+bug/341898/comments/59") dated  2009-04-02.  

The link I just provided is to the specific post.  The entire discussion was refered to in the 4th post in the second link above.

---

### Post by TravisEvans on 2009-06-27
so yeah unfortunately that code in a terminal didn't affect it any same result. 

I'll give this other log editng thing a try if i can find it in this odd explorer deal


thanks again I think were making progress here!



Travis

---

### Post by ozybushwalker on 2009-06-28
My motherboard has the AMD 780G chipset - onboard ATI graphics.
When I first installed Mythbuntu 9.04 I selected the proprietary graphics driver. That didn't work well but I don't clearly recall the problem. I reinstalled and selected the open source graphics driver and that works fine, displaying both SD and HD free to air digital channels.

Which ATI graphics driver are you using?

My tuner is Leadtek Winfast DTV-2000H. I'm guessing from your posted lspci that you have a completely different tuner, one for analog TV? What model? Are you sure the tuner card is supported?

---

### Post by uncle hammy on 2009-06-28
Add to your /etc/X11/xorg.conf in the "Device" section

```
Option "DRI" "off" 
```

and I am pretty sure your problem will be resolved.

---

