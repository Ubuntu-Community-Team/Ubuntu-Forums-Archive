---
title: "[SOLVED] 64bit gutsy geforce 8600, out of ideas ;D"
date: 2008-02-27
forum: Multimedia &amp; Video
---

### Post by -random on 2008-02-27
[http://ubuntuforums.org/showthread.php?t=573359](http://ubuntuforums.org/showthread.php?t=573359) was going my way, but it's closed :P bleh..

So iv'e tried all of the above,

sudo dpkg-reconfigure -phigh(or not) xserver-org,
re-install nvidia driver, disable/enable restricted.. linux-restricted-modules disabled ="" and  tried "nv" aswel.. nvidia-glx(-new also) .. and my 64bit still doesn't boot up with the graphics enabled to use compiz, view is fuzzy/hazy, uses vesa driver (even if i change it), resolotion goes back to hUgE. Don't know what to try next?

Did anyone else get it working on gutsy 64bit?

Any ideas would be appreciated!

p.s. when i boot up the screen goes black 3 times before the login screen shows, after a long wait at the startup part showing 'Running local startup scripts /etc/rc.local [ok]'

---

### Post by Aldanga on 2008-02-27
I've got the same problem with a 7600GS. Exactly the same: I've tried all the stuff you have and am running 64-Bit. I can't find a solution anywhere.

---

### Post by -random on 2008-02-28
aye.. maybe 64bit just isn't worth it?

The only "bonus" running 64 bit in my opinion is that i get to see/use a couple of hundred more megs of ram (i hav 4gb), which i don't use anyway.

(sorry for going off-topic admin-ppl, but it seems this thread isn't going anywhere soon..)

---

### Post by slambrick on 2008-02-28
Have you tried ENVY ? I have Ubuntu gutsy 64bit. initially I could not get it to keep the nvidia driver at boot it would always fail. but Envy fixed it all. fixed it good. I have since had to do a rebuild due to file system crash. went straight to envy after the initail install was done and am right back with no video driver issues at all. I love Compiz and skyboxes and use Awn for my applet access. It's great Go ENVY.
[http://http://albertomilone.com/nvidia_scripts1.html]("http://http://albertomilone.com/nvidia_scripts1.html")

---

### Post by -random on 2008-02-28
> **slambrick said:**
> ... fixed it all. fixed it good. ...

love the way you put it 8) I'll give it a shot! Thanks for the help!

---

### Post by -random on 2008-02-29
So... i just simply donwnloaded envy, installed all the required packages and ran it!

Thanks for the help guys!

---

