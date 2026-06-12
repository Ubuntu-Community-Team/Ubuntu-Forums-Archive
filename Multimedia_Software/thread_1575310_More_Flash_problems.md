---
title: "More Flash problems"
date: 2010-09-15
forum: Multimedia Software
---

### Post by m1001879 on 2010-09-15
Hey guys, sorry if i'm treading over old ground here but i'm finding it absolutely impossible to get flash working on ubuntu. I'm using firefox and have tried installing adobe flash player through their website (nothing happens, download doesn't start) and through the terminal (error messages), I've also tried installing other flash players from the ubuntu software centre and, while they install fine, they don't seem to actually work. I'm using ubuntu with windows (windows on C drive, ubuntu on D drive), could this be part of the problem?

Hopefully one of you can help me solve this, other than this little problem ubuntu has been awesome so far!

---

### Post by sikander3786 on 2010-09-15
See the link below for an installation guide.

[https://help.ubuntu.com/community/AMD64/FirefoxAndPlugins](https://help.ubuntu.com/community/AMD64/FirefoxAndPlugins)

However the easiest method for me to configure flash, java, fonts, codecs etc has been the installation of ubuntu-restricted-extras (see local law for copyright on certain formats). I highly recommend this one. Type in a terminal and hit enter, type your password (it won't show up any stars on the screen, just hit enter after you've typed it, in case you didn't know).

```

sudo apt-get update && sudo apt-get install ubuntu-restricted-extras

```

[COLOR="Red"]**Edit:**[/COLOR]

For possible issues with Flash:
[http://firefox-tutorials.blogspot.com/2010/06/flash-issues-solutions.html](http://firefox-tutorials.blogspot.com/2010/06/flash-issues-solutions.html)

(courtesy of forum member lovinglinux)

---

### Post by m1001879 on 2010-09-15
Tried it all, including using flash-aid, still no joy :-(

---

### Post by Claus7 on 2010-09-15
Hello,

could you open your browser and go to Help->About Mozilla Firefox and tell us the version you see?

Regards!

---

### Post by m1001879 on 2010-09-15
version 3.6.8

---

### Post by Claus7 on 2010-09-15
Hello,

ok, one more: if you open a terminal can you ping any address? Because you say that you cannot download the package from Adobe. Can you open other pages with firefox? And if not, can you open other pages with another browser? 

Ok not one more, yet you get the point.

Regards!

---

### Post by m1001879 on 2010-09-15
Forgive my computer illiteracy (windows user) but how do you ping addresses? I've tried downloading flash from different websites (even torrented the file) and tried different flash applications but NOTHING seems to work.

---

### Post by Claus7 on 2010-09-15
...

In case you can do all the above, what I would suggest you is manually to go and place the libflashplayer.so file to your computer in such a way so as to be recognised from firefox. 

In order to have an idea, open firefox and in the address bar type:
about:plugins (between t and l is : p without space inbetween) and hit enter.

There, you could see the paths of the installed plugins. If there is nothing about flash, then you should place flash file to:
/usr/lib/firefox-addons/plugins/libflashplayer.so

and see if this is working. 

In order to verify this go to:
cd /usr/lib/firefox-3.6.8

and type:
ls -l

there you will see something like:
plugins -> ../firefox-addons/plugins

which shows you the place where your browser will seek the plugin for flash.

Hope this helped,
Regards!

---

### Post by Claus7 on 2010-09-15
Hello,

> **m1001879 said:**
> Forgive my computer illiteracy (windows user) but how do you ping addresses? I've tried downloading flash from different websites (even torrented the file) and tried different flash applications but NOTHING seems to work.

no problem.

Just type:
ping [www.ubuntu.com](www.ubuntu.com)

and see if your screen is getting new data. If yes, your connection is working. If not, then you have some problems.

Regards!

---

### Post by m1001879 on 2010-09-15
no problems with connection. also, when i follow advice on some other pages (e.g. to get flashplugin-nonfree) i get error messages about broken packages

---

### Post by Claus7 on 2010-09-15
Hello,

Then try this:
[http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/)

you should download a tar file in your pc. Extract the content and place it in the correct path as expressed above.

Regards!

---

### Post by m1001879 on 2010-09-15
> **Claus7 said:**
> Hello,

Then try this:
[http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/)

you should download a tar file in your pc. Extract the content and place it in the correct path as expressed above.

Regards!

when i click on 'download' absolutely nothing happens. thanks for your help though!

edit: my most common error message when trying to install various flash players is E: broken packages

edit 2: i've just double checked the adobe flash player package on the ubuntu software centre and it says 'flash is not available on this computer (amd64). flash works fine when i use windows, just not when i use ubuntu

---

### Post by m1001879 on 2010-09-15
Claus, I think I can get the TAR file of the "square" flash player, now what? Keep in mind you're talking to a total linux/ubuntu newbie!

---

### Post by sikander3786 on 2010-09-16
It means you've got broken packages on your system that are not letting you install any other software. Go to System >>> Administration >>> Synaptic Package Manager, click custom filters and select broken and see if any packages are listed there. If there are some try to fix them and then try to install flash player from any of the sources you want to.

If you are already getting problems with flash and you are also a newbie, I won't recommend you to install the "square" flash player. Just try to install it from the repositories at first.

---

### Post by Claus7 on 2010-09-16
Hello,

thing is that something has broken down your system, with such a way as not allowing you to install some new packages as far as I can tell.

One thing would be to fix that with the guideline from *sikander3786*.

What I suggested you is to install manually flash, in case something else was hindering the process. That way at least, if everything else was ok, you would be able to use flash.

It might be that fixing the broken packages issue might fix the flash installation from synaptic making the installation process pretty easy. 

Just a query: what do you mean with the word "square"? 

And something else. If some packages are broken I have not understood why you are facing downloading problems with firefox. Are you able to download anything else? Thinking your ubuntu partition is an independent one, I would not like to mess things with other partitions you might have.

That is up to now,
Regards!

---

### Post by formaldehyde_spoon on 2010-09-16
> **m1001879 said:**
> Claus, I think I can get the TAR file of the &quot;square&quot; flash player, now what? Keep in mind you're talking to a total linux/ubuntu newbie!

Right click on the .tar.gz file, select 'extract here'. 
You'll see a .so file. 
Go to your Home folder, click View > Show Hidden Files 
From your Home folder go into .mozilla/plugins 
Put the .so file there, restart Firefox 


> **Claus7 said:**
> ... Just a query: what do you mean with the word &quot;square&quot;? 

...

Square is a new (beta) offshoot version of 10.1, and includes an official 64 bit version: [http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html)

---

### Post by lovinglinux on 2010-09-16
> **formaldehyde_spoon said:**
> Right click on the .tar.gz file, select 'extract here'. 
You'll see a .so file. 
Go to your Home folder, click View > Show Hidden Files 
From your Home folder go into .mozilla/plugins 
Put the .so file there, restart Firefox 




Square is a new (beta) offshoot version of 10.1, and includes an official 64 bit version: [http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html)

I just released version 1.0.12 of FLASH-AID, which supports the new 64bit version of flash.

[http://flash-aid-extension.blogspot.com](http://flash-aid-extension.blogspot.com)
[https://addons.mozilla.org/en-US/firefox/addon/161939/versions/](https://addons.mozilla.org/en-US/firefox/addon/161939/versions/)
[http://github.com/lovinglinux/flash-aid/downloads](http://github.com/lovinglinux/flash-aid/downloads)

---

### Post by michael37 on 2010-09-17
> **lovinglinux said:**
> I just released version 1.0.12 of FLASH-AID, which supports the new 64bit version of flash.


Interesting extension, thanks for putting it together.

Please make sure you include legal notices (otherwise what you do is probably illegal.  I am not a lawyer, so check with lawyers if neceesary).

1. Adding "Adobe Software License Agreement", see reference on page [http://labs.adobe.com/technologies/flashplayer10/](http://labs.adobe.com/technologies/flashplayer10/)
> 
Important: Installing the Flash Player prerelease means you have accepted the terms of the Adobe Software License Agreement. This is prerelease software, not a final release.


2. Providing links to additional Adobe licenses, see references on page [http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html)

"By downloading the software listed below, I acknowledge that I have read and agreed to the terms of the Flash Player "Square" License, the Adobe.com Terms of Use and the Adobe Online Privacy Policy."

3. Clarify that you are not redistributing software, rather, you include links to download from Adobe site.
License above clearly states that "3.3 Distribution. This license does not grant you the right to sublicense or distribute the Software. "

---

### Post by formaldehyde_spoon on 2010-09-17
> **michael37 said:**
> Interesting extension, thanks for putting it together.

Please make sure you include legal notices (otherwise what you do is probably illegal.  I am not a lawyer, so check with lawyers if neceesary).

1. Adding "Adobe Software License Agreement", see reference on page [http://labs.adobe.com/technologies/flashplayer10/](http://labs.adobe.com/technologies/flashplayer10/)


2. Providing links to additional Adobe licenses, see references on page [http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html)

"By downloading the software listed below, I acknowledge that I have read and agreed to the terms of the Flash Player "Square" License, the Adobe.com Terms of Use and the Adobe Online Privacy Policy."

3. Clarify that you are not redistributing software, rather, you include links to download from Adobe site.
License above clearly states that "3.3 Distribution. This license does not grant you the right to sublicense or distribute the Software. "
A. as in other thread, it is not illegal (breaking any law).
B. showing Adobe legal text will make no difference to EULA validity of other actions performed anyway, so your three "suggestions" are pointless
C. besides protecting a product as an income stream (not applicable here, as Flash is free to non-commercial users), EULAs main function is just to protect [Adobe] from liability arising from use of it's software, so stop panicking: your quote in #3 is protecting them in this case.

---

