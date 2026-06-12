---
title: "Webcam stopped working"
date: 2012-01-22
forum: Multimedia Software
---

### Post by mohitdaksh on 2012-01-22
I have been spending a few days banging my head and googling about this problem because I was embarrassed that I didn't remember what caused this behavior.

I bought a cheap webcam two weeks ago, it worked fine until last week. I am working on a project for which I needed to send a video feed from my home serve to the client. From somewhere I saw zoneminder and installed it. 

Then my website stopped responding. I searched google and found someone say that zoneminder takes over all the ports under its control and I will have to use alternative ports for the HTTP and other default ports. Being a newbie that I am, I uninstalled zoneminder right away. 
Now I **think** my web cam stopped working after that.
For first few days my opencv code which used to work started giving this error
```
*HIGHGUI ERROR*: V4L2: *Pixel* format of incoming image is unsupported by OpenCV
```v4l-conf was not working, nothing was working except cheese and kamoso. They were showing the video feed.

I tried all the solutions I could find on google but nothing worked for me. May be they made the problem worse because now even kamoso and cheese don't show video
cheese gives this error
```
/dev/video0 [v4l2]: no overlay support

```The webcam LEDs are on so its connected properly.

Now I don't want to reinstall just because of this but I fear this might be the only option left.

 Any suggestions??



EDIT: Now cheese gives error
> libv4l2: error setting pixformat: Device or resource busy
Segmentation fault


And I did not do any changes between the last post and this edit.

And a code that I saw somewhere on the net displays webcam feed correctly on the localhost

---

### Post by mohitdaksh on 2012-01-23
For anyone who has this problem + has "**webcam-server**" package installed.  **Remove** "webcam-server" ( Or may be stop it when you want to use your webcam for other purposes but I am not sure).


I think webcam-server does not allow other applications to access the webcam

---

