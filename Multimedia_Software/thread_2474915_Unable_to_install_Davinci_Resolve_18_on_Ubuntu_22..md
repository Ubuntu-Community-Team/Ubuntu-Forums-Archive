---
title: "Unable to install Davinci Resolve 18 on Ubuntu 22.04"
date: 2022-05-11
forum: Multimedia Software
---

### Post by cookiemaster555 on 2022-05-11
Has anyone using Linux successfully installed Davinci Resolve 18 on Ubuntu? Please help.

So I downloaded DR 18 linux from the official website and it came with a PDF with clear instructions and I followed them.


So I did these things in the terminal as instructed:

[I]unzip ./DaVinci_Resolve_18.0b2_Linux.zip

chmod +x ./DaVinci_Resolve_18.0b2_Linux.run

sudo ./DaVinci_Resolve_18.0b2_Linux.run -i[/I]

I get this error message :

[I]AppImages require FUSE to run. 
You might still be able to extract the contents of this AppImage 
if you run it with the --appimage-extract option. 
See _[https://github.com/AppImage/AppImageKit/wiki/FUSE](https://github.com/AppImage/AppImageKit/wiki/FUSE) _
for more information

[/I]Ok So I went to that link but then they gave me this warning:

[I][B]Warning: Do not install the fuse package as of 22.04 or you may break your system

[/B][/I]So I am stuck in this predicament 

I need fuse to install the appimage but if I install fuse I may break my system??? 


:?::?:#-o#-o#-o

Anybody out there that have successfully installed DR 18 on Ubuntu 22.04??? if so how you did it?

---

### Post by mhgsys on 2022-05-14
Reading the link you've provided... 
If I'm correct: ```
sudo apt install libfuse2
```  would be the correct way to go for you.

NOTE: the warning tells you not to install fuse.. like on Ubuntu (<= 21.10):, and does not apply to libfuse2 for Ubuntu (>= 22.04):

---

### Post by edmarmolejos on 2022-05-14
I think this can be your solution, you must first convert the Davinci-Resolve installer into deb, because it comes for Cent OS 7.3, Makeresolve helps to convert it. Follow the steps on the page. [https://www.danhetufveson.com/makeresolvedeb](https://www.danhetufveson.com/makeresolvedeb)

If after converting the installer to deb does not work, you have to wait for the official version. Beta 17 version and Ubuntu 20.4 gave difficulties with drivers. When they launched the stable version, it was solved.

---

