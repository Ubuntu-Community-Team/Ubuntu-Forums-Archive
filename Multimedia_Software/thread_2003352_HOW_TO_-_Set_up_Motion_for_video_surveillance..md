---
title: "HOW TO - Set up Motion for video surveillance."
date: 2012-06-14
forum: Multimedia Software
---

### Post by Roasted on 2012-06-14
Excuse my lack of typed instructions in this post. I just completed a screencast video tutorial and figured I'd link them here in case other users could benefit. Two 15 minute segments total.

[http://www.youtube.com/watch?v=NwDLkMPLTw0](http://www.youtube.com/watch?v=NwDLkMPLTw0)

[http://www.youtube.com/watch?v=ZAoA_J5HD0M](http://www.youtube.com/watch?v=ZAoA_J5HD0M)

:guitar:

---

### Post by Roasted on 2012-08-31
Hey everyone! Just want to update you on a little extra bit of info I recently came across. Once I added more cameras to the network, I felt the need to simultaneously see them at once on a single window. Of course, utilizing Motion's "web server" functionality really only allowed for one camera per browser tab. I wanted to see smaller instances that I could click on for full size scaling. This is the basic idea I was after:

[IMG]http://i.imgur.com/EDnOW.jpg[/IMG]

I ended up resorting back to some HTML/CSS classes I took quite a few years ago. With the help of a buddy who's a current web designer, a basic structure was formed. This was the end result:

> <!DOCTYPE html>
<html>
 <head>
 <style type="text/css">
 body { 
 text-align:center;
 background-color:#000000;
 }
 .container {
 width:100%;
 }
 .motion {
 border: 0;
 width: 32%;
 height: auto;
 }
 .clear {
 clear:both;
 }
 </style>
 </head>
 <body>
<a href="http://192.168.1.10:8081"><img class="motion" src="http://192.168.1.10:8081" /></a>
<a href="http://192.168.1.10:8082"><img class="motion" src="http://192.168.1.10:8082" /></a>
<a href="http://192.168.1.10:8083"><img class="motion" src="http://192.168.1.10:8083" /></a>
<br />
<a href="http://192.168.1.10:8084"><img class="motion" src="http://192.168.1.10:8084" /></a>
<a href="http://192.168.1.10:8085"><img class="motion" src="http://192.168.1.10:8085" /></a>
<a href="http://192.168.1.10:8086"><img class="motion" src="http://192.168.1.10:8086" /></a>
<br />
<a href="http://192.168.1.10:8087"><img class="motion" src="http://192.168.1.10:8087" /></a>
<a href="http://192.168.1.10:8088"><img class="motion" src="http://192.168.1.10:8088" /></a>
<a href="http://192.168.1.10:8089"><img class="motion" src="http://192.168.1.10:8089" /></a>
 </body>
</html>

The top part is basically for outlining some structure points for the rest of the file. Down further, you can see there are 9 lines which look nearly identical, with a <br /> in between a few of them. This structures the layout to be a 3x3 grid. Three cameras, <br />, three cameras, <br />, three cameras = 3x3 grid. You'd adjust this accordingly if you want 1x2, 2x2, etc. Keep in mind, wherever you place the <br /> is where you'll end up having a "line break" and dropping the next camera to the next line. 

Let's break down one of these lines.
> <a href="http://192.168.1.10:8089"><img class="motion" src="http://192.168.1.10:8089" /></a>

So you have three sections:
[LIST=1]
[*]<a href="http://192.168.1.10:8089">
[*]<img class="motion" 
[*]src="http://192.168.1.10:8089" /></a>
[/LIST]

About 1 - This makes your image clickable. Without this, it won't give you the ability to click on the image and see it full scale.
About 2 - This line is referencing the motion class, which is where it gets its parameters from, such as height, width, etc.
About 3 - This line is what is giving you your actual mjpg feed.
Note - The IP is the same in each example because this IP is the IP of the server itself that's running Motion. The port following the IP is whatever you set webcam_port to in the motion.conf or threadX.conf files for that specific camera. That's why each IP is the same while each port is different. AKA: same IP because it's the same server, different port because it's a different camera.

I already covered the fact that you adjust your layout accordingly to how many cameras you have above (1x2, 2x2, 3x3, etc.), but what's more is you can fine tune the exact sizing of your windows as well. In the above example, you can see the width is 32% while there's a 3x3 grid layout. This means that I'm utilizing almost 100% of the screen width to place the 3 feeds horizontally. Using 32% instead of 33% is nice because it creates a little more of a break in between each feed. Likewise, 24% in a 4x4 layout will give you similar results. You can adjust these accordingly to what you like.

For what it's worth, I found height being auto and only adjusting the width manually was the best way to go, likely because majority of monitors out there are of course wider than they are tall. Sometimes doing it in reverse (width auto, height setting manually) skews feeds disproportionally. 

On top of that, you can also take things a step further. In my case, I have two cameras with different resolutions. This scales them differently on my page. With the resolution of my monitor (1280x1024) and the resolution of my cameras (1280x800 and 640x480) I felt (after having mixed and matched different scenarios) as though having them on top of each other would be optimal. I basically copied the "motion" class above, gave it a new name, and referenced it with the 2nd camera further below. FYI - you can rename the classes anything you want. Just make sure you change them in the <a href= lines as well so they're referenced appropriately. Take note of motion1 and motion2 and their independent width settings:

> <!DOCTYPE html>
<html>
 <head>
 <style type="text/css">
 body { 
 text-align:center;
 background-color:#000000;
 }
 .container {
 width:100%;
 }
 .motion1 {
 border: 0;
 width: 32%;
 height: auto;
 }
 .motion2 {
 border: 0;
 width: 75%;
 height: auto;
 }
 .clear {
 clear:both;
 }
 </style>
 </head>
 <body>
<a href="http://192.168.1.10:8081"><img class="motion1" src="http://192.168.1.10:8081" /></a>
<br />
<a href="http://192.168.1.10:8082"><img class="motion2" src="http://192.168.1.10:8082" /></a>
 </body>
</html>

You can find more information about various Motion topics on their FAQ page [located here.]("http://www.lavrsen.dk/foswiki/bin/view/Motion/FrequentlyAskedQuestions")

---

### Post by jfmd on 2012-09-17
Your videos are really well done, great job and thanks!  When I get some time this weekend, I'm going to try to set this up using your videos.

---

### Post by NewYorkLaw on 2012-11-15
Well done videos. Still I prefer Xeoma for it has much more possibilities (like browsing of all cameras in web browser at a time, no-stress remote access and so on). And I like its touchscreen design more. It also has how-tos on youtube but they are not as good as yours. Perhaps you could do videos for Xeoma too, would be great if you compared them.

---

### Post by scabs on 2013-04-11
Forgive me if this sounds silly.  I know the app is called motion, however are you able to set this up with a constant stream and only record when motions is detected?

---

### Post by evilsoup on 2013-04-11
I'm sure that would be possible, though I don't know if there is a software implementation of motion detection on Linux.

Either way, you'd be better off starting a new thread with that question.

---

### Post by zSeries on 2013-04-11
There are four capture modes
1) snapshot - take a picture every n seconds regardless of motion
2) timelapse movie - create a movie with frames taken n seconds apart
3) jpeg images -  on motion detect with pre and post frames
4) movie - on motion detect 
You can use any combination on any camera.

---

### Post by dlw on 2013-04-29
Sys is Ubuntu 12.10
motion version is 3.2.12
Trying to set up webcam to take a video but only snap a frame when there is motion.

Logitech C910 starts with 'sudo service motion start' but stops after a few seconds.
That's all that happens for now.
Any help appreciated.

---

### Post by zSeries on 2013-05-02
I am no  expert but when Motion starts I get loads of info messages in the SYSLOG. Have you looked there?

---

### Post by Dragonbite on 2014-01-14
Sorry to resurrect an old thread, but a quick question would be if this setup could work with a Raspberry Pi.

---

