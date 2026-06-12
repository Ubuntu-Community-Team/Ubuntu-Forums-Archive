---
title: "Logitech (pwc) Webcam Tips"
date: 2010-01-02
forum: Multimedia Software
---

### Post by kidcharles on 2010-01-02
I did a few tweaks to my Logitech Quickcam Pro 4000 settings and thought I would share them. These tips would probably be helpful to anyone with a driver that uses the pwc module (Phillips Web Cams).

**If your video doesn't work:**

Try unplugging the camera and entering the following command to restart the camera:
```
sudo modprobe -r pwc
```
Then plug the camera back in.

**If the white balance is off:**
I found that the default white balance showed everything too blue and wanted a warmer look. Install the setpwc utility to fix that:
```
sudo apt-get install setpwc
```
I then used the following command to set the white balance:
```
setpwc -w outdoor
```
I set it to "outdoor" because I had some natural light coming in through the window.

**Increase frame rate:**
I noticed in Skype that the default framerate was low. I'm not sure how it looks after being transmitted but I was able to increase the framerate in the video preview with:
```
setpwc -f 30
```
That command set the framerate to 30 fps which looked nice.

There are other things you can do with setpwc if you check its man page with:
```
man setpwc
```

---

