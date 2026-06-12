---
title: "Getting adobe-flashplugin to work with Chromium"
date: 2016-01-13
forum: Multimedia Software
---

### Post by pastim on 2016-01-13
Looking to keep flash up to date in Chromium I found this - [https://wiki.ubuntu.com/Chromium/Getting-Flash](https://wiki.ubuntu.com/Chromium/Getting-Flash) - which said that my old pepperflashplugin-nonfree had been deprecated.  However, installing adobe-flashplugin did not work on my 14.04 system.  After quite a lot of investigation, including installing Chromium and adobe-flashplugin on my 15.10 laptop, which did work, I found out why.

There are at 3, possibly four problems with a 14.04 system that has been around for a couple of years and had not only pepperflashplugin-nonfree but also another [COLOR=#333333][FONT=monospace]pepflashplugin-[/FONT][/COLOR][COLOR=#333333][FONT=monospace]installer from [/FONT][/COLOR]https://launchpad.net/~skunk/+archive/ubuntu/pepper-flash installed.  To cut a longish story short, to get adobe-flashplugin to work:

1. install adobe-flashplugin
2. make sure pepperflashplugin-nonfree (and any other similar tool) has been uninstalled
3. in /etc/chromium-browser/default, make sure CHROMIUM-FLAGS are just set to "" (pepperflashplugin-nonfree may have modified it - the code there should still work as it is, but best to keep it simple!)
4. in ~/.local/share/applications/chromium-browser.desktop (if any) make sure the Exec line does not include any pepperflash arguments (mine did - I have no idea which tool set this up, but it fooled me for a long time) - if you have no such desktop, just check the system wide one in /usr/share/applications as well.
5. And now you can EITHER:
 create a file called pepper-flash.info in new directory /usr/lib/chromium-browser/pepper containing:
```
[FONT=Liberation Serif]
PLUGIN_NAME='PepperFlash';[/FONT]
[FONT=Liberation Serif]FILE_NAME='/usr/lib/adobe-flashplugin/libpepflashplayer.so';[/FONT]
[FONT=Liberation Serif]VERSION="$(strings"${FILE_NAME}" 2> /dev/null | grep LNX | cut -d ' ' -f 2| sed -e 's/,/./g')";[/FONT]
[FONT=Liberation Serif]VISIBLE_VERSION="${VERSION}";[/FONT]
[FONT=Liberation Serif]DESCRIPTION='Non-freeFlash Player Plugin distributed by Google';[/FONT]
[FONT=Liberation Serif]MIME_TYPES='';[/FONT]

```
OR, in /etc/chromium-browser/customizations create a file called 10-flash containing:
```

flashso="/usr/lib/adobe-flashplugin/libpepflashplayer.so"
if test -f "$flashso"; then
    CHROMIUM_FLAGS="$CHROMIUM_FLAGS --ppapi-flash-path=$flashso --ppapi-flash-version="
    echo "Using PPAPI flash."
else
    echo "PPAPI flash has config file in /etc, but library does not exist and won't be used. Package is uninstalled, not purged."
fi

```
6. If you now run Chromium, the chrome://plugins should now show the flash plugin, albeit with an old (linux) version number.  If you then run the Adobe Test at [https://www.adobe.com/software/flash/about/](https://www.adobe.com/software/flash/about/) you should find you are on the latest version - as of 13th Jan 2016 this is 20,0,0,267

Why the adobe-flashplugin installation on my 14.04 system did not do either of the actions in step 5 above I don't know.  The issues I had with step 4 are a mystery to me.

But it all works now, with 'standard' ubuntu software.  The reviews of adobe-flashplugin from the ubuntu software centre show that I was not alone in having problems.  Indeed I'm not even sure that the version obtained from there is the same one as obtained using apt-get.

---

### Post by ajgreeny on 2016-01-13
Interesting that you had so much trouble with 14.04's flash.

I have found that all you need to do is purge any flash packages you have installed at present, then to get the 20,0,0,267 flash version on chromium all you need is Adobe-flashplugin package from the partner repos and it works.

You can also get the same 20,0,0,267 flash working in Firefox by installing freshplayerplugin from the ppa [http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu](http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu)

This was a bit flaky originally but now seems to work very well.

Did you by chance still have the flasplugin-installer package on your machine as that can cause some problems and gives you a different flash version in my experience.

I just long for the day when I can get rid of flash entirely but at present that is just not possible for some of the sites I use, eg The BBC

---

### Post by pastim on 2016-01-13
> **ajgreeny said:**
> Interesting that you had so much trouble with 14.04's flash.

I have found that all you need to do is purge any flash packages you have installed at present, then to get the 20,0,0,267 flash version on chromium all you need is Adobe-flashplugin package from the partner repos and it works.

You can also get the same 20,0,0,267 flash working in Firefox by installing freshplayerplugin from the ppa [http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu](http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu)

This was a bit flaky originally but now seems to work very well.

Did you by chance still have the flasplugin-installer package on your machine as that can cause some problems and gives you a different flash version in my experience.

I just long for the day when I can get rid of flash entirely but at present that is just not possible for some of the sites I use, eg The BBC
I wish it was that simple, but on my system it really wasn't.  t took me several hours over several days to figure it all out.   Looking at the reviews on ubuntu software centre I am not the only one.  That's why I decided to document the solutions I needed.

I have no idea why the installation of adobe-flashplugin was incomplete.

I don't have the flashplugin-installer installed now, but may have had at some point in the past.  

I haven't tried the firefox one you mention, but I don't use that much on my desktop.

---

