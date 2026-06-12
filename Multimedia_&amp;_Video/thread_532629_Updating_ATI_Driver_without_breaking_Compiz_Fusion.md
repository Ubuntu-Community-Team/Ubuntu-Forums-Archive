---
title: "Updating ATI Driver without breaking Compiz Fusion"
date: 2007-08-23
forum: Multimedia &amp; Video
---

### Post by quadomatic on 2007-08-23
I have Compiz Fusion XGL Working (Lucky me) but I want to update my ATI driver. I believe im using fglrx. How can I update the driver without breaking Compiz Fusion?

It looks like I'm using a pretty old version of the driver. When I run fglrxinfo i get this:

```
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON X800 GTO
OpenGL version string: 2.0.6334 (8.34.8)
```

I guess I'm using 8.34.8, and the latest version is 8.40.4

I originally activated the driver by using the Restricted Drivers Manager.

My Specs are in my signature.

---

### Post by superyounan1 on 2007-08-23
this topic has been discussed exhaustively, dig around a bit next time.

if you already have XGL and your effects running well, then you should be able to upgrade without breaking anything, follow these instructions:

[http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide)

sometimes in the process you might end up with 'vesa' drivers or whatever, but that same guide has info on how to verify the installation and what to do if something went sideways. 

good luck

---

### Post by quadomatic on 2007-08-23
Thanks for the reply.

It doesn't look like the newest version of the ATI driver is in the repositories. I'll probably have to install it from the website.

---

### Post by quadomatic on 2007-08-23
Yea...so...I finished updating

and Compiz Fusion broke...

Now to figure out what went wrong.

If someone here can help me, I used method 2 on the page that was posted in the 1st reply.

---

### Post by quadomatic on 2007-08-23
Nm

---

### Post by quadomatic on 2007-08-23
Alright! I managed to fix it by following the troubleshooting guide.

However, now ATI Catalyst Control Center won't work.

Really this isn't a big deal, but it had an option for enabling Vsync. How would I enable vsync without it?

---

