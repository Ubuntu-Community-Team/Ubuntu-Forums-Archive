---
title: "DVDStyler Installation"
date: 2008-11-18
forum: Multimedia Software
---

### Post by DarkLion on 2008-11-18
I am running Ubuntu Intrepid and cannot get DVDStyler to install. It keeps giving me an error message that says Error: Dependency Is Not Satisfiable: libwxsvg0. Does anyone know how to get all the dependencies for DVDStyler? I thank you for your help.

---

### Post by TheSerious on 2008-11-18
bump for the same problem.

---

### Post by Ubuntiac on 2008-11-19
Bumpity bumpity bump bump bump.

Me three.

First it complains about libwxsvg0 which seems to be Hardy only, then *that* complains for linavcodec1 which seems to actually exist in Intrepid universe repo's (yes, I have them turned on).

Welcome to Dependency Hell. :evil:

---

### Post by notrealdan on 2008-11-21
I had the same problem and worked my way through all the dependencies and finally got DVDStyler installed.  I was thrilled.  It even lunched OK!  However, as soon as I tried to drag a video file over to it, it got a seg fault.  Every video file, every time.

I found this version and replaced the one I had installed with it:
[http://www.getdeb.net/release/3326](http://www.getdeb.net/release/3326)

Works perfectly!  Hope this helps.

-Dan

---

### Post by DarkLion on 2008-11-22
Thank you for the help! I have installed the version from getdeb and it works. My only problem is finding a video converter that does what it is supposed to, so that I can convert from avi to mpg. If any one knows of any I would appreciate it. I have tried winff and it does not work. Once again, Thank You for your help.If DVDStyler converts from avi then I would love to know how to do it.

---

### Post by jethro10 on 2008-11-26
Right, hope this helps

DvdStyler is wonderful and can be installed by adding the repos on this page, to your repositories in System->Administration->Synaptic package manager.
[https://launchpad.net/~fabricesp/+archive](https://launchpad.net/~fabricesp/+archive)

The newest styler can then be found in the package manager after you have re-freshed the repository list.

Darklion, your last question, DvdStyler, newest version will automatically re-code AVI's to DVD compliant files before burning the disk, so it can be a "one stop shop" for avi to DVD manufacture if you wish.
However, look at DeVeDe, also in Synaptic as it also does the same approximate job.

DeVeDe is stronger on Avi conversion and Styler is stronger on menu layouts, but both will do the job.

J

---

### Post by binbash on 2008-11-26
> **jethro10 said:**
> Right, hope this helps

DvdStyler is wonderful and can be installed by adding the repos on this page, to your repositories in System->Administration->Synaptic package manager.
[https://launchpad.net/~fabricesp/+archive](https://launchpad.net/~fabricesp/+archive)

The newest styler can then be found in the package manager after you have re-freshed the repository list.

Darklion, your last question, DvdStyler, newest version will automatically re-code AVI's to DVD compliant files before burning the disk, so it can be a "one stop shop" for avi to DVD manufacture if you wish.
However, look at DeVeDe, also in Synaptic as it also does the same approximate job.

DeVeDe is stronger on Avi conversion and Styler is stronger on menu layouts, but both will do the job.

J

Thanks for the repo link

---

### Post by DarkLion on 2008-11-28
I appreciate the information. I have DeVeDee and it does work quite well. I have also found that ManDvd has the ability to make a custom menu, i/e a picture from the video that you are attempting to burn via video capture option. It also has a built in burning program and also converts many file formats without a separate program. You can also add audio tracks to your menu, however, it seems to only support mp3 formats at this time. I thank everyone for their advice and recommendations concerning this matter.

---

