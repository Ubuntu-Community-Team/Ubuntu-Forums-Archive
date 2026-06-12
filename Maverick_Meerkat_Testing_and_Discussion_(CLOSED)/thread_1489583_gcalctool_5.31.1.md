---
title: "gcalctool 5.31.1"
date: 2010-05-21
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by go7Ul1ai on 2010-05-21
I like the update to Calculator (gcalctool). It makes me happy.

[IMG]http://imgur.com/bVXnA.png[/IMG]

---

### Post by philinux on 2010-05-21
Is it the nice pastel shades? ;)

---

### Post by MacUntu on 2010-05-21
I'm just glad the base conversion got reworked - the way it was during Lucid before they decided to revert it was a catastrophe.

---

### Post by vkontakte on 2010-05-21
> **lee.jarratt said:**
> I like the update to Calculator (gcalctool). It makes me happy.

[IMG]http://imgur.com/bVXnA.png[/IMG]
I can't understand why to repeat hand calculator?

---

### Post by 23meg on 2010-05-21
And on top of it all, [it now starts faster than Chromium]("http://castrojo.tumblr.com/post/619330509").

---

### Post by gnomeuser on 2010-05-21
> **23meg said:**
> And on top of it all, [it now starts faster than Chromium]("http://castrojo.tumblr.com/post/619330509").

I think this adds more weight to Chromiums process than it does to anything else. They are paranoid about being slow so they test rigorously for performance and correctness. gcalctools failure to do so allowed it's developers to simply not know that their code sucked.. In ignorance shall be found the seed of all failure.

---

### Post by zekopeko on 2010-05-21
> **gnomeuser said:**
> I think this adds more weight to Chromiums process than it does to anything else. They are paranoid about being slow so they test rigorously for performance and correctness. gcalctools failure to do so allowed it's developers to simply not know that their code sucked.. In ignorance shall be found the seed of all failure.

It would be good if distros would benchmark apps (at least those in the default install) on some basic things such as startup time (on a reference machine). It's up to app developers to implement a more comprehensive test suite.

---

### Post by kahumba on 2010-05-21
> **gnomeuser said:**
> I think this adds more weight to Chromiums process than it does to anything else. They are paranoid about being slow so they test rigorously for performance and correctness. gcalctools failure to do so allowed it's developers to simply not know that their code sucked.. In ignorance shall be found the seed of all failure.

