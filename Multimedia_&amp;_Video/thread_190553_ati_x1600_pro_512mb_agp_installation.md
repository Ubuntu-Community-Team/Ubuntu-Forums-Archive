---
title: "ati x1600 pro 512mb agp installation"
date: 2006-06-06
forum: Multimedia &amp; Video
---

### Post by phinux on 2006-06-06
i have already tried both of these sites around 8 times each. even on debian, fedora 5, suse 10.1, and solaris i have still failed. i end up with my fglrxinfo showing my ati x1600 and not mesa. my glxinfo shows ati with hardware acceleration enabled. those are both really good news, however when i open a file with text and try to scroll down something strange happens. i can see the text scrolling but its scrolling behind the text that is already showing making is look all cluttered. the text that is showing at the time i open the file is overlaping the stuff i scroll down to. this same thing happens when i have internet open or any thing else. right now i'm going to have to reformat since opening a few winodows makes my screen look like a bunch of crap all piled up. can someone help me install my video?

[http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide)
[https://wiki.ubuntu.com/BinaryDriverHowto/ATI](https://wiki.ubuntu.com/BinaryDriverHowto/ATI)

---

### Post by fabrizio gorla on 2006-06-08
Same HW same problem....
don't think it is a procedure matter...
...it is the driver that ...
I'm back to vesa waiting for the next gen of drivers...

---

### Post by iramhernandez on 2006-12-19
I'm having problems with x1600 pro 512mb agp also.  I get fglrx supposedly working but performance is poor.  I manually install drivers from ATI's website, I get screen tearing too.  I have a feeling this is related to AGP.

---

### Post by ddaedalus on 2006-12-21
same here. just disable the dri module in your xorg.conf. but this also disables 3d-acceleration :(

---

### Post by Zober on 2007-01-11
Same issue here.  I havent tried this yet, because I really dont want to switch to fedora, but this bloger claims to have it working.

[http://www.basilgohar.com/blog/category/linux/](http://www.basilgohar.com/blog/category/linux/)

Please let me know if anyone tries this.

---

### Post by ddaedalus on 2007-01-11
The fact, that composite and dri don't work together on ATI is known long since. The setting

Section "DRI"
Mode 0666
EndSection

is IIRC set by default in Ubuntu.
Can't confirm this, since the crappy drivers ATI made me sell my ATI X1600.

---

### Post by iramhernandez on 2007-01-15
Newest drivers 8.33.6 are working very well now.  Followed steps at [http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide")

---

### Post by Ravanous on 2007-01-19
I have the PCI-Express version of this card paired up with a Shuttle SK22G2 SE.

I cannot get a GUI in the installer and ended up doing a text install.

Black & White loading splash screen & the blank, no video at all.

I have tried booting in init level 3, so I could follow the steps from the cchtml wiki, but that seems to do no good either, same style loss of video.

Any suggestions for me?

---

### Post by Ravanous on 2007-03-10
> **Ravanous said:**
> I have the PCI-Express version of this card paired up with a Shuttle SK22G2 SE.

I cannot get a GUI in the installer and ended up doing a text install.

Black & White loading splash screen & the blank, no video at all.

I have tried booting in init level 3, so I could follow the steps from the cchtml wiki, but that seems to do no good either, same style loss of video.

Any suggestions for me?

Just wanted to follow up, I followed the cchtml link instructions and got 8.34.8 working on my machine

---

### Post by Hiew on 2007-03-11
I'm not very experienced in using linux, but i would use it as my main os ONLY if i can just get 3D support on my ATI x1600 512mb AGP video card....its the only thing holding me back
i tried the manual installation on [http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide)

It seemed to work, however when kubuntu starts up the resolution is set to something really big in X but when i check my monitor (monitor's menu)it says its running at 1280x1024 (which is what i want 2D to work on...

sorry i'm a little scatterbrained right now, and hope someone could help me on this issue...

fglrxinfo is giving me this:

```
$ fglrxinfo
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.5.1)
```

Would using EasyUbuntu work just as well?

---

### Post by theicyj on 2007-04-11
Has anyone figured out how to get the ATI x1600 pro working on Ubuntu yet?  I am having many of the same problems as listed above.  I have done 3 fresh installs after following numerous "guides".   All I want is 3d acceleration!

---

### Post by Ravanous on 2007-04-11
> **theicyj said:**
> Has anyone figured out how to get the ATI x1600 pro working on Ubuntu yet?  I am having many of the same problems as listed above.  I have done 3 fresh installs after following numerous "guides".   All I want is 3d acceleration!

Have you tried method 2 of the instructions posted for edgy in the cchtml wiki?

If you have, then what problems are you having and what version of the ATI drivers are you using?

---

### Post by theicyj on 2007-04-23
Yeah, I have tried that guide, word-for-word, with no success.  I may try to reinstall Ubuntu (since it is final now) and follow the guide again.  Anyone else get 3d acceleration w/ this card working under Ubuntu yet?

UPDATE: I reinstalled Ubuntu and the new restricted driver worked great!  Still no desktop effects though, but at least the games work.

---

### Post by Ravanous on 2007-04-24
> **theicyj said:**
> Yeah, I have tried that guide, word-for-word, with no success.  I may try to reinstall Ubuntu (since it is final now) and follow the guide again.  Anyone else get 3d acceleration w/ this card working under Ubuntu yet?

I just upgraded to Feisty over the weekend & I have to do the drivers over again. I will try it out and report back here.

In the meantime if someone else has had any success with Feisty, please post any additional notes that you have.

---

### Post by traffas on 2007-04-24
I've not been able to get the x1600 PCIe card to work under Feisty 64-bit.

---

### Post by iramhernandez on 2007-04-24
I was able to get the x1600 working on edgy but the trick was to use the 2.16.10 kernel instead of the newest 2.16.11 kernel (I forget the exact version numbers since I am not on my ubuntu computer now).  I have since upgraded to feisty and it works flawlessly and it was very easy to install by just clicking 'enable restricted drivers' in the menu.  I'll update this thread with specific instructions on how I got it to work on edgy when I get home tonight.

---

### Post by A2Bacon on 2007-04-24
Is there no other ways of installing the x1600 than by downgrading the kernel? Why does this video card have such poor support? I've searched all over Google for answers, and it seems there are a lot of problems and very little to zero solutions..

---

### Post by Ravanous on 2007-04-24
> **iramhernandez said:**
> I was able to get the x1600 working on edgy but the trick was to use the 2.16.10 kernel instead of the newest 2.16.11 kernel (I forget the exact version numbers since I am not on my ubuntu computer now).  I have since upgraded to feisty and it works flawlessly and it was very easy to install by just clicking 'enable restricted drivers' in the menu.  I'll update this thread with specific instructions on how I got it to work on edgy when I get home tonight.

I had no problems getting it to work in both the original one & whatever the latest one was using Method 2 from the cchtml wiki.

btw...I just noticed there is a page for Feisty over there now.

---

### Post by Geff on 2007-08-07
Same **** here....

For two weeks I'm trying to make a Sapphire X1600 PRO AGP (on a gugabyte nForce2 mobo) to work on Ubuntu 7 and N-O-T-H-I-N-G.

I've reinstalled the system like 6 times. Tried every single installation tutorial, walkthrough and crap out there and nothing.

In the end, the fglrxinfo shows "Mesa-*******-3D" and nothing 3d-related works. Google Earth crashes...

---

### Post by Ravanous on 2007-08-07
I ended up having to Ctrl+Alt+F1 and then doing everything from the command line cuz my X would go blank.

I do however have everything working right now. No more MESA crap.

I basically got into commandline mode and read everything off the cchtml wiki on my other machine while I typed it out here. There was probably a better way, such as scp-ing the commands over as a text file, but I was getting frustrated.

---

### Post by ravendiana on 2007-08-13
I have the same problem, and I'm an utter noob  I don't have a working version of the driver to copy and i'm in drake?  for that matter how do I upgrade?  will i need to save my files elsewhere?

---

### Post by Ravanous on 2007-08-13
> **ravendiana said:**
> I have the same problem, and I'm an utter noob  I don't have a working version of the driver to copy and i'm in drake?  for that matter how do I upgrade?  will i need to save my files elsewhere?

[Here's a link]("http://wiki.cchtml.com/index.php/Ubuntu_Installation_Guide") to the cchtml wiki page for ubuntu. There is a guide for DD.

I would backup stuff no matter what before trying one of those guides. If you are stuck at specific points on that post here and we'll see how we can help you get past :)

---

### Post by Mongo5000 on 2007-08-14
Looks like the cchtml wiki is gone.  Does anybody have another copy of their guides?

---

### Post by Ravanous on 2007-08-14
Here are the Google cache versions for:
[Dapper]("http://64.233.169.104/search?q=cache:35cIQFav3WkJ:wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide+cchtml+wiki+dapper&hl=en&ct=clnk&cd=1&gl=us&client=firefox-a")
[Edgy]("http://64.233.169.104/search?q=cache:t_MxR6jQxicJ:wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide+cchtml+wiki+edgy&hl=en&ct=clnk&cd=1&gl=us&client=firefox-a")
[Feisty]("http://64.233.169.104/search?q=cache:gEfCo7LmPD4J:wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide+cchtml+wiki+feisty&hl=en&ct=clnk&cd=1&gl=us&client=firefox-a")

---

