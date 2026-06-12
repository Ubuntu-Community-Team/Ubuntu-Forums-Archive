---
title: "built in webcam"
date: 2009-02-10
forum: Multimedia Software
---

### Post by Robert John Kelly on 2009-02-10
k well i installed ubuntu a few months ago, just now noticing that my webcam hasn't worked this entire time. i have an acer 5670 i have no idea what model the built in webcam is. can anyone lend a helping hand?

---

### Post by edgarinventor on 2009-02-10
My webcam isn't built in, but this might also work for you, so read it trough:

I found that installing Ekiga, and then plugging the webcam, then doing Edit>Preferences, and pushing the detect button, gives you an accurate description of your Webcam.

In my case, a Lindy Webcam that Ubuntu insisted to list as Shanga(?!), brought this: "SN9C1xx PC Camera"

I've used it on Ekiga, it worked;
Pasted that into xawtv, it worked, too! :)

So have a go at both Xawtv and specially, Ekiga.

---

### Post by Robert John Kelly on 2009-02-10
i don't want to use ekiga i want to use my webcam itself

---

### Post by edgarinventor on 2009-02-10
> **Robert John Kelly said:**
> i don't want to use ekiga i want to use my webcam itself

Ekiga serves only to detect your webcam, write it's description of the webcam, and try to insert that description into the program you use the camera with. You can even un-install Ekiga, afterwards.

---

### Post by steveneddy on 2009-02-10
To view the web cam itself, use Camorama

```
sudo apt-get install camorama
```

---

### Post by Robert John Kelly on 2009-02-10
k steve that seemed to install it but i have no idea how to use it

---

### Post by Robert John Kelly on 2009-02-10
that ekiga crap doesn't even work

---

### Post by steveneddy on 2009-02-12
> **Robert John Kelly said:**
> k steve that seemed to install it but i have no idea how to use it

OK, Bob, tell me what you would like to do with your web cam?

I only use my web cam in Skype.

I just Camorama to test the web cam and maybe take a few pics.

---

### Post by Regnulify on 2009-02-12
Webcam support can be strange. I had to install the uvc drivers to get the camera in my hp dv7 to work. You can get those drivers here: [http://linux-uvc.berlios.de/#download](http://linux-uvc.berlios.de/#download)

you can see if your camera is being detected by running lsusb at the terminal.

Also, I cannot get xsane or camerama to work, but Cheese does work. So you need to try different apps to get one that works. If you have preferences/multimedia systems selector you can check it there. I am not sure what that app is called to install it if you don't have it.

---

