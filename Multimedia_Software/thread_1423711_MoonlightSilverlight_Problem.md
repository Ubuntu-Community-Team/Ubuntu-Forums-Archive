---
title: "Moonlight/Silverlight Problem"
date: 2010-03-07
forum: Multimedia Software
---

### Post by HBSC on 2010-03-07
Hello out there, 

I know the whole MS Silverlight is likely an annoying old issue, so I apologize in advance. 

I installed the two moonlight packages from the repos (moonlight-plugin-core and moonlight-plugin-mozilla). Now moonlight appears to be installed in Firefox, but I still can't stream Silverlight video.

I have also attempted to install Firefox for windows in wine, but when I attempt to install  Silverlight.exe I get an error:

> Unable to find a volume for file extraction
Please verify that you have proper permissionsAny ideas?

---

### Post by xtnsgo on 2010-03-07
> **HBSC said:**
> Hello out there, 

I know the whole MS Silverlight is likely an annoying old issue, so I apologize in advance. 

I installed the two moonlight packages from the repos (moonlight-plugin-core and moonlight-plugin-mozilla). Now moonlight appears to be installed in Firefox, but I still can't stream Silverlight video.

I have also attempted to install Firefox for windows in wine, but when I attempt to install  Silverlight.exe I get an error:

Any ideas?

I've recently run across this:
 
[http://go-mono.com/forums/#nabble-td1568103](http://go-mono.com/forums/#nabble-td1568103)

It looks promising--post dated February 25th (close to the end) seems to suggest it is solved.  Maybe this will help, or at least get you going in the right direction, anyway.  

As far as the WINE aspect, i must plead total ignorance.  I did see this, though: [http://ubuntuforums.org/showthread.php?t=966848]("http://ubuntuforums.org/showthread.php?t=966848")

best of luck!

---

### Post by HBSC on 2010-03-11
Thank you for the reply, I think I'm getting closer! 
The thread you sent me too suggests that the problem might be that there are two moonlight plugins popping up when I navigate to ```
about:plugins
``` in firefox... 

Still not solved, but I have a feeling I'll get it soon :)

---

### Post by wojox on 2010-03-11
Purge those old package's and install from here: [http://www.go-mono.com/moonlight/](http://www.go-mono.com/moonlight/)

---

### Post by HBSC on 2010-03-11
I attempted that with:
```
sudo apt-get remove
```

Then installed the plugin from [http://www.go-mono.com/moonlight/](http://www.go-mono.com/moonlight/). I still can't stream any silverlight video, and my about:plugins output from firefox is:

> Silverlight Plug-In

    File name: libmoonloaderxpi.so
    3.0.40818.0

MIME Type 	                    Description      Suffixes Enabled
application/x-silverlight 	Novell Moonlight 	xaml 	Yes
application/x-silverlight-2 	Novell Moonlight 		Yes


Am I not completely removing the previous moonlight packages?

---

### Post by HBSC on 2010-03-11
Edit -- "about:plugins" was supposed to be 
```
about:plugins
```
...I didn't mean to have a random smiley face sticking it's tongue while I was asking for help!

---

### Post by gradinaruvasile on 2010-03-11
In my experience moonlight seldom worked. And when it did, it wasnt working right.
It is like gnash if you ask me. It seems microsoft (or novell?) isnt serious at all about the cross platform compatibility (at least not with Linux).

Lets serious here - when someone tries to make silverlight work under Linux he gets a lot of replies: install this from here, no install that from there... For me never worked, i tried several times with alpha/beta/stable moonlight plugins. So i expect that inexperienced users will be even more confused.
Also, my firefox became unstable after installing the moonlight plugins.

For silverlight i just installed Firefox under wine and the silverlight plugin for it. That was the only was i saw working silverlight on linux...

---

