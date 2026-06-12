---
title: "Flash 10 Issues"
date: 2008-11-02
forum: Multimedia Software
---

### Post by steveneddy on 2008-11-02
I updated to Flash 10 when it first came out and updated that in September, but I was never able to get any better performance than if I used the stock 

[COLOR=Blue]**flashplugin-nonfree**[/COLOR]

available in the repos.

And if I check the version number in

**about:plugins**

in Firefox 3 it states that the actual Flash version is version 9, r124.

My question:

Is there a way to get true Flash performance in Linux while using FF3 on 64 bit?

My main issue is that if there are multiple Flash on a main web page and there are Flash drop down menus, they drop down **under** the main Flash video.

Very annoying.

Dishnetwork.com and MTV.com are two that come to mind with this issue.

Does anyone have any answer to why this issue still exists and is there any way to resolve this issue?

I use Hardy 8.04 LTS and will not be updating to 8.10 any time soon. 

I need a stable operating environment with as few issues as possible. At the moment the system is stable and reliable and if there are fixes that would make the Flash environment alter my stability, that would not be acceptable, but I would still like to know what these fixes are.

---

### Post by gandaran on 2008-11-02
> in Firefox 3 it states that the actual Flash version is version 9, r124.

you said you updated to flash 10, did you remove the flash 9 first?
it looks as if you still have flash 9 installed!
type **locate libflash** on a terminal/console, post the **full** output here so we can tell you what you have installed for flash

---

### Post by steveneddy on 2008-11-02
> **gandaran said:**
> you said you updated to flash 10, did you remove the flash 9 first?
it looks as if you still have flash 9 installed!
type **locate libflash** on a terminal/console, post the **full** output here so we can tell you what you have installed for flash

I did uninstall Flash 9 during installation of Flash 10.

I suppose that I didn't make it clear that I had actually un-installed Flash 10 and reinstalled flashplugin-nonfree for a more stable environment.

I was just making the observation that the flashplugin-nonfree is actually version 9 and not version 10.

I would actually like to use Flash 10 with FF3 in Linux but would like for it to operate properly, ie. drop down menus dropping down **over** the main Flash video on a web page.

I believe that I am having the same issue at work using XP with FF3 installed in that the drop down menus on a Flash web site drop down under the main Flash video.

I'll need to get to work on Monday to verify this, though.

So is it Firefox having issues with Flash or Flash in Linux?

---

### Post by gandaran on 2008-11-02
> So is it Firefox having issues with Flash or Flash in Linux?
I think flash 10 is the best linux flash to come out, not as good as the windows version but has improved a lot and I have never seen one of those drop-down menu problems you get with flash 9, I could say it's nearly perfect if it wasn't the fact it still uses a lot of cpu resources for playing flash videos.

---

### Post by steveneddy on 2008-11-02
> **gandaran said:**
> I think flash 10 is the best linux flash to come out, not as good as the windows version but has improved a lot and I have never seen one of those drop-down menu problems you get with flash 9, I could say it's nearly perfect if it wasn't the fact it still uses a lot of cpu resources for playing flash videos.

I never really noticed a difference is the way that Flash 9 played Flash videos against Flash 10, but the drop down menu issue is maddening.

---

### Post by steveneddy on 2008-11-02
OK - I reinstalled Flash 10, verified in the FF3 about:plugins page.

Also running nspluginwrapper .0.9.9 from the repos.'

Do I need to try and get nspluginwrapper 1.1.0 to get this issue resolved in Hardy?

Is there an answer for this in Hardy?

---

### Post by steveneddy on 2008-11-02
This must be a Firefox issue because after updating to Flash 10, Opera displays the Flash web pages correctly, or the drop down menus drop down over the main Flash video on the page.

See dishnetwork.com

In FF3 the dropdown menus drop UNDER the main video and in Opera the dropdown menus drop down OVER the video like they were designed to.

---

### Post by gandaran on 2008-11-02
tried dishnetwork.com with firefox, didn't see any problem! looks perfect to me.
> Do I need to try and get nspluginwrapper 1.1.0 to get this issue resolved in Hardy?
sorry I don't know anything about nspluginwrapper, I use the ubuntu 32-bits version, no need for it.

---

### Post by Grams79 on 2008-11-02
I installed the Adobe Flash Player 10 and it is BUGGY!
Sometimes I have to refresh the Firefox browser just to see the movie.

---

### Post by steveneddy on 2008-11-02
> **gandaran said:**
> tried dishnetwork.com with firefox, didn't see any problem! looks perfect to me.

sorry I don't know anything about nspluginwrapper, I use the ubuntu 32-bits version, no need for it.

So FF3, Ubuntu 64 bit with Flash does not work.

Flash 10 in Opera looks good and seems to render correctly. I just hate Opera.

---

