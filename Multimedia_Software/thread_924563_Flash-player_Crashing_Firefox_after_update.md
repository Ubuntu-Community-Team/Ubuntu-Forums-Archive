---
title: "Flash-player Crashing Firefox after update"
date: 2008-09-19
forum: Multimedia Software
---

### Post by Aiello on 2008-09-19
After updating flash player through the Update-Manager, it is continually crashing Firefox. One some pages everything loads fine, while on others Firefox crashes. According to Synaptic, my current version of flash is 10.0.12.10ubuntu1~ppa3. 
Any help would be greatly appreciated.
-Thanks!

---

### Post by Aiello on 2008-09-20
Any ideas?

---

### Post by Aiello on 2008-09-21
Any suggestions at all? Firefox is becoming constantly crashing on pages with flash and becoming nearly unusable.

---

### Post by gandaran on 2008-09-21
why not go back to flash 9 or a more stable flash 10 version
where did you get that flash 10? from the proposed repository?

---

### Post by Aiello on 2008-09-21
I do believe I got it from the repositories. Everything was working perfectly until the update. Any suggestions how I can get back to a more stable version?

---

### Post by gandaran on 2008-09-21
do you have the proposed and backports repos enabled or did you add another repo to synaptic.
flash 10 is only available in the proposed repository and you only enable them if you know what you are doing, many applications there are still unstable.
find out the flash origin is synaptic.

---

### Post by Aiello on 2008-09-21
I remembered I had enabled a user-created repository to get around some of the short comings of Flash 9 (no full-screen, ect). I have disabled this repository and reinstalled Flash 9. Everything seems okay for now.

EDIT: I spoke too soon. I now have the standard Flash 9 installed and Firefox is still crashing like none other. *Sigh*

---

### Post by gandaran on 2008-09-21
if you still would like to use flash 10 , you can install it manually it's easy, but I don't recommend the latest release, I have had some firefox crashes with it, the version before was stable, you just have to find it and download.

---

### Post by gjoellee on 2008-09-21
you don't have the latest flash 10. Download it here: [http://kshoster.net/?c=downloads&h=deb](http://kshoster.net/?c=downloads&h=deb)

---

### Post by gandaran on 2008-09-21
> **Aiello said:**
> EDIT: I spoke too soon. I now have the standard Flash 9 installed and Firefox is still crashing like none other. *Sigh*

heres what I do after a firefox crash, I go in to the hidden home folder, delete the .metacity and .nautilus folders and reboot immediately. seams to work for me.

---

### Post by Aiello on 2008-09-21
If only I could get back to that older version of Flash 10. It worked flawlessly.

---

### Post by gandaran on 2008-09-21
> **Aiello said:**
> If only I could get back to that older version of Flash 10. It worked flawlessly.
I still have it, I usually keep all flash versions in a backup folder
if I could I would send it to you.

---

### Post by Aiello on 2008-09-21
That would be highly appreciated!

---

