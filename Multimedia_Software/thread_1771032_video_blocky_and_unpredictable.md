---
title: "video blocky and unpredictable"
date: 2011-05-29
forum: Multimedia Software
---

### Post by GlennW on 2011-05-29
Every since an upgrade to 11.04 via fresh install, much video playback (primarily vimeo and metacafe) are blocky. See attached screenshot. The blocks flash and move around the screen somewhat and basically make the clip unwatchable.

Any thoughts on the matter?

Regards......

---

### Post by lovinglinux on 2011-05-30
Install [Flash-Aid](https://addons.mozilla.org/en-US/firefox/addon/flash-aid/) and run the extension wizard. It will detect installed flash plugins, remove them and install the best option according to your system architecture and version. Additionally, it will apply some tweaks that should improve performance and fix common issues.

Additionally, you may like [FlashVideoReplacer]("https://addons.mozilla.org/en-US/firefox/addon/flashvideoreplacer/"), which allows to watch Vimeo, Metacafe, YouTube, Ustream and Blipt.tv with a different plugin. I recommend gecko-mediaplayer. But if you want to use Totem, then you need to modify an option in the extension preferences to make it work. See documentation at [http://www.webgapps.org/add-ons/flashvideoreplacer/documentation](http://www.webgapps.org/add-ons/flashvideoreplacer/documentation)

---

### Post by GlennW on 2011-05-30
Thanks lovinglinux for your assistance in this case. I checked using the same video clips that caused the problems and although the video controls flicker when the cursor hovers over them, there are no black blocks obscuring the clip itself.

Best regards.

---

### Post by lovinglinux on 2011-05-30
> **GlennW said:**
> Thanks lovinglinux for your assistance in this case. I checked using the same video clips that caused the problems and although the video controls flicker when the cursor hovers over them, there are no black blocks obscuring the clip itself.

Best regards.

You are welcome.

---

### Post by NoBugs! on 2011-05-31
What graphics card is it? I noticed 11 had problems with ATI, while 10.04 lts had run fine.

---

### Post by HDTimeshifter on 2011-06-05
> **lovinglinux said:**
> Install [Flash-Aid](https://addons.mozilla.org/en-US/firefox/addon/flash-aid/) and run the extension wizard. It will detect installed flash plugins, remove them and install the best option according to your system architecture and version. Additionally, it will apply some tweaks that should improve performance and fix common issues.

Additionally, you may like [FlashVideoReplacer]("https://addons.mozilla.org/en-US/firefox/addon/flashvideoreplacer/"), which allows to watch Vimeo, Metacafe, YouTube, Ustream and Blipt.tv with a different plugin. I recommend gecko-mediaplayer. But if you want to use Totem, then you need to modify an option in the extension preferences to make it work. See documentation at [http://www.webgapps.org/add-ons/flashvideoreplacer/documentation](http://www.webgapps.org/add-ons/flashvideoreplacer/documentation)

I had the blocks (but in white) as well.  Flash-aid didn't help, but the flashvideoreplacer did.

---

### Post by HDTimeshifter on 2011-06-18
Now I have a problem with YouTube.  It works when it's embedded on other sites and forums, but if I go directly to the YouTube site, it fails to play and I get this error:  "Could not open location; you might not have permission to open the file."

---

### Post by lovinglinux on 2011-06-18
> **HDTimeshifter said:**
> Now I have a problem with YouTube.  It works when it's embedded on other sites and forums, but if I go directly to the YouTube site, it fails to play and I get this error:  "Could not open location; you might not have permission to open the file."

Clear the cookies. If that doesn't help, try to block YT cookies.

---

### Post by HDTimeshifter on 2011-06-18
I removed the YT cookie, but no help.  How do you block cookies in Firefox?  I don't see a setting for that in Preferences.

---

### Post by lovinglinux on 2011-06-18
> **HDTimeshifter said:**
> I removed the YT cookie, but no help.  How do you block cookies in Firefox?  I don't see a setting for that in Preferences.

In the Privacy tab, next to "Accept cookies..." there is an "Exceptions" button. Click that and add a rule to block youtube.com. TRemove the rule if it doesn't help, then try to disable hardware acceleration, by right-clicking the video and selecting "Settings".

---

### Post by HDTimeshifter on 2011-06-18
There is no Exceptions button in Privacy in FF 4.0.1 (I've attached a screen shot).

---

### Post by lovinglinux on 2011-06-18
> **HDTimeshifter said:**
> There is no Exceptions button in Privacy in FF 4.0.1 (I've attached a screen shot).

It only shows up when you set to "Use custom settings for history"

---

### Post by HDTimeshifter on 2011-06-18
Thanks - blocking seems to have fixed the problem.

However, there is one video that requires a login (to verify age at least eighteen), but it won't allow logins without cookies, and it didn't work when I did allow cookies.

---

### Post by lovinglinux on 2011-06-18
> **HDTimeshifter said:**
> Thanks - blocking seems to have fixed the problem.

However, there is one video that requires a login (to verify age at least eighteen), but it won't allow logins without cookies, and it didn't work when I did allow cookies.

You can try my [FlashVideoReplacer]("http://www.webgapps.org/add-ons/flashvideoreplacer") extension.

---

### Post by HDTimeshifter on 2011-06-18
Already installed Flashvideoreplacer to fix the macro blocking problem.  Is there a way to select Flash to play the video?  Maybe old Flash will work in this case.

> **HDTimeshifter said:**
> I had the blocks (but in white) as well.  Flash-aid didn't help, but the flashvideoreplacer did.

---

### Post by lovinglinux on 2011-06-18
> **HDTimeshifter said:**
> Already installed Flashvideoreplacer to fix the macro blocking problem.  Is there a way to select Flash to play the video?  Maybe old Flash will work in this case.

Oops, sorry. Right-click the FlashVideoReplacer icon and it will disable the add-on and reload the video you are watching with Flash.

---

### Post by HDTimeshifter on 2011-06-18
The play icon in the middle of the video?  It only shows view/copy/save/etc. image options - nothing about disabling the add-on.

---

### Post by HDTimeshifter on 2011-06-18
Ok, found how to disable it through the preferences and now it works.  Have to restart FF to disable or enable it.

---

### Post by lovinglinux on 2011-06-18
> **HDTimeshifter said:**
> The play icon in the middle of the video?  It only shows view/copy/save/etc. image options - nothing about disabling the add-on.

> **HDTimeshifter said:**
> Ok, found how to disable it through the preferences and now it works.  Have to restart FF to disable or enable it.

No, the icon added to your navigation toolbar. If you can't see it, right-click on any toolbar, select Customize, then drag the FVR icon to a toolbar.

---

### Post by HDTimeshifter on 2011-06-18
Yeah, I found that icon afterwards, but right clicking pulls up the Gnome toolbar menu, but if I left click I get the FVR preferences menu - however there is no option to disable it.  I did find the option to autoplay, so it works like Flash again instead of having to press play to start a video.

---

### Post by lovinglinux on 2011-06-18
> **HDTimeshifter said:**
> Yeah, I found that icon afterwards, but right clicking pulls up the Gnome toolbar menu, but if I left click I get the FVR preferences menu - however there is no option to disable it.  I did find the option to autoplay, so it works like Flash again instead of having to press play to start a video.

Oops, sorry again. I am doing a lot of coding between replies, so I guess my brain is just overloaded. I meant middle-click :oops:

---

### Post by HDTimeshifter on 2011-06-19
Oh, always forget about the middle button - sneaky.  Much more convenient than going all the way through the FF preferences and restarting FF.

---

### Post by lovinglinux on 2011-06-19
> **HDTimeshifter said:**
> Oh, always forget about the middle button - sneaky.  Much more convenient than going all the way through the FF preferences and restarting FF.

Indeed. Keep in mind that if you disable a site in the preferences, it won't be enabled when you middle-click the toolbar icon.

---

### Post by HDTimeshifter on 2011-06-19
Yes, and I like the fact that middle clicking is more of a temporary disable.

Thanks - this is the best support I've received on the forums.  I just wish they would fix Flash - it seems to break every other release, and can't believe Flash 64 is still beta when 64-bit Ubuntu has been around for at least 2.5 years.

---

### Post by lovinglinux on 2011-06-19
> **HDTimeshifter said:**
> Yes, and I like the fact that middle clicking is more of a temporary disable.

Thanks - this is the best support I've received on the forums.  I just wish they would fix Flash - it seems to break every other release, and can't believe Flash 64 is still beta when 64-bit Ubuntu has been around for at least 2.5 years.

You are welcome and thanks for the compliment.

Adobe doesn't care about Linux users. They even announced this week they will stop the development of Adobe Air for Linux and it seems the next generation of Adobe Reader also won't be supported. Fortunately, Mozilla is implementing PDF support directly on Firefox. Nobody cares about Adobe Air anyway.

---

### Post by HDTimeshifter on 2011-06-20
I've never even heard of Adobe Air.

Adobe becoming like MS.  IE9 sucks so bad even on Windows 7 with so much incompatibility that we're using FF and Chrome at work more than IE on Windows.  I hope Google Chrome OS really threatens MS dominance and complacency.  I have dual boot drives for Ubuntu and Win7, but only boot to Windows once in a blue moon to test for incompatibility - I can back up files from Linux to my Win disk, but Windows can't see my Linux disk, so that's more reason to stay in Linux.

Back on topic - I uninstalled FlashAid, since it didn't seem to do anything for me, but then videos stopped loading (even for FVR) - I would get a blank screen, so I reinstalled it.

---

### Post by lovinglinux on 2011-06-20
> **HDTimeshifter said:**
> Back on topic - I uninstalled FlashAid, since it didn't seem to do anything for me, but then videos stopped loading (even for FVR) - I would get a blank screen, so I reinstalled it.

That is weird, because Flash-Aid doesn't interact with flash, unless you run the script wizard.

---

