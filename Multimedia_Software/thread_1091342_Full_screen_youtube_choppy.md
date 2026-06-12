---
title: "Full screen youtube choppy"
date: 2009-03-09
forum: Multimedia Software
---

### Post by Westnile on 2009-03-09
Hey guys.
My youtube video playback in full screen is choppy.

I have an ati radion 9800 1gb of ram and a amd 3500cpu.

I have installed the non free version of Flash.

My video drivers appear to be properly installed and configured. Ie: When I run fglrxinfo I get the correct feedback.  
When I run glxinfo I get correct feedback, 
When I run glxinfo grep | direct I get correct feedback.

When I run system monitor during youtube video playback my CPU usage reaches 100% but my ram useage doesnt change from its usual 50% 

Whats the deal?

---

### Post by warp99 on 2009-03-09
Your not going to like the answer. Here's the reason why it's choppy straight from the developers:

[http://blogs.adobe.com/penguin.swf/2008/05/flash_uses_the_gpu.html](http://blogs.adobe.com/penguin.swf/2008/05/flash_uses_the_gpu.html)

Flash will also not run hardware acceleration with Compiz, so it defaults to software mode. In any case Adobe Flash is a resource hog. On an Intel 8200 Quad core in SLI mode with dual nVidia 9500 GT cards my 64-bit Kubuntu install will consume 30-50% CPU cycles. To be fair the 64-bit version of Flash only uses software rendering mode, no hardware acceleration

Now you can get flash to work with Compiz with a little hack and a hex editor. It's very easy. Just open the libflashplayer.so file in your favorite hex editor then locate the string "compiz" and replace that word with any random array of letters/numbers (xxxxxx seems to work fine). Now flash will not default to software rendering when it greps to see if compiz is enabled.

---

### Post by Westnile on 2009-03-09
Lol, your right. I dont like the answer.

What could they have possibly been thinking?
ATI's market share is massive. Why would they not check to be sure flash would work properly on these cards?? 

What a bunch of idiots.

I hate life.

Note: If I wanted to know when this problem gets solved, how would I do that?

---

### Post by warp99 on 2009-03-09
First thing I would do is check the glx vendor string string to see if it's SGI:

```
glxinfo |grep -i vendor
```

If SGI is there well... no soup for you. :(

Another thing you can do is add some options to you xorg.conf in the device section to speed up rendering regardless if flash is using the GPU or not:

```
Section "Device"
        Identifier  "Configured Video Device"
	Driver      "fglrx"
	[b]Option	    "PseudoColorVisuals" "off"
	Option	    "UseInternalAGPGART" "no" # If you have an AGP slot
	Option	    "OpenGLOverlay" "off"
	Option	    "VideoOverlay" "on"[/b]
	Option	    "UseFastTLS" "1" # May have problems
	Option	    "EnablePrivateBackZ" "on" # Same here

```

The ones in bold you can add without any problems, but the last two may give you a speed increase and/or make the system unstable or just have no effect at all, so add those one at a time and see if you get a performance increase.

If flash is able to use the GPU you can turn off compiz completely or just replace your window manager before you watch any full screen movies like so:

To diable compiz
```
metacity --replace
```
To enable again
```
compiz --replace
```

If you want to get really fancy you can make a desktop launcher or make a script that checks which manager is loaded, then loads the opposite like a toggle. 

Any finally just do the flash hack with a hex editor if you want compiz running with flash. Adobe says it's too unstable, but flash is already too unstable as it is. It's always worth a try.

Even with all these little tweaks Flash is still going to be a resource hog. Case in point I have a MythTV server with a 256MB nVidia 6200 card, an AMD 3400+ CPU, and the composite extensions are disabled. Even with Flash using the GPU it takes 60%-80% of processing power when watching Hulu.com depending on the video quality (360/480). When I had a 128MB ATI 9500 Card in the machine Flash still took about the same amount of CPU processing power. Because of this poor performance I have to schedule all of the backend jobs late at night since anything else running would bring the system to its knees. 

If you think this is bad Flash performance on OS X is even worse. ;)

---

### Post by Westnile on 2009-03-09
Thanks for your help. I already checked for SGI and unfortunately there truly is no soup for me.
I'll try those tweaks you mentioned though.

Thanks for all your help.

---

### Post by dolphinholmer on 2009-05-06
No soup here either:

server glx vendor string: SGI
client glx vendor string: SGI

Which essentially means no flash video:(

I tried swfdec, which is better than adobe flash for youtube (not sure why that should be), but fails to play or hangs the browser on many sites that use flash, such as the BBC. So it's a non starter really. Same story with gnash.

Thanks warp99, but the xorg.conf options didn't help either.

Is there anywhere else to go with this?

---

### Post by greyfox1 on 2009-05-12
I didn't try the hex editor bit as I couldn't find libflashplayer.so in ~/.mozilla/plugins or /usr/lib/mozilla/plugins, but I did add the lines to xorg.conf and have noticed a difference!  Thanks much for that.  I didn't try the last two "experimental" lines, but just added the rest and fullscreen videos from hulu are much more smooth now.  I'm using an NVIDIA 7900GT with an AMD single core processor @ 2.5 GHz (the exact model escapes me ATM).  Anyway, thanks!

---

### Post by dolphinholmer on 2009-06-15
Some further notes on this issue:

See bug report:
[https://bugs.launchpad.net/ubuntu/+bug/346289](https://bugs.launchpad.net/ubuntu/+bug/346289)

Which includes a link to this tweak:
[http://blogs.adobe.com/penguin.swf/2008/08/secrets_of_the_mmscfg_file_1.html](http://blogs.adobe.com/penguin.swf/2008/08/secrets_of_the_mmscfg_file_1.html)
which made some difference to me.

Also worth mentioning if you're using Intel graphics is this How-to:
[http://ubuntuforums.org/showthread.php?t=1130582](http://ubuntuforums.org/showthread.php?t=1130582)

---

### Post by Endolith on 2009-06-15
Mine's actually a lot better since I upgraded to Jaunty.  It works pretty smoothly whether Compiz is on or off, surprisingly.

---

### Post by badrra on 2009-12-03
There is really a better solution. Check this link [http://badrra.wordpress.com](http://badrra.wordpress.com) 

Just follow the instructions and your good to go. 

Have fun.

---

