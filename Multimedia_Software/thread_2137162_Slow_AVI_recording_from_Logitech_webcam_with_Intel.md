---
title: "Slow AVI recording from Logitech webcam with Intel integrated media accelerator"
date: 2013-04-19
forum: Multimedia Software
---

### Post by bytescribe on 2013-04-19
Hi, all...

Need some advice...

My friend and I had the idea of using his webcam to shoot a video of him cutting my hair so I could learn how to cut hair (and save some money on cosmetology school let alone paying for someone else like at Great Clips).

Well, here's the deal:

1) I have a refurbished Dell Latitude D620 laptop with an Intel Core2 Duo 64-bit processor, and if I remember the eBay description correctly, an Intel integrated "media accelerator 950" card.
2) My friend's got a Logitech USB webcam--not sure when he bought it so I am not sure how old it is,
3) I am running Ubuntu 12.10 64-bit

Pretty much everything about the computer works fine except that when we try to play back the video--an AVI--it runs CRAZY slow...

1)Is this just my graphics card being old and integrated?

and/or

2)What software--if any--do we need to install to make this video run better? We've already got VLC installed, as well as the default video player that comes with Ubuntu.

Also, the following is what my friend looked up as far as getting the webcam to work--and the terminal output said something about "ffmpeg being deprecated...try avconv." This message was the result of the following input attempts into the terminal:

[I]ffmpeg -f video4linux2 -r 25 -s 640x480 -i /dev/video0 out.avi
avconv -f video4linux -r 25 -s 640x480 -i /dev/video0 out.avi
avconv -f v4l2 -r 25 -s 640x480 -i /dev/video0 out.avi[/I]

There are obviously holes in our knowledge, so if you could fill us in, and give us some ideas (apart from spending megabucks on a new computer), that would be great. :-)

Thanks,
Kat ^.^
.

---

### Post by mörgæs on 2013-04-20
How does it work if you record in OGG format?

---

### Post by bytescribe on 2013-04-22
Hi. Well, I'm not sure exactly how to do that, since the instructions my friend found were for recording .avi from the terminal. But I will mention your recommendation when I see him this coming Wednesday. :-) I might look it up myself if I have time, though. 

Thanks for the recommend! :-)

---

