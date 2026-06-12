---
title: "Vodafone USB sticks!!!!"
date: 2010-07-10
forum: Networking &amp; Wireless
---

### Post by simo on 2010-07-10
Hi,
I had much trouble with my Vodafone Huawei based USB stick so I did much of research on the net and found following 3 solutions:

1. Download and install [[COLOR="Navy"]VMC[/COLOR]]("http://www.betavine.net/bvportal/resources/datacards/os/ubuntu") it will work but some programs will not recognize net connection (ie. Firefox, Banshee...)

2. Adding [[COLOR="Navy"]ppa:network-manager/trunk[/COLOR]]("https://launchpad.net/~network-manager/+archive/trunk") to your repository and updating your system. Sometimes you will maybe need to "Eject" USB drive to see connection in NetworkManager, but net will work and will be detected. NOTE: it's a daily build so it's not stable!

3. [[COLOR="navy"]Betavine Connection Manager[/COLOR]]("http://www.betavine.net/bvportal/blog/view.html?blogId=133&postId=ff8080812942915f01294cd0e6e322bc&redirectUrl=redirect:/community/linux")
It's still in alpha, but I'm using it and it's wonderful! I hold good hopes about this project. Installing this you will get app similar to VMC, and what is the best of all, you will have integration with NetworkManager. Created profiles will be available in NetworkManager so connection will be detcted and you dont need to use BCM! Only NetworkManager! As I said, project is still alpha but it works...and yes It has repository for Ubuntu 10.4 Lucid! For more information go to link. ;)

---

### Post by pdc on 2010-07-10
thanks for this;

another method !! is sakis 3g

I used it recently for vodafone UK and vodafone NL and it worked very well

[http://www.sakis3g.org/](http://www.sakis3g.org/)

I can recommend it

---

### Post by ekeis98 on 2010-07-12
Hi,

thanks to Simo for the links. I'll try them out.

I've had the SAKIS-scripts on my list. They worked exactly once :-( Unfortunately the dialogs that come up on my netbook screen are too big for the low resolution. In that case I prefer wvdial. Simple to configure, easy to start and stop, best connection control.

Best regards,
Oliver

---

