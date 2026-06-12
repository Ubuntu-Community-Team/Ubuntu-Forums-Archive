---
title: "Mythtv frontend problem"
date: 2008-03-11
forum: Mythbuntu
---

### Post by Chris Musampa on 2008-03-11
Have been using ubuntu on my laptop and desktop machines for about 2 weeks (after trying is with vmware for a week or so) now and am almost ready to dispense with windows.  Just a couple more (hopefully) solvable issues and big bad bill is dust :)  

I've searched but can't find anything so here goes:

I've set the desktop up with mythbuntu as a combined back and frontend and need to be able to use the laptop (ubuntu) as a frontend, the main reason I shelled out the extra for the Nebula card was because its software was so good at this.  I can boot the laptop from the mythbuntu cd and watch just fine, but from my ubuntu hd boot the video is compressed into a narrow vertical strip (2" wide).  I've tried aspect ratio overide with no effect, I even tried running it in a window.  I've also removed and reinstalled myth frontend.

Obviously the hardware is fine as it works from the live cd, the laptop is an Acer3614WLMI, I'm stuck, any ideas?

---

### Post by Chris Musampa on 2008-03-11
Booted up the mythbuntu cd again, it has the graphics and screen set as 'intel experimental modesetting' and 'custom-1'.  My installed ubuntu has the same intel graphics driver but 'LCD Panel 1280x800'.

I tried setting graphics to 'vesa', the mythtv screen was full width but only 2-3 fps](*,)

How do I find out what the 'custom-1' settings on the mythbuntu cd are?

---

### Post by Chris Musampa on 2008-03-12
I'll be amazed if this can't be sorted, but its got me stumped and is now the last thing stopping me making gutsy my default boot, very irritating.  

Anybody???

---

### Post by PmDematagoda on 2008-03-12
This thread has been moved to the Mythbuntu section.

---

### Post by Calash on 2008-03-12
Hmm....that is very odd.  If the LiveCD of Mythbuntu works with your backend so should your Ubuntu install.

What version(s) are you running?  I am wondering if there is a difference between the Live CD Mythbuntu and what you have on the hard drive that may be causing the problem.

---

### Post by majoridiot on 2008-03-12
> **Chris Musampa said:**
> Booted up the mythbuntu cd again, it has the graphics and screen set as 'intel experimental modesetting' and 'custom-1'.  My installed ubuntu has the same intel graphics driver but 'LCD Panel 1280x800'.

I tried setting graphics to 'vesa', the mythtv screen was full width but only 2-3 fps](*,)

How do I find out what the 'custom-1' settings on the mythbuntu cd are?

i suggest booting the livecd and confirming that the video works ok.  once confirmed, exit to a terminal (CTRL+ALT+F1) and
copy /etc/X11/xorg.conf to your hard drive or a flash drive. (CTRL+ALT+F7) to get back to your X session and reboot
from the hard drive.

again, (CTRL+ALT+F1) to get to a terminal, then copy the known-working xorg.conf to the X11 directory.  you will
need to do this as sudo, first backing up the existing one to your home directory, in case you want to restore it:

```
$ sudo cp /etc/X11/xorg.conf /home/yourusername/xorg.bak
$ sudo cp /path/to/saved/xorg.conf /etc/X11/xorg.conf
```

then (CTRL+ALT+F7) back to your X session and either (CTRL+ALT+BKSPC) to restart the X server or reboot to start fresh.

give it a test and see how it goes... if the video is ok, you can further tweak out xorg.conf to suit your needs.

---

### Post by Chris Musampa on 2008-03-13
Calash, I'm running Ubuntu 7.10 on the laptop and Mythuntu 7.10 on the combined back/frontend.

Majoridiot, that thought has crossed my mind but thought as the mythbuntu/ubuntu desktops look so different it might break my system, however getting this tv frontend working is pretty much a deal breaker for me ditching windows so I'll try it when I get home.  Thanks for the suggestion.

---

