---
title: "Ubuntu jaunty - amarok"
date: 2009-05-25
forum: Multimedia Software
---

### Post by 11cerealkiller26 on 2009-05-25
Hi I install amarok from synaptic but the problem is when i start to play mp3 or any audio file, i didnt hear any sound from amarok player...please help me..thanks

---

### Post by infinitejones on 2009-05-25
Have you tried playing the same audio file using another music player? Such as Rhythmbox, which should be on your applications -> sound & video menu already.

That way, we'll know if the problem is with Amarok specifically, or something else...

---

### Post by alawson on 2009-05-25
I have the same problem since upgrading to 9.04.
MP3s play fine with RythymBox, but not with Amarok.
I saw another thread reporting problems with playback from Banshee too...

---

### Post by pcdreamer on 2009-05-25
Hi, 
I had same problem with Amarok and also playing DVD's. I found this link and got both Amorok and the ability to play DVD's going. Hope this helps.

[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

---

### Post by ECPCLINUX on 2009-05-25
I installed Amarok 1.4 in Jaunty. I just like the style of 1.4 better, at least for now. I found this website and followed it to a T and it worked perfect. Here it is:

[http://diabolicalorsmart.com/tech/installing-amarok-14-in-ubuntu-ja](http://diabolicalorsmart.com/tech/installing-amarok-14-in-ubuntu-ja)

or if you rather keep Amarok 2.0 maybe this Sticky by ubuntu-freak will help:

[http://ubuntuforums.org/showthread.php?t=766683&highlight=amarok+jaunty](http://ubuntuforums.org/showthread.php?t=766683&highlight=amarok+jaunty)


Good luck!

---

### Post by 11cerealkiller26 on 2009-05-25
My rythmbox is working fine to play my mp3 and other format, but only amarok did'nt work, how can i resolve this one

---

### Post by 11cerealkiller26 on 2009-05-25
> **infinitejones said:**
> Have you tried playing the same audio file using another music player? Such as Rhythmbox, which should be on your applications -> sound & video menu already.
 
That way, we'll know if the problem is with Amarok specifically, or something else...
 
My rythmbox is working fine to play my mp3 and other format, but only **[COLOR=#ff0000]amarok[/COLOR]** did'nt work, how can i resolve this one

---

### Post by Ravskie on 2009-05-27
Hey just want to help can you try this :

sudo apt-get remove --purge phonon-backend-gstreamer
sudo apt-get autoremove
sudo apt-get install phonon-backend-xine
sudo apt-get install amarok


hope it works ....

---

### Post by Ravskie on 2009-05-27
Ignore the first one it might not work.... 

I use rhythmbox and i try to install AMAROK and i got same issue like yours... 
try to install this and it works for me ....


ubuntu-restricted-extras
 libxine1-ffmpeg
phonon-backend-xine
phonon-backend-gstreamer


Hope this one will help ......

---

### Post by skipknyc on 2009-05-27
> **ECPCLINUX said:**
> I installed Amarok 1.4 in Jaunty. I just like the style of 1.4 better, at least for now. I found this website and followed it to a T and it worked perfect. Here it is:

[http://diabolicalorsmart.com/tech/installing-amarok-14-in-ubuntu-ja](http://diabolicalorsmart.com/tech/installing-amarok-14-in-ubuntu-ja)

or if you rather keep Amarok 2.0 maybe this Sticky by ubuntu-freak will help:

[http://ubuntuforums.org/showthread.php?t=766683&highlight=amarok+jaunty](http://ubuntuforums.org/showthread.php?t=766683&highlight=amarok+jaunty)


Good luck!

A thousand thanks, my friend! :D

This site has excellent instructions for installing Amarok 1.4 in J-J904, as well:

[http://ubuntu-blog.com/how-to-install-amarok-14-in-ubuntu-904](http://ubuntu-blog.com/how-to-install-amarok-14-in-ubuntu-904)

Warmest regards,
Skip K

---

### Post by Lakeside5 on 2009-05-27
I must be doing something wrong.  I still can't put music on my iPod :(  I plug my iPod touch into a usb port (I am running Hardy Heron) and the iPod icon  does show up with the other 'stuff' in 'computer' directory. I right-clicked on it and 'open with'  rhythmbox...but it doesn't show up there, same thing with amarok, at least with Amarok I get an error message: No suitable input plugin. This often means that the url's protocol is not supported. Network failures are other possible causes.
gphoto2://[usb:005,012]/  I don't know what that means, and I just don't know what to do.

---

### Post by Sonny Boy on 2009-05-29
> **Ravskie said:**
> Ignore the first one it might not work.... 

I use rhythmbox and i try to install AMAROK and i got same issue like yours... 
try to install this and it works for me ....


ubuntu-restricted-extras
 libxine1-ffmpeg
phonon-backend-xine
phonon-backend-gstreamer


Hope this one will help ......

tks, that worked out for me too. (I installed libxine1-all-plugins)
:D

---

### Post by ECPCLINUX on 2009-06-05
> **skipknyc said:**
> A thousand thanks, my friend! :D

This site has excellent instructions for installing Amarok 1.4 in J-J904, as well:

[http://ubuntu-blog.com/how-to-install-amarok-14-in-ubuntu-904](http://ubuntu-blog.com/how-to-install-amarok-14-in-ubuntu-904)

Warmest regards,
Skip K

No problem, glad these instructions worked well for you as well. I love my old 1.4 Amarok. :)

---

### Post by opossumjack on 2009-06-07
Thanks a lot guy... Now everything works for me :D

---

### Post by Screaming Monkey on 2009-06-07
> **Ravskie said:**
> Ignore the first one it might not work.... 

I use rhythmbox and i try to install AMAROK and i got same issue like yours... 
try to install this and it works for me ....


ubuntu-restricted-extras
 libxine1-ffmpeg
phonon-backend-xine
phonon-backend-gstreamer


Hope this one will help ......

I know this worked for me.  Thanks!

---

