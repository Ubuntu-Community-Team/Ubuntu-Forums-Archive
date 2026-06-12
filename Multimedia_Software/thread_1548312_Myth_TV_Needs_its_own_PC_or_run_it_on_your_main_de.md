---
title: "Myth TV? Needs its own PC or run it on your main desktop?"
date: 2010-08-08
forum: Multimedia Software
---

### Post by Nick_Jinn on 2010-08-08
I have never used MythTV but I am about to try it out. I am debating between using my desktop PC which I usually leave running which is next to the entertainment center anyway, or converting an old mini desktop with a Pentium M processor, 1gb ram and a basic intel video card, into a dedicated DVR and Multimedia machine.

Has anyone tried running MythTV as just an app within their primary desktop? How does that work out?

Also, are there any good tutorials for setting up MythTV?

One thing I am wondering about is if I need a converter cable for S-video out or if it will take care of it on its own. Is there something I can download from Synaptic that will convert the signal to standard low def TV for my Nvidia Svideo out or do I still need a converter? The last converter I had didnt work out of the box for linux but did for windows.......Maybe I dont even need it if there is something I can download in Synaptic?

---

### Post by gordintoronto on 2010-08-08
I can't answer any of your questions, but I thought I would mention that MythTV has its own forums at:
[http://www.mythtvtalk.com/forum/](http://www.mythtvtalk.com/forum/) 

Oh, you should also Google: mythtv tutorial 
Some of the results are very old, but some are current.

---

### Post by Nick_Jinn on 2010-08-08
Thanks!

Help from here (Since Im using the Ubuntu Version of MythTV) is still appreciated though.

---

### Post by rubylaser on 2010-08-08
Myth will work fine on a desktop install.  And get it installed with a frontend and backend on the same box, just follow these directions. [http://www.hackourlives.com/master-backend-server-and-single-mythtv-setup-on-a-ubuntu-10-04-box/]("http://www.hackourlives.com/master-backend-server-and-single-mythtv-setup-on-a-ubuntu-10-04-box/")

You'll need a video card that supports OpenGL 2 and have the drivers installed to allow 3D acceleration. You won't need a converter cable for S-Video if your TV and video card both have an S-Video port.. You will need to add some lines to your /etc/X11/xorg.conf file like this...

```
Section "Device"
BoardName "GeForce 8400GS"
Driver "nvidia"
Identifier "Device[0]"
Option "TVStandard" "NTSC"
Option "TVOutputFormat" "SVIDEO"
Screen 0
VendorName "NVidia"
EndSection
```

That might work, it's been a long time since I've hooked a MythTV up via S-Video. Hope that helps.

---

### Post by Nick_Jinn on 2010-08-08
They do both have them.



Hey, I did a clean install and my colors are inverted again when I play video....Does anyone remember the fix for that?

---

### Post by cascade9 on 2010-08-09
> **Nick_Jinn said:**
> One thing I am wondering about is if I need a converter cable for S-video out or if it will take care of it on its own. Is there something I can download from Synaptic that will convert the signal to standard low def TV for my Nvidia Svideo out or do I still need a converter? The last converter I had didnt work out of the box for linux but did for windows.......Maybe I dont even need it if there is something I can download in Synaptic?

If you need a 'converter cable' then I'm guessing you have a TV with no S-Video input. 

I've been playing with a nVidia card with TV out (a gigabyte 6600GT) the gigabyte 'TV out/in' box only has S-video and component outputs. I'm using a S-video to composite adapter, and it seems to work no problems at all.

---

### Post by Nick_Jinn on 2010-08-09
Thank you for sharing that.

My TV does have S-video in, but I have been using VGA....I think thats the right name???The red, white and yellow? Same ones most gaming consoles use?

Do you still need an adapter for S-video to VGA?

---

### Post by Nick_Jinn on 2010-08-09
Nevermind. I think the adapter I have is VGA to RCA or something. 

My laptop has VGA and S-video, but my desktop only has S-video :(
I guess my adapter is worthless unless I want to watch TV from my laptop. 

But a regular S-video should work without doing anything fancy from my PC to the S-video in on my television?

---

### Post by cascade9 on 2010-08-09
Red, white and yellow is composite. Well, the yellow in video composite, and teh red and white (or red and black) is audio. 

Composite isnt as good as s-video. Because all the signals are mixed toegther with composite, its much more messy. The typical problem you get with composite is 'bleeding reds'. That tends to happen a lot more with consoles. 

With s-video, because the intensity and colour are seperated, its a cleaer picture. Not as good as component, where the red, blue and green signals are seperated, but thats not an option for you so dont worry about it ;) 

If your TV has an s-video input, and both your laptop and desktop have s-video outputs, smile! Its a better system than composite, and you wont need any fiddly adapters, just a s-video cable.

---

### Post by Nick_Jinn on 2010-08-09
Are you sure S-video isnt only compatible if you have a digital TV. This is an old analog TV and its not working. I tried the Desktop as well as the laptop.

---

### Post by cascade9 on 2010-08-09
I am 100% sure that s-video works on analog TVs.  I've used s-video on a lot on them, from VCR/DVD players, consoles and TV-out. 

To hook up an nVidia card to a TV, it should be as easy as going to nvidia-settings-> X Server Display Configuration-> Detect Displays and then  cofiguring how you want the X screen setup.

---

### Post by Nick_Jinn on 2010-08-09
See, I didnt do that. I just plugged it in and wondered by it didnt work. :(

---

### Post by Nick_Jinn on 2010-08-09
Its working. This is awesome :)

Thanks for your help, again.

I even have it as a 'twin screen' so I can drag video over to the TV side and still work on my PC while I put movies on the TV side.

---

### Post by cascade9 on 2010-08-10
No problem, glad it helped.  

Enjoy your TV out. ;)

---

### Post by Nick_Jinn on 2010-08-10
For some strange reason it stopped working.

Im thinking about trying again on a clean install. I liked Ubuntu Ultimate at first but I think its a little bloated. It eats up more RAM. I think its either Mint or Studio.

Id like to get OpenGEU to work but I feel stifled by the E17 controls. Gnome is just easy. If I had Gnome or even KDE or XFCE controls with the E17 desktop effects, rather than just Gnome app support with the E17 controls....mixing Compiz with E17 desktop effects and themes is cool though.


But yeah, it worked the first time and the second time its just not doing it.

Im going to do this install anyway and if its still a problem I will report back.

---

