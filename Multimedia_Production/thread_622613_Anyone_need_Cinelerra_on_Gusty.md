---
title: "Anyone need Cinelerra on Gusty?"
date: 2007-11-24
forum: Multimedia Production
---

### Post by gali98 on 2007-11-24
Hi. I compiled cinelerra on Gusty and just wanted to know if anyone wants it.  It is compiled into one package (it's usually compiled into 4 but I don't know really how to do such right now.)
It works fine as far as I can tell. It's in a simple deb. It was not compiled with opengl. If you want it I can upload it somewhere....
Hope I can help someone somewhere..
Kory

---

### Post by loell on 2007-11-25
you didn't just create a deb via checkinstall, did you? ;)

cause if you did, it would certainly give problems to who-ever installs it.

---

### Post by gali98 on 2007-11-25
> **loell said:**
> you didn't just create a deb via checkinstall, did you? ;)

cause if you did, it would certainly give problems to who-ever installs it.

lol I did.:KS Why would it though?
I just thought I would help....:(
I mean as long as they install all the other dependencies. 
Kory

---

### Post by loell on 2007-11-25
of course your effort to help, is deeply appreciated :)

its true that when you install a deb package from checkinstall and  that as long as you satisfy its dependencies manually on the target machine then everything might be OK, but tracking those dependencies would be very messy, and once a user wants to uninstall, he'll have to manually uninstall all those unnecessary dependencies from his system.

I started in checkinstall too , and learn a few tricks in building decent deb package through debhelper. just make some small steps and eventually you'll get there.

