---
title: "Best MP3/WMA w/lots of music  &amp; FlashPlayer problem"
date: 2007-08-05
forum: Multimedia &amp; Video
---

### Post by Snipersnest on 2007-08-05
Ok I don't want to convert music or anything. I'm just wondering what would be the best music player to use with like a library? I have about 40gb of music and I want to add it in like Media Player.

Also I found Swiftfox..but I don't think its to much different (for me anyhow). Parts I guess are faster but its almost the same. (to me) 

I wanted to install Flash so I followed the thing off Ubuntuguide.org to install Flash Player but every page I load still says install it.. so then I tried the normal installer from adobe.com I got the same results. Is there away to get these working for both FireFox and Swiftfox? Would it be two seperate installs?

Thanks

---

### Post by davem2312 on 2007-08-05
I have tried Banshee, Amarok, and Rhythmbox music players (with library use) with 160GB of music, and Rhythmbox was by far the fastest in terms of loading songs.

To play mp3s with Rhythmbox, you need gstreamer plugins.  Try this.

sudo apt-get install ubuntu-restricted-extras gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-base gstreamer0.10-plugins-base-apps gstreamer0.10-plugins-good gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-alsa gstreamer0.10-gl gstreamer0.10-ffmpeg gstreamer0.10-fluendo-mp3

These plugins should get everything to play in Rhythmbox, except for wmas, you need w32codecs for that.  However, you must own a copy of windows to install w32codecs legally, because these are proprietary codecs.

ubuntu-restricted-extras in most cases should get the flash player to work, unless you have an AMD64 processor or something.

---

### Post by Snipersnest on 2007-08-05
Thanks that sure worked out for the Flash player.. But umm w32codecs doesn't work? No installation candidate. 

Thanks for the help

---

### Post by davem2312 on 2007-08-05
Understand that this is illegal if you do not own a copy of MS windows

Add sources to apt
[B]
sudo gedit /etc/apt/sources.list[/B]

add these lines

[B]
deb [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) edgy free non-free
deb-src [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) edgy free non-free
[/B]

then at the terminal again

[B]wget -q [http://medibuntu.sos-sts.com/repo/medibuntu-key.gpg](http://medibuntu.sos-sts.com/repo/medibuntu-key.gpg) -O- | sudo apt-key add -
sudo apt-get update
sudo apt-get install w32codecs
[/B]

---

### Post by Snipersnest on 2007-08-06
I own 3 computers that came with Windows XP so I'm good :)
 
Thanks for the sources, I didn't know things were still getting pulled from Edgy.

---

