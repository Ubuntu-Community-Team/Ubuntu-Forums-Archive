---
title: "New in ubiquity = wubi default if partition table full?"
date: 2011-03-08
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by kansasnoob on 2011-03-08
I'm going to be doing some ubiquity testing later today with the new daily build and I was just parsing the changelog:

> ubiquity (2.5.23) natty; urgency=low

  [ Evan Dandrea ]
  * Ensure we always have an automatic partitioning option selected.
  * Merge in latest change to apt-clone from Michael Vogt:
    - Current apt_pkg API methods.
    - Better command line argument parsing.
    - Set DPkg::Chroot-Directory (LP 727758).
  * Do not attempt to proceed to a second page with the biggest_free
    option (LP: #727842, LP: #652852).  This will change once we have an
    interface for the biggest_free option.
  [B][COLOR="Red"]* If the partition table is full and a copy of Windows exists, replace the
    resize option with a copy of wubi.exe to the Windows startup folder,
    followed by a reboot.[/COLOR][/B]
  * Temporary fix for translations with carriage returns (LP: #730498).
  * Update translations from Launchpad.
  * Automatic update of included source packages: console-setup
    1.57ubuntu10.

  [ Colin Watson ]
  * Set Dir::Media::MountPath as well as Acquire::cdrom::mount (in line with
    base-installer), and pass all the options set by configure_apt to
    python-apt as well so that attempts to install packages from python-apt
    will behave consistently (LP: #727783).

  [ Julien Lavergne ]
  * bin/ubiquity-dm:
   - Wait lxsession before launching the panel, to have theming support.
     (LP: #684802)
  * src/panel/panel.c
   - Load lxpanel background for the panel when it's available.

 -- Evan Dandrea <ev@ubuntu.com>  Mon, 07 Mar 2011 09:16:26 +0000


I don't use Wubi - I don't even have Windows installed anymore - so I thought I'd give a shout out to those testers who might be interested in checking that out. I do have an old Win XP computer stashed away so I'll probably drag it out before Beta 1 :)

---

### Post by dino99 on 2011-03-08
i'm feeling that design become worst and worst

---

### Post by coffeecat on 2011-03-08
> [B][COLOR=Red]* If the partition table is full and a copy of Windows exists, replace the
    resize option with a copy of wubi.exe to the Windows startup folder,
    followed by a reboot.[/COLOR][/B]Hmmm. I think I can see where they're coming from. No doubt this is for newcomers - at least give them an option to try Ubuntu out rather than dumping them into the advanced partitioning option. An experienced user should know what to do about a full partition table anyway.

I'll give it a try if I can find time - I'm using my test machine for some bug testing on an app developed by another forum member atm. But thanks for pointing this out, kansasnoob. :)

---

### Post by kansasnoob on 2011-03-08
> **dino99 said:**
> i'm feeling that design become worst and worst

I think it's generally a good idea. Of course since I don't commonly use Wubi I have no idea what the current status of the bugs addressed here is:

[http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198)

We're seeing more and more Win 7 machines, particularly laptops/netbooks, that have 4 primary partitions by default. So I think Wubi **[COLOR="Red"]should[/COLOR]** be a reliable alternative for those who have no knowledge of safe partitioning practices.

At least in this situation the user would already have an Ubuntu Live CD/USB in their possession so they could easily fix any boot problems encountered in Wubi :) One of my greatest frustrations has been encountering a user that performed a Wubi install with no live media available to repair things if they break :(

---

### Post by dino99 on 2011-03-08
> **kansasnoob said:**
> I think it's generally a good idea. Of course since I don't commonly use Wubi I have no idea what the current status of the bugs addressed here is:

[http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198)

We're seeing more and more Win 7 machines, particularly laptops/netbooks, that have 4 primary partitions by default. So I think Wubi **[COLOR="Red"]should[/COLOR]** be a reliable alternative for those who have no knowledge of safe partitioning practices.

At least in this situation the user would already have an Ubuntu Live CD/USB in their possession so they could easily fix any boot problems encountered in Wubi :) One of my greatest frustrations has been encountering a user that performed a Wubi install with no live media available to repair things if they break :(

Cant understand that wubi way:

- dont need to add confusion and complication by adding wubi (newcomers have never heard about that thing anyway, and instead of having a real install, they get a fake one: realy stupid)

- instead of wubi fallback choice, it might popup a detailed manual installation howto including the different cases like w7, raid, resizing partitions, ... and a link pointing to a sticky on ubuntuforums about "partitioning" if a newcomer need to know.

---

### Post by zekopeko on 2011-03-08
> **dino99 said:**
> Cant understand that wubi way:

- dont need to add confusion and complication by adding wubi (newcomers have never heard about that thing anyway, and instead of having a real install, they get a fake one: realy stupid)

- instead of wubi fallback choice, it might popup a detailed manual installation howto including the different cases like w7, raid, resizing partitions, ... and a link pointing to a sticky on ubuntuforums about "partitioning" if a newcomer need to know.

Hahaha! You say "i'm feeling that design become worst and worst " and then propose an infinitely more complex solution. Brilliant.

---

### Post by dino99 on 2011-03-08
> **zekopeko said:**
> Hahaha! You say "i'm feeling that design become worst and worst " and then propose an infinitely more complex solution. Brilliant.

Reading a single howto is more brilliant than headache app, better to learn how to do than blindly hit "Enter" key and falling back to that wubi thing adding its own bugs

---

### Post by kansasnoob on 2011-03-08
@ dino99,

Currently if 4 primary partitions already exist it throws the noob into learning what partition is or is not safe to remove/copy-n-move/etc. And I've tried many times to explain Linux/Ubuntu device designations to Windows users and, even after doing so they come back with a reply something like:

> So should I delete drive C or drive E

And I often say, "did you not read what I said about device designations?"

So, if we can simplify things, I think that's great!

I think a large part of the problem is that we end-users tend to think development resources are endless because SABDFL is pretty darn rich. No doubt Ubuntu only exists because of his generosity but ......................

---

### Post by coffeecat on 2011-03-08
> **dino99 said:**
> 
- instead of wubi fallback choice, it might popup a detailed manual installation howto including the different cases like w7, raid, resizing partitions, ... and a link pointing to a sticky on ubuntuforums about "partitioning" if a newcomer need to know.

And you think a newcomer who knows nothing about partitioning will read that? No. They will give up discouraged and try another distro or simply go back to Windows thinking that Ubuntu is too geeky for them. Giving them an opportunity to try Ubuntu using wubi gives them a taste. If they like what they see and then want to learn about partitioning they have all the members of this forum to help when they at least have some experience of the Ubuntu desktop.

---

### Post by bcbc on 2011-03-08
Thanks for the heads up kansasnoob. I'm puzzled by this development... I get the impression the developers don't like Wubi (zero maintenance *or even comments* on critical bugs), but yet it seems to keep being pushed into a more prominent place (recently the ubuntu.com download site, and now this) so clearly some big cheese at Canonical likes it. Maybe the big cheese should also hire some wubi developers.

PS wubi [doesn't yet work]("https://bugs.launchpad.net/ubuntu/+bug/693671") in Natty

---

### Post by macroshaft on 2011-03-08
> **dino99 said:**
> Reading a single howto is more brilliant than headache app, better to learn how to do than blindly hit "Enter" key and falling back to that wubi thing adding its own bugs

Dino, try to remember you come at this as an experienced user. Ubuntu aims itself at average Joe user so the people who will be using this don't care what wubi is, they don't care what a partition table is. They don't want to have to learn how to do rocket science with their hard disk and that's why they haven't switched to linux years ago.

What is offered here is a option that says 'this looks like it could get tricky, click this button to just make it go'. Anyone who wants to know more will certainly pick it up quick enough but if we want to appeal to the masses the installer needs to just work, even if you don't know anything more advanced than how to check your email.

---

### Post by drs305 on 2011-03-08
I think I like the approach they are taking (by offering a Wubi install when a free partition can't be made).

I do hope more attention is paid to the update bugs though.

---

### Post by coffeecat on 2011-03-11
> **kansasnoob said:**
> > [B][COLOR=Red]* If the partition table is full and a copy of Windows exists, replace the
    resize option with a copy of wubi.exe to the Windows startup folder,
    followed by a reboot.[/COLOR][/B]

I thought  I'd resurrect this thread to do some testing rather than just debate whether or not this is a good idea. :)

Using a test system with Win XP on sda1 and three other primary partitions, I booted up with today's daily. Ubiquity is now 2.5.25.

It does what it says on the tin but rather gracelessly; I hope they work on this. When you click on next with the "install alongside" option ticked, Ubiquity and the live desktop promptly crash (or that's what it looks like). After which I got the little Ubuntu logo and the pulsating coloured dots and I waited, and waited, and waited, and waited... Unsure whether the live USB was booting down, booting up again or booting sideways I forced the issue with the computer reset button and it duly rebooted into Windows with the Wubi installer open. So far, so good, but when I tried to do a wubi install it wanted to download the ISO again. Which is not very friendly to someone with limited bandwidth who has already downloaded the ISO to make the USB/CD and all that does is transfer a 1.4 MB executable to the Windows partition.

Good idea but needs a bit of polish, methinks.

---

### Post by bcbc on 2011-03-11
wubi.exe should find and use the desktop/netbook CD on the local computer. It won't use the alternate or dvd image.

It also won't work so well if you are installing from a USB due to a rather crude check on the size of the ISO (based on the USB partition size). I believe it will work if the USB partition is < ~892MB but haven't tested this.

Also, if you run wubi.exe standalone in this manner, it will allow you to select different flavours - ubuntu, netbook, kubuntu etc. If you get creative and choose something different from the CD it will also download a new copy.

If you're not sure why Wubi is downloading a new image, the log file should give some clues. (Check your windows user's %temp% directory. This one should be called wubi-11.04-rev20x.log.)
It's rev200 right now, but I expect this will change soon as Colin Watson has identified the bug that is preventing Wubi Natty installs.

---

### Post by coffeecat on 2011-03-11
> **bcbc said:**
> It also won't work so well if you are installing from a USB due to a rather crude check on the size of the ISO (based on the USB partition size). I believe it will work if the USB partition is < ~892MB but haven't tested this.

That's interesting. I was using a 4GB USB stick with a persistence file taking up all the available space. I'll burn a CD and try that. Thanks.

---

### Post by Rubi1200 on 2011-03-11
> **coffeecat said:**
> And you think a newcomer who knows nothing about partitioning will read that? No. They will give up discouraged and try another distro or simply go back to Windows thinking that Ubuntu is too geeky for them. Giving them an opportunity to try Ubuntu using wubi gives them a taste. If they like what they see and then want to learn about partitioning they have all the members of this forum to help when they at least have some experience of the Ubuntu desktop.
I completely agree on this point. 

We have already seen enough Wubi users ask on the forums how to make it into a proper install that it is worthwhile pursuing this course of action.

@dino99:  Is Wubi an ideal solution for trying another operating system? Probably not. 

But, it is also not as bad as some users on the forums try to make it out to be; quite unjustifiably in my opinion.

There are plenty of people who came to Ubuntu because of Wubi and the efforts of the Wubi developers.

---

### Post by coffeecat on 2011-03-11
> **coffeecat said:**
> I'll burn a CD and try that.

Yes, it worked somewhat better from a CD, but as soon as I clicked on next after choosing "install alongside" Ubiquity simply vanished and the shutdown sequence started. This bit clearly needs work; it's quite alarming. I was prompted to remove the CD and press enter as usual. Then Windows booted normally and I got the Wubi installer on the desktop. The user does need to know to re-insert the CD at this point. Wubi appeared to install OK from the CD, but when I rebooted and chose Ubuntu from the wubi menu I was greeted with a "Try (hd0,0): NTFS5" error message. Google reveals that I am not alone, but I haven't resolved that one yet.

Ah. The joys of Alpha testing! :wink:

---

### Post by bcbc on 2011-03-11
> **coffeecat said:**
> Yes, it worked somewhat better from a CD, but as soon as I clicked on next after choosing "install alongside" Ubiquity simply vanished and the shutdown sequence started. This bit clearly needs work; it's quite alarming. I was prompted to remove the CD and press enter as usual. Then Windows booted normally and I got the Wubi installer on the desktop. The user does need to know to re-insert the CD at this point. Wubi appeared to install OK from the CD, but when I rebooted and chose Ubuntu from the wubi menu I was greeted with a "Try (hd0,0): NTFS5" error message. Google reveals that I am not alone, but I haven't resolved that one yet.

Ah. The joys of Alpha testing! :wink:

That does sound confusing. The only way around it would be to copy the ISO to the desktop as well, which is a bit much.

Regarding getting stuck (after that Try messaqe) that's the bit that's not working. But the fix has just been released so I guess in the next build there'll be a new wubi.exe.

---

