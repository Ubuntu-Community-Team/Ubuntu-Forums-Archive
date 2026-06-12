---
title: "Newbie Help..."
date: 2010-09-15
forum: Multimedia Software
---

### Post by firegeek on 2010-09-15
Asus AT3IONT-I Deluxe
Thermaltake "Q"
WD Caviar Black 1tb
Corsair XMS3 2x2gb DDR3

Build was surprisingly simple and fast. I even tied all the wires up nicley before testing which usually is a jinx. All wired correctly. Installed Unbuntu 10.04 because that was the version that I downloaded a couple of weeks ago when I decided to take on this adventure. I'm holding off with the "Boxee" install until I solve a few issues. The main one is that the os sees a 72" Sony that's not there. It's a 60" Sony Bravia SXRD Projection TV. All looks good at 1080p but I cannot see the tool-bars. I can wonder my mouse up and get the drop downs but cannot figure out what to do. I tried another screen resolution; the only one available in 16:9 but still barely brought the toolbars in sight. At this point I have a usb keyboard and mouse plug into the front of the box, but would love to get my Logitech Full-Size BT keyboard and track pad working. I feel pretty good to get this far--as my only Linux experience is  via a boot disk. Right now I not even worrying about sound. I just have it hooked straight to the tv via hdmi instead of going through my receiver. Once I'm able to get the screen dialed in it will be a lot easier. BTW--I'm hard wired to my lan via Ethernet cable and was able to get to the internet and sync my bookmarks with Exmarks. I know this is probably no great excitement for most, but I'm tickled to death to get this far. I have two Tivo's hooked to this tv, so Ill probably forgo a tuner. Just want me some big screen internet, Boxee, podcast, etc. Thanks to all in advance. I have been lurking around and this has enabled to get this far...

---

### Post by solar george on 2010-09-15
Have you installed the NVidia drivers from the restricted drivers manager? It's possible that they may help.

---

### Post by firegeek on 2010-09-15
I did that right after posting this thread. I tried every screen resolution available, and many more to choose from after installing Nvidia drivers. But, still cannot ever get to the point of seeing the toolbars. I can see glimpses of them. Is it possible that it doesn't have a compatible setting for this tv? I have two Tivos, PS3, Wii and several other devices connected to this set and they have no problem.

---

### Post by solar george on 2010-09-15
I've come across one TV that quite happily accepts any resolution input and then crops apparently randomly to make it fit so its possible there's not a setting that will work properly. How are the other devices connected? Have you any idea what the native resolution of your TV is?

---

### Post by firegeek on 2010-09-15
Not 100% positive of the "native resolution" but it I think its 1920x1080p...I'm wondering now if I should go ahead install Boxee. Isn't supposed to be "big screen" friendly. The PS3 plays 1080p br disk better than anything I've seen. It must have something to do with the GPU. But, I didn't reinvent the wheel. Several others are running this same specs but I don't know if it's on this big of panel.

---

### Post by solar george on 2010-09-15
Hmm yes if your TV is actually native 1920x1080 then I've not got any ideas left, the only thing I was thinking is maybe its native resolution is different and it uses scaling to get 1080p

---

### Post by firegeek on 2010-09-15
Update: I went ahead and installed the latest version of "Boxee" and it all looks great and fits the screen well. During install I was prompted to set the screen resolution and it was already 16:9 at 1920x1080 and once it looked great. After signing in and fooling around a little, watching feeds, using the browser, etc. No sound yet and that's another issue but one at a time--I exited to Unbuntu 10.4 and same issue. I couldn't view the toolbars. I had to hover along the top of the screen and blindly click the mouse to get the drop-downs.

---

### Post by bolojo on 2010-09-16
Hi, I don't have a 60" TV but I have a 27" LG TV and I faced the same problem. My TV also accepts 1920x1080 aka 1080p and it's connected to at3iont-i with hdmi cable. I also had your problem with toolbars of gnome, I also installed boxee which I don't like. I solved this situation by adjusting my TV's  "Image ratio" to "Simple scanning" or something like that (the default setting is 16:9, which doesn't work). Hope this helped!
> **firegeek said:**
> Update: I went ahead and installed the latest version of "Boxee" and it all looks great and fits the screen well. During install I was prompted to set the screen resolution and it was already 16:9 at 1920x1080 and once it looked great. After signing in and fooling around a little, watching feeds, using the browser, etc. No sound yet and that's another issue but one at a time--I exited to Unbuntu 10.4 and same issue. I couldn't view the toolbars. I had to hover along the top of the screen and blindly click the mouse to get the drop-downs.

---

### Post by Yellow Pasque on 2010-09-16
firegeek: post your /var/log/Xorg.0.log if still having issues
Also, you'll probably have to update ALSA to get sound from the ION through HDMI if that's what you're trying to do: [http://ubuntuforums.org/showthread.php?t=1046137](http://ubuntuforums.org/showthread.php?t=1046137)

---

### Post by firegeek on 2010-09-17
I have a workable screen/desktop at this point. I added 'scaling' to my search and found tons of good info on this subject. I made a few manual adjustments in the Nvidia tools and changed the settings in properties for the toolbars. My next issue is trying to get the Bluetooth working in which I also found a thread strictly dedicated to this mb with many good tips. Thanks to all for the help and future help. It's been a long time since I posted to a forum a "noob" and didn't flamed...

---

