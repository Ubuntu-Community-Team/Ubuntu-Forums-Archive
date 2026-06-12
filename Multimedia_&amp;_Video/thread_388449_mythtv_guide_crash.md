---
title: "mythtv guide crash"
date: 2007-03-19
forum: Multimedia &amp; Video
---

### Post by Dubstar_04 on 2007-03-19
I have been experiencing problems with my pc crashing when i enter the tv guide from live tv!!

I'm obviously not sure what the problem is also I don't know how to debug the the problem or where to look for error or crash logs!!

The problem is so serious that it actually freezes the who pc. e.g i cant ctrl+alt+<-(del) to recover to and x display it has to be a power off job!!

This and the channel change speed are my only issues with mythtv now!!

any help really appriciated!!

---

### Post by majoridiot on 2007-03-20
in the frontend-

Utilities/Setup-->Setup-->TV Settings-->Playback

make sure "Enable OpenGL vertical sync for timing is disabled.

hope it helps. :D

---

### Post by Dubstar_04 on 2007-03-26
Yeah that sorted the problem. Thanks very much.

---

### Post by majoridiot on 2007-03-26
glad it worked! :) 

as an additional note, this generally is a problem fix for nvidia cards and may or may not help with
ati drivers, which apparently have ongoing issues that ati is working on.

---

### Post by Dubstar_04 on 2007-03-30
its doing it again!! 

The guide in the live tv is causing crash issues. I have the vertical sync turned off. I'm now using ubuntu 7.10 beta and it is absolutly superb as a media centre pc. it has been much faster setting up than edgy and few little niggles. 

The tv guide crash issue is weird. could it be caused by using the open source nv drive rather than the proprietry nvidia one??

I have really taken to ubuntu, and the new feisty is excellent!!

---

### Post by majoridiot on 2007-03-30
> **Dubstar_04 said:**
> The tv guide crash issue is weird. could it be caused by using the open source nv drive rather than the proprietry nvidia one??

absolutely.  i suggest installing the nvidia driver- either with the restriced driver manager (system>>administration>>restricted driver manager)
if using a regular desktop... or you could use envy, as well.

---

### Post by Dubstar_04 on 2007-04-01
I checked the xorg.conf last night and it seems that the 'nvidia' driver is in use, with with a no logo option so thats why I was confused!!

The tv guide will load and and can be used to browse but as soon as i try to select a program or exit the guide it crashes, and flickers between the guide and live tv and then displays a message about video failing to be displayed so i select return to menu and it starts flickering again!!  

I'm stuck for ideas!!

---

### Post by majoridiot on 2007-04-01
what sort of errors are you showing in your logs? -- mythbackend.log, syslog, xorg.0.log, etc...

what setting are you using for live preview of video- high medium or low cpu usage?

also, does this problem happend when viewing your library of recorded programs with live-preview
of video?

---

### Post by Dubstar_04 on 2007-04-02
If the proper nvidia driver were installed i would have the nvidia setup utillity in the Applications>system tools> Nvidia settings?? Is this correct as that is not showing!!

I will open myth in a window and the go the tv guide and see what logs / errors i can see.

Thanks for your help in this matter

---

### Post by majoridiot on 2007-04-02
yes, it should show there.  you can check to see if it was properly installed and to where:

```
$ which nvidia-settings
```

remember that you must run it as **sudo** for settings to properly save... and likely will need
to restart X (crtl-alt-tab).

---

### Post by Dubstar_04 on 2007-04-02
This is the results

```
$ which nvidia-settings
/usr/bin/nvidia-settings

$sudo /usr/bin/nvidia-settings

```

This displayed the proper nvidia config app. it is not accessible from the applications menu though!!

---

### Post by majoridiot on 2007-04-02
i added mine as a custom app launcher on the panel using "gksudo /usr/bin/nvidia-settings" as the 
launch instruction.  be sure to use gksudo and not sudo.

right-click and select add to panel... custom launcher.

---

### Post by Dubstar_04 on 2007-04-02
Problem solved!!!

I had two functions assigned to the  'guide' button whilst in live tv mode!!! what a dummy!!

At least it is sorted!!

Just the return from xine problem now, then sort out the auto boot and shutdown using your guide and da da!! my myth box will be finished!!

Thanks for your help.

---

### Post by majoridiot on 2007-04-02
> **Dubstar_04 said:**
> I had two functions assigned to the  'guide' button whilst in live tv mode!!! what a dummy!!

i've done that myself, so no worries.  glad you got it working! :)

---

### Post by Dubstar_04 on 2007-04-03
Thanks for your help. Wonder if you can shed any light on my xine prob??

[http://ubuntuforums.org/showthread.php?t=398809](http://ubuntuforums.org/showthread.php?t=398809)

Superm1 and I are trying to come to the bottom of the problem!!

---