I'm glad you mentioned the word ignorance.
It's amazing that they didn't bother fixing it until they were put to shame openly in such a fashion, so yes, ignorance is probably the best word for this phenomena.
Now, they also need to make gedit start up faster (obviously it's got a slow startup for a text editor no matter if with or without plugins , and obviously comparing it to the startup of Chrome is unfair since the latter is orders of magnitude more sophisticated).

Once they're done with gedit (if problem acknowledged in the first place) I got a whole (shameful) list of other silly slow stuff that a self respecting (in this context, Gnome) developer wouldn't commit, unless there's ignorance.

---

### Post by gnomeuser on 2010-05-21
> **kahumba said:**
> I'm glad you mentioned the word ignorance.
It's amazing that they didn't bother fixing it until they were put to shame openly in such a fashion, so yes, ignorance is probably the best word for this phenomena.
Now, they also need to make gedit start up faster (obviously it's got a slow startup for a text editor no matter if with or without plugins , and obviously comparing it to the startup of Chrome is unfair since the latter is orders of magnitude more sophisticated).

Once they're done with gedit (if problem acknowledged in the first place) I got a whole (shameful) list of other silly slow stuff that a self respecting (in this context, Gnome) developer wouldn't commit, unless there's ignorance.

Before people accuse me of calling the gcalctool developers fools, ignorance here is meant in the form of being unknowledgable.

To address a problem, you must first be aware that one exists.

Clearly the gcalctool developers never realized that they had grown slow at application startup. This however is telling of most projects, we don't have the capability to easily see what impact changes made to the project have. 

This is what projects such as GStreamer and Chromium do well, Chromium specifically compile tests every commit and they run regression tests to ensure that they know that their correctness, stability and performance never regress. This is policy, WebKit e.g. has a policy of never becoming slower. 

The unknown is the enemy, remember children verifiable knowledge can never be underestimated. Even if that is the knowledge that you suck.

---

### Post by kahumba on 2010-05-22
I kept smiling while reading your reply. Are you kidding me?
Please don't confuse stuff/regressions that are hard to detect with the obvious ones. I'm clearly talking about the latter. I'm also talking about those devs who developed the (slow) stuff like gedit, Evolution, Nautilus which is the slowest file browser I ever used on any OS which is slow at both start-up and file-browsing (listing), they just didn't do their homework, but I did, I actually learned on purpose a bit of C++ and gtkmm (I'm a Java dev) and starting developing "my own" file browser exactly because of Nautilus and cause there's no other decent file browser (thunar has its own glitches) and it was pretty easy getting it to startup fast and list files orders of magnitude faster (I can give you examples) while keeping the appearance (the order) of the files exactly as in Nautilus with their appropriate icons, description and so on, in other words, I've come to the conclusion Nautilus is poorly/lazily written. Sadly I'm working on a commercial product so I had to freeze this development.

I'm sorry that in the Linux community there's many folks who are just protective and find whatever excuses or just hijack the issue which is part of the reason why such problems persist for a long time.

I could go on and on and you could of course find excuses or half truths of why I'm "silly" or plain "wrong" or just tell me like "it's open source make a better one" or so.

---

### Post by zekopeko on 2010-05-22
@kahumba

Might I suggest you look at Dash? It's C# so it should be more familiar to you as a Java  dev. Plus it's a side project of the awesome Daniel Fore who created Nautilus-Elementary. 

[https://launchpad.net/dashfilebrowser](https://launchpad.net/dashfilebrowser)

---

### Post by vkontakte on 2010-05-22
> **zekopeko said:**
> @kahumba

Might I suggest you look at Dash? It's C# so it should be more familiar to you as a Java  dev. Plus it's a side project of the awesome Daniel Fore who created Nautilus-Elementary. 

[https://launchpad.net/dashfilebrowser](https://launchpad.net/dashfilebrowser)
It's strange to suggest anything on mono. It's mono pain apps written on it are slow at startup.

---

### Post by kahumba on 2010-05-22
> **zekopeko said:**
> @kahumba

Might I suggest you look at Dash? It's C# so it should be more familiar to you as a Java  dev. Plus it's a side project of the awesome Daniel Fore who created Nautilus-Elementary. 

[https://launchpad.net/dashfilebrowser](https://launchpad.net/dashfilebrowser)

Thanks a lot, but I dislike Mono. Also, even if it hadn't ties with Microsoft I'd still not use it because a file browser to be really successful must have a fast startup and (less important but still pretty much important) consume relatively little memory which can't really be achieved if using solutions like Java/Mono or alike.

Edit: btw I did try to implement a file browser first in Java and it went along quite well, it listed files very quickly and so on, but for such types of apps a fast startup and a reasonable amount of memory usage  are a must and I couldn't achieve it, so I had to bite the bullet and learn C++/gtkmm.

---

### Post by zekopeko on 2010-05-22
> **vkontakte said:**
> It's strange to suggest anything on mono. It's mono pain apps written on it are slow at startup.

That isn't actually true. Startup time depends on numerous factors. Try Pinta which is a C# app and is yet super fast to start.

---

### Post by zekopeko on 2010-05-22
> **kahumba said:**
> Thanks a lot, but I dislike Mono. Also, even if it hadn't ties with Microsoft I'd still not use it because a file browser to be really successful must have a fast startup and (less important but still pretty much important) consume relatively little memory which can't really be achieved if using solutions like Java/Mono or alike.

Edit: btw I did try to implement a file browser first in Java and it went along quite well, it listed files very quickly and so on, but for such types of apps a fast startup and a reasonable amount of memory usage  are a must and I couldn't achieve it, so I had to bite the bullet and learn C++/gtkmm.

I suggest you try building Dash from source. I'm getting 6.9mb of RAM usage when displaying my home. 

Nice thing about it is that it's using Cairo for the file views so it could provide some nice effects later on.

---

### Post by kahumba on 2010-05-22
Thanks, that sounds very good, but as I mentioned C# is out of question because it has dubious ties with Microsoft (to say the least) and since the FSF said that the patent situation around the C#/Mono stack (despite being GPLv2) is uncertain and we should avoid it if possible I tend to trust them (more, than to Microsoft/Novell).

---

### Post by zekopeko on 2010-05-22
> **kahumba said:**
> Thanks, that sounds very good, but as I mentioned C# is out of question because it has dubious ties with Microsoft (to say the least) and since the FSF said that the patent situation around the C#/Mono stack (despite being GPLv2) is uncertain and we should avoid it if possible I tend to trust them (more, than to Microsoft/Novell).

FSF is FUD-ing.
If you use parts of the Mono stack that are part of the ECMA spec you are safe from patents (at least from Microsoft).

But no matter. Have you considered writing patches for Nautilus instead? Writing another browser from scratch looks like a waste of effort to me.

---

### Post by kahumba on 2010-05-22
> **zekopeko said:**
> Have you considered writing patches for Nautilus instead? Writing another browser from scratch looks like a waste of effort to me.
1) Nautilus is written in C, as I Java dev I like C++ (much) more.
2) I'm free to implement what _I_ consider important and it will work the way _I_ consider important.
3) There's just too much to change in Nautilus and getting that much changed would be impossible because they'd  simply not agree.
For example I think the file manager window must use less space for gui tools and more space for actual content (area where files are listed), that is, a "Google Chrome approach" to file browsers, among others, remove the "menu bar" altogether, a toolbar which to the left contains useful buttons like "new", "copy" and to the right (the rest of it) works like the "bookmars toolbar" in Firefox with easy drag-n-drop and "bookmark folders" support, a way to quicker mark files as executable in literally 2 clicks and many other quick and useful and well thought "hacks" which for a normal Linux user should prove very handy, including a way to pause and resume file copy/move operations.

---

### Post by zekopeko on 2010-05-22
> **kahumba said:**
> 1) Nautilus is written in C, as I Java dev I like C++ (much) more.
2) I'm free to implement what _I_ consider important and it will work the way _I_ consider important.
3) There's just too much to change in Nautilus and getting that much changed would be impossible because they'd  simply not agree.
For example I think the file manager window must use less space for gui tools and more space for actual content (area where files are listed), that is, a "Google Chrome approach" to file browsers, among others, remove the "menu bar" altogether, a toolbar which to the left contains useful buttons like "new", "copy" and to the right (the rest of it) works like the "bookmars toolbar" in Firefox with easy drag-n-drop and "bookmark folders" support, a way to quicker mark files as executable in literally 2 clicks and many other quick and useful and well thought "hacks" which for a normal Linux user should prove very handy, including a way to pause and resume file copy/move operations.