### Post by laga on 2008-03-13
I don't think copying the xorg.conf file will break your system. If the config doesn't work, bulletproox will kick in and save you :)

Maybe you can post both xorg.conf files so we can see the difference, too? I'm just being curious here..

---

### Post by majoridiot on 2008-03-13
> **Chris Musampa said:**
> Calash, I'm running Ubuntu 7.10 on the laptop and Mythuntu 7.10 on the combined back/frontend.

Majoridiot, that thought has crossed my mind but thought as the mythbuntu/ubuntu desktops look so different it might break my system, however getting this tv frontend working is pretty much a deal breaker for me ditching windows so I'll try it when I get home.  Thanks for the suggestion.

i recommended the liveCD xorg.conf because it works with your video.  this will give 
you the most basic settings for the video card and screen settings.  you can always 
tweak out the various settings later.

if you can't suss this yourself, posting the working (livecd) and non-working (current) xorg.conf
files will help us to help you.

---

### Post by Chris Musampa on 2008-03-13
Right folks I did as you said and copied the xorg.conf from the livecd filesystem, rebooted from the hd, replace xorg.conf with the one on the flash drive and rebooted.

Screens and graphics now has the screen set as 'custom 1' but mythfrontend still has the same problem - AAARRRGGGH!

I've attached the xorg.conf if it's any help.

---

### Post by majoridiot on 2008-03-13
> **Chris Musampa said:**
> Right folks I did as you said and copied the xorg.conf from the livecd filesystem, rebooted from the hd, replace xorg.conf with the one on the flash drive and rebooted.

Screens and graphics now has the screen set as 'custom 1' but mythfrontend still has the same problem - AAARRRGGGH!

I've attached the xorg.conf if it's any help.

for best results, please post a copy of the xorg.conf from the livecd that does work and your xorg.conf that does not- and
clearly identify which is which ;)

---

### Post by Chris Musampa on 2008-03-13
> **majoridiot said:**
> for best results, please post a copy of the xorg.conf from the livecd that does work and your xorg.conf that does not- and
clearly identify which is which ;)

Sorry for not being clearer, the one I previously attached was from the my system which was copied from the livecd working filesystem.  It made no difference to frontend operation.

This one was my original one:

---

### Post by majoridiot on 2008-03-13
give the attached xorg.conf a shot and see if it gets you any closer...

---

### Post by Chris Musampa on 2008-03-13
> **majoridiot said:**
> give the attached xorg.conf a shot and see if it gets you any closer...

Thanks for the reply again major.

I tried your atached file, pressed ctrl+alt+bkspc and started mythfrontend, the 'prescaling images' message was huge but the menu text after that was slightly smaller than usual, live tv still has the same problem.

