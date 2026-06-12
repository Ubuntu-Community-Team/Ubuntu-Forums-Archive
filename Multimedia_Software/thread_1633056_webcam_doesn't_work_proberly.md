---
title: "webcam doesn't work proberly"
date: 2010-11-28
forum: Multimedia Software
---

### Post by fally777 on 2010-11-28
The web cam on my Dell Inspiron mini 10 doesn't work properly. Cheese only takes very dark pictures but no video and the main screen stays dark all the time. Skype transmits a very dark image, too. How can that be tweaked.

Bus 001 Device 002: ID 174f:1403 Syntek Integrated Webcam

---

### Post by no2498 on 2010-11-29
open cheese click edit/preferences
you can change some settings there


hope this helps

---

### Post by fally777 on 2010-11-30
I checked that already. That doesn't do the trick

---

### Post by no2498 on 2010-12-01
ok in/on my 10.04 computer i have a video4linux control panel
look in system/preferences for it if its installed
hope that helps you

---

### Post by heathen35 on 2010-12-25
Was having similar problem too.
Camera showed up when I entered lsusb in terminal and didn't get any errors using cheese or any other video capture software but picture was completely dark.
video4linux control panel works and guvcview works as well.
Only had to change Exposure(Absolute) to 1 and picture showed right up.

Hope your problem is as easy.

---

