---
title: "How to crop a video?"
date: 2010-10-23
forum: Multimedia Software
---

### Post by kramer65 on 2010-10-23
Hello,


I've got a little video and I want to crop it so that a part of it falls away. I installed and tried Openshot, Kino, Pitivi and Kdenlive, but I can't seem to find a way to crop my video.

Isn't there any way to crop videos in Ubuntu, or am I just blind and overlooking the function?

Any help or tip is welcome!

---

### Post by lisati on 2010-10-23
I haven't used openshot much but it appears to have an option where once you have added a clip to a track, you can right click on the clip, select properties, click on the "length" tab, and specify a new length.

---

### Post by bluekarasu on 2010-10-23
you can use Handbrake or Avidemux.

---

### Post by kramer65 on 2010-10-24
@ Lisati. Thanks for the tip, but I don't mean that I want to make the video shorter, I mean that I want to cut the bottom part of what you see away ([cropping]("http://en.wikipedia.org/wiki/Cropping_%28image%29")).

@ Bluekarasu. Handbrake doesn't seem to be able to be installed in Ubuntu anymore (see [here]("http://handbrake.fr/downloads.php")). I installed Avidemux, but I can't find the option to crop video. Any idea where I can find the crop function?

---

### Post by JohnAStebbins on 2010-10-24
> **kramer65 said:**
> 
@ Bluekarasu. Handbrake doesn't seem to be able to be installed in Ubuntu anymore (see [here]("http://handbrake.fr/downloads.php")).
Just follow the link to the nightly builds.  There is a PPA for installing handbrake there.

---

### Post by AlexDudko on 2010-10-24
In Kino the function is called Trim.
(Located in the right menu)

---

### Post by kramer65 on 2010-10-25
@ Alexdudko. Trim is unfortunately not the function I mean. I attached an image to this post which I hope explains better what I mean. I want a part of what you see taken away. So not a part in time, but a part in the visual area of the video.

Anyone?


--edit--
@ JohnAStebbins
I am not so familiar with PPA packages, but I tried to install it by running the following:
```
sudo add-apt-repository ppa:stebbins/handbrake-snapshots
sudo apt-get update
```It did a whole bunch of stuff, and it's finished. Is handbrake now installed? How would I start Handbrake now?

---

### Post by AlexDudko on 2010-10-25
Now I see what you mean. Never used **handbrake**, so I can't be very helpful for you. But its documentation has the function.
About installing: as far as I know you should also execute the installation command after that: > apt-get install "program name" 

---

### Post by JohnAStebbins on 2010-10-25
> It did a whole bunch of stuff, and it's finished. Is handbrake now installed? How would I start Handbrake now?
```

sudo apt-get install handbrake-gtk

```
It will add a menu item "Applications->Sound & Video->HandBrake"
And from the command line, it's 'ghb'

---

### Post by bigsmitty64 on 2010-10-25
In kdenlive you can use the "composite" feature to layer tracks on top of one another and resize the layers and get the effect you're looking for maybe? Just a thought.

---

### Post by rrrenzo on 2011-09-12
For anyone who is reading this and is still want and answer
After researching for a while, i found that function on both openshot and avidemux
For openshot: right click on the track, and select properties. Then go to the layout tab. you will see a list of parameters. height and with are the % of zoom you want, and x,y are the offsets.
edit: just realized that this doesnt last all the video, somehow

For avidemux, go to main menu- video - filters.
the first tab on the left should be the "transform" tab, and on that tab, the "crop" option should be available, among rezzing and other stuff.

Hope this help someone

BTW, if some knows if this option is available in kinos, plz tell me. openshot is good, but I really rather have just 1 editor

---

### Post by alecspoons on 2012-03-27
I've just been playing about with this.

To make the cropping effect last right through the clip, you need to set the parameters the same for both key frames.

---

### Post by chickenPie4breakfast on 2012-03-29
> **alecspoons said:**
> I've just been playing about with this.

To make the cropping effect last right through the clip, you need to set the parameters the same for both key frames.

yes you have to have the same parameters for the "start of clip" and "end of clip" keyframes.  Keyframes are a bit funny in Openshot in that you cant create them anywhere in the video as you can in a lot of other editors. Each clip in Openshot has only two keyframes-  one at the very beginning and one at the end. If you want to create another you have to split the cip into smaller pieces and each new piece will now have two key frames of its own at the begining and end. So if you have a few clips on your timeline you will have to go through them and make sure the same size is made for each keyframe on all of them if you want to resize(crop) all the video.
I tend to  just use Virtual dub which I run under wine.

---

