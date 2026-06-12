---
title: "Screen Resolution problems"
date: 2009-06-02
forum: Multimedia Software
---

### Post by felinoel on 2009-06-02
I am used to a screen resolution of 1280x1024 and for some reason I can't get back to it and am at half that size, which is odd because its the same driver and it worked before? It is NVIDIA accelerated graphics driver version 180, maybe my video card got fried or something? Is there any other way besides proprietary driver to get my old resolution back?

---

### Post by MichaelSammels on 2009-06-02
Are you using nVidia Settings? This can be installed via the Terminal:

```
sudo apt-get install nvidia-settings
```

And this runs it:
```
sudo nvidia-settings
```

---

### Post by felinoel on 2009-06-02
> **MichaelSammels said:**
> Are you using nVidia Settings? This can be installed via the Terminal:

```
sudo apt-get install nvidia-settings
```

And this runs it:
```
sudo nvidia-settings
```
Yes, and I even did the above regardless and it still only has 640x480 as the highest res.


An oddity though, when I go to my login screen it appears to have a high res there, almost as high as 1280x1024 if not higher, is that possible to have it be the right res there and the wrong one in my login?

---

### Post by felinoel on 2009-06-02
And in the nvidia settings there is a place to manually enter a screen res, when I enter 1280x1024 it does not work, if needed I can try it again to get the exact error message

---

### Post by felinoel on 2009-06-02
> **felinoel said:**
> And in the nvidia settings there is a place to manually enter a screen res, when I enter 1280x1024 it does not work, if needed I can try it again to get the exact error message

.

---

### Post by felinoel on 2009-06-03
> **felinoel said:**
> .

.

---

### Post by overdrank on 2009-06-03
Hi and how did you install the nvidia drivers?
Have you tried to reinstall the drivers?

---

### Post by felinoel on 2009-06-03
I used the Hardware Drivers thing under System > Admin.
I think I did, wasn't that what MichaelSammels had me do?

---

### Post by felinoel on 2009-06-03
.

---

### Post by felinoel on 2009-06-04
> **felinoel said:**
> .

.

---

### Post by overdrank on 2009-06-05
> **felinoel said:**
> I used the Hardware Drivers thing under System > Admin.
I think I did, wasn't that what MichaelSammels had me do?

Hi and no, that was the nvidia-settings. When you use the nvidia-setting you can not change your resolution?

Edit I see from your other thread you  have a 
00:05.0 VGA compatible controller: nVidia Corporation C51 [GeForce 6150 LE] (rev a2)

You may also try and boot into recovery mode and use xfix to correct the graphics.
Recovery mode is usually the second choice from the grub when booting and you should be given 4 options which one is xfix. After xfix is complete you should be given the 4 options again and choose to boot normally.

---

### Post by felinoel on 2009-06-05
> **overdrank said:**
> Hi and no, that was the nvidia-settings. When you use the nvidia-setting you can not change your resolution?

Edit I see from your other thread you  have a 
00:05.0 VGA compatible controller: nVidia Corporation C51 [GeForce 6150 LE] (rev a2)

You may also try and boot into recovery mode and use xfix to correct the graphics.
Recovery mode is usually the second choice from the grub when booting and you should be given 4 options which one is xfix. After xfix is complete you should be given the 4 options again and choose to boot normally.Well I can, but not the the resolutions it once was able to reach.

When I am in the recovery mode what do I do? I just tell xfix to run?

---

### Post by felinoel on 2009-06-06
> **felinoel said:**
> .

.

---

### Post by overdrank on 2009-06-06
Ok at what point did you stop being able to access the resolution of 1280x1024?
Was it after some updates or upgrade?
I assume it is after the upgrade to Jaunty 9.04 you mention in your other thread. 

> **felinoel said:**
> Well I can, but not the the resolutions it once was able to reach.

When I am in the recovery mode what do I do? I just tell xfix to run?
What resolutions are presented by nvidia-settings for you to choose?

When you are in recovery mode you should have been given 4 choices and the last one is xfix and you select it. **I believe you will not have to use xfix as you have access to the nvidia-settings**.
You may also look at [X/Config/Resolution]("https://wiki.ubuntu.com/X/Config/Resolution")

---

### Post by felinoel on 2009-06-06
> I had gotten a notification a couple days ago to install some updates, I did, then it told me to restart and after I had it restart my proprietary drivers weren't working, those are for my speakers and screen resolution, now I have no audio and my screen is at 640x480 a size I am way not used to and have a difficult time using due to such; I have tried since then to reinstall them but have failed.

Any thoughts on what my problem could be?> 
Updating the system made it notice the proprietary drivers, but the screen resolution is so small I can't click anything to install these proprietary drivers.

My audio is working fine now, but my old screen resolutions are gone? Its still too tiny to get anything done, which is odd because its the same driver and it worked before? It is NVIDIA accelerated graphics driver version 180, maybe my video card got fried or something?> I am used to a screen resolution of 1280x1024 and for some reason I can't get back to it and am at half that size, which is odd because its the same driver and it worked before? It is NVIDIA accelerated graphics driver version 180, maybe my video card got fried or something? Is there any other way besides proprietary driver to get my old resolution back?No it was before 9.04, I think I was two version behind and I was installing some updates it said I had and it stopped working, thats when I updated to 9.04 and thats when it noticed my proprietary drivers again.

---

### Post by felinoel on 2009-06-06
> **overdrank said:**
> What resolutions are presented by nvidia-settings for you to choose?Ones that are below 640x480

> When you are in recovery mode you should have been given 4 choices and the last one is xfix and you select it. **I believe you will not have to use xfix as you have access to the nvidia-settings**.
You may also look at [X/Config/Resolution]("https://wiki.ubuntu.com/X/Config/Resolution")
I see, maybe I accessed it wrong?

---

### Post by felinoel on 2009-06-06
> **overdrank said:**
> When you are in recovery mode you should have been given 4 choices and the last one is xfix and you select it. **I believe you will not have to use xfix as you have access to the nvidia-settings**.
You may also look at [X/Config/Resolution]("https://wiki.ubuntu.com/X/Config/Resolution")

When I ran xfix and then resume startup, when a whole bunch of test flashed by my screen it said nvidia failed as well as virtualbox failed, which would explain why my virtualbox hasn't been working...

Anyways it is now back to a tolerable resolution, but it says no proprietary drivers are installed, won't let me install the nvidia proprietary drivers, and my audio is gone again... :confused:

---

### Post by felinoel on 2009-06-06
I left my computer, shutting it down, then later I came back to it... and now its working fine? :confused:

Ummm thanks for the help... I think?

Oh well, now I can try to get my VirtualBox working.

---

