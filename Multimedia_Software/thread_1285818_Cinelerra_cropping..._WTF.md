---
title: "Cinelerra cropping... WTF?"
date: 2009-10-08
forum: Multimedia Software
---

### Post by LeDechaine on 2009-10-08
Okay, I want to create a stop motion video. I set the FPS to 5, the video size to 640x480.

It is mentioned in the cinelerra help that if you do a 4:3 video (like a 640x480 video) the original images must be **scaled** to 4:3 too. If they're not, they will be cropped.

Well. Looks like they are cropped anyway. My images, from my digital camera, are in 3264x2448 (which is actually 4:3 too). After rendering the video, I realised Cinelerra cropped all my images just to give me a stop motion video of 640x480 pixels taken from my 3264x2448 images!

So, Cinelerra just can't resize images and you have to do this by yourself before, even if they're scaled? Or is there an option i've not seen or understood, somewhere in the preferences?

---

### Post by wildhostile on 2009-10-08
> **LeDechaine said:**
>  . 

Hi LeDechaine,

If your final video will be 640x480 and you are using 3264x2448 photos, you will have to resize them to fit in your video size. You can either use the camera or the projector tool in the compositor window. Look in the Cinelerra's doc to learn how to use them.
How many photos do you have? Why do you use this framerate?

Roland.

---

### Post by LeDechaine on 2009-10-08
Thanks for your reply, i'll try that.

I'm using this framerate because I want to do some "stop motion" videos with more than 500 photos.

The first stop motion video uses 125 photos. ;)

---

### Post by LeDechaine on 2009-10-08
Whatever. I give up. This program only crops what it wants you to crop. You just CAN'T choose the entire size of the image. The program chooses the 640x480 part of the image IT wants, and then you do what you want to do with. You can't zoom it. You can't resize it. You can't do a video of 640x480 with large files because if you want to create a video with (example) 1600x1200 images, Cinerella assumes that you want to do a 1600x1200 video. And then you get a blank video.

And whatever, even if there's a way to do this in Cinelerra, i guess i would have had to do this 125 times for my 125 pictures.

Fixed this problem by using nautilus-image-resize to resize 125 images to 640x480 before feeding them to the 640x480-locked-window-cinerella.

Even if it takes 10 seconds by image resizing all my 500 images to 640x480 it takes WAY less time to do this than to try to understand how Cinelerra works.

Thanks anyway.

---

### Post by wildhostile on 2009-10-08
> **LeDechaine said:**
>  . 

You don't need that framerate. 24 or 25 will be ok... Well you'll see.
don't know if it will be usefull ==> [http://makefx.wordpress.com/2009/01/04/stop-motion-animations-with-cinelerra-the-pesci-example](http://makefx.wordpress.com/2009/01/04/stop-motion-animations-with-cinelerra-the-pesci-example)

Good luck LeDechaine.

---

### Post by wildhostile on 2009-10-08
> **LeDechaine said:**
>  . 

you can get live help on the cinelerra's IRC channel ==> irc://freenode.net/cinelerra

Roland.

---

