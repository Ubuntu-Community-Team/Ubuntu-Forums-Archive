---
title: "Cant watch any flash videos/youtube"
date: 2009-12-25
forum: Multimedia Software
---

### Post by kawana on 2009-12-25
My sister has ubunut on her laptop and it just randomly stopped playing youtube videos, or really all videos in general. It keeps saying that we need to install a flash plugin but no matter what I do i cant install it. ive tried manually installing them but no luck. Ive tried deleting the old flash player and reinstalling it but it doesn't work. Any ideas what the problem might be?

---

### Post by lovinglinux on 2009-12-25
See **Solution** [*[COLOR="Red"]**FOT004**[/COLOR]*] from the Troubleshooting section of the [**[COLOR="DarkRed"]Firefox optimization and troubleshooting thread[/COLOR]**](http://ubuntuforums.org/showthread.php?t=1193567&highlight=FOT004).

---

### Post by HappyFeet on 2009-12-25
Uninstall the flash plugin, then do:
```
sudo apt-get clean && sudo apt-get autoremove
```
Then go [here]("http://get.adobe.com/flashplayer/?promoid=DXLUJ") and download the .deb file for ubuntu 8.04+

---

### Post by kawana on 2009-12-25
> **HappyFeet said:**
> Uninstall the flash plugin, then do:
```
sudo apt-get clean && sudo apt-get autoremove
```Then go [here]("http://get.adobe.com/flashplayer/?promoid=DXLUJ") and download the .deb file for ubuntu 8.04+

Thanks that worked, but i just noticed that her browser is really laggy. when scrolling up and down its all jerky andnot smooth. and when typing it takes awhile for the computer to catch up. its not an old computer, its pretty new and doesn't hardly have anything on it. Also videos are really laggy. Any ideas as to the cause of the problem?

---

### Post by HappyFeet on 2009-12-25
Did you install any video drivers? Are you using compiz?

---

