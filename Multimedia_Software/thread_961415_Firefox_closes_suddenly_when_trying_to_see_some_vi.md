---
title: "Firefox closes suddenly when trying to see some video stuff"
date: 2008-10-28
forum: Multimedia Software
---

### Post by Jayhawker on 2008-10-28
Each time i want to check a page with video or direct tv, using last Firefox 3.03, it closes itself without any warning. So, I can't see You tube videos or any video from whatever site you want. 

Please, is there a way to solve that.

---

### Post by Jayhawker on 2008-10-28
Please, I really need a solution because browsing is very hard in this terms

---

### Post by daniel.hodge on 2008-10-28
Your problem may be that a flash plugin is not installed in Firefox. If that's the case...

In the Add/Remove under Applications, make sure the search filter is set to 'All available software". Type flash in the search box. A list of plugins should come up. I used the adobe-non-free plugin. Check the box to the left of it and click apply at the bottom right. It should prompt for a root password. Enter your password and it should download and install the plugin for you.

---

### Post by Jayhawker on 2008-10-28
> **daniel.hodge said:**
> Your problem may be that a flash plugin is not installed in Firefox. If that's the case...

In the Add/Remove under Applications, make sure the search filter is set to 'All available software". Type flash in the search box. A list of plugins should come up. I used the adobe-non-free plugin. Check the box to the left of it and click apply at the bottom right. It should prompt for a root password. Enter your password and it should download and install the plugin for you.

Thank You but no "Adobe-non-free plugin in the box. Any idea, please.

---

### Post by daniel.hodge on 2008-10-28
My fault for not mentioning the correct name. Attached is a screenshot. If your system is running correctly, this is what you should see, minus the checked boxes. I used the highlighted plugin. It may work for you.

---

### Post by Jayhawker on 2008-10-28
> **daniel.hodge said:**
> My fault for not mentioning the correct name. Attached is a screenshot. If your system is running correctly, this is what you should see, minus the checked boxes. I used the highlighted plugin. It may work for you.

Many thanks for all your attention, but it was already istalled in my computer. Can it be another problem

---

### Post by daniel.hodge on 2008-10-28
Nothing I've encountered. Did you have Firefox 2 running, doing the same thing? If so, did it run better? I would suggest switching back to an earlier version. I'm sorry I can't be of much help. I'm fairly new to Ubuntu myself.

---

### Post by envoys on 2008-10-28
I have the same issue within Firefox with the flash player installed. I have to disable Flash Player inside firefox to be able to browse OK, although I don't see any flash videos, which is fine by me. Sometimes it works fine, like browsing youtube, than out of no where, it just closes and I have to open it back up, luckily firefox saves the session, than I go again to the same video that crashed it before and it doesn't crash it after, strange. i will post back my findings when I have time to take a deeper look, but I am pointing it at the adobe flash plugin, I have gnash or something like that on my work computer for flash plugin in firefox and it never crashes.

---

### Post by gandaran on 2008-10-28
get rid of libflashsupport if you have it installed, firefox 3.0.3 and flash 10 work very well, you don't need to install anything else for flash.

---

### Post by zobcat on 2008-10-28
Do you have flash 10? It fixes alot of these problems. 

Go here:
[http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash](http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash)

Download the .deb for Ubuntu. Hopefully that fixes it for you.

---

### Post by kuproverto on 2008-10-28
I'm having the same problem on my main computer which runs Ubuntu 8.04, Firefox 3.03 and the flashplugin-nonfree 9.0.124

On my testbed machine I installed Ubuntu 8.10 RC which comes with Firefox 3.03 and flashplugin-nonfree 10.0.12.36 and all the sites that crashed Firefox before now work fine.

I'd wait until v8.10 is released then install it.

---

### Post by zobcat on 2008-10-28
> **kuproverto said:**
> I'm having the same problem on my main computer which runs Ubuntu 8.04, Firefox 3.03 and the flashplugin-nonfree 9.0.124

On my testbed machine I installed Ubuntu 8.10 RC which comes with Firefox 3.03 and flashplugin-nonfree 10.0.12.36 and all the sites that crashed Firefox before now work fine.

I'd wait until v8.10 is released then install it.

Did anyone try the Flash 10 deb from Adobe's site? I'd hate to wait until Friday's Final Release.

---

### Post by Jayhawker on 2008-10-28
> **gandaran said:**
> get rid of libflashsupport if you have it installed, firefox 3.0.3 and flash 10 work very well, you don't need to install anything else for flash.

Thank You, but no way. I've uninstalled libflashsupport but the problem remains. ¿?

---

### Post by gandaran on 2008-10-28
> **Jayhawker said:**
> Thank You, but no way. I've uninstalled libflashsupport but the problem remains. ¿?
and flash 10 you have it? no other flash applications installed?
just firefox 3.0.3 and adobe flash 10 ! reboot your computer and try again

edit:
you may need java, do you have it? install the sun-java6-plugin and the gstreamer plugins for online wmv play, the gstreamer-ffmpeg plugin could help with the flash problem

---

### Post by Jayhawker on 2008-10-29
> **gandaran said:**
> and flash 10 you have it? no other flash applications installed?
just firefox 3.0.3 and adobe flash 10 ! reboot your computer and try again

edit:
you may need java, do you have it? install the sun-java6-plugin and the gstreamer plugins for online wmv play, the gstreamer-ffmpeg plugin could help with the flash problem

Yes I have Flash 10, and java. But no way at all. The fact a lot of people is having this problem,as I see,maybe is a sign there is a flaw to solve.

---

### Post by whoelse on 2008-10-29
I had the same problem when two different multimedia plugins were installed, vlc and totem in my case, even if one was deactivated. I had to remove the vlc plugin completely, that worked for me.

---

### Post by gandaran on 2008-10-29
> **Jayhawker said:**
> Yes I have Flash 10, and java. But no way at all. The fact a lot of people is having this problem,as I see,maybe is a sign there is a flaw to solve.
no I don't think there is a flaw now, with updated firefox and the last flash 10 release, yes there used to be with firefox 3.0.1 and flash 9 and also the first beta flash 10 versions.
the fact that a lot of people still have problems I think is more due to in trying to get flash working they followed some tutorials and installed a lot of crap which makes it very difficult to fix now.
make a fresh install of ubuntu intrepid 8.10 when it comes out tomorrow and just install the flashplugin-nonfree in synaptic, you'll be running firefox 3.0.3 and flash 10 release, I'll bet you wont have the crashing problem!

are you sure you don't have any other flash version still installed?
there are many ways to install flash and in deferent directory's!

---

### Post by shahgols on 2008-10-29
FWIW, I am running ubuntu 8.0.4.  I installed Flash 10 a few weeks ago.  The problem I was having was that when watching youtube videos, every 2-3 videos, the video would not play.  There would just be a white screen in place of the video basically.  Anyways, I uninstalled flash 9 (had forgotten to do that), and uninstalled libflashsupport and so far it's been smooth.  I hope it stays that way though.

---