for reference ,  [http://doc.ubuntu.com/ubuntu/packagingguide/C/]("http://doc.ubuntu.com/ubuntu/packagingguide/C/")

---

### Post by gali98 on 2007-11-25
Hey thiankd, I'll check it out. Hopefully I can get one working. Or I guess I could just write a tutorial to compile it from svn.....
Thanks,
Kory

---

### Post by Benjiduncan on 2007-11-27
Hey, I'd sure like a copy of cinelerra. So if you can get that deb uploaded you'd make a lot of people's day. :)

---

### Post by fsman on 2007-11-27
repos for cinelerra are here
[http://cvs.cinelerra.org/getting_cinelerra.php#ubuntu](http://cvs.cinelerra.org/getting_cinelerra.php#ubuntu)

enjoy

---

### Post by fantan on 2007-11-28
Hi,

I downloaded the cinelerra package for my Gutsy from this repo: 
deb [http://giss.tv/~vale/ubuntu32](http://giss.tv/~vale/ubuntu32) ./

After installing and starting cinelerra, I get the following error message:

"cinelerra: error while loading shared libraries: libGL.so.1.2: cannot open shared object file: No such file or directory
albert@Gutsy:~$"

Where to get this shared object file?

Thanks for advance,

fantan

---

### Post by markekeller on 2007-11-28
The packages *xorg-driver-fglrx* and *libgl1-mesa-glx* both contain this file.

I got that same error when I installed that package a while back, myself.  It seems that it was compiled with OpenGL support, but if you're using fglrx (are you? I was, at least), it won't run.

---

### Post by Wolf011358 on 2007-11-29
Hey guys, I've been following your thread for getting Cinelerra running on Gutsy.  I am not having any luck myself with it.  I am running Gutsy on an AMD 32 machine.  I did an apt-get install from the appropriate repo, and read about libfaac 1.25.  Got that installed, and still nothing.  It's like it's not there.   What am I missing?  It's really frustrating.

Thanks

---

### Post by fsman on 2007-11-29
i found that it is a bit of "trail and error" to get the right repo.
The gandalf fiesty repos work just fine in Gutsy - and no opengl for those who need it.

---

### Post by thefriend on 2007-11-30
> **markekeller said:**
> The packages *xorg-driver-fglrx* and *libgl1-mesa-glx* both contain this file.

I got that same error when I installed that package a while back, myself.  It seems that it was compiled with OpenGL support, but if you're using fglrx (are you? I was, at least), it won't run.

Well these two files need to uninstall the nvidia-glx-new package and so don't work for me.
Do you have any idea for users with nvidia graphic cards?

the gandalf repo is not reachable.

What can I do to get cinelerra to work?

---

### Post by chatuu on 2007-12-01
i am having the same problem =/

anyone ???


helppp

---

### Post by swmiller6 on 2007-12-02
[http://lab.dyne.org/cinelerra/Gutsy](http://lab.dyne.org/cinelerra/Gutsy)

That worked for me...

swmiller6

---

### Post by chatuu on 2007-12-02
i did it.. same erros...


libgl.so.1.2 can not be loaod ....

=/

---

### Post by leandropds on 2007-12-05
Dear friends!

for resolve the problem, is very easy

on konsole write

#sudo ln -s /usr/lib/libGL.so.1 /usr/lib/ligGL.so.1.2


i wait feedback

thanks
:lolflag:

---

### Post by bridd on 2007-12-06
I used the same link ([http://lab.dyne.org/cinelerra/Gutsy](http://lab.dyne.org/cinelerra/Gutsy)) but when I got to the step  

./configure

I used: ./configure  --prefix=/usr/

All worked fine the first time for me... In gutsy, compiling Cinelerra from source using these instructions appears to be much easier than under previous Ubuntu versions, it's great!

---

### Post by dad311 on 2007-12-06
> **swmiller6 said:**
> [http://lab.dyne.org/cinelerra/Gutsy](http://lab.dyne.org/cinelerra/Gutsy)

That worked for me...

swmiller6

Was this tested on x86 or 64 bit?

---

### Post by lhtown on 2007-12-07
> **leandropds said:**
> Dear friends!

for resolve the problem, is very easy

on konsole write

#sudo ln -s /usr/lib/libGL.so.1 /usr/lib/ligGL.so.1.2


i wait feedback

thanks
:lolflag:

There is a typo. It should be:
#sudo ln -s /usr/lib/libGL.so.1 /usr/lib/libGL.so.1.2

---

### Post by Evil_Network on 2007-12-07
I had zero issues with 7.10 both 32 and 64 bit. I used the deb from giss.tv and installed thru Synaptic. I am using an ATI X1600 and have tried with both a generic and proprietary driver. 

I'm new to Linux in general, but an old hand at FreeBSD. I'm an ex-employee of Avid and Pinnacle looking to find a semi-decent editing package on Linux.

--Evil

---

### Post by thefriend on 2007-12-13
Hello Thank you for your help.

I tried 
#sudo ln -s /usr/lib/libGL.so.1 /usr/lib/ligGL.so.1.2
this helped me to start cinelerra...
**But:**

Cinelerra is working now - but if I open a *.mov video **it closes without notice.**

Sometimes i see the videotrack filling for about 1 second then Cinelerra closes....

who can help me?

---

### Post by perbiu on 2007-12-25
I also successfully installed Cinelerra last-last month on Gutsy with no problems encountered, except lately after i recieved a Software Update, The error started:

*cinelerra: error while loading shared libraries: libGL.so.1.2: cannot open shared object file: No such file or directory*

i tried this:
*#sudo ln -s /usr/lib/libGL.so.1 /usr/lib/ligGL.so.1.2*

But nothing happens.

---

### Post by gali98 on 2008-02-25
I know that this is kind of an old thread to dig up but since I started it I guess I can still post to it. As far as cinelerra goes, for right now it is kind of hit and miss on getting it to work. Really the best way to get it to work for you is to compile it yourself. We may have a better hope than that though. i saw this a little while ago and it may interest you.
[http://www.linux.com/feature/126441](http://www.linux.com/feature/126441)
It seems that this will be good since it will probably work out the license deal, and maybe could be included with ubuntu or ubuntu studio or something. It's a long way off, but there is still hope of it.
Kory

---

