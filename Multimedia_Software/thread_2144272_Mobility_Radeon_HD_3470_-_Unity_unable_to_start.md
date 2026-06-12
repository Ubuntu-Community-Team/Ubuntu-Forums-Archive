---
title: "Mobility Radeon HD 3470 - Unity unable to start"
date: 2013-05-11
forum: Multimedia Software
---

### Post by icu12345 on 2013-05-11
I have a Toshiba Satellite A300 Laptop with Ati Mobility Radeon HD 3470 Graphics card. Today I tried installing proprietary drivers from the amd website. However, once the driver installation was through it turned out my hardware was unsupported. On top of that, Unity couldn't start at all - launcher was gone, there was just a plain desktop which had a strange area in the middle looking like the attached image.

[ATTACH=CONFIG]242475[/ATTACH]

This area in the middle is completely unresponsive. The second image I attached shows what happens if I change the desktop.

[ATTACH=CONFIG]242476[/ATTACH]

So I decided to uninstall all proprietary drivers and revert to the default ubuntu driver. 
I am new to ubuntu so I wasn't sure how to get rid of those drivers. I followed these suggestions: [http://askubuntu.com/questions/68306/how-do-i-remove-the-propretary-ati-drivers](http://askubuntu.com/questions/68306/how-do-i-remove-the-propretary-ati-drivers)
Nothing changed. So I decided to reinstall Ubuntu (pluged  live USB in, selected Install Ubuntu and then selected Reinstall). Well, apart from the fact that I lost a program or two, nothing changed. Desktop still has this area in the middle and Unity is gone.

What do I do? Please help...

---

### Post by Bucky Ball on 2013-05-11
*Thread moved to **Multimedia & Video***


Please edit post and attach large images rather than have them in the body of your post. Thanks. 

('Go Advanced' > paperclip attachment icon)

---

### Post by icu12345 on 2013-05-11
I have a Toshiba Satellite A300 Laptop with Ati Mobility Radeon HD 3470 Graphics card. Today I tried installing proprietary drivers from the amd website. However, once the driver installation was through it turned out my hardware was unsupported. On top of that, Unity couldn't start at all - launcher was gone, there was just a plain desktop which had a strange area in the middle looking like this:



This area in the middle is completely unresponsive. Here's what happens if I change the desktop:



So I decided to uninstall all proprietary drivers and revert to the default ubuntu driver. 
I am new to ubuntu so I wasn't sure how to get rid of those drivers. I followed these suggestions: [http://askubuntu.com/questions/68306/how-do-i-remove-the-propretary-ati-drivers](http://askubuntu.com/questions/68306/how-do-i-remove-the-propretary-ati-drivers)
Nothing changed. So I decided to reinstall Ubuntu (pluged  live USB in, selected Install Ubuntu and then selected Reinstall). Well, apart from the fact that I lost a program or two, nothing changed. Desktop still has this area in the middle and Unity is gone.

What do I do? Please help...

---

### Post by icu12345 on 2013-05-11
Done. Do you think there's a way to undo this damage without a clean installaion of the operating system?

---

### Post by Mark Phelps on 2013-05-11
The default AMD drivers from their website won't work with video chipsets older than the HD 5x-series.  So, installing them "broke" your display setup.  You should have asked here first.

Also, your video card will not work with fglrx drivers in any Ubuntu version newer than 12.04.1.

---

### Post by Bashing-om on 2013-05-11
icu12345; Hi !

A lot depends on what version of ubuntu you are running and it's kernel version; Be advised:
> IF its an HD 2x/3x/4x then you are out of luck as AMD announced <last> summer that it is relegating these chipsets to legacy status and will not be developing new drivers for them. Existing restricted drivers from AMD won't work either, because they require X-server v1.12 and Ubuntu 12.10 uses X-server v1.13.(Mark Phelps)

That said, should be possible to get you back up with the open source driver.[INDENT=2]
regards

[/INDENT]

---

### Post by QIII on 2013-05-11
Threads merged and duplicate images removed.  Please do not start duplicate threads in other areas of the forums.

Again, please use the attachment feature to upload large images.

Cheers.

---

### Post by icu12345 on 2013-05-11
> **Mark Phelps said:**
> The default AMD drivers from their website won't work with video chipsets older than the HD 5x-series.  So, installing them "broke" your display setup.  You should have asked here first.

Also, your video card will not work with fglrx drivers in any Ubuntu version newer than 12.04.1.

I'm with Ubuntu 13.04. Thanks for clarifying. How do I get back to the open source driver? I'm new to ubuntu so I'd need help on that...

> **Mark Phelps said:**
> The default AMD drivers from their website won't work with video chipsets older than the HD 5x-series. So, installing them "broke" your display setup. You should have asked here first.

Also, your video card will not work with fglrx drivers in any Ubuntu version newer than 12.04.1.
The ati driver was listed as legacy driver for linux: [http://support.amd.com/us/gpudownload/linux/legacy/Pages/legacy-radeon_linux.aspx](http://support.amd.com/us/gpudownload/linux/legacy/Pages/legacy-radeon_linux.aspx)

---

### Post by The Cog on 2013-05-11
I found this advice elsewhere:

Be aware that the open source driver often causes overheating.

A suggestion might be to install 12.04 or 12.04.1 (NOT 12.04.2, as it will have the same issues you are currently experiencing), which will be supported until April, 2017. You can enjoy Ubuntu with your current hardware that way.

So, to get back to the open source driver:
```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```
That will effectively "rename" your xorg.conf file so there is no confusion later.

Then:
```
sudo apt-get purge fglrx fglrx-amdcccle fglrx-updates fglrx-amdcccle-updates
```
Reboot.

Let us know if you encounter any problems.

Best wishes.

---

### Post by icu12345 on 2013-05-11
Did this before starting the thread. fglrx is completely purged from my system (used this: [https://wiki.ubuntu.com/X/Troubleshooting/VideoDriverDetection?action=show&redirect=X%2FTroubleshooting%2FFglrxInteferesWithRadeonDriver#Problem:_Need_to_purge_-fglrx](https://wiki.ubuntu.com/X/Troubleshooting/VideoDriverDetection?action=show&redirect=X%2FTroubleshooting%2FFglrxInteferesWithRadeonDriver#Problem:_Need_to_purge_-fglrx))

However, the problem persists. Even after I reinstalled ubuntu from a live usb.. If it's any help, unity starts normally at the login screen. When I log in with my username, unity disappears and the desktop gets the funny spot in the middle.. I created a new user and there's no problems with it.. but I want to recover my current user. Using another user would just be a workaround..

---

### Post by rrich1974 on 2013-05-12
just use ubuntu 12.04 and be happy with your graphic card.

---

### Post by icu12345 on 2013-05-12
I was happy with my graphics card until the legacy AMD drivers messed my desktop up. Any way to recover it?

---

### Post by Yellow Pasque on 2013-05-12
See if this helps (you need to run the commands as the problematic user): [http://askubuntu.com/a/202020](http://askubuntu.com/a/202020)

---

### Post by icu12345 on 2013-05-12
Thanks, this solved it :)
However, the unity-reset was not found in this repository: [FONT=Ubuntu Mono]sudo add-apt-repository ppa:amith/ubuntutools.
[/FONT]Anyway, a user has indicated that the unity reset script has been integrated in the unity tweak tool for Raring, so I just downloaded the tweak tool and typed [FONT=Ubuntu Mono]unity-tweak-tool --reset-unity
[/FONT]Thank you :)

---

