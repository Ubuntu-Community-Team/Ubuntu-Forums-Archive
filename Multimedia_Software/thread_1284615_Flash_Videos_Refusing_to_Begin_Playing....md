---
title: "Flash Videos Refusing to Begin Playing..."
date: 2009-10-06
forum: Multimedia Software
---

### Post by Grimhound on 2009-10-06
I've been experiencing a major pain where Flash videos are refusing to start, instead just staying on the play arrow even after being manually clicked to begin play several times. Is there any knowledge on if there's an effort to fix this?

---

### Post by HappyFeet on 2009-10-06
How did you install it?

---

### Post by Grimhound on 2009-10-06
> **HappyFeet said:**
> How did you install it?

Flash? Through Synaptic.

---

### Post by lovinglinux on 2009-10-06
See **Solution** [*[COLOR="Red"]**FOT004**[/COLOR]*] from the Troubleshooting section of the [**[COLOR="DarkRed"]Firefox optimization and troubleshooting thread[/COLOR]**](http://ubuntuforums.org/showthread.php?t=1193567&highlight=FOT004).

---

### Post by hantechbl on 2009-10-06
> **Grimhound said:**
> I've been experiencing a major pain where Flash videos are refusing to start, instead just staying on the play arrow even after being manually clicked to begin play several times. Is there any knowledge on if there's an effort to fix this?

Same with Me.

---

### Post by lovinglinux on 2009-10-06
> **hantechbl said:**
> Same with Me.

See previous post.

---

### Post by Grimhound on 2009-10-06
> **lovinglinux said:**
> See **Solution** [*[COLOR="Red"]**FOT004**[/COLOR]*] from the Troubleshooting section of the [**[COLOR="DarkRed"]Firefox optimization and troubleshooting thread[/COLOR]**](http://ubuntuforums.org/showthread.php?t=1193567&highlight=FOT004).

It didn't do anything. flashplugin-nonfree was the only thing installed.

---

### Post by HappyFeet on 2009-10-06
Download the .tar.gz flash file from adobe, extract it, and put the **libflashplayer.so** file in ~/.mozilla/plugins

Remove any flash you have first.

---

### Post by lovinglinux on 2009-10-06
> **Grimhound said:**
> It didn't do anything. flashplugin-nonfree was the only thing installed.

I know, but gnash comes installed by default. That's why you see a PLAY symbol. It's gnash taking over the flash content. So run those commands and you should be fine.

---

### Post by Grimhound on 2009-10-06
> **lovinglinux said:**
> I know, but gnash comes installed by default. That's why you see a PLAY symbol. It's gnash taking over the flash content. So run those commands and you should be fine.

I did run it. The result was:
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.

Nothing was removed. Nothing was there to remove. The issue still exists.

---

### Post by lovinglinux on 2009-10-06
> **Grimhound said:**
> I did run it. The result was:
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.

Nothing was removed. Nothing was there to remove. The issue still exists.

Weird.

---

### Post by lovinglinux on 2009-10-06
When you click the play button, does it show a circle with dots (loading)?

---

### Post by Grimhound on 2009-10-06
> **lovinglinux said:**
> When you click the play button, does it show a circle with dots (loading)?

Nope. The button presses, but the button stays and it just remains on that first frame with the play button. However, if the video allows it I can right click and force a Play to get it off that first frame and to begin loading the actual video.

---

### Post by lovinglinux on 2009-10-06
> **Grimhound said:**
> Nope. The button presses, but the button stays and it just remains on that first frame with the play button. However, if the video allows it I can right click and force a Play to get it off that first frame and to begin loading the actual video.

The play arrow is a big one, with a circle around it and a black background or is a small one, without a circle and with the video background?

---

### Post by Grimhound on 2009-10-07
> **lovinglinux said:**
> The play arrow is a big one, with a circle around it and a black background or is a small one, without a circle and with the video background?

I think what I'm getting stuck on is the flash preloader many sites use that then redirects to the video file.

---

### Post by lovinglinux on 2009-10-07
> **Grimhound said:**
> I think what I'm getting stuck on is the flash preloader many sites use that then redirects to the video file.

So I think it could be a network issue, not a flash issue. Try **Solution** [*[COLOR="Red"]**FOT005**[/COLOR]*] from the Troubleshooting section of the [**[COLOR="DarkRed"]Firefox optimization and troubleshooting thread[/COLOR]**](http://ubuntuforums.org/showthread.php?t=1193567&highlight=FOT005).

Also, if you have AdBlock extension installed, replace it with AdBlock Plus.

If you are trying to watch YouTube videos then it could be an YouTube problem. Buffering has been very slow for me today, even stalling sometimes.

---

### Post by Grimhound on 2009-10-07
> **lovinglinux said:**
> So I think it could be a network issue, not a flash issue. Try **Solution** [*[COLOR="Red"]**FOT005**[/COLOR]*] from the Troubleshooting section of the [**[COLOR="DarkRed"]Firefox optimization and troubleshooting thread[/COLOR]**](http://ubuntuforums.org/showthread.php?t=1193567&highlight=FOT005).

Also, if you have AdBlock extension installed, replace it with AdBlock Plus.

If you are trying to watch YouTube videos then it could be an YouTube problem. Buffering has been very slow for me today, even stalling sometimes.

No. It isn't a network issue. It's a flash issue where in-flash commands are ignored or not getting through. When I press on a flash button, nothing happens. I have to go around it by issuing a hard command off of the right click menu that skirts around interfacing with the flash itself. I have no Adblockers, and from the beginning have had nothing that should have interfered with flashplugin-nonfree, even that which you said was supposed to be there.

---

### Post by lovinglinux on 2009-10-07
> **Grimhound said:**
> No. It isn't a network issue. It's a flash issue where in-flash commands are ignored or not getting through. When I press on a flash button, nothing happens. I have to go around it by issuing a hard command off of the right click menu that skirts around interfacing with the flash itself. I have no Adblockers, and from the beginning have had nothing that should have interfered with flashplugin-nonfree, even that which you said was supposed to be there.

Have you tried another browser, to see if the problem persists?

---

### Post by Grimhound on 2009-10-07
> **lovinglinux said:**
> Have you tried another browser, to see if the problem persists?
It persists in Chrome and Firefox.

---

### Post by Grimhound on 2009-10-07
bump

---

### Post by lovinglinux on 2009-10-08
> **Grimhound said:**
> bump

Sorry, I'm out of ideas.

---

