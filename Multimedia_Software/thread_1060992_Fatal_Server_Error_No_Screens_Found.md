---
title: "Fatal Server Error: No Screens Found"
date: 2009-02-05
forum: Multimedia Software
---

### Post by MrCharles on 2009-02-05
I'm a Linux newb - so please understand.

I just install Ubuntu 8.10  Everything went fine - until I enabled NVidia Drivers and Re-booted.   Now I get no GUI login - Only 'Fatal Server Error: No screens found giving up"    

xinit: Connection Refused (errno 111): unable to connect to x server
xinit: No such process (errno 3): Server Error


I have no idea what to do in this situation.
I have dual Nvidia 8800GTS - that I'd like to setup for twinview - but as of now I can't even get a GUI!

Help!

---

### Post by xc3RnbFO8P on 2009-02-05
Try, in Terminal:
> sudo dpkg-reconfigure gdm

---

### Post by MrCharles on 2009-02-05
invoke-rd.d: initscript gdm, action "reload" failed

should I have shut down gdm first?

when i dont' stop it - i just get a dialog that say "Changes will take effect whena ll current X sessions have ended"

either way - startx still shows errors

All from the NVidia driver - breaking my xconfig

problem is - I have no idea howto edit my xconfig from terminal - nor do i understand what the values mean.   thinking I'm just going to go back to winblows

---

### Post by MrCharles on 2009-02-05
Tried this btw
[http://ubuntuforums.org/showthread.php?t=1054842](http://ubuntuforums.org/showthread.php?t=1054842)

Didn't work for me.

Anyone out there have any suggestions?

---

### Post by MrCharles on 2009-02-06
For the record.
I was finally able to get everything working using the 180.11 Drivers in Synaptic (which are outdated btw).  I just had to edit my xconfig from terminal to add the PCI BusID.  However -it's posing many conflicts with both Compiz and my Dual Screens.

Unfortunately at this point - I'm unsatisfied with this issue, and will be returning to windows.

---

### Post by redroad55 on 2009-02-06
Here are some thoughts 8.10 is a new release .. The windows equivalent would be vista and xp .. where we, many held back moving to vista because we didn't want the headaches of working out the bugs of anew release not to mention the nightmare phone calls..calling microsoft and they would claim it was a hardware problem they would say call the manufacturer..called manufacturer and they would say It's a software problem call microsoft..on and on blah blah blah blah .. So in short try the 8.04 LTS (long term support) it is the more stable version .. It is the XP version if you will..best to you

---

### Post by toolfan202 on 2009-02-06
I am getting the same issue.  However different factors have contributed to the downfall of my x server.

First, I am using dual ATI3870m with crossfirex instead of nvidia, just couldn't afford the new nvidia 9800s :(  Anyway.

While I was trying to enable my desktop effects I found that my hardware drivers were not activate for my video cards.  I then proceeded to activate them, everything went smoothly, downloaded-installed, then asked for a reboot.  Upon the restart I get Ubuntu loading to a command line after the loading screen.  I did a startx and got the same messages you did.  (Fatal screen error, no screens found, unable to connect to x server... blah blah blah)  I think in this stage, 8.10 cannot support dual graphics cards and is screwing itself over when you try to get them to work.  Anyway, since I am in fact a newbie in most of the ways of Linux, I am hoping the someone out there will know how I would be able to edit whatever file Linux is corrupting while trying to enable the graphics drivers.  And please set me straight if I am misconstrued on any of my information.  Also I will be rebooting to check the results of sudo dpkg-reconfigure gdm to see if I get a similar, if no the same, message.

Thanks in advance.

---

### Post by toolfan202 on 2009-02-06
Ok, it seems that my sudo dpkg-reconfigure gdm gives the same results as previously posted.  Any help is greatly appreciated.  If nothing can be done I will just reinstall Ubuntu 8.10 though I really don't want to do that.  And to MrCharles, I wouldn't be so quick to give up on Ubuntu just yet, there will always be snags, you just have to be patient enough to see through them.  Hang in there, don't take the windows way out ;)

---

