---
title: "how to install libflashplayer.so??"
date: 2010-12-31
forum: Multimedia Software
---

### Post by scott_tiger on 2010-12-31
I have downloaded Flashplayer from Adobe site in tar.gz format.
When i extracted i got a libflashplayer.so file.
I don't know how to install the libflashplayer.so file ..

---

### Post by Zzl1xndd on 2010-12-31
You should be able to get Flash Player from Synaptic or by installing the Ubuntu Restricted Extras.

Also Adobe does offer a .deb, you can down load it [here ]("http://get.adobe.com/flashplayer/otherversions/") just select Linux .deb.

---

### Post by scott_tiger on 2010-12-31
I know that but want to install the libflashplayer.so file format.
For installing .deb format we need just dpkg -i cmd.
I want to learn to install in .so format of file..

---

### Post by jmszr on 2010-12-31
scott_tiger,

This Firefox add-on: [https://addons.mozilla.org/en-US/firefox/addon/161939/](https://addons.mozilla.org/en-US/firefox/addon/161939/) , FLASH-AID will "Remove conflicting flash plugins from Ubuntu Linux systems and install the appropriate version according to system architecture" .

I use this add-on and it works very well; it is developed by Ubuntu Forums member "lovinglinux".

Hope this helps.

---

### Post by Zzl1xndd on 2010-12-31
Its been a while but you should be able to just drop the file in /usr/libs/firefox-addons/plugins/

---

### Post by kenney on 2010-12-31
If you are using the 64 bit os, try this version of flash as well

[http://labs.adobe.com/downloads/flashplayer10_square.html](http://labs.adobe.com/downloads/flashplayer10_square.html)

---

### Post by cchhrriiss121212 on 2010-12-31
If this is a beta version it is best to put it here:
/home/user/.mozilla/plugins

That is all you need to do, firefox or chrome will see it when they next start up.

---

### Post by I'mGeorge on 2010-12-31
> **scott_tiger said:**
> I have downloaded Flashplayer from Adobe site in tar.gz format.
When i extracted i got a libflashplayer.so file.
I don't know how to install the libflashplayer.so file ..

you need to move libflashplayer.so to /usr/lib64(or lib32 if you don't use Ubuntu x86_84)/mozilla/plugins

---

### Post by ajgreeny on 2010-12-31
You can find the current site of the libflashplayer.so from firefox by typing ```
about:plugins
``` in the addressbar, then find the entry like:-> **Shockwave Flash**

 File:  /usr/lib/adobe-flashplugin/libflashplayer.so
Version: 
  Shockwave Flash 10.2 d151You will note that I have the 10.2 beta version running very well in my 32 bit system, and I think it's better than then current Ubuntu version from the repos.

What I did was use gksudo nautilus to open  /usr/lib/adobe-flashplugin folder, then renamed the old libflashplayer.so as libflashplayer.so101, and copied the new libflashplayer.so in place of it.  You can also do it in terminal with mv and cp commands, but I wanted to see what was going on, so used nautilus.

The new version was found right away by FF next time I opened it with no problem.

---

### Post by ajgreeny on 2010-12-31
EDIT:
The forum seems to be going nowhere several times when posting replies, but the reply has already been sent, hemce two duplicate posts.

---

### Post by ajgreeny on 2010-12-31
EDIT: See previous post.

---

### Post by Yellow Pasque on 2010-12-31
You should either put the file in ~/.mozilla/plugins or install a .deb
Putting the file somewhere in /usr (as others have suggested) goes against Debian policy and is a good way to set yourself up for future problems.

---

### Post by ajgreeny on 2010-12-31
> **Temüjin said:**
> You should either put the file in ~/.mozilla/plugins or install a .deb
Putting the file somewhere in /usr (as others have suggested) goes against Debian policy and is a good way to set yourself up for future problems.
I have done this many times in the past (ie, put the libflashplayer.so file in  /usr/lib/adobe-flashplugin/) many times in the past when looking at beta versions of flash, and not once has it caused me a problem.  Even when Ubuntu eventually tells me that a new updated version of flash is available, it updates what it still believes is the older stable version, so there is no problem there either.

I have never had a flash plugin in my /.mozilla/plugins folder since I've been using Ubuntu; it has always been in a /usr/lib folder somewhere as far as i can remember.

There are quite a few ways in which Ubuntu does things differently to the Debian standard ways, so I don't see how that holds up.

---

### Post by lidex on 2010-12-31
Interestingly, although this may be related to version, I no longer have a "~/.mozilla/plugins" directory and I don't use chrome so I can't speak to how that is affected. On natty with firefox v.4.0 b8. A locate in terminal returns:
```
/usr/lib/firefox-addons/plugins/libflashplayer.so
/usr/lib/mozilla/plugins/libflashplayer.so

```

I do not manually access these directories. I have been using lovinglinux's flash-aid extension to update.
[https://addons.mozilla.org/en-US/firefox/addon/161939/](https://addons.mozilla.org/en-US/firefox/addon/161939/)

---

### Post by Yellow Pasque on 2011-01-01
> **ajgreeny said:**
> I have done this many times in the past (ie, put the libflashplayer.so file in  /usr/lib/adobe-flashplugin/) many times in the past when looking at beta versions of flash, and not once has it caused me a problem.
That doesn't mean that it's good practice. I can't count the number of threads where people had problems due to old or misplaced Flash libs (hence the popularity of cleaning scripts like FLASH-AID).

> There are quite a few ways in which Ubuntu does things differently to the Debian standard ways, so I don't see how that holds up.
Ubuntu follows Debian policy on packaging and filesystem layout, so it does hold up.

---

### Post by wojox on 2011-01-01
If it's 64 bit run:

```
wget http://download.macromedia.com/pub/labs/flashplayer10/flashplayer10_2_p3_64bit_linux_111710.tar.gz
```

```
tar -xvf flashplayer10_2_p3_64bit_linux_111710.tar.gz -C /usr/lib64/mozilla/plugins
```

---

### Post by Yellow Pasque on 2011-01-01
If it's 64-bit, it would be better to use [https://launchpad.net/~sevenmachines/+archive/flash](https://launchpad.net/~sevenmachines/+archive/flash)
That way, it gets automatically updated.

---

### Post by lovinglinux on 2011-01-01
hey guys,

I just released [Flash-Aid 2.0]("http://www.webgapps.org/addons/flash-aid") and I'm very excited about it, because it has tons of new features, including 64bit updates.

By default, the extension detects currently installed flash plugins in various locations, like /usr/lib/mozilla/plugins, ~/.mozilla/plugins, /opt/firefox/plugins and even the wine directory. It also detects gnash, swfdec, lightspark, adobe-flashplugin, flashplugin-nonfree and flashplugin-installer. When executed, it will remove all detected flash plugins and install the best option for the system, considering architecture and Ubuntu version. It will also apply some tweaks like OverrideGPUValidation, to improve performance and avoid fullscreen erros.

The default mode automatically select all those options and install the beta version from Adobe, except on Hardy 64bit, in which it installs the version from the repositories. The square preview 64bit crashes in fullscreen on Hardy. Anyway, the default mode is pretty simple and automatic. You just need to click a button. However, the extension also includes an "Expert Mode", which allows to select which plugin to install and remove. Among the options of plugins to install, there is a custom mode that allows to insert a local path to the tar.gz file downloaded from Adobe or the url from Adobe site and the extension takes care of extracting and installing it.

One of the best new features is that the extension is now capable of checking for updates of the beta versions and prompt if you want to run Flash-Aid to get the update. 

In Flash-Aid 1.0.x when Adobe released a new beta and removed the old link from the site, I had to update the extension in order to make it work again. This is no longer necessary, because the extension downloads from a redirection link on my site, that simply points to the download url on Adobe's site. So all I need to update the link and the update timestamp and the extension will warn you about the new version and get the proper file. 

I have tested it on Hardy 32/64bit, Karmic 32/64bit, Lucid 32/64bit, Maverick 32/64bit on Firefox 4.0b8, 4.0b9pre, 3.6.13 and 3.5.16. 

This version won't be displayed in the Mozilla site until they review it, but you can get from the extension web site:

[http://www.webgapps.org/addons/flash-aid]("http://www.webgapps.org/addons/flash-aid")

I haven't updated the documentation yet, but the extension also include some tips and should be pretty easy to understand how it works.

Have fun and Happy New Year.

---

### Post by ray13z on 2011-03-25
> **lovinglinux said:**
> hey guys,

I just released [Flash-Aid 2.0]("http://www.webgapps.org/addons/flash-aid") and I'm very excited about it, because it has tons of new features, including 64bit updates.
...
Have fun and Happy New Year.

Works like a charm on firefox 4 (stable) in Ubuntu 10.10 amd64. No problems.
Thank you lovinglinux

---

### Post by lovinglinux on 2011-03-25
> **ray13z said:**
> Works like a charm on firefox 4 (stable) in Ubuntu 10.10 amd64. No problems.
Thank you lovinglinux

You are welcome.

---

