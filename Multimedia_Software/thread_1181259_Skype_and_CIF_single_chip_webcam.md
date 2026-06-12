---
title: "Skype and CIF single chip webcam"
date: 2009-06-07
forum: Multimedia Software
---

### Post by folksteve on 2009-06-07
Im still quite the newbie to ubuntu and have only been using it for about 10 months. After upgrading to Jaunty i tested my webcam and everything was hunky dorey on skype and all other programs (amsn, cheese).

Now after an update the webcam works on everything else (very poorly) and not at all in skype.

Have tried all sorts of workarounds and installing the libv4l drivers with no joy.

Any help is very much appreciated.

Thanks

---

### Post by tolotos on 2009-06-08
What kind of update did you perform? An update via the normal update Manager or with something else? Is dmesg reporting any errors when you plug your webcam in?

---

### Post by folksteve on 2009-06-08
The libv4l files were installed with a .deb from a repository that said they were the latest versions.

There are no problems with dmesg when plugging it in, skype detects the webcam but when it comes to testing it, there is no picture at all.

---

### Post by tolotos on 2009-06-09
Have you tried starting skype from terminal in order to see whether it prints any errors? Or if any of the other programms (i.e.: cheese) prints some errors?
Furthermore you could check, whether you have the newest skype version.

Do you really need the newest lbv4l libraries, due to extra functions, or would older ones suit you too? Because I would otherwise suggest, downloading some older releases an try it with these.

---

### Post by folksteve on 2009-06-09
Just tried running skype from the terminal and this is what i got:

ALSA lib pcm_bluetooth.c:1569:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib pcm_bluetooth.c:1569:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib pcm_bluetooth.c:1569:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib pcm_bluetooth.c:1569:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib pcm_bluetooth.c:1569:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib pcm_bluetooth.c:1569:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
Starting the process...
Skype Xv: Xv ports available: 64
Skype XShm: XShm support enabled
Skype Xv: Using Xv port 355

And ran cheese with no errors

Dont want to uninstall libv4l as it means taking off things like amsn, google earth, etc, etc.

---

### Post by tolotos on 2009-06-10
Hmm unfortunatly the errors in skye seem to have nothing to do with your problem....
Was your camera supported natively by ubuntu, or did you have to install some packages like for example Easycam2? What is lsusb printing in terminal?

> **folksteve said:**
> 
Dont want to uninstall libv4l as it means taking off things like amsn, google earth, etc, etc.
Well, if you should one day reconsider, here is the link to a repository with older versions of libv4l: [http://de.archive.ubuntu.com/ubuntu/pool/main/libv/libv4l/](http://de.archive.ubuntu.com/ubuntu/pool/main/libv/libv4l/) (Just in case)

---

### Post by latev on 2009-08-02
Any luck with the webcam? I seem to be having the same problem - the webcam works fine when I go gstreamer-properties and then "test video" - I can see myself. Skype also detects it fine, however the test button produces gibberish on the screen - something is wrong. Any idea how to reconfigure the webcam in Skype?

---

### Post by folksteve on 2009-08-03
After many attempts at trying to solve the problem i have come to the conclusion that it is purely a Skype thing and there is nothing i can do about it :(

Plus ive spent far too much time trying to solve these problems as i was using Ubuntu as my main work station and was losing out on too much time that could be spent doing important things e.g. work, study, live, wife, etc.

Im getting myself a newish iMac in september as it is a similar environment and it just works (plus it looks damn sexy) which is what i need. We've still got Ubuntu on my wifes netbook (Ubuntu netbook remix) and we both love it, especially now i have some knowledge working in a Linux OS (and Skype works perfectly on the netbook :D )

As far as i know there is no way to configure the webcam in Skype. On the windows version there is usually a tab which takes you to an external program for such a job. Sadly with the desperately needing a serious update version of Skype for Linux i have not seen one. This lack of updates and time spent on it is also a major factor in why skype doesnt work well on Linux.

I hope you find a solution Latev which doesnt invlolve re-installing Ubuntu over and over again (which i have had to do before for various things).

Dont get me wrong Ubuntu works pretty damn well for most things and can be fantastic fun. But personally, i need something a bit more reliable.

Good luck, let me know if you find a solution :KS:D :P :guitar:

---

### Post by latev on 2009-08-03
I managed to resolve the issue actually - shortly after I did my posting here

I have a 64 bit ubuntu and for me the following trick makes my camera work in skype

LD_PRELOAD=/usr/lib32/libv4l/v4l2convert.so skype

hope it helps

BTW - I too feel Linux and Ubuntu in particular is a great OS, however it needs some serious developers, management and of course tons of cash  - to get involved and in less than 2-3 years we may have a real competitor to M$. For now sadly things "simply don't work" and I'm yet to find a Linux distro that I can't break a dozen things just by playing around with the things that come by default or to have to spend hours on the internet just to get my damn mouse, webcam or soundcard working...

I wonder why they keep introducing new things and changing things around while at the same time the old things are so buggy....who knows
Stability is a very serious problem for the Desktop Lin distro...

---

### Post by pearldrums on 2009-11-05
how might this be modified for a 32 bit version?

---

### Post by areskz on 2009-12-10
Change lib32 for lib

LD_PRELOAD=/usr/lib/libv4l/v4l2convert.so skype

---

### Post by humbleheadbanger on 2010-09-03
hey,I am using 64 bit ubuntu also

I have the same issue. I can see myself in gstreamer-properties, but nothing in skype i have done the export XLIB_SKIP_ARGB_VISUALS=1 && LD_PRELOAD=/usr/lib32/libv4l/v4l2convert.so skype' command for my single CIF chip webcam but still no picture. I thought that if I could see myself in Gstreamer-properties I should be able to see myself in skype. I'm not a novice user (even though my posts might say so) but I think I need some help here.

thanks

---

### Post by drpbl on 2011-08-25
for 32 bit version use:

LD_PRELOAD=/usr/lib/libv4l/v4l2convert.so skype

I know, counter-intuitive.  Just drop the 32 after lib32 on the 64 bit LD_PRELOAD.

---

