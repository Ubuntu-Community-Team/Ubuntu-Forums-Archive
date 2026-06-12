---
title: "widevine media optimizer"
date: 2014-11-20
forum: Multimedia Software
---

### Post by newblank25 on 2014-11-20
Widevine media optimizer is a plugin required to run movies from my library site. Is there an equivalent for it in the ubuntu 14.04 environment? Is it in the software center? thx for help

---

### Post by mc4man on 2014-11-20
There is no linux support at the moment

---

### Post by jawilljr2 on 2014-11-20
> **newblank25 said:**
> Widevine media optimizer is a plugin required to run movies from my library site. Is there an equivalent for it in the ubuntu 14.04 environment? Is it in the software center? thx for help

Are you talking about Hoopla Digital?

If so you can get it to work in Firefox by using [Pipelight.](http://pipelight.net/cms/install/installation-ubuntu.html)

Try these commands:

```
sudo add-apt-repository ppa:pipelight/stable
sudo apt-get update
sudo apt-get install --install-recommends pipelight-multi
sudo pipelight-plugin --update
```

Now that Pipelight is installed you need to install Microsoft's Widevine.

```
sudo pipelight-plugin --enable widevine
```

Restart Firefox. Once Firefox is opening Pipelight will downloaded the latest version of widevine. 

Now try logging into Hoopla Digital and try to play a movie.

Also see [this thread.](http://ubuntuforums.org/showthread.php?t=2195896&highlight=netflix)

Hope this helps.

---

### Post by newblank25 on 2014-11-21
I opened the terminal. cut & pasted each line of code. everything was installed. then did the same for last bit of code. Opened up firefox & went to  hoopladigital. Tried a movie but got black screen & error message. thx for help.

---

### Post by jawilljr2 on 2014-11-21
> **newblank25 said:**
> I opened the terminal. cut & pasted each line of code. everything was installed. then did the same for last bit of code. Opened up firefox & went to  hoopladigital. Tried a movie but got black screen & error message. thx for help.

What is the error message?

Also do have have flasg installed?

---

### Post by newblank25 on 2014-11-22
i'll install flasg & see if that helps.

---

### Post by newblank25 on 2014-11-22
i do have flash installed & extra plugins

---

### Post by jawilljr2 on 2014-11-22
> **newblank25 said:**
> i do have flash installed & extra plugins

Ok, what was the error message?

Also were there any error messages when you ran those commands above?

---

### Post by cmcanulty on 2015-06-13
I did all of the above and still get the missing plugin error, so irritating when linux can't do something like this, any further ideas? I am running xubuntu 14.04 64bit all updated.

```
Missing Plugin
Hoopla requires the Widevine Media Optimizer browser plugin to view video content.
```

Oops got it working by going to chrome instead of firefox weird.

---

### Post by hongmao on 2015-07-17
Hi, I'm still not able to use widevine, but I'm not switching to chrome, because I am as paranoid as the users described by Dedoimedo in one of his latest articles. I am however able to share more details, though I'm not a web developer myself:

The error message from the browser console is this:
[ATTACH=CONFIG]263253[/ATTACH]

Regarding this code:
[ATTACH=CONFIG]263252[/ATTACH]

I'm guessing the problem has to do with the Pipelight project's naming of their implementation to 'WidevineMediaOptimizer,' not 'WidevinePlugin?'

---

### Post by jawilljr2 on 2015-07-17
try the following command:

```
sudo pipelight-plugin --create-mozilla-plugins
```

Restart Firefox and try again.

 That is what I had to do for later versions of Firefox.

---

### Post by cmcanulty on 2015-07-18
Hey jawilljr2 that works, thanks! I had tried numerous other fixes. Now I can use firefox instead of chrome which I don't like using

---

### Post by hongmao on 2015-07-22
It turns out the problem with mine was that I was using a spoofed user-agent, because I thought if the website presumed I was using windows, it would load the player...

---

### Post by cmcanulty on 2015-08-29
This fix no longer works for me in firefox, can it be updated? Thanks

---

### Post by NoBugs! on 2015-11-07
The error message they give is incorrect. It actually works just fine in Chromium browser, and I didn't have to install any extra plugins.

---

### Post by Otto-C on 2015-11-23
Bump. 

 Any information getting Firefox to run?

tia
otto-c

---

### Post by cmcanulty on 2015-11-24
I can't get it to work in firefox though now I at least get a black box with an arrow put it won't play

---

### Post by shaddow2 on 2016-10-22
There is  no difference between Chrome and Chromium as far as a regular user is concerned.  Chromium is modified by the FOSS group which makes it free. Chrome has parts that are licensed and is not free but free to down load.
Some distos  not all distros like Arch has in the AUR a version with Widevine which is necessary to view Netflix.

The newer Version of Firefox no longer supports the wine version called Pipelight.

Hopes this clarifies  things a bit.

---

