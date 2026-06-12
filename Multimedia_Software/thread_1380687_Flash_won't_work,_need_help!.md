---
title: "Flash won't work, need help!"
date: 2010-01-13
forum: Multimedia Software
---

### Post by SchizmWolf on 2010-01-13
I've just installed Xubuntu 8.04 Hardy on two older PCs. One of them I got to work fine, and the other one... well, flash doesn't work no matter what I do. I've tried all the following:
```
 
sudo apt-get install ubuntu-restricted-extras

sudo apt-get install xubuntu-restricted-extras

sudo apt-get install -f

sudo apt-get install flashplugin-nonfree

sudo rm -rf /.macromedia | sudo ln -s /dev/null /.macromedia

```

I'm running out of ideas here, guys, and it's stressing me out because this is my family's computer and I leave for college in two days. I'm afraid that if I don't get this problem resolved before I leave, they'll be calling me every five minutes until it IS fixed. Whether or not I'm the one who fixes it.

Please, I'm grasping at straws!

---

### Post by boriskarloffinablender on 2010-01-14
what make is the pc?

---

### Post by SchizmWolf on 2010-01-14
> **boriskarloffinablender said:**
> what make is the pc?

It's a Gateway from 2003 or 2004. It's got about 256mB RAM and somewhere around 1.4 Ghz processor. That's all I've got for system specs at the moment, though I could get more when I'm off work.

---

### Post by Dennis N on 2010-01-14
Did you check in Firefox to see if any flash plugin is being detected?

Type into the Firefox address window:
```
about:plugins
```

---

### Post by SchizmWolf on 2010-01-14
> **Dennis N said:**
> Did you check in Firefox to see if any flash plugin is being detected?

Type into the Firefox address window:
```
about:plugins
```

From what I saw, it didn't have any flash plugins, which seemed odd to me. It DID have about a dozen different java plugins, but I didn't see flash with a cursory glance. 
Also, as a side not, I updated firefox on the offchance it was the pre-installed version of firefox. No dice.

---

### Post by PRC09 on 2010-01-14
Have you tried the .deb from Adobe page.It has always worked for me in the past....


[http://get.adobe.com/flashplayer/thankyou/?installer=Flash_Player_10_for_Linux_(.deb](http://get.adobe.com/flashplayer/thankyou/?installer=Flash_Player_10_for_Linux_(.deb))

---

### Post by boriskarloffinablender on 2010-01-14
> **SchizmWolf said:**
> It's a Gateway from 2003 or 2004. It's got about 256mB RAM and somewhere around 1.4 Ghz processor. That's all I've got for system specs at the moment, though I could get more when I'm off work.

hmmm, so it's not because it's a ppc then. i 2nd the guy above me who suggests the deb. that's what i always use on 32 bit. never had a problem.

---

### Post by Dennis N on 2010-01-14
> **SchizmWolf said:**
> From what I saw, it didn't have any flash plugins, which seemed odd to me.

The plugin would be called 'Shockwave Flash' if it's detected.

Try installing the .deb package from the Adobe website as suggested above and see it that is detected by Firefox and works. That package is Flash ver. 10. The one in the main Hardy repos is still really Flash ver 9 and won't work on sites needing Flash ver 10 (such as Hulu does now). 

If you use Firefox 3.0.17 and it's still not detected, it's probably because the .deb installer put it into the wrong directory where Firefox is not configured to look. 

(I found that to be the case with 32 bit Ubuntu 8.04 and ended up copying the adobe web site version from /usr/lib/adobe-flashplugin into /usr/lib/flashplugin-nonfree and that worked.)

---

### Post by SchizmWolf on 2010-01-17
> **PRC09 said:**
> Have you tried the .deb from Adobe page.It has always worked for me in the past....


[http://get.adobe.com/flashplayer/thankyou/?installer=Flash_Player_10_for_Linux_(.deb]("http://get.adobe.com/flashplayer/thankyou/?installer=Flash_Player_10_for_Linux_%28.deb"))

That's how I installed it in the first place - that's why I'm so puzzled o.O I'll need to see if I can go to the mozilla website and manually get FF4, because I'm not entirely sure that the update I ran on it earlier got the newest version.

---

