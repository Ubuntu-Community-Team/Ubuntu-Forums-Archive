---
title: "Gnome-shell slowness problem with ATI"
date: 2010-12-06
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by sonicb00m on 2010-12-06
I know this probably isn't the best forum to put it in but I am trying to get Gnome shell running nicely in 10.10 with my ATI HD5500 card but the desktop is very slow. I tried setting the vblank export trick in .profile but while it helped a little it didn't solve the problem.

Any ideas for this?

---

### Post by Anduu on 2010-12-06
First off...which version are you running?

2.31.5 from the official repos is very old and quite clunky.
2.91.2 from ricotz ppa is going on almost a month old now but performs better.
If you are compiling from source (not sure what the version is at right now...) it has become quite a bit better in a short time.

Secondly...if you are expecting Compiz-like performance you will be disappointed.Mutter just isn't there yet...if it will ever be I don't know.

From what I have read this new generation of ATI cards still needs some work so give it some time and I am sure things will improve.

---

### Post by sonicb00m on 2010-12-06
Yeah its 2.31.5..... it was from the Ubuntu Tweak PPA so I'll upgrade to the Ricotz and give it a go. Thanks.

---

### Post by sonicb00m on 2010-12-06
I added the PPA with "add-apt-repository" but the packages don't update. They still stay at 2.31.5

edit *

found this instead
[http://www.webupd8.org/2010/10/install-gnome-shell-from-git-in-ubuntu.html](http://www.webupd8.org/2010/10/install-gnome-shell-from-git-in-ubuntu.html)

---

### Post by Anduu on 2010-12-06
We have a pretty good thread going right here on the Natty forum [http://ubuntuforums.org/showthread.php?t=1603874](http://ubuntuforums.org/showthread.php?t=1603874)

---

### Post by sonicb00m on 2010-12-06
yeah maybe so but trawling through 31 pages of information is not really very plausible. I had already tried to find solutions to my problems in that thread.

I can't get that stuff on that page to compile. It throws out errors unrelated to the fixes mentioned on that page.

I think i'll throw the towel in. I can't really be bothered going to all that effort. No doubt by the time i've wasted several days trying to get an updated gnome shell on my 10.10 box I bet the ATI problem is still the same :D

---

