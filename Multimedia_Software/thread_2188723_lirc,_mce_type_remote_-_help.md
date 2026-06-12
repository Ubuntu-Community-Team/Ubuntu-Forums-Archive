---
title: "lirc, mce type remote - help?"
date: 2013-11-18
forum: Multimedia Software
---

### Post by squakie on 2013-11-18
I'm having a little problem - using lirc, a remote programmed to be a mce remote, and xbmc.

In xbmc if I go to something like videos and down to the "add videos", add some videos and come back to the videos menu, I have no "back" or whatever key - I can't get out of the menu.  I end up plugging in a wireless mouse just so I can exit the menu.

With a mouse I would normally just click on the "x" in the upper right to close the menu, right click on the visible xbmc "desktop" not in the menu, or click the "back arrow" symbol in the bottom right.  I can't get to any of those with the remote.

I assume it's something with the keys not being defined in the lircd.conf file for the mceusb remote definitions, but I also don't want to have to go through the recording process and manually define every key.  I don't know enough about the codes returned with the command line utility to test the remote, so I would have no idea how to just include those extra keys into the existing definition.

I've tried pressing every key  on my remote with no luck.

So, what simple thing am I missing?

Thanks.

---

### Post by TheFu on 2013-11-18
If you have an MCE remote and everything is not "just working", then you've probably selected the wrong remote.  I did and had all sorts of issues until the model was fixed. After that, it "just worked".  Not bad for a $17 model from Newegg. Haven't connected a keyboard to that machine in over a year. Everything is handled via ssh or the remote.

The lircd setting in mine is just this line
[B]include "/usr/share/lirc/remotes/mceusb/lircd.conf.mceusb"
[/B]in the main config file. Zero customization needed at all.

BTW, I believe that **Add videos** should be how you add entire directories, not a single video. I must be mis-reading the post.  [http://blog.jdpfu.com/2011/02/21/xbmc-tips](http://blog.jdpfu.com/2011/02/21/xbmc-tips) might help folks not too familiar with XBMC setup.

---

### Post by squakie on 2013-11-18
> **TheFu said:**
> If you have an MCE remote and everything is not "just working", then you've probably selected the wrong remote.  I did and had all sorts of issues until the model was fixed. After that, it "just worked".  Not bad for a $17 model from Newegg. Haven't connected a keyboard to that machine in over a year. Everything is handled via ssh or the remote.

The lircd setting in mine is just this line
[B]include "/usr/share/lirc/remotes/mceusb/lircd.conf.mceusb"
[/B]in the main config file. Zero customization needed at all.

BTW, I believe that **Add videos** should be how you add entire directories, not a single video. I must be mis-reading the post.  [http://blog.jdpfu.com/2011/02/21/xbmc-tips](http://blog.jdpfu.com/2011/02/21/xbmc-tips) might help folks not too familiar with XBMC setup.

Hummmmm.....I'll have to see if there is another code or not for the remote - I just picked the only one that said MCE. 

As far as videos, I probably picked a bad example of adding a single movie.  I have been using it just to load all  the movies, etc., in catagorized sub-folders - otherwise I can't imagine the work it would take ;)

Thanks for the input - I'll need to check the def's for my remote again (OneForAll 5 in 1).  I also have a Harmony 650, but it's "reserved" for my sister and brother in-law (darn!).

---

### Post by squakie on 2013-11-18
BTW - what button do you use on your remote to "go back"?  Everything is pretty much working as I need except that.  There are probably some others, but nothing I use that I know of (unless my playback controls don't work - never tried them ;)  ).

Thanks!

---

### Post by TheFu on 2013-11-18
I have an older version (120?) of [this]("http://www.newegg.com/Product/Product.aspx?Item=N82E16880101002")  I use the button with the return curl to the upper left of the main circle (lower left of the green button).

For all the things wrong with this remote, it isn't that buttons don't work. The main complaint is that it is IR and extremely limited off-axis support. Off by 10 deg and the signals are not seen. Which sorta sucks the big one. ;(

---

### Post by squakie on 2013-11-19
> **TheFu said:**
> I have an older version (120?) of [this]("http://www.newegg.com/Product/Product.aspx?Item=N82E16880101002")  I use the button with the return curl to the upper left of the main circle (lower left of the green button).

For all the things wrong with this remote, it isn't that buttons don't work. The main complaint is that it is IR and extremely limited off-axis support. Off by 10 deg and the signals are not seen. Which sorta sucks the big one. ;(

I'm starting to think I may need to go ahead and use the Harmony 650 remote any way -  I just can't get a "back" out of the dang remote no matter what key I press.

BTW - I don't usually go around plugging products, and I imagine there are a ton of perfectly usable used IR receivers out there, but I opted for[ this ]("http://www.ebay.com/itm/MCE-83-00000005G-Infrared-USB-Receiver-New-Bulk-IR601-/390686820382?pt=LH_DefaultDomain_0&hash=item5af6bfc81e")one.  It took me (believe it or not) 3 DAYS to learn the dang thing isn't plug and play - I had to actually power my system down, put the device then power up.  Only then does the device works.  Otherwise it just sits there blinking it's little red LED at you until you're ready to grind it into the concrete with a very heavy boot ;)

---

### Post by squakie on 2013-11-19
Yesssss!  I reprogrammed the remote for XBOX360 and used the xboc lircd file - now it works!!

Thanks, TheFu for pointing me in the right direction!

---

