---
title: "Flash Player Plugin problems"
date: 2013-04-01
forum: Multimedia Software
---

### Post by chrish8786 on 2013-04-01
Wherever I search for assistance I find hordes of users with the same inexplicable problems. Firefox just goes into a never ending search for plugins to install. Ubuntu Software Centre says the Flash Player Plugin is already installed. I can download a file tar.gz whatever that is. In Gates world I would just push a run button, but cannot find anyone in Ubuntu who will give a straight answer on what to do with the file. This is 2013. What sort of Operating System doesn't want to allow users to watch YouTube? Seriously Ubuntu, get your act together, this is ridiculous !!!!

---

### Post by carl4926 on 2013-04-01
> **chrish8786 said:**
> Wherever I search for assistance I find hordes of users with the same inexplicable problems. Firefox just goes into a never ending search for plugins to install. Ubuntu Software Centre says the Flash Player Plugin is already installed. I can download a file tar.gz whatever that is. In Gates world I would just push a run button, but cannot find anyone in Ubuntu who will give a straight answer on what to do with the file. This is 2013. What sort of Operating System doesn't want to allow users to watch YouTube? Seriously Ubuntu, get your act together, this is ridiculous !!!!
Install Chrome Browser from Google and all will be well

Flash Player support in Linux was dropped by Adobe, it has nothing to do with Ubuntu.

---

### Post by chrish8786 on 2013-04-02
Thank you carl4926 for trying. The Chromium Browser insists that 'The Adobe Flash Player is required for video playback'. The prescribed workaround for this problem is to load Flash through Firefox. Which doesn't work. Compatibility of Flash Player with Ubuntu has everything to do with Ubuntu. If the operating system, ie Ubuntu, will not allow this user to watch Youtube then the operating system, ie Ubuntu, must go. Just by the way, I prefer Chromium as a browser and there are Flash Player problems with my laptop today as well. Good Luck.

---

### Post by QIII on 2013-04-02
Hello!

Adobe has stopped providing support for Linux -- not just Ubuntu.

The relationship is not one of Ubuntu failing to support Flash.  It is the other way around.  There is nothing that the distributors of any Linux distro can do.

---

### Post by chrish8786 on 2013-04-02
Thank you QIII for your attempt. Am I to understand that you no longer enjoy Youtube out of loyalty to Linux distro's?

---

### Post by ibjsb4 on 2013-04-02
Ubuntu 12.04 has Flash and is supported to 2017 :)

---

### Post by carl4926 on 2013-04-02
I said Chrome
Not Chromium

