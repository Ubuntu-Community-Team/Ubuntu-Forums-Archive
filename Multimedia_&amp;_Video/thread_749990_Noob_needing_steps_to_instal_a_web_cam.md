---
title: "Noob needing steps to instal a web cam"
date: 2008-04-09
forum: Multimedia &amp; Video
---

### Post by scraghty604 on 2008-04-09
Ok so i am running ubuntu 7.10 on acer 5570z with a i believe a logitech quickcam pro.

If someon could tell me the steps need to get this suka working, i only would be using it for 
aMsn thanxs again guys

---

### Post by linuxwizard on 2008-04-09
Try using Ekiga see if the cam works/detected. You may have to work with the settings > Open Ekiga > Edit > Preferences > Video > Video Devices > try changing some of the settings.
To test your webcam you can do this:
There are 6 icons on the left side of the main Ekiga window. Push the 4th button from the top (a grey round webcam). If eveything is ok, you'll see the output of the webcam. If not, you'll see the Ekiga logo bouncing slowly.

If cam does not work post the results of the command > lsusb

---

### Post by scraghty604 on 2008-04-09
i play aroudn and tried everysetting this is the response i got every time

Error while opening video device UVC Camera (046d:08c3)

A moving logo will be transmitted during calls. Notice that you can always transmit a given image or the moving logo by choosing "Picture" as video plugin and "MovingLogo" or "StaticPicture" as device.

Could not open the chosen channel.

---

### Post by scraghty604 on 2008-04-09
ok i take it back


why wont it work in aMsn?

---

### Post by linuxwizard on 2008-04-09
scraghty604 > ok i take it back


Did you get it working in Ekiga?

---

### Post by scraghty604 on 2008-04-09
yes i did 

settings are as follows

Video plugin : V4L2

Video device : UVC camera (046d:08c3)
Format: NTSC
Channle :  0


i did notice when trying to set up in Amsn there was a video chanell set to 1 coud not chang

---

### Post by linuxwizard on 2008-04-09
That is why I said in my first post you may have to work with the settings. Their is a difference between V4L & V4l2  Glad to hear you got your webcam working. I don't use Amsn can't help you on setting your cam there.

---

### Post by scraghty604 on 2008-04-10
i gues the next step is to dl the lastest verison of aMsn everytime i do somethign it says i need the newest version might as well have it

---

