---
title: "Firefox plugins"
date: 2009-08-09
forum: Multimedia Software
---

### Post by jet-san on 2009-08-09
Hi

Today I've removed my Ubuntu 32bit and installed brand new 64bit version.

Everything was fine untill I tried to see some videos in Firefox.
I can see only the huge play sign.
[http://img8.imageshack.us/img8/7674/screenshot1rhh.png](http://img8.imageshack.us/img8/7674/screenshot1rhh.png)
When click on it it change into black square which cover video.
I can't play them.
This is an example of one of those I can't see.
[http://studio.wp.pl/i,skok-do-basenu,mid,738956,wideo.html?ticaid=18893](http://studio.wp.pl/i,skok-do-basenu,mid,738956,wideo.html?ticaid=18893)
I don't know what it contain, so my apologize if it's "bad":)
I can see same grey "play" signs on every add.
When I click them it disappear and I can see advertisement.

Help me!!!!!
Jet

P.S.
Yes, I've got some plugins...
I've just noticed I even have problems with [http://video.google.com/](http://video.google.com/)

---

### Post by Jenkins1 on 2009-08-09
I don't know what plug-ins that you have but sounds like a "flash block" plug-in or a different version of flash installed to the adobe non-free version. I know that I installed a different version and that did give me a button to click. To install the adobe version you need to install the multiverse repository and to install flashplugin-nonfree and flashplugin-installer. Although which version of flash all depends on you opinion of "free" but we will not go into that debate.

---

### Post by digitalsp on 2009-08-09
I sometimes get this too on my 64 bit machine. Usually a reload of the browser or reboot cure things for me. You should maybe try other browsers too. See post to enable flash in [Google Chrome]("http://linux.digitalsp.com/2009/08/enabling-flash-plugin-for-google-chrome.html")

The video clip in your post is awesome - you have to see it...

---

### Post by jet-san on 2009-08-09
> **digitalsp said:**
> The video clip in your post is awesome - you have to see it...

Haha, very funny...

I tried this one
```
$ sudo apt-get install flashplugin-nonfree
```
but doesn't work:/

---

### Post by lovinglinux on 2009-08-09
See **Solution** [*[COLOR="Red"]**FOT004**[/COLOR]*] from the Troubleshooting section of the [**[COLOR="DarkRed"]Firefox optimization and troubleshooting thread[/COLOR]**](http://ubuntuforums.org/showthread.php?t=1193567&highlight=FOT004).

---

### Post by Jenkins1 on 2009-08-09
> **jet-san said:**
> Haha, very funny...

I tried this one
```
$ sudo apt-get install flashplugin-nonfree
```
but doesn't work:/

Go to system > administration > software sources 
then enter your user/sudo password. Then check that the "software restricted by copyright or legal issues (multiverse)" has a tick by it.
Then click "Close" and then "reload". then try sudo apt-get install flashplugin-nonfree.

---

### Post by jet-san on 2009-08-10
> **lovinglinux said:**
> See **Solution** [*[COLOR=Red]**FOT004**[/COLOR]*] from the Troubleshooting section of the [**[COLOR=DarkRed]Firefox optimization and troubleshooting thread[/COLOR]**]("http://ubuntuforums.org/showthread.php?t=1193567&highlight=FOT004").

> **lovinglinux said:**
> **Solution** [*FOT004*]**:**

Some video issues are caused by conflicting plug-ins. It's not a good idea to have multiple plug-ins for the same type of content.

To remove conflicting flash plug-ins and install only the one from Adobe open "Applications >> Accessories >> Terminal", then paste (CTRL+SHIFT+V) the code below in the terminal window and hit enter:

```
sudo apt-get remove swfdec-mozilla
sudo apt-get remove mozilla-plugin-gnash
sudo apt-get remove adobe-flashplugin
sudo apt-get remove flashplugin-nonfree
sudo apt-get install flashplugin-nonfree
```


Thanks, it's working fine now!!!!!!!!!
I can watch videos at last:D

Regards
Jet

---

### Post by lovinglinux on 2009-08-10
> **jet-san said:**
> Thanks, it's working fine now!!!!!!!!!
I can watch videos at last:D

Regards
Jet

You are welcome.

---