Ubuntu have not added the Pepper flash plugin for chromium yet
Only Chrome will provide it:
[https://www.google.com/intl/en_uk/chrome/browser/?hl=en-GB](https://www.google.com/intl/en_uk/chrome/browser/?hl=en-GB)

---

### Post by QIII on 2013-04-02
> **chrish8786 said:**
> Thank you QIII for your attempt. Am I to understand that you no longer enjoy Youtube out of loyalty to Linux distro's?

No, you are not to understand that.  If I had a burning desire to watch something on YouTube that required Flash and that did not work on Linux, I would use one of my Windows machines.  But since I haven't encountered any problems with Flash, that has been unnecessary to date.

---

### Post by carl4926 on 2013-04-02
> **chrish8786 said:**
> Thank you QIII for your attempt. Am I to understand that you no longer enjoy Youtube out of loyalty to Linux distro's?

No. I think you are being a little patronizing 

In any case. Youtube works for me in firefox with the flash player installed...

---

### Post by chrish8786 on 2013-04-02
'Ubuntu 12.04 has Flash and is supported to 2017'
Thank you ibjsb4. That is more like what I want to hear. Now if I can figure out how to get it working again???

---

### Post by chrish8786 on 2013-04-02
> **carl4926 said:**
> No. I think you are being a little patronizing 

In any case. Youtube works for me in firefox with the flash player installed...

I don't like being the poor relation in anybody's double standard. Is there a good reason why you are trying to pick a fight on QIII's behalf? I just want my Flash Player working again. The Ubuntu Software Centre offers Chromium as a browser, NOT Chrome. I don't know how to install Chrome. I also don't know if it is a good idea.

---

### Post by carl4926 on 2013-04-02
> **chrish8786 said:**
> I don't like being the poor relation in anybody's double standard. Is there a good reason why you are trying to pick a fight on QIII's behalf? I just want my Flash Player working again. The Ubuntu Software Centre offers Chromium as a browser, NOT Chrome. I don't know how to install Chrome. I also don't know if it is a good idea.

No fight intended. Peace.

Download and click/double click - follow the prompts
It's widely used and safe

---

### Post by chrish8786 on 2013-04-02
> **carl4926 said:**
> No fight intended. Peace.

Download and click/double click - follow the prompts
It's widely used and safe

Thank you. Yes that worked and was straightforward. Hooray, I have audio and visual again, but only in Chrome. Both Firefox and Chromium Browsers were working properly in the last few days, does anyone know how to fix them?

---

### Post by carl4926 on 2013-04-02
Make sure you are up to date

```
sudo apt-get update && upgrade
```

---

### Post by chrish8786 on 2013-04-02
> **carl4926 said:**
> Make sure you are up to date

```
sudo apt-get update && upgrade
```

OK, ran that. Got response 

'Fetched 1,907 kB in 8s (228 kB/s)                                              
Reading package lists... Done
upgrade: command not found'

No fix, Firefox still wants an Adobe Flash Player to play video.

---

### Post by carl4926 on 2013-04-02
Just try

```
sudo apt-get upgrade
```

---

### Post by chrish8786 on 2013-04-02
> **carl4926 said:**
> Just try

```
sudo apt-get upgrade
```

OK, ran that and got
'Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.'

No fix for Firefox. Thanks for trying.

---

### Post by carl4926 on 2013-04-02
Well, looks like you'll have to use Chrome.
Not sure why some have this trouble. I have a bunch of Linux machines and all have flash working in Firefox

---

### Post by ManamiVixen on 2013-04-02
[B]NOBODY ASKED THE OBVIOUS QUESTION?!?!?

[/B] 				 				 					 						 	[**[COLOR=#000000]chrish8786[/COLOR]**]("http://ubuntuforums.org/member.php?u=1799682") What are your computers specs? Specifically your CPU.

---

### Post by carl4926 on 2013-04-02
> **chrish8786 said:**
> OK, ran that. Got response 

'Fetched 1,907 kB in 8s (228 kB/s)                                              
Reading package lists... Done
upgrade: command not found'

No fix, Firefox still wants an Adobe Flash Player to play video.


FYI, my bad, it should be
```
[FONT=consolas]sudo apt-get update && sudo apt-get upgrade[/FONT]
```

But you seem up to date.

If chrome is playing Youtube I guess your graphics tec are OK

---

### Post by chrish8786 on 2013-04-02
> **ManamiVixen said:**
> [B]NOBODY ASKED THE OBVIOUS QUESTION?!?!?

[/B]                                                                                     [**[COLOR=#000000]chrish8786[/COLOR]**]("http://ubuntuforums.org/member.php?u=1799682") What are your computers specs? Specifically your CPU.

I am running an Intel i5. Have switched to onboard graphics because the graphics card died and all working well. Can you tell me why this is an obvious question? Thanks.

---

### Post by ManamiVixen on 2013-04-02
Oh. On older CPU's, like Early P4's or Athlon XP's, later versions of flash player 11.2 will not run due to the fact older CPU's are missing SSE2 instructions which is required by the newer versions of flash. But seeing as you have a modern CPU, that rules out that possibility as to why flash isn't working.

---

### Post by deadflowr on 2013-04-02
To the OP, how did you originally install flash?

In firefox there,at one point, was an add-on called flash-aid.
See if it's still there install it and let it figure out the flash problems you're having.

Or a simple thing to test out is to switch the flash versions running in chrome
.
To do so, enter
```
chrome://plugins
``` 
In the address bar.
click on the details button at the top right.
scroll down the list of plugins.
locate the shockwave flash plugin.
If flash is installed on the system ,then there will be two flash choices, both will be flagged with a disable button.
Disable the one marked 11.6-something.
load a youtube page and see if runs using the flash version 11.2, which is what should run if you disable flash 11.6.
If not, no harm, simply re-enable the 11.6 version.

---

### Post by ewr2san on 2013-05-13
sudo apt-get install flashplugin-installer 

That works on ubuntu 13.04 64bit for me.

---

### Post by crummychrome on 2013-05-13
a lil off topic, but in the subject range i guess?...

I've been having problems with flash in chat like tinychat.com...used to have problems with stickam.com before they shutdown. maybe my system is old, I don't know the cause...

I have a dell dimension c521 with 2ram and hardly any mem..
I try to chat on tiny chat - its fine. But when I try to broadcast my camera, i get stuck at the below picture without being able to choose options to accept flash..(?)
[[IMG]http://img838.imageshack.us/img838/355/screenshotfrom201305131.png[/IMG]]("http://imageshack.us/photo/my-images/838/screenshotfrom201305131.png/")

Uploaded with [ImageShack.us]("http://imageshack.us")

Now i've been able to change these settings through the chrome browser, but not chromium or firefox. is it something to do with shockwave? should i install something else? I have no clue...

---

### Post by CraigPid on 2013-05-14
You can always just go to the flash download site and get it.They may have dropped support for Linux but they still offer a download of 11.2. If you read the instructions it will tell you the proper place to extract the files to.
    Craig

---

### Post by MikeFlint on 2013-06-16
My Flash player stopped working in Chromium after a recent upgrade last week (on 12.04).  I went to the plugins page and *disabled* the 11.2 Flash Player plugin ... and Flash is now working again.  Know idea what's playing Flash now.

btw, Opera never seems to have issues with Flash, so that's a good fallback.

---