So basically KDE's Dolphin with some enchantments.

---

### Post by kahumba on 2010-05-22
I saw the KDE Dolphin and I didn't like it, I'd rather say a Mac Finder with enhancements plus features.

---

### Post by vkontakte on 2010-05-22
&#1087;&#1080;&#1086;&#1085;&#1077;&#1088;&#1080;&#1103; &#1085;&#1072; &#1084;&#1072;&#1088;&#1096;&#1077; :d

---

### Post by zekopeko on 2010-05-22
> **kahumba said:**
> I saw the KDE Dolphin and I didn't like it, I'd rather say a Mac Finder with enhancements plus features.

When I read "a toolbar which to the left contains useful buttons like "new", "copy"  the first thing to pop in my mind was Windows XP's Explorer. It had something similar. Dolphin crossed my mind because it has left and right sidebar.

---

### Post by kahumba on 2010-05-22
@ [vkontakte]("http://ubuntuforums.org/member.php?u=1076998") I know Russian but I don't get what exactly you mean by that, and afaik you're not allowed to talk here anything but English.

---

### Post by kahumba on 2010-05-22
> **zekopeko said:**
> When I read "a toolbar which to the left contains useful buttons like "new", "copy"  the first thing to pop in my mind was Windows XP's Explorer. It had something similar. Dolphin crossed my mind because it has left and right sidebar.
Well my version will be without sidebars (on purpose), instead it will have a "Places" button which will pop a list with 2 types of files: "important folders" (like the traditional Desktop, home, music, video folders) and below, the "mounted" partitions, see screen.jpeg, it's what I managed to do in Java before I dumped it and started implementing it in C++ (screen2.jpeg) but there's still quite a lot to be added and changed to the C++ version.
This "Places" button will probably morph over time into a "Live" button which will change it's list of items depending on the current situation, not sure for now, anyway I'm working on another thing right now so I won't come back to it anytime soon.

---

### Post by zekopeko on 2010-05-22
> **kahumba said:**
> Well my version will be without sidebars (on purpose), instead it will have a "Places" button which will pop a list with 2 types of files: "important folders" (like the traditional Desktop, home, music, video folders) and below, the "mounted" partitions, see screen.jpeg, it's what I managed to do in Java before I dumped it and started implementing it in C++ (screen2.jpeg) but there's still quite a lot to be added and changed to the C++ version.
This "Places" button will probably morph over time into a "Live" button which will change it's list of items depending on the current situation, not sure for now, anyway I'm working on another thing right now so I won't come back to it anytime soon.