### Post by gandaran on 2008-09-21
Aiello
      download the flash 10.0.0 d569 here [http://www10.zippyshare.com/v/91012699/file.html](http://www10.zippyshare.com/v/91012699/file.html)
extract the contents to desktop, drag the plugins folder to the hidden home .mozilla folder, thats all you have to do to install, remove the flashplugin-nonfree in synaptic first.
if you'd prefer to install in the root file system, just drag the libflashplayer.so file to /usr/lib/mozilla/plugins.
probably you'll still get the crashes, just delete the .metacity home folder and reboot the computer, in the end this will fix the problem.

---

### Post by joshzam on 2008-09-22
> **gandaran said:**
> Aiello
      download the flash 10.0.0 d569 here [http://www10.zippyshare.com/v/91012699/file.html](http://www10.zippyshare.com/v/91012699/file.html)
extract the contents to desktop, drag the plugins folder to the hidden home .mozilla folder, thats all you have to do to install, remove the flashplugin-nonfree in synaptic first.
if you'd prefer to install in the root file system, just drag the libflashplayer.so file to /usr/lib/mozilla/plugins.
probably you'll still get the crashes, just delete the .metacity home folder and reboot the computer, in the end this will fix the problem.

I'm having the same problem with Firefox crashing and was very eager to try your proposed solution, but the above web site is one of the many pages that caused my browser to crash! I, too, only noticed this behavior start with the most recent Flash update. Any other advice would be much appreciated.

---

### Post by eye208 on 2008-09-22
Have you installed libflashsupport?

---

### Post by gandaran on 2008-09-22
> **joshzam said:**
> I'm having the same problem with Firefox crashing and was very eager to try your proposed solution, but the above web site is one of the many pages that caused my browser to crash! I, too, only noticed this behavior start with the most recent Flash update. Any other advice would be much appreciated.
disable or remove the flash before you visit the website, tools » addons »  plugins » right click the flash plugin enable/disable
remenber after a firefox crash delete the home .metacity and .nautilus folder, reboot imediatly
don't install libflashsupport with flash 10, libflashsupport  makes firefox crash! it's only needed for flash 9 sound problem.

---

### Post by gandaran on 2008-09-22
any one trying my method please let me know if it works
it has worked for me including one time I had serious system crashes, after three crashes and three reboots I got my computer back, working stable to this day except for two firefox crashes with the new flash release which I just fixed going back to the older version

---

### Post by joshzam on 2008-09-22
I'm trying your method. I have:

- disabled the newest Flash plugin to be able to access that web site
- downloaded the penultimate(?) Flash plugin (d569)
- closed Firefox
- uninstalled flashplugin-nonfree via Synaptic
- replaced the libflashplayer.so in the .mozilla plugins folder with the newly downloaded version
- deleted the .metacity home folder
- rebooted(?!)
- found my Firefox still crashing from the same sites as before

For what it's worth, crashing is not the only symptom I've noticed since the latest flashplugin update. I've also noticed that many Flash web animations are either constantly blurry or plagued with black lines after certain animations or frmo me scrolling the page. I can deal with the sub-par quality (thought I don't like it) but the crashing is testing my patience.

Thanks, gandaran, for trying to help. But this hasn't helped me this time.

---

### Post by AntiHeroJoe on 2008-09-22
I'm having the same issue. A few days ago, Update Manager said it had some libflashwhatever updates for me, and I let it do it's thing. Now Firefox just outright crashes on some websites. No error at all, Firefox just disappears along with whatever I was doing.

Is this not a wide-spread enough issue to warrant some kind of follow-up through Update Manager to fix or revert this? I'm really quite surprised by this. Should I not trust what Update Manager pushes to me?

---

### Post by Aiello on 2008-09-22
gandaran, thanks for all your help, but unfortunatly Flash 10 and your solution have not worked for me. I have gone back to Flash 9, which still crashes and some of its features do not work, but it is still much more stable than Flash 10.
I just wish there would be a reliable flash player by now.

---

### Post by eye208 on 2008-09-23
If you run across a site that makes Firefox crash, remove libflashsupport and try again.

I had 100% reproducible crashes due to libflashsupport. As soon as I removed it, Flash 9 became rock solid for me.

---

### Post by joshzam on 2008-09-24
Firefox was updated to 3.0.2 this morning on my Hardy and all seems right again. Flash looks good. No more crashing. Fingers crossed!!!

---

### Post by eye208 on 2008-09-24
Try [http://www.imeem.com/](http://www.imeem.com/). That site used to be a good indicator of Flash (in)stability.

---

### Post by joshzam on 2008-09-26
> **eye208 said:**
> Try [http://www.imeem.com/](http://www.imeem.com/). That site used to be a good indicator of Flash (in)stability.

Yuch, I can see why. But I survived! Solid as a rock. Thank goodness.

---

### Post by gandaran on 2008-09-26
> **joshzam said:**
> Yuch, I can see why. But I survived! Solid as a rock. Thank goodness.

yes, rock solid, firefox 3.0.3 and flash 10.0 r12

---

