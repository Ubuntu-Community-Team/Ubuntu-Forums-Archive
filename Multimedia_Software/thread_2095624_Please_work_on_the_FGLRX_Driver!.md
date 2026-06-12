---
title: "Please work on the FGLRX Driver!"
date: 2012-12-17
forum: Multimedia Software
---

### Post by eumpfenbach on 2012-12-17
Just upgraded to Ubuntu 12.04. Regretting it. All the video I watch is really choppy.

My graphics card:

VGA compatible controller: Advanced Micro Devices [AMD] nee ATI RS880 [Radeon HD 4250]

When I try and install "Post release Updates" for the FGLRX Driver it fails, even if I completely delete non-updated release first (which works).

When I go to system details, it lists the Graphics driver as "VESA: RS880". Is this normal?

Confused by this whole thing. 75% of what I use this computer for is watching video. If I can't get the video to smooth out, I'm deleting 12.04 and going back to whatever older version I had.

Any advice would be appreciated.

---

### Post by QIII on 2012-12-17
Edit:  scratch what was here.

Don't use the Post Release Updates.  It usually does not work.

---

### Post by eumpfenbach on 2012-12-17
I am using 12.04 and still having issues.

"system settings" tells me that FLGRX is installed and working under "additional drivers", but as I posted above, I see VESA: RS880 under "graphics" in "Details". This normal? Should it say FLGRX?

I doubt heat is my issue, given that it never works smoothly. If it were heat, wouldn't it work fine until it overheated and then I would see it malfunctioning?

Should I maybe try 12.10 and see if that works better with the "open source Radeon driver"?

---

### Post by eumpfenbach on 2012-12-17
Thanks by the way. I realize you can't fix it and wasn't really expecting my post to result in an overhaul of the driver. Should have titled it "please help me fix FLGRX or find a replacement".

---

### Post by QIII on 2012-12-17
See my update.  I realized you were using Precise after I posted.

My bad.

Just use the "normal" fglrx driver offered.

---

### Post by eumpfenbach on 2012-12-17
Sure, but even without the post-release updates I am getting choppy video.

---

### Post by eumpfenbach on 2012-12-17
I tried multiple video players as well. Not that.

---

### Post by QIII on 2012-12-17
The driver itself is not the issue with the choppiness.  I'm on a cellphone right now, but I'll try to get back after work.

---

### Post by Yellow Pasque on 2012-12-17
```
sudo apt-get remove --purge fglrx*
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup #if file doesn't exist, no worries
sudo rm -rf /etc/ati #
```

```
sudo apt-get install build-essential cdbs dh-make dkms execstack dh-modaliases fakeroot libqtgui4
```


```
cd ~
wget http://www2.ati.com/drivers/legacy/12-6/amd-driver-installer-12.6-legacy-x86.x86_64.zip
unzip amd-driver-installer-12.6-legacy-x86.x86_64.zip
chmod +x amd-driver-installer-12.6-legacy-x86.x86_64.run
sudo sh ./amd-driver-installer-12.6-legacy-x86.x86_64.run --buildpkg Ubuntu/precise
sudo dpkg -i fglrx*.deb
sudo amdconfig --initial -f
```

---

### Post by Yellow Pasque on 2012-12-17
^If that doesn't work, post the /var/log/Xorg.0.log

---

### Post by eumpfenbach on 2012-12-17
Appreciate the help but still getting choppy video

Log attached.

---

### Post by eumpfenbach on 2012-12-19
Bumping this once and then trying 12.10, then downgrading if I can't get solved.

---

