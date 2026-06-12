---
title: "nVIDIA Questions (revisited?)"
date: 2006-09-18
forum: Multimedia &amp; Video
---

### Post by useResa on 2006-09-18
I have searched the forum and found some similar threads, but not sure what solution to pick or whether any solution is applicable for my situation.

I have installed the latest nVidia driver (to be found at [http://www.nvidia.co.uk/content/license/driver_license.asp?language=en&url=http://uk.download.nvidia.com/XFree86/Linux-x86/1.0-8774/NVIDIA-Linux-x86-1.0-8774-pkg1.run](http://www.nvidia.co.uk/content/license/driver_license.asp?language=en&url=http://uk.download.nvidia.com/XFree86/Linux-x86/1.0-8774/NVIDIA-Linux-x86-1.0-8774-pkg1.run)) based on instructions from a collegue. Later I found this thread [http://www.ubuntuforums.org/showthread.php?t=259913](http://www.ubuntuforums.org/showthread.php?t=259913). This is basically the instructions that I also followed.

When I start Ubuntu now, just before the login screen I see a big white screen with the text nVidia, so I suppose the nVidia driver is indeed installed. Furthermore I also have a new launcher "NVIDIA X Server Settings" in Applications --> System Tools.

However, when I type ```
lspci | grep VGA
``` I get the following result > 0000:01:00.0 VGA compatible controller: nVidia Corporation: Unknown device 01d7 (rev a1)

This sort of suprised me, because I would expect that a known device would be mentioned here.

Please find also attached what nvidia packages I have installed.

Now for the questions:
1. When I shutdown I only see a black screen. The PC shuts down, so basically there is no problem, but I kind of got used to the shutdown screen. So if I could get it back, that would be nice

2. In the various threads there is talk about the nvidia type of card. How can I check what card is installed in my laptop (Dell Latitude D620)?

3. I also read some threads about XGL & compiz. Is this worth installing and what do I gain?

Maybe some of my questions are not completely clear. If so let me know.
I am quite a newb to the Linux world (have Ubuntu since approx 1 month now).

I hope that someone can help me out and sorry if my questions are a repetition of questions earlier asked.

---

### Post by tseliot on 2006-09-18
> **useResa said:**
> I have searched the forum and found some similar threads, but not sure what solution to pick or whether any solution is applicable for my situation.

I have installed the latest nVidia driver (to be found at [http://www.nvidia.co.uk/content/license/driver_license.asp?language=en&url=http://uk.download.nvidia.com/XFree86/Linux-x86/1.0-8774/NVIDIA-Linux-x86-1.0-8774-pkg1.run](http://www.nvidia.co.uk/content/license/driver_license.asp?language=en&url=http://uk.download.nvidia.com/XFree86/Linux-x86/1.0-8774/NVIDIA-Linux-x86-1.0-8774-pkg1.run)) based on instructions from a collegue. Later I found this thread [http://www.ubuntuforums.org/showthread.php?t=259913](http://www.ubuntuforums.org/showthread.php?t=259913). This is basically the instructions that I also followed.

When I start Ubuntu now, just before the login screen I see a big white screen with the text nVidia, so I suppose the nVidia driver is indeed installed. Furthermore I also have a new launcher "NVIDIA X Server Settings" in Applications --> System Tools.

However, when I type ```
lspci | grep VGA
``` I get the following result 

This sort of suprised me, because I would expect that a known device would be mentioned here.

Please find also attached what nvidia packages I have installed.
If you want to know the exact model of your card you can post the output of this command and I'll tell you which model is:
```
lspci -n | grep 300
```

> **useResa said:**
> Now for the questions:
1. When I shutdown I only see a black screen. The PC shuts down, so basically there is no problem, but I kind of got used to the shutdown screen. So if I could get it back, that would be nice[/CODE]
Read point 13 of the Problems Section:
[http://doc.gwos.org/index.php/Latest_Nvidia_Dapper#PROBLEMS_SECTION](http://doc.gwos.org/index.php/Latest_Nvidia_Dapper#PROBLEMS_SECTION)

but add "vga=791" instead of removing "splash".

If that doesn't work just remove splash

[QUOTE=useResa;1515188]3. I also read some threads about XGL & compiz. Is this worth installing and what do I gain?
It can make your system unstable and you might have to do a fresh installation to solve the problem.

---

### Post by useResa on 2006-09-18
tseliot,

Thank you for your quick response.

The result of the lspci command is > 0000:01:00.0 0300: 10de:01d7 (rev a1) 
Changing splash into VGA=791 did the trick.
I do get the shutdown messages again, thnx for the tip.
  
Maybe I have to wait with the XGL and compiz until I am more experienced :rolleyes:

Regards

---

### Post by useResa on 2006-09-21
In addition to the items mentioned in the previous post (of which most have been answered), I encountered another problem with the latest Nvidia driver.

When I used my laptop in the docking station, I only can use the monitor when I use the analog input. The digital input shows the start-up and then dies (just before the logon screen), it goes complete black and remains like that.

With the old driver both channels worked ok.
Can anyone help me from banging my head against the wall](*,)
Anyhelp is highly appreciated

---

### Post by tseliot on 2006-09-21
> **useResa said:**
> In addition to the items mentioned in the previous post (of which most have been answered), I encountered another problem with the latest Nvidia driver.

When I used my laptop in the docking station, I only can use the monitor when I use the analog input. The digital input shows the start-up and then dies (just before the logon screen), it goes complete black and remains like that.

With the old driver both channels worked ok.
Can anyone help me from banging my head against the wall](*,)
Anyhelp is highly appreciated

Try adding this to the Section Device of your xorg.conf:
```
Option "UseDisplayDevice" "DFP"
```

---

### Post by useResa on 2006-09-21
Thank you tseliot for your suggestion, I'll try it and will post the reply.

In my previous post you indicated that you could tell me the type when I would post the outcome of the lspci command. Could you please reply to that question? I posted the outcome earlier, it was
> 0000:01:00.0 0300: 10de:01d7 (rev a1)

Thnx in advance and I'll get back with the results

---

### Post by tseliot on 2006-09-21
> **useResa said:**
> Thank you tseliot for your suggestion, I'll try it and will post the reply.

In my previous post you indicated that you could tell me the type when I would post the outcome of the lspci command. Could you please reply to that question? I posted the outcome earlier, it was


Thnx in advance and I'll get back with the results

Your card is a Quadro NVS 110M

---

### Post by eombah on 2006-09-21
> **tseliot said:**
> Try adding this to the Section Device of your xorg.conf:
```
Option "UseDisplayDevice" "DFP"
```

Hi tseliot,

useResa and I are doing this together so I will reply on your suggestion.
It did not solve the problem, instead, the analog output didn't work either.
It seems to me that it is some sort of syncing problem. 
When I am in digital mode, I see the bios, I see Ubuntu booting and then right after the bootup screen disappears, I see the cursor blinking in the top left corner of the screen and then all goes black. The power button of the monitor (a Dell 1907FP) goes from green to orange, I think that indicates that it is not getting any signal.

thanks for your support.

regards, Bart.

---

### Post by AllenGG on 2006-09-21
Hi TS : having the exact same problem, my query : is it the video card at fault ?
card is: 0000:01:00.0 0300: 10de:0343 (rev a1)
(MSI brand, NVidia FX5600)

---

### Post by tseliot on 2006-09-21
> **eombah said:**
> Hi tseliot,

useResa and I are doing this together so I will reply on your suggestion.
It did not solve the problem, instead, the analog output didn't work either.
It seems to me that it is some sort of syncing problem. 
When I am in digital mode, I see the bios, I see Ubuntu booting and then right after the bootup screen disappears, I see the cursor blinking in the top left corner of the screen and then all goes black. The power button of the monitor (a Dell 1907FP) goes from green to orange, I think that indicates that it is not getting any signal.

thanks for your support.

regards, Bart.

> **AllenGG said:**
> Hi TS : having the exact same problem, my query : is it the video card at fault ?
card is: 0000:01:00.0 0300: 10de:0343 (rev a1)
(MSI brand, NVidia FX5600)

I think you should ask on this forum since my experience with DVI monitors is very limited (I don't use them and only my father has a Digital monitor):
[http://www.nvnews.net/vbulletin/forumdisplay.php?f=14](http://www.nvnews.net/vbulletin/forumdisplay.php?f=14)

The nvidia staff will help you there

---

### Post by AllenGG on 2006-09-21
Aha !  thanks TS

---

### Post by eombah on 2006-09-27
Hi,

I solved the problem, see thread at [http://www.nvnews.net/vbulletin/showthread.php?t=67489](http://www.nvnews.net/vbulletin/showthread.php?t=67489) .

So, for the archive, you should add the following line to the Device section of your xorg.conf:

   Option "UseDisplayDevice" "DFP-1"

regards, Bart.

---

