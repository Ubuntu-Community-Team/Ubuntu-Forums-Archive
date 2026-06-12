---
title: "mythbuntu on Asus Chromebox"
date: 2014-12-28
forum: Mythbuntu
---

### Post by Marc_Aronson on 2014-12-28
I am looking to install mythbuntu on an [Asus Chromebox-M004U]("http://www.amazon.com/Asus-CHROMEBOX-M004U-ASUS-Desktop/dp/B00IT1WJZQ/ref=sr_1_1?ie=UTF8&qid=1419817827&sr=8-1&keywords=asus+chromebox"). I've found articles on how to install ubuntu on that device, but I haven't found an article or installing mythbuntu on that device. 

Has anyone successfully installed mythbuntu on this device?

I found [these instruction to install ubuntu]("http://rogerstringer.com/2014/09/21/upgrade-asus-chromebox-ram-bigger-ssd-ubuntu/"), but it doesn't provide an option for mythbuntu. 

Would it work to install Ubuntu and then follow [the instruction in this guide]("http://parker1.co.uk/mythtv_ubuntu.php")? The implication of this guide is that it's as simple as doing an "apt install mythtv" followed by a few tweaks. 

Update on Jan 11.

> **melben said:**
> [COLOR=#000000]I made a bootable usb stick with the mythbuntu 14.04 64bit installer, then followed the standalone install instructions on the kodi forums (1st post of this thread [/COLOR][http://forum.kodi.tv/showthread.php?tid=194362](http://forum.kodi.tv/showthread.php?tid=194362)[COLOR=#000000] and the wiki it links to).[/COLOR]


Based on Ben's post (# 3, below), I was able to successfully install mythbuntu 14.04 without any problems. The device works well as combined front-end/back-end system, using a 2.5" / portable USB 2.0 drive to store the recordings and an HDHOMERUN tuner. 

I initially tried to install mythbuntu using a USB-attached DVD reader with a mythbuntu image burned to DVD. That did not work. Once I created a USB thumb drive with a bootable mythbuntu install image, it worked without a hitch. 

Thanks for the help!

Marc

---

### Post by khPWXxF on 2014-12-29
There have been lots of viewing of this interesting postings but no responses.  
XMBC / Kodi seems to have had some success but possibly this summarises the situation for mthtv:
[http://www.gossamer-threads.com/lists/mythtv/users/578224](http://www.gossamer-threads.com/lists/mythtv/users/578224)

Phil

---

### Post by melben on 2014-12-30
I just got a Chromebox for Christmas and installed Mythbuntu with only the frontend and it's working well so far (with fairly limited use).

I made a bootable usb stick with the mythbuntu 14.04 64bit installer, then followed the standalone install instructions on the kodi forums (1st post of this thread [http://forum.kodi.tv/showthread.php?tid=194362](http://forum.kodi.tv/showthread.php?tid=194362) and the wiki it links to).

After removing the write protect screw and updating the coreboot firmware you boot with the usb stick installer (press esc for boot menu) and the rest is a standard Mythbuntu install.

I'm hoping that with the progress they're making with the deinterlacing ([http://forum.kodi.tv/showthread.php?tid=165707](http://forum.kodi.tv/showthread.php?tid=165707)) that this will be usable in Myth TV in the future, but the bob deinterlacing is OK (and there is always the kodi pvr addon).

Ben

---

### Post by Marc_Aronson on 2014-12-30
Ben, thanks for the response -- this is very helpful!

I'm not planning to use KODI/XBMC on this device. Are you having any deinterlacing problems when having 1080i mpeg2 video through the mythtv frontend?

thanks!

Marc

---

### Post by melben on 2015-01-02
1080i mpeg2 works mostly fine. I did have an issue when changing channels in Live TV, but I don't generally use live TV, I was just experimenting.

Bob deinterlacing is quite a step down from the VDPAU deinterlacing I'm used to. Everything is a little fuzzy, but watchable. When I tried Kodi in Openelec 5, the Motion Compensating deinterlacing gave a picture quality very similar to VDPAU, but I like the MythTV frontend, so I'm a little undecided what to use. Fortunately I still have my existing frontend/backend in use while I play with the chromebox.

Ben

---

### Post by Marc_Aronson on 2015-01-02
Ben, thanks for the pointers -- the install went without a hitch!

Phil, the article you linked to is about HDMI sticks. We are talking about the [Asus Chrome Box]("http://www.amazon.com/Asus-CHROMEBOX-M004U-ASUS-Desktop/dp/B00IT1WJZQ/ref=sr_1_1?ie=UTF8&qid=1420254999&sr=8-1&keywords=asus+chromebox"). Totally different beast.

Marc

---

### Post by ankur5 on 2015-05-18
[COLOR=#111111][FONT=Arial]Purely from the perspective of experience with this Chromebox... it's awesome! Packaging, form factor, ease of installation, elegance of solution: all categories earn five stars. I'm a freelance copywriter and B2B sales consultant... I can do everything I need on this simple, small, and inexpensive box.

Read full details here - [Google Chrombox]("http://www.patrika.com/news/computer/google-chromebox-for-business-in-india-launched-1037730/")[/FONT][/COLOR]

---

