---
title: "Flash player not prompting to use my webcam"
date: 2009-08-07
forum: Multimedia Software
---

### Post by dullo on 2009-08-07
When i want to go on a webcam website such as Stickam or use my webcam to chat on Meebo. Flash Player never prompts me to let me click "Allow" so my webcam never shows up. I need to be able to use my webcam. Can anyone help?

---

### Post by khelben1979 on 2009-08-07
What version of flash are you running? (right click on a YouTube window and you'll see it)

[Adobe.com - get the flash player]("http://get.adobe.com/flashplayer/?promoid=DXLUJ")

---

### Post by dullo on 2009-08-07
The latest version. Flash Player 10
I even tried reinstalling it but still the same problem.

---

### Post by dullo on 2009-08-07
bumpp

---

### Post by khelben1979 on 2009-08-08
Are you able to use the webcam with [cheese]("http://en.wikipedia.org/wiki/Cheese_%28software%29")?

---

### Post by dullo on 2009-08-08
[IMG]http://i28.tinypic.com/dxlht3.jpg[/IMG]

---

### Post by khelben1979 on 2009-08-09
> **dullo said:**
> [img]http://i28.tinypic.com/dxlht3.jpg[/img]

:d

---

### Post by dullo on 2009-08-09
Anyone have any ideas? Anyone at all?

edit: skype also works fine with the webcam

---

### Post by khelben1979 on 2009-08-09
Does this give you the same result when using Firefox 3.5.2?

---

### Post by dullo on 2009-08-09
I'm running 3.0.13 right now. How can I upgrade?

---

### Post by khelben1979 on 2009-08-09
Either just download it from mozilla.org or look for it in the [Synaptic Package Manager]("http://en.wikipedia.org/wiki/Synaptic_package_manager").

---

### Post by dullo on 2009-08-09
Still nothing even with the most recent Firefox.

---

### Post by khelben1979 on 2009-08-09
From what I can see, this don't work on my system either.

---

### Post by dullo on 2009-08-10
I'm surprised that this has never been covered then, because I also searched as best I could. Somebody HALP

---

### Post by dullo on 2009-08-10
bump

---

### Post by dullo on 2009-08-12
b u m p

---

### Post by dullo on 2009-08-13
for realz?
BUMP

---

### Post by Mr Rough on 2009-08-14
Try going to this URL [http://www.macromedia.com/support/documentation/en/flashplayer/help/settings_manager04.html](http://www.macromedia.com/support/documentation/en/flashplayer/help/settings_manager04.html)

Once there a config will load. On the first tab (Global Privacy) click the "Always Ask" button. This should make all sites default to prompting.

If you want to tweak it on a per site basis, go to the Web Privacy tab and click the specific site and you can choose the option.

Hope it helps.

---

### Post by dullo on 2009-08-18
ahh, nope thats probably the best response so far but it still doesn't seem to be working.

---

### Post by dullo on 2009-08-21
bump.

---

### Post by no2498 on 2009-09-05
if ask did not work try
allow remember
for the web site you use

---

### Post by Bogus1 on 2009-10-18
I have the same problem.
But this fix will not work, as Adobe Flash Player fails to find any webcam attached to the system. Problem only seems to be with Flash Player, as aMSN, Skype etc all find and can use the webcam without any trouble.

---

### Post by Minipalmer on 2009-12-05
Did anyone find a solution for this?

I found this site, which allows you to click "always allow" for any of the sites you've visited

[http://www.macromedia.com/support/documentation/en/flashplayer/help/settings_manager06.html](http://www.macromedia.com/support/documentation/en/flashplayer/help/settings_manager06.html)

But it still didn't work for me.

I actually got the player to ask on tokbox.com, but it wouldn't let me click anything!

---

### Post by monraaf on 2009-12-05
try this: 

[http://ubuntuforums.org/showpost.php?p=8100915&postcount=8](http://ubuntuforums.org/showpost.php?p=8100915&postcount=8)

---

### Post by Minipalmer on 2009-12-05
> **monraaf said:**
> try this: 

[http://ubuntuforums.org/showpost.php?p=8100915&postcount=8](http://ubuntuforums.org/showpost.php?p=8100915&postcount=8)

Sorry for being a complete newb, but should I just slap that in a terminal? How is that going to help Flash when it says "Skype" on it?

Thanks for posting

---

### Post by monraaf on 2009-12-05
Just replace skype with firefox ;)

so exit firefox and then type either this:

```

LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so firefox

```

or this:

```

LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so firefox

```

in a terminal.

---

### Post by Minipalmer on 2009-12-05
That did it, thanks! Though now I have to get my mic to work...

---

### Post by Minipalmer on 2009-12-05
Got mic support using this!

[http://www.blog.arun-prabha.com/2009/11/06/ubuntu-9-10-microphone-setup/](http://www.blog.arun-prabha.com/2009/11/06/ubuntu-9-10-microphone-setup/)

SOLVED!

TY Ubuntu forums.

---

### Post by lleachii on 2010-06-09
Please visit [https://bugs.adobe.com/jira/browse/FP-775]("https://bugs.adobe.com/jira/browse/FP-775") to track the bug report and vote for this issue.

---

### Post by bugadazcoubz on 2011-02-17
I have the same problem...

one time it did work. in some webcamtesting site. 
but than (i think it was chrome, because in mozilla it didnt work at all) brower crashed, and never been able to put it to work again.

in flash config, it says flash doesnt recognize webcam.
could it be some configuration file, to say to browser to use dev/video0 as default video? or is it because its USB, so it must be reached by flash (probably browsers too) by other ways?!?!?!?! some USB config...

dont know.
its not a driver problem (i guess) because cam works with cheese, and with some other programs....
my guess is that must have something to do with wich file browsers use to use my usb webcam.
i've read something about some firewall conflicts with webcam chat, in for instance aMSN... some router config I guess... dont know about this

---

### Post by no2498 on 2011-02-17
bugadazcoubz
a few things to try
install flash aid for fire fox
install grease monkey for fire fox
try the browser opera
opera worked first for me

---

