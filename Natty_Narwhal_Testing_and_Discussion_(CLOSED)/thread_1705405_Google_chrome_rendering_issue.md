---
title: "Google chrome rendering issue"
date: 2011-03-12
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by Sashin on 2011-03-12
Anyone else have this problem, chrome isn't rendering properly at open. I can fix it by unmaximising and remaximising but it's still very annoying.

[http://i51.tinypic.com/15eyvn.png](http://i51.tinypic.com/15eyvn.png)

---

### Post by Harry33 on 2011-03-12
> **Sashin said:**
> Anyone else have this problem, chrome isn't rendering properly at open. I can fix it by unmaximising and remaximising but it's still very annoying.

[http://i51.tinypic.com/15eyvn.png](http://i51.tinypic.com/15eyvn.png)

Nope,

In Natty (NVidia) I use dev channel v 11..
In an other setup, Maverick (Intel) I use latest stable v.10.
Both work OK.

---

### Post by jmmL on 2011-03-12
I've got this problem as well. I'm using the daily-chromium ppa with up-to-date natty and nvidia drivers from the natty repos.

---

### Post by Sashin on 2011-03-12
And I'm using Intel drivers and its happening.

---

### Post by kerry_s on 2011-03-12
do you have compiz set to maximize all windows?

---

### Post by Sashin on 2011-03-12
Only if its default.

---

### Post by Eestlane on 2011-03-12
Yeah, same here.
r300g (using xorg-edgers), chromium-daily

---

### Post by Sashin on 2011-03-13
It seems to happen on my desktop as well, it uses an nvidia graphics card with experimental open source drivers.

---

### Post by VinDSL on 2011-03-13
I'm using Chromium 10.0.648.133 (77742) -- which is basically Google Chrome Stable Channel without the branding, and...

Everything is rendering just fine, at opening.  ;)

---

### Post by prettyboy85712 on 2011-03-13
No issues here using the daily-chromium ppa.

---

### Post by Daniel Salcedo on 2011-03-13
I have the **same problem** with rendering with Chrome. I read all the posts above. Is there **other "Solution(s**)?

_***Thanks in advance for your future replies!***_

Daniel :P

---

### Post by kerry_s on 2011-03-14
unmaximize chrome
hold alt+left mouse click & drag the whole window past the top just to where the tab starts
grab the bottom edge of the window & pull it all the way to the bottom
right click the chrome launcher & quit

now should open fine.

---

### Post by Sashin on 2011-03-14
That doesn't work at all...

---

### Post by kerry_s on 2011-03-14
> **Sashin said:**
> That doesn't work at all...

i'll go pic's then.

ps: if some web site resizes your window, you might have to fix again.

---

### Post by VinDSL on 2011-03-15
> **kerry_s said:**
> i'll go pic's then.
Heh!  I love pics!  :D

Ok, here's what I see, when I start Chromium.

[LIST]
[*]Always starts in maximized mode.
[*]I click the maximize button, and it resizes.
[*]Everything stays that way until I close and restart.
[/LIST]
This is 'normal' behavior, yes?

Or, do I have problems, and not realize it?!?!?

---

### Post by kerry_s on 2011-03-15
> **VinDSL said:**
> Heh!  I love pics!  :D

Ok, here's what I see, when I start Chromium.

[LIST]
[*]Always starts in maximized mode.
[*]I click the maximize button, and it resizes.
[*]Everything stays that way until I close and restart.
[/LIST]
This is 'normal' behavior, yes?

Or, do I have problems, and not realize it?!?!?


if your not getting that gap(see pic 1) where the title bar should be your fine.
as far as i can tell it only happens when the window is smaller then the screen area.

---

### Post by VinDSL on 2011-03-15
BTW, just a thought...

I wonder if this could be related to the theme?!?!?

I'm running "Ubuntu Black Magic Theme - U.F."

Linkage: [https://chrome.google.com/extensions/detail/nnckfbibnhikbljjnipfknnmjpafdbla](https://chrome.google.com/extensions/detail/nnckfbibnhikbljjnipfknnmjpafdbla)

I run this theme in both Google Chrome & Chromium...  ;)

Extra credit:

Changing these flags will make a huge difference in performance.

[INDENT]Go to about:flags
Enable GPU Accelerated Compositing
Enable GPU Accelerated Canvas 2D
Enable Web Page Prerendering
Restart Now (bottom-left of about:flags page)[/INDENT]

This works in both Chrome & Chromium too...

---

### Post by kerry_s on 2011-03-15
> **VinDSL said:**
> BTW, just a thought...

I wonder if this could be related to the theme?!?!?

I'm running "Ubuntu Black Magic Theme - U.F."

Linkage: [https://chrome.google.com/extensions/detail/nnckfbibnhikbljjnipfknnmjpafdbla](https://chrome.google.com/extensions/detail/nnckfbibnhikbljjnipfknnmjpafdbla)

I run this theme in both Google Chrome & Chromium...  ;)

Extra credit:

Changing these flags will make a huge difference in performance.

[INDENT]Go to about:flags
Enable GPU Accelerated Compositing
Enable GPU Accelerated Canvas 2D
Enable Web Page Prerendering
Restart Now (bottom-left of about:flags page)[/INDENT]

This works in both Chrome & Chromium too...

no theme don't matter.
i always have those flags on.

thanks for the flags reminder, i just turned those off & now hulu.com works again. been looking for why i was getting black screen with only sound, been searching all day! :)

