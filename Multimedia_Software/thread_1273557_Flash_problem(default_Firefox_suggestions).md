---
title: "Flash problem(default Firefox suggestions)"
date: 2009-09-23
forum: Multimedia Software
---

### Post by shahab.fm on 2009-09-23
I have a question regarding flash on Ubuntu 32 bit. The problem is that when I install the flash from Adobe, everything is working fine. But if only I do listen to what Firefox says I am missing(when flash is not installed), then it will just work with Youtube and other flash based stuffs(like buttons on websites , ...) wont work !!! I should say it is the one that actually works as a flash blocker as well and you should click on the flash to play it ...|

My question is that does anyone know what Firefox installs on Ubuntu that messes everything up ? I want to un-install them and see if it would work ... I really don't want to re-install my computer again :( I already tried disabling the plugin under Firefox but didnt work ...

---

### Post by RedRat on 2009-09-23
I had to do a reinstall of FF3 recently. I had installed Adobe FP from the repos and could not get it to work. I queried help on this and was told that the Adobe Flash Player in the repos is "borked" and to use the one from Adobe. I uninstalled the one I had and installed the one from the Adobe site and that worked. Note that I too run 8.04 Hardy.

As to your question about other things installed, it might just be "NoScript" or you might want to check your Preferences to ensure that "Allow Java Script" to function.

---

### Post by lovinglinux on 2009-09-23
> **shahab.fm said:**
> I have a question regarding flash on Ubuntu 32 bit. The problem is that when I install the flash from Adobe, everything is working fine. But if only I do listen to what Firefox says I am missing(when flash is not installed), then it will just work with Youtube and other flash based stuffs(like buttons on websites , ...) wont work !!! I should say it is the one that actually works as a flash blocker as well and you should click on the flash to play it ...|

My question is that does anyone know what Firefox installs on Ubuntu that messes everything up ? I want to un-install them and see if it would work ... I really don't want to re-install my computer again :( I already tried disabling the plugin under Firefox but didnt work ...

I don't understand your post. Are you saying you were happier before installing flash from Adobe and want to revert to that condition?

If your answer is yes, then simply uninstall the flash player from Adobe, because I believe you already have gnash installed.

```
sudo apt-get remove flashplugin-nonfree adobe-flashplugin
```

If you don't want to go back, just fix the Adobe plugin then run this:

```
sudo apt-get remove swfdec-mozilla
sudo apt-get remove mozilla-plugin-gnash
sudo apt-get remove adobe-flashplugin
sudo apt-get remove flashplugin-nonfree
sudo apt-get install flashplugin-nonfree
```

---

### Post by shahab.fm on 2009-09-23
> **lovinglinux said:**
> I don't understand your post. Are you saying you were happier before installing flash from Adobe and want to revert to that condition?

If your answer is yes, then simply uninstall the flash player from Adobe, because I believe you already have gnash installed.

```
sudo apt-get remove flashplugin-nonfree adobe-flashplugin
```

If you don't want to go back, just fix the Adobe plugin then run this:

```
sudo apt-get remove swfdec-mozilla
sudo apt-get remove mozilla-plugin-gnash
sudo apt-get remove adobe-flashplugin
sudo apt-get remove flashplugin-nonfree
sudo apt-get install flashplugin-nonfree
```

Hey dude, I exactly want to do the opposite and uninstall the **** that Firefox installed ... I tried disabling flash plugin from Firefox, didnt work !!! Should I simply delete its files from Plugin folder in Firefox or is there a way to remove it by command ?

The adobe for its self is working perfect and I dont have any problem with Opera.

---

### Post by lovinglinux on 2009-09-23
> **shahab.fm said:**
> Hey dude, I exactly want to do the opposite and uninstall the **** that Firefox installed ... I tried disabling flash plugin from Firefox, didnt work !!! Should I simply delete its files from Plugin folder in Firefox or is there a way to remove it by command ?

The adobe for its self is working perfect and I dont have any problem with Opera.

If you want to completely remove all flash plugins, run the following command and then delete the related plugins inside ~/.mozilla/plugins, if there are any:

```
sudo apt-get remove swfdec-mozilla
sudo apt-get remove mozilla-plugin-gnash
sudo apt-get remove adobe-flashplugin
sudo apt-get remove flashplugin-nonfree
```

Keep in mind this will also remove flash plugin from Opera, since it's not Firefox that installed the flash plugin. The flash plugin installation is generic for all browsers.

Nevertheless, I believe your problems is due to conflicting plugins. So before trying to remove all flash plugins, try this:

```
sudo apt-get remove swfdec-mozilla
sudo apt-get remove mozilla-plugin-gnash
sudo apt-get remove adobe-flashplugin
sudo apt-get remove flashplugin-nonfree
sudo apt-get install flashplugin-nonfree
```

From my experience, flash does not play well on any browser. Nevertheless, you might experience better performance with Firefox 3.5.3, which is faster than Opera. The alpha releases of Chromium and Firefox 3.6.1a are the best for flash.

You can also try to improve your flash experience using my tutorial [**[COLOR="DarkRed"]Firefox optimization and troubleshooting thread[/COLOR]**](http://ubuntuforums.org/showthread.php?t=1193567).

---

### Post by shahab.fm on 2009-09-24
The 2nd fix worked :) 

Thx for the help ...

---

