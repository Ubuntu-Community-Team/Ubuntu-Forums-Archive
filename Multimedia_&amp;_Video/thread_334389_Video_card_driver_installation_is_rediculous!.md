---
title: "Video card driver installation is rediculous!"
date: 2007-01-08
forum: Multimedia &amp; Video
---

### Post by jondecker76 on 2007-01-08
Hello

I really like Ubuntu, and linux in general. I've only been using it for about a month now, but i've learned quick.

That being said, video driver installation is the biggest mess I've ever dealt with. I've been a professional c++/c/java/php programmer for over 10 years, and have over 400 professional software titles under my belt - and even with my level of experience, I've had to completely reinstall Ubuntu 8 times during my learning process. Granted, my knowledge of linux is extremely limited.

THe problem is:
1) Installing the NVidia driver using the add/remove would not work with any of my NVidia cards (5200,5600,6200) using the NVidia Xorg binary driver - even if they would have worked for me, they were extremely out of date.

2) Installing the download from the NVidia website..  Finally - updated and recent drivers..  But, I had no success with this either. I downloaded NVIDIA-Linux-x86-1.0-9746-pkg1.run, chmodded to make it executable and from a terminal ran sudo sh NVIDIA-Linux-x86-1.0-9746-pkg1.run. However, i get a warning that it can't be installed while XServer is running.. Ok, so I chose recovery mode from the grub menu..  Again I ran sudo sh NVIDIA-Linux-x86-1.0-9746-pkg1.run.. I don't get the x server running message this time, instead I get a message saying that i have to 'telinit 3' before running..  SO I try that, and I'm put back into the x windows envirnment that it will not install under. Ok, one more try..  Recovery mode again, sudo sh blah blah blah, and I chose to ignore the telinit 3 message..  Now I get a warning that the libc development package isn't installed. At this point I tried one more time after using synaptic to install 'linux-libc-dev'. Again, i got the same message and gave up.

3)Last resort was to use Automatix2..  And it worked.. Though the driver version is also outdated (though not as bad as the ones from the Ubuntu repositories).

So yes, I got it to work - but my problem with this is that its an AWEFUL pain getting NVidia drivers to work (and I had an even worse time with the ATI fglrx drivers, but thats another story). Also, I don't like using 3rd party software (I.E. automatix2) to do the work for me, how am I supposed to learn? What if I want *current* drivers?

I've spent literally weeks reading posts on installing drivers, and I still had this many problems.

Is it just me, or is it like this for everybody?? Is there any recommended reading I should check out?  I would really like to install the latest NVidia drivers from their website and learn to do it the correct way, but all but exhausted with it at this point.

---

### Post by scrooge_74 on 2007-01-08
Check this out is like the bible around here

[http://albertomilone.com/guides.html](http://albertomilone.com/guides.html)

---

### Post by jondecker76 on 2007-01-08
Wow, amazing link, thanks a lot!

So I would guess that the driver installation issue is as complex for many people as it was for me. Hopefully this will be addressed in the next version of Ubuntu, as it is one of the bigger drawbacks I feel that is keeping it from being worthy for "main stream" use

thanks again

---

### Post by scrooge_74 on 2007-01-08
The problem is with restricted drivers, since they don't come by default, but I read that they will come in Feisty, you have to do it by yourself.

Since i did not follow directions as I was suppose to it took me a couple of hours to get it up and running. Lucky for me I had some practice with console web browsers :D

Have fun!

---

### Post by tseliot on 2007-01-09
You can also try Envy:
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by jondecker76 on 2007-01-09
Thank you, i might try envy. I would like to learn on my own though, so I guess I will try it one more time myself then if I'm still stuck, use envy

thanks

---

### Post by sgx on 2007-01-09
...Sorry, no umpires or instant replay, you must follow orders...but it really is just these steps
Install kernel source and headers, and binutils if not installed
download driver, move it to /
in terminal, root types       telinit 3
and then   sh "whatever driver you downloaded'
Reboot after installer runs,, and edit your x86/xorg config per nvidia website insructions.
Reboot again...Done

---