---

### Post by VinDSL on 2011-03-15
> **kerry_s said:**
> thanks for the flags reminder, i just turned those off & now hulu.com works again. been looking for why i was getting black screen with only sound, been searching all day! :)LoL!  :D

Every cloud has a silver lining...

---

### Post by VinDSL on 2011-03-15
You know, now you got me thinking!

I was looking at your pics again and remembered...

When I first installed Chromium, I had that ugly RED gap at the top, but I had bigger fish to fry.

The first thing I do, when I install a browser, is import my bookmarks.

With Chromium, I got lazy and copy n' pasted my Chrome data into it.

I went to ~/.config/google-chrome and copy n' pasted everything to ~/.config/chromium

When I restarted Chromium, all of my Chrome bookmarks, passwords, history, settings, et cetera, were there.  

The only thing missing was the ugly red gap at the top.

Just saying...  ;)

---

### Post by kerry_s on 2011-03-15
you don't use sync?
i use sync, so no matter what computer all my stuff is there, currently i'm on my google notebook turning off those flags.

---

### Post by VinDSL on 2011-03-15
> **kerry_s said:**
> you don't use sync?
i use sync, so no matter what computer all my stuff is there, currently i'm on my google notebook turning off those flags.
I run my own Xmarks FTP server, for syncing, but it only works with Firefox.  It's sitting in Atlanta, so yes, I sync remotely.

Here's my local drill...

I sync Firefox using Xmarks.  Then, for 'syncing' Chrome/Chromium, I delete all the existing bookmarks (and passwords) and import them from Firefox.

Sounds kind of contrived (and it is) but it's easy, and takes less time than typing this reply...  ;)

---

### Post by kerry_s on 2011-03-15
you do know there's xmarks for chrome/chromium:
[https://chrome.google.com/webstore/detail/ajpgkpeckebdhofmmjfgcjjiiejpodla](https://chrome.google.com/webstore/detail/ajpgkpeckebdhofmmjfgcjjiiejpodla)

might make even that easier, so you don't have to import every time you make changes in firefox.

i don't use firefox anymore, never even opened it, just remove & replace with epiphany browser, which i only use as a backup browser, for example when i was trying to figure out that hulu mess.

---

### Post by VinDSL on 2011-03-16
> **kerry_s said:**
> you do know there's xmarks for chrome/chromium:
[https://chrome.google.com/webstore/detail/ajpgkpeckebdhofmmjfgcjjiiejpodla](https://chrome.google.com/webstore/detail/ajpgkpeckebdhofmmjfgcjjiiejpodla)

might make even that easier, so you don't have to import every time you make changes in firefox.
Yeah, I knew about that, but...

I run my own Xmarks server, e.g. I don't store the data on their server, I store it on my own server.

Put another way, I'm using Xmarks for a front-end, and storing the data to my server.

The last I checked, you can't store Chrome/Chromium data on your own Xmarks server, using that extension.  You have to save the data to their server(s).

Personally, I don't trust my personal data to servers that I have no control over, you know?

---