I rebooted and tried again, all myth messages are back to normal size but tv viewing still the same. :(

If its any help I will reproduce any logs or other output you request?

---

### Post by Calash on 2008-03-13
I am wondering if this may be an issue with the TV playback setup on your live system.

I am not at home right now, but under Options on your front end there should be something along the lines of Settings, then TV Playback settings.  You may want to check this on the Live CD, then on your HD install and see if they are different.

---

### Post by Chris Musampa on 2008-03-13
> **Calash said:**
> I am wondering if this may be an issue with the TV playback setup on your live system.

I am not at home right now, but under Options on your front end there should be something along the lines of Settings, then TV Playback settings.  You may want to check this on the Live CD, then on your HD install and see if they are different.

As far as i can tell i've tried changing all the settings (one at a time) in both 'playback' and 'appearance' with no joy, Im now going to reboot the livecd again and note all the relevant settings to compare.

---

### Post by Chris Musampa on 2008-03-13
Tried that, my settings in my hdd frontend are the same as on the livecd.

Any other ideas, did I read somewhere you can use mplayer as a frontend?

---

### Post by majoridiot on 2008-03-13
> **Chris Musampa said:**
> Thanks for the reply again major.

I tried your atached file, pressed ctrl+alt+bkspc and started mythfrontend, the 'prescaling images' message was huge but the menu text after that was slightly smaller than usual, live tv still has the same problem.

I rebooted and tried again, all myth messages are back to normal size but tv viewing still the same. :(

If its any help I will reproduce any logs or other output you request?

it may help to post /var/log/Xorg.0.log for both the livecd boot and your hd boot.  to compare
them against each other to see why one is working and the other not.

---

### Post by Chris Musampa on 2008-03-13
> **majoridiot said:**
> it may help to post /var/log/Xorg.0.log for both the livecd boot and your hd boot.  to compare
them against each other to see why one is working and the other not.

Dumb question alert!

How do I post them?  Too large to attach (over 19KB), complains i've used 23 images in  (limit=8) if I just post the text?

---

### Post by majoridiot on 2008-03-13
> **Chris Musampa said:**
> Dumb question alert!

How do I post them?  Too large to attach (over 19KB), complains i've used 23 images in  (limit=8) if I just post the text?

the only dumb question is one asked you already know the answer to, my friend. ;)

[http://paste.uni.cc/](http://paste.uni.cc/)

then post the link to each one here, being sure to identify the working one and we'll see if we can help.

---

### Post by Chris Musampa on 2008-03-14
> **majoridiot said:**
> the only dumb question is one asked you already know the answer to, my friend. ;)

[http://paste.uni.cc/](http://paste.uni.cc/)

then post the link to each one here, being sure to identify the working one and we'll see if we can help.

Lol, as someone who considers myself fairly tech savvy it sounded pretty dumb :)

It's not likely I'll get chance to get back to this before tomorrow (just so you don't think I've given in to temptation and chucked the lappy out of the window), but your help is appreciated.

---

### Post by Chris Musampa on 2008-03-18
Well  I decided to try a fresh install of Ubuntu + MythTV = same problem (narrow video when viewing TV).
Tried Mythbuntu clean install then install Ubuntu from the control center = desktop wouldn't work (no window controls or borders).
Tried Mythbuntu clean install then install Kubuntu from the control center = stopped partway through installing Kubuntu desktop, now even after rebooting the system seems to think a package installer is running (even though I can't see any process which looks like one).

I surrender! :(


I'm used to my PCs doing exactly what I want them to do with no hassles and I have now had enough of my computer fighting me at every turn (this thread, wireless networking, touchpad config, processor scaling, fan control, etc) back to  windows for me for the time being.  

I liked the idea of open source OS and apps and was willing to forgive several niggles but enough is enough, I will revisit desktop Linux at some point in the future when hopefully it will be a bit more mature and quite a bit slicker.

Thanks to those who tried to help me.

---

### Post by Chris Musampa on 2008-04-06
Update:

I gave it another go, installed mythbuntu then added ubuntu and made it the default desktop - SUCCESS!

I've also noticed it controls my laptop fan better than the original ubuntu install (it used to run at constant speed whereas now it runs at its lowest speed but spins up occasionally for a few seconds).  Seems a bit odd that the mythbuntu install should detect my hardware better than ubuntu, but I now have a system which does everything I need it to without having to switch back to windows.

A happy bunny.  :biggrin:

---

### Post by majoridiot on 2008-04-07
> **Chris Musampa said:**
> Update:

I gave it another go, installed mythbuntu then added ubuntu and made it the default desktop - SUCCESS!

I've also noticed it controls my laptop fan better than the original ubuntu install (it used to run at constant speed whereas now it runs at its lowest speed but spins up occasionally for a few seconds).  Seems a bit odd that the mythbuntu install should detect my hardware better than ubuntu, but I now have a system which does everything I need it to without having to switch back to windows.

A happy bunny.  :biggrin:

glad you got it working, chris!  nothing quite like the thrill of getting things sussed and fixed yourself, eh? :D

---

### Post by Chris Musampa on 2008-04-07
Cheers major, more of a workaround than a fix, but it means i can carry on learning my way around.

---

