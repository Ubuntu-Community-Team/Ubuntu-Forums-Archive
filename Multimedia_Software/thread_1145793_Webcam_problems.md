---
title: "Webcam problems"
date: 2009-05-02
forum: Multimedia Software
---

### Post by jrice219 on 2009-05-02
I have a Crystal Eye webcam built-in to my Acer Extensa 4420 laptop. I am trying to get on Stickam but it won't let me use my camera. Weird because the camera works fine in Cheese. I'm running Ubuntu 8.10 desktop edition, 32-bit

Any help?

---

### Post by jrice219 on 2009-05-02
No help for a beginner?

---

### Post by skotos on 2009-05-02
> **jrice219 said:**
> Weird because the camera works fine in Cheese.Unfortunately it is not so weird. It probably depends on the new expected level of abstraction that video devices are working with.
The same happened to me with my Aspire 9815WKMi webcam. Skype and cheese were the only two apps which were able to run it thru the new ucvideo layer. Starting from Jaunty another small app has begun recognizing it... but I am still far from being happy with my webcam since I cannot choose the app I want to run it with yet.

If I remember well enough, I would first try to look for a package that should be named acer tools in the repositories. That helped me a lot when I first tryed to set up the acer wireless nic, keyboard and webcam.

HTH. Others might be more specific. Welcome to the forums!

FYI - I have almost everything working fine and out of the box on my Acer notebooks. Starting from Jaunty even the bluetooth device was automatically discovered and configured. Some minor issues still exist but it's not easy, after an upgrade, to exactly tell the cause: you always have to correct the errors you have discovered and then you will be able to understand the state of the art that you have reached.

Do not forget that this is free software and that it is really difficult to work with the lack of so many hardware details and specifications.

---

### Post by jrice219 on 2009-05-03
> **skotos said:**
> Unfortunately it is not so weird. It probably depends on the new expected level of abstraction that video devices are working with.
The same happened to me with my Aspire 9815WKMi webcam. Skype and cheese were the only two apps which were able to run it thru the new ucvideo layer. Starting from Jaunty another small app has begun recognizing it... but I am still far from being happy with my webcam since I cannot choose the app I want to run it with yet.

If I remember well enough, I would first try to look for a package that should be named acer tools in the repositories. That helped me a lot when I first tryed to set up the acer wireless nic, keyboard and webcam.

HTH. Others might be more specific. Welcome to the forums!

FYI - I have almost everything working fine and out of the box on my Acer notebooks. Starting from Jaunty even the bluetooth device was automatically discovered and configured. Some minor issues still exist but it's not easy, after an upgrade, to exactly tell the cause: you always have to correct the errors you have discovered and then you will be able to understand the state of the art that you have reached.

Do not forget that this is free software and that it is really difficult to work with the lack of so many hardware details and specifications.

Thanks that helped a lot! I'm still learning my way around the open drivers and such. I was having problems before with my video and card and was able to fix that from ATI's driver for linux. I'll give the "acer tools" a shot. Thanks again for the welcome and the help :D

---

### Post by jrice219 on 2009-05-04
I found nothing on "acer tools" Any other suggestions?

---

### Post by skotos on 2009-05-13
I have no experience with stickam and this kind of web sites, but two other CLI apps providing the same UVC driver support might better suite to you: luvcview and uvccapture.

Under Jaunty, support for my webcam with V4L 2 has been enabled by default, thus a wider variety of webcam apps should be available for your Acer laptop, as well.

I would suggest you to give Jaunty a try on a live CD or a USB key to check if the latest distro might be of help.
To know more on linux and Acer laptops in general, googling a bit might be of help: I have for instance found [this]("http://www.linux-on-laptops.com/acer.html") with some interesting info on a model that is similar to mine.

Yes, I do not find info on .deb acer tools anymore...

PS CLI apps are to be run inside the shell.

---