If I were you I would stick with sidebars. Todays widescreens have more horizontal space then vertical. Sticking everything in a toolbar isn't such a good idea. I suggest you look at the mockups by DanRabbit on DeviantArt (if you missed them).

---

### Post by kahumba on 2010-05-22
Many people would agree with you, however the interactive difference is 1 click vs 2 clicks, but the saved space is huge. So I'd rather issue one more click once in a while than have constantly occupied about 1/4 of the file browser area by a side pane (not to mention 2 side panes!).
You're free to disagree, that's one of the reasons I'm doing it on my own and hopefully release it to the folks in the open, some might like it too.

---

### Post by knarf on 2010-05-25
Before embarking on YetAnotherFileManagerProject you might want to have a look at rox filer, available in the rox-filer package. It seems to fulfill many of your requirements as it uses available screen space efficiently, lacks sidebars and menu bar, is low on resources and fast to start. It is written in C though which you seem to dislike and it is based around some RISC-OS derived concepts which are rather alien to the current Gnome desktop.

It is also one of the better file managers to use with a tiling window manager like Xmonad or Ion - just an added benefit for those who like that sort of WM.

---

### Post by kahumba on 2010-05-25
> **knarf said:**
> Before embarking on YetAnotherFileManagerProject you might want to have a look at rox filer, available in the rox-filer package. It seems to fulfill many of your requirements as it uses available screen space efficiently, lacks sidebars and menu bar, is low on resources and fast to start. It is written in C though which you seem to dislike and it is based around some RISC-OS derived concepts which are rather alien to the current Gnome desktop.

It is also one of the better file managers to use with a tiling window manager like Xmonad or Ion - just an added benefit for those who like that sort of WM.

Thanks, I just installed it, it's fun using it and even a bit entertaining cause it indeed behaves "differently" and is fast. But I can't use it for serious because it doesn't support a lot of essential stuff from the free desktop specification (doesn't use native icons/theme, and even doesn't know how to open jpeg, png, etc types of files), I won't go further because this alone is a game "stopper".
My first file manager in Java was like this - didn't use the system icons and didn't know how to handle files (which app to start to open a given type of file, so in the end I had to learn the free desktop specifications) which I hoped the user would customize himself but it was naive to think so, only a minority of ppl would do that.

---

### Post by knarf on 2010-05-25
> **kahumba said:**
> Thanks, I just installed it, it's fun using it and even a bit entertaining cause it indeed behaves "differently" and is fast. But I can't use it for serious because it doesn't support a lot of essential stuff from the free desktop specification (doesn't use native icons/theme, and even doesn't know how to open jpeg, png, etc types of files), I won't go further because this alone is a game "stopper".
You could take the current code and add the fdo-related stuff. Rox file knows about mime types but it uses its own mechanism to decide which action to apply ('Run Action' in the context menu, choices stored in individual files in .config/rox.sourceforge.net/MIME-types/). You had just not configured filer to open those file types. One of the things you could do is add those missing bits: fdo-compatible mime support (either by changing filer or adding some code to create files in  .config/rox.sourceforge.net/MIME-types/), additional theme support (it does have themes but does things its own way, this could be changed or wrapped) etc. The basic file management infrastructure it offers is sound so it would make a good starting point.

---

### Post by vikrant82 on 2010-05-25
> **knarf said:**
> Before embarking on YetAnotherFileManagerProject you might want to have a look at rox filer, available in the rox-filer package. It seems to fulfill many of your requirements as it uses available screen space efficiently, lacks sidebars and menu bar, is low on resources and fast to start. It is written in C though which you seem to dislike and it is based around some RISC-OS derived concepts which are rather alien to the current Gnome desktop.

It is also one of the better file managers to use with a tiling window manager like Xmonad or Ion - just an added benefit for those who like that sort of WM.

Rocks!! Awesome!! Made my day :) Dolphin, you had your time!!

> oesn't use native icons/theme, and even doesn't know how to open jpeg, png, etc types of files), I won't go further because this alone is a game "stopper"
I could make it to use any icon theme I like.  Its there in the preferences.
Also, I am happily able to open files, once I define action for that MIME type?

---

### Post by ammonkey on 2010-05-25
@kahumba your screenshots looks good. i would definitly be interested looking/testing the code. Is there any available repository?

---

### Post by kahumba on 2010-05-25
Thanks, as I said in a post earlier the development is frozen cause I'm currently working on a commercial product, but as I finish it and get back to the file browser and make it usable for a normal user I'll send you a notice.

---

