---
title: "wacom &quot;touch&quot; not working on hp tx2"
date: 2009-07-30
forum: Multimedia Software
---

### Post by wolfgangpauli on 2009-07-30
Hi, 

I can't get them wacom "touch" to work under linux on my new notebook. The stylus works fine, but when I touch the screen with one finger, the cursor jumps to the top left corner of the screen as soon as I start moving the finger. If I do that on top of the desktop, it seems to scroll through my open windows. Any ideas?

here is what I think is the relevant log entries in Xorg.log

(**) touch: always reports core events
(**) touch device is /dev/input/by-path/pci-0000:00:14.5-usb-0:2:1.0-event-mouse
(**) touch (touch) is not a pad
(**) touch is in absolute mode
(**) WACOM: suppress value is 2
(**) Option "USB" "on"
(**) touch: reading USB link
(**) Option "TopX" "0"
(**) Option "TopY" "0"
(**) Option "BottomX" "9600"
(**) touch: bottom x = 9600
(**) Option "BottomY" "7200"
(**) touch: bottom y = 7200
(**) touch: threshold = 15
(**) touch: max x = 9600
(**) touch: max y = 7200
(**) touch: max z = 256
(**) Option "Touch" "on"
(**) /dev/input/by-path/pci-0000:00:14.5-usb-0:2:1.0-event-mouse: Touch is enabled
(**) Option "BaudRate" "9600"
(II) XINPUT: Adding extended input device "touch" (type: Wacom Touch)
(==) Wacom device "touch" top X=0 top Y=0 bottom X=9600 bottom Y=7200 resol X=0 resol Y=0

The resol X=0, resol Y=0 don't seem to make a lot of sense, maybe that is it??? Can't find any docs on that though ...


my xorg.conf looks like this.
Section "InputDevice"
        Identifier      "touch"
        Driver          "wacom"
#   The by-path below is for the HP TX2z
        Option "Device" "/dev/input/by-path/pci-0000:00:14.5-usb-0:2:1.0-event-mouse"
#   The by-path below is for the Dell Latitude XT
#       Option "Device" "/dev/input/by-path/pci-0000:00:13.1-usb-0:2:1.0-event-mouse"
        Option          "Type"          "touch"
        Option          "USB"           "on"
        Option          "Touch"         "on"
        Option          "TopX"          "0"
        Option          "TopY"          "0"
        Option          "BottomX"       "9600"
        Option          "BottomY"       "7200"
EndSection

---

### Post by Favux on 2009-07-30
Hi wolfgangpauli,

When the cursor jumps to the corner like that it usually means Xinput isn't receiving anything.

What version of Ubuntu are you using?  What does your "ServerLayout" look like?  Do you have Vista or Win7 installed?

---

### Post by wolfgangpauli on 2009-07-30
Hi,

Thank you for your reply!

I am using kubuntu jaunty amd64 from the alternative installation image that i downloaded yesterday.

thanks,

Wolfgang

---

### Post by Favux on 2009-07-30
Hi wolfgangpauli,

OK.  You seem to have the xorg.conf, did you patch the kernel or use Ayuthia's kernel deb.s?  See Appendix 2 here for the link:  [http://ubuntuforums.org/showthread.php?p=6274392](http://ubuntuforums.org/showthread.php?p=6274392)

And the other thing you will want to do is comment out the n-trig subsection of the 10-wacom.fdi if you haven't already.

---

### Post by wolfgangpauli on 2009-07-31
Great! Thanks. Just needed to install the restricted modules to get my wireless card back into business (since I was still on kernel 2.6...11, not 13).

Wolfgang

---

### Post by Favux on 2009-07-31
Hi wolfgangpauli,

Outstanding!  Be sure to give Ayuthia any feedback you have.  He's got it working pretty well now.  I think he's struggling with MPX/multi-touch.

---

### Post by discorsage on 2009-08-07
Hi, I am having the same problem that I saw you post about.  The stylus works, but the finger causes the mouse to go to the corner.  Were you able to fix this?  I am using regular ubuntu 9 and I saw that you were using kubuntu.  Thanks!

---

### Post by Favux on 2009-08-07
Hi discorsage,

See the link in post #4 above and go to appendix 2 near the bottom.

Good luck!

---

### Post by wolfgangpauli on 2009-08-11
yeah, works great!

---

