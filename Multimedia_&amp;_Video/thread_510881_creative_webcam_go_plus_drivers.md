---
title: "creative webcam go plus drivers"
date: 2007-07-27
forum: Multimedia &amp; Video
---

### Post by tk03759 on 2007-07-27
I'm going to post this, although I have a strong feeling I'll get no response (no similar topics have gotten responses, and oddly, none of my other posts on any topic have recieved any responses lately).

Here goes. I'm trying to install my Creative Webcam Go Plus on my Ubuntu Fiesty with the most recent updates. According to the opensource creative site, it's possible (or so I got from reading it).

[http://opensource.creative.com/webcam.html](http://opensource.creative.com/webcam.html)

I went there and clicked "Webcam Go/Webcam Go Plus." It brought me to a new page, where I clicked "Installation Instructions." I downloaded version 1.65 because I believed it to be the most stable release, and followed the rest of the instructions as best I could and it looked like it all worked. I then tested the cam on Stickam.com and it showed a mess of things (this camera works on the site with its original, not updated, drivers on Windows XP). I also tried installing XawTV using Add/Remove. It seems to have installed, but it will not open. If I try from the terminal, I get

```
user@computer:~$ xawtv
This is xawtv-3.95.dfsg.1, running on Linux/i686 (2.6.20-16-generic)
X Error of failed request:  XF86DGANoDirectVideoMode
  Major opcode of failed request:  136 (XFree86-DGA)
  Minor opcode of failed request:  1 (XF86DGAGetVideoLL)
  Serial number of failed request:  67
  Current serial number in output stream:  67

```

I also tried vidcat (w3cam) from the terminal and got this:

```
tyler@Tyler-ubuntuDesktop:~$ vidcat
Can't open device /dev/video
```

Any help would be greatly appreciated.
_____________________________________________________
Edit:

I tried the camera in Camorama today and saw some kind of input from the webcam. I could see my generic shape, but there were lines going through it and the image appeared twice. It was too jumbled to really see, but nonetheless, it was being picked up. 

I don't know what that means or what to do about it.

---

### Post by BrewBelly on 2007-07-29
I feel your frustration.

I do a lot of hanging out in video conference "rooms" based of FLASH (like staickam).  I haven't gotten a response from anyone here who has gotten a webcam to work in browser-embedded FLASH apps with feisty.  I have found that the help folks at Stickam are on the ball and they may be able to help you.  Getting a webcam to work with any app is a crapshoot, it it the only reason I boot this laptop to winXP.

---

### Post by tk03759 on 2007-07-30
I've noticed the same thing. I think that the lack of integration of webcams and their linux drivers is more than just a minor issue in Ubuntu. Its a big hit in both the professional and home media areas of computing today. I wonder if there's anything that can be pushed for or even submitted for an upcoming version or update that could make webcams easier to integrate?

I hadn't thought of contacting stickam, but now I did put in a request.

---

### Post by jpmswiss on 2007-08-02
Hello webcamgo brothers!

I bought my webcam go about 6 years ago and recently plugged it into my Feisty. The only app. I found to work a little bit was Kopete. The color is not very good - but I was surprised to get at least that!

Good luck.

---

### Post by tk03759 on 2007-08-04
> I bought my webcam go about 6 years ago and recently plugged it into my Feisty. The only app. I found to work a little bit was Kopete. The color is not very good - but I was surprised to get at least that!

I think I tried kopete once just to see if it worked, but I had issues with the program so I just let it be.

Btw, on a seperate note,[ this thread]("http://ubuntuforums.org/showthread.php?t=487401") claims to have found a camera that at least shows video in Stickam.

---

