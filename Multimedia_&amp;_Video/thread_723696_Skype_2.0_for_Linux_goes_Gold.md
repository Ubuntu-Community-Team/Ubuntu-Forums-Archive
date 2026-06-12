---
title: "Skype 2.0 for Linux goes Gold"
date: 2008-03-13
forum: Multimedia &amp; Video
---

### Post by rsambuca on 2008-03-13
The Skype 2.0 version with videoconferencing has just been released.  [Details here.]("http://share.skype.com/sites/garage/2008/03/skype_20_for_linux_gold.html")

---

### Post by bilal.17 on 2008-03-13
Yes finally.. ive been using the beta version for a while.. i hope this version is more stable as the beta had quite a few bugs.. going to download it now

---

### Post by wieman01 on 2008-03-14
Yahoo!

---

### Post by haelen on 2008-03-14
Crashes before I can even try it (at the "Agreement" screen)  on my Dell Inspiron  :(

Tim

---

### Post by bilal.17 on 2008-03-14
ye i cant even install this latest version as well ... it just tells me that the installation failed 
```
 dpkg: error processing /tmp/skype-debian_2.0.0.63-1_i386   ( --install) :
trying to overwrite '/usr/share/icons/skype.png' , which is also in package skype-common
dpkg-deb: subprocess paste killed by signal (Broken pipe)

```

---

### Post by pjalegria on 2008-03-14
same where....:(

---

### Post by xc3RnbFO8P on 2008-03-14
You have to uninstall Skype before you install it again. (beta 2.0)

---

### Post by haelen on 2008-03-14
Which I did :)

---

### Post by bilal.17 on 2008-03-14
thx it worked when in uninstalled it and installed again... but for some reason when i tried that earlier it did not work... but thx anyways

---

### Post by pjalegria on 2008-03-14
Didnt work for me too...
Can someone help???

---

### Post by xc3RnbFO8P on 2008-03-14
did you uninstall skype and skype common?

---

### Post by pjalegria on 2008-03-14
Only Skype

---

### Post by jvaudrey on 2008-03-14
Hello

I did "sudo apt-get remove skype" then "sudo apt-get autoremove" then "sudo apt-get install skype"

Worked fine now

---

### Post by pjalegria on 2008-03-14
Now it works...:lolflag: thanks

---

### Post by Jabz.biz on 2008-03-15
OK, I`m a noob in linux, but I wanted to let you know I cannot get it work either. "Wrong architecture i386". Next I will try to install it without the installer,...as soon as I find out how I can do that (any help?!) :) 

Regards, Jab

---

### Post by xc3RnbFO8P on 2008-03-15
> **Jabz.biz said:**
> OK, I`m a noob in linux, but I wanted to let you know I cannot get it work either. "Wrong architecture i386". Next I will try to install it without the installer,...as soon as I find out how I can do that (any help?!) :) 

Regards, Jab

Skype do not support 64 bit.

---

### Post by Jabz.biz on 2008-03-15
Hey Ringi, thanks for your help...I hate to say that, but that`s really awful. I was very enthusiastic about having Skype on my laptop. :( I`m thinking about be coming the first guy on earth using Ekiga...and I gonna talk a lot of people into it. :)

---

### Post by rsambuca on 2008-03-15
Skype works perfectly fine on the 64 bit platform.  Just follow Cappy's excellent instructions here.  All you do is cut and paste the command into the terminal and everything is done for you.
[URL="http://ubuntuforums.org/showthread.php?t=432295"]
HOWTO: Install Skype on 64-bit Ubuntu[/URL]

---

### Post by daigidan on 2008-03-15
This is truly awesome. :D My webcam failed to work with the beta on my 64-bit system, but after installing Gold it's working flawlessly, as is the microphone on the cam. Now to integrate it with my MythTV setup...

Thanks to Cappy and rsambuca for the clear and concise howtos!

---

### Post by grainbarcelona on 2008-03-17
Same problem here: I uninstalled skype. I downloaded thew new version ok, installed it, but when I want to run it, it shows some screen with license info for a few seconds & then disappears. It simply shuts down. Anyone having ideas on what to do about it?
Thanks for any help you can give

---

### Post by xc3RnbFO8P on 2008-03-17
Run Skype from terminal:

> skype

and show the output.

---

### Post by grainbarcelona on 2008-03-17
This is what I get when I run skype from terminal:
:~$ skype
Aborted (core dumped)

---

### Post by vishzilla on 2008-03-17
Downloaded the latest from Medibuntu repo! It works fine

---

### Post by xc3RnbFO8P on 2008-03-17
Found this, in terminal:
> mv .Skype .Skype.old

If it don't work (I just found out) 

I use Pcman file manager:
in tools> Open current folder as root
in new window: View> Show hidden files
Rename **.skype** to **.skype.old**
Make a new folder (right click with mouse) and name the folder **.skype **
Start Skype, now you have to write your account name and password.

---

### Post by allan25 on 2008-03-17
Is it possible to use skype and [www.rhubcom.com]("http://www.rhubcom.com")  together on my Ubuntu.. (I have gizmoproject now ) !  Reviews here suggest that it works well as standalone regardless if you are using with other person on windows or mac. I just like the design though.

---

### Post by xc3RnbFO8P on 2008-03-17
I got my Skype 2.0 through Update Manager, no problem (I had 2.0 beta).

---

