---
title: "Strange beeping sound when viewing flash video"
date: 2011-02-21
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by tjeremiah on 2011-02-21
Whenever I view flash content video, say on Youtube or Justin tv, I get this weird continuous beeping sound that never ends. Anyone else? It started late last week. Also, my flash is up to date (64bit).

---

### Post by Harry33 on 2011-02-22
> **tjeremiah said:**
> Whenever I view flash content video, say on Youtube or Justin tv, I get this weird continuous beeping sound that never ends. Anyone else? It started late last week. Also, my flash is up to date (64bit).

Up to date flash.
So you have downloaded the native 64-bit architecture flash from Adobe
(Flash Player Square v. 10.3 d162).

I don't have any that kind of issues.
Works fine with FF 4.0 b11 and Chromium 10.0.648.82 beta).

---

### Post by farooq23 on 2011-02-22
> **tjeremiah said:**
> Whenever I view flash content video, say on Youtube or Justin tv, I get this weird continuous beeping sound that never ends. Anyone else? It started late last week. Also, my flash is up to date (64bit).

Yes I am getting the same noice

---

### Post by ronacc on 2011-02-22
see Steve Jobs told you that flash ate kittens and would destroy your box .

---

### Post by tjeremiah on 2011-02-22
> **Harry33 said:**
> Up to date flash.
So you have downloaded the native 64-bit architecture flash from Adobe
(Flash Player Square v. 10.3 d162).

I don't have any that kind of issues.
Works fine with FF 4.0 b11 and Chromium 10.0.648.82 beta).

yeah, same updated flash. I use FF, not Chrome.

---

### Post by portis on 2011-02-22
Is it related to this bug?
[https://bugzilla.redhat.com/show_bug.cgi?id=638477]("https://bugzilla.redhat.com/show_bug.cgi?id=638477")

---

### Post by tjeremiah on 2011-02-22
> **portis said:**
> Is it related to this bug?
[https://bugzilla.redhat.com/show_bug.cgi?id=638477]("https://bugzilla.redhat.com/show_bug.cgi?id=638477")

I didnt read through the whole thing but it sounds similar.

---

### Post by portis on 2011-02-22
You can try the script in that bug report to patch the libflashplayer.so
It works for me.
Don't forget to change the #!/bin/sh to #!/bin/bash

> **tjeremiah said:**
> I didnt read through the whole thing but it sounds similar.

---

### Post by snizovtsev on 2011-02-22
> **portis said:**
> Is it related to this bug?
[https://bugzilla.redhat.com/show_bug.cgi?id=638477](https://bugzilla.redhat.com/show_bug.cgi?id=638477)
Thanks! I've applied the binary patch from the thread and it have helped me.

---

### Post by tjeremiah on 2011-02-23
> **snizovtsev said:**
> Thanks! I've applied the binary patch from the thread and it have helped me.

how do you apply it?:confused: When I click on the attachment, I get nothing to download.

---

### Post by tjeremiah on 2011-02-24
I right click and saved it to desktop but have no idea where to put it for it to work. I ran the terminal and it tells me no such file. How did you fix this error with the patch?

---

### Post by tjeremiah on 2011-02-26
guys, how did you apply the patch? The guy doesnt give much detail or step by step as to how.

---

### Post by portis on 2011-02-26
Download the script, then run it

$ sudo bash ./fix-flash.sh /usr/lib/flashplugin-installer/libflashplayer.so

> **tjeremiah said:**
> guys, how did you apply the patch? The guy doesnt give much detail or step by step as to how.

---

### Post by andrek on 2011-03-04
After applying the patch, Chromium doesn't recognize the plugin. Any idea how to make it work?

---

### Post by portis on 2011-03-04
Strange, on my machine, chromium and flash plays quite well with that patch.

> **andrek said:**
> After applying the patch, Chromium doesn't recognize the plugin. Any idea how to make it work?

---

### Post by vhaarr on 2011-03-06
> **andrek said:**
> After applying the patch, Chromium doesn't recognize the plugin. Any idea how to make it work?

Same here, on 64bit.

---

### Post by RPG Master on 2011-03-17
> **vhaarr said:**
> Same here, on 64bit.
Same here on 64-bit firefox. I had to go and redownload the vanilla flash "square". How did y'all get it to work?

---

### Post by rburkartjo on 2011-03-18
yes how do you get it to work.i am having same problems

---

### Post by SevenMachines on 2011-03-18
The LD_PRELOAD method of memcopy.so replacement when loading the browser works here on 64 bit with 10.3.162.29 flash, the binary patch doesnt since it leaves the plugin unrecognised

[EDIT] For anyone using the ppa, i've uploaded a hacky preload memcpy version, i imagine the binary patch would be breaking some sort of legal thing anyway so. sadly this does mean a preload for browsers, eg
 
```
  $ LD_PRELOAD=/usr/lib/flashplugin-installer/memcpy-revert.so firefox 
```or you could add
```
LD_PRELOAD=/usr/lib/flashplugin-installer/memcpy-revert.so
export LD_PRELOAD
``` to the top of /usr/bin/firefox
> 
flashplugin64-nonfree (10.3.162.29-0ubuntu0~sevenmachines3) natty; urgency=low    
* memcpy-revert.c added to install to allow workaround to memcpy bug     Browsers can now be run using preload,ie,     
$ LD_PRELOAD=/usr/lib/flashplugin-installer/memcpy-revert.so firefox

---

### Post by giant420 on 2011-04-03
> **SevenMachines said:**
> The LD_PRELOAD method of memcopy.so replacement when loading the browser works here on 64 bit with 10.3.162.29 flash, the binary patch doesnt since it leaves the plugin unrecognised

[EDIT] For anyone using the ppa, i've uploaded a hacky preload memcpy version, i imagine the binary patch would be breaking some sort of legal thing anyway so. sadly this does mean a preload for browsers, eg
 
```
  $ LD_PRELOAD=/usr/lib/flashplugin-installer/memcpy-revert.so firefox 
```or you could add
```
LD_PRELOAD=/usr/lib/flashplugin-installer/memcpy-revert.so
export LD_PRELOAD
``` to the top of /usr/bin/firefox
Is there any fix for chromium? Your post only seems to apply to firefox.

---

