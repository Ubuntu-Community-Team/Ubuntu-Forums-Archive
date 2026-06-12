---
title: "GeForce 6600 display problem"
date: 2006-03-12
forum: Multimedia &amp; Video
---

### Post by kuratkull on 2006-03-12
I have this rather rare problem. I have only found a few examples of this problems on the web.

After the install when X starts, the screen is very distorted: full of little colourful boxes, and occasionally it flickers to a new pattern. I already know it has something to do with the video drivers, but how can i change them?
I can't see the desktop at all, even not for once(like some other cases i have read about). This happens to previous versions of Ubuntu too.
I would really like to solve this, as i have tried many other Debian based distros, but this seems to be the best :)

PS! Oh, if you happen to know why the ubuntu Live CD says on boot that my monitor is our of range(and displays a blank screen only with the message in the centre), then i would be grateful too. LG Flatron 775FT


Tanel

---

### Post by arganot on 2006-03-12
i'm trying to use the live cd of ubuntu 5.10 and have the same problem with the pretty lines of green----blue----brown ect.......i have sound i can here ubuntu finish loading...just cant see anything but lines and dots--blocks....
i'm also using a g-force 6600gt graghics card if anyone can point me in the direction to fix this i would love to see ubuntu without doing a full install
thanks for any help

---

### Post by kuratkull on 2006-03-12
I would like to point out that this problem is mensioned in the ubuntu bugtracker too, but nobody seems to care about that. Because this really is a serious "bug"...

---

### Post by kuratkull on 2006-03-14
here's a fix
[http://doc.gwos.org/index.php/Latest_Nvidia_Dapper](http://doc.gwos.org/index.php/Latest_Nvidia_Dapper)
it should work with other versions too, not only with dapper.
i used sudo apt-get install nvidia-glx
instead of
sudo apt-get install nvidia-glx linux-restricted-modules-`uname -r`

and it fixed my ubuntu :)

---

### Post by jcschlic on 2006-03-14
i too am trying to run the live cd and come into the same problems with my 6800gs.  i hear ubuntu finish loading but get all the weird lines.  Is there an update to the live cd that already comes with at least a generic nvidia driver?  I see people suggesting "open up the terminal"...to do patches...but I don't understand that...(like the above posting)

How do open up the terminal in the first place?  --especially if I get all these squiggly lines to begin with...

Maybe I should just try a really old video card first.........problem is is that if that doesn't work nothing will work because I don't even have onboard video...

---

