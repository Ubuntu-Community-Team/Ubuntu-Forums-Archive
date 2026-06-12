---
title: "[SOLVED] Canonical Repositories Mess Up"
date: 2007-12-06
forum: Multimedia &amp; Video
---

### Post by skwon11 on 2007-12-06
I'm a newbie... thank you to anybody who replies.

In an effort to get flash video to play I followed the lead of this website [https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu) and attempted to download the Canonical repositories (I'm running 6.06).  

I now get this message when opening Synaptic

E: Type 'http://archive.canonical.com/ubuntu' is not known on line 32 in source list /etc/apt/sources.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.

Can anybody tell me what happened?  Even better... how do I get rid of this?  Thanks again.

---

### Post by kko1 on 2007-12-06
Hello.

You probably wanted to add a "custom" repository, which would require you to write the entire line in the dialog box given. My guess, based on the error message, is that you at least forgot the "deb " from the start. It's good you mentioned the version you are using, you want *dapper* repositories. I suspect the line you were going for is this:

```
deb http://archive.canonical.com/ubuntu dapper-commercial main
```

You can also edit the file */etc/apt/sources.list* manually.

All lines (repository entries) in the file should begin either with "deb " (for binary packages, that is, programs) or with "deb-src " (for source code), or be *commented out* with a # character.

Please let us know if this helps, and mark the thread resolved accordingly. ;)

kko1

---

### Post by skwon11 on 2007-12-06
Thanks again...

Not working.  I pasted the line of code you wrote and now the folllowing appears.  

First

[B]Could not download all repository indexes

The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.[/B]

Followed by

[B]E: Type 'http://archive.canonical.com/ubuntu' is not known on line 31 in source list /etc/apt/sources.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: Type 'http://archive.canonical.com/ubuntu' is not known on line 31 in source list /etc/apt/sources.list
E: Unable to lock the list directory[/B]

I don't know if it makes a difference but I don't see a matching LTS Updates Binary package to a Source one.  

Thanks again to anybody helping me.  If all fails, I guess I can reinstall... but I'd rather learn something then accept failure.

---

### Post by kko1 on 2007-12-06
Hello again.

Let's see if we can't get this sorted out. ;)

Could you copy & paste your */etc/apt/sources.list*, so we can see what's there and what's not.

Please do it inside "code" tags (you get those from the # character in the toolbar, when writing).

```
Like this.
```

kko1

Edit: PS. This is by far not serious enough to need a re-install, don't worry. :) Plus, it's a good attitude to rather learn than give up.

Edit 2: Also take a look at [https://help.ubuntu.com/community/Repositories/CommandLine](https://help.ubuntu.com/community/Repositories/CommandLine) (linked to from the instruction page you were using). You don't have to manage repositories from the command line, but the page will give you a better idea about what the *repository entries* mean.

Edit 3: Mods, if you notice - this thread could probably be moved to beginner talk, as it's turned out to be mostly about repositories at this point.

---

### Post by skwon11 on 2007-12-06
Thanks for the encouragement.

As requested...

```
## Major bug fix updates produced after the final release of the
## distribution.
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu/ dapper universe main restricted multiversedeb-src http://us.archive.ubuntu.com/ubuntu/ dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu dapper-security main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted
deb http://security.ubuntu.com/ubuntu dapper-security universe
deb-src http://security.ubuntu.com/ubuntu dapper-security universe
http://archive.canonical.com/ubuntu feisty-commercial main

deb http://archive.canonical.com/ubuntu dapper-commercial main

```

---

### Post by kko1 on 2007-12-07
Hello.

It was as I suspected, there's an entry that's missing "deb " from the start. (The page I referred to tells you the intended format of a repository entry, that is, of a single line in */etc/apt/sources.list*.)

This is the wrong entry:
```
http://archive.canonical.com/ubuntu feisty-commercial main
```

The above entry is also wrong in another way, because it refers to "feisty", which is Ubuntu 7.04, that is two versions newer than "dapper". You want all your *ubuntu* repositories to refer to the same version. (If you get to using external (non-ubuntu) repositories for some programs later on, they may be using different names for their repositories, but don't worry about that at this point.)

*Now that you've added the line I suggested, at the bottom of your sources.list, you can remove the above entry.* (Editing the file manually, with *super user* capabilities is probably the easiest way.)

***

There seems to also be another editing mistake in the file:
```
deb http://archive.ubuntu.com/ubuntu/ dapper universe main restricted multiversedeb-src http://us.archive.ubuntu.com/ubuntu/ dapper universe
```

You'll notice that it's two lines wrapped up to one. Maybe it happened when you were pasting the file, or maybe it's in the original file. If it's in the original file, you have to fix it.

Replace the above entry with this one, that contains two entries, one "deb " and one "deb-src ":
```
deb http://archive.ubuntu.com/ubuntu/ dapper main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper main restricted universe multiverse
```

You will notice that I re-organised the lines so the order is "main restricted universe multiverse". See [http://www.ubuntu.com/community/ubuntustory/components](http://www.ubuntu.com/community/ubuntustory/components) for an explanation of these *components*.

One more tip, to help you understand the *repository entries*. This:
```
deb http://archive.ubuntu.com/ubuntu/ dapper main restricted universe multiverse
```
...is the same as this:
```
deb http://archive.ubuntu.com/ubuntu/ dapper main
deb http://archive.ubuntu.com/ubuntu/ dapper restricted
deb http://archive.ubuntu.com/ubuntu/ dapper universe
deb http://archive.ubuntu.com/ubuntu/ dapper multiverse
```

***

Two more things. One, you have "dapper-updates" enabled, but only for "deb-src ". I think you want to have it enabled also for the actual (binary) packages. So, replace this:
```
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper-updates main restricted
```
...with this:
```
deb http://us.archive.ubuntu.com/ubuntu/ dapper-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper-updates main restricted
```

And two, since you generally have *multiverse* enabled, you could enable it also in the "dapper-security" repositories. Replace this:
```
deb http://security.ubuntu.com/ubuntu dapper-security universe
deb-src http://security.ubuntu.com/ubuntu dapper-security universe
```
...with this:
```
deb http://security.ubuntu.com/ubuntu dapper-security universe multiverse
deb-src http://security.ubuntu.com/ubuntu dapper-security universe multiverse
```

This should fix your *sources.list*. Now, I could've just done those edits myself, and pasted you the complete file, but this way you'll probably better see how it works. ;)

After that, good luck with the flash. If you can't work it out on your own, it's probably more useful to start a new thread for that topic rather than continue in this one.

Hope this helped.

kko1

---

### Post by skwon11 on 2007-12-07
Thank you... like a charm... one last thing... in downloading I received a message that one of the respositories could not be... as follows...

**[http://us.archive.ubuntu.com/ubuntu/dists/dapper-backports/Release:](http://us.archive.ubuntu.com/ubuntu/dists/dapper-backports/Release:) Unable to find expected entry  unive$deb-src/binary-i386/Packages in Meta-index file (malformed Release file?)**

Should I worry?  Thank you again.

---

### Post by wolfen69 on 2007-12-07
it is nothing to worry about.

---

### Post by kko1 on 2007-12-07
Hi!

Good to hear that it worked. And yes, like wolfen69 said, you shouldn't worry about that error. It's not serious, and moreover it seems to be in the repository end, so you couldn't fix it if you tried. ;)

Now you could mark the thread *(re)solved*, so it'll be clear in the listings. You can do that from the "Thread tools" -menu above the thread, when viewing the thread.

Have fun with your Ubuntu! :)

kko1

---

