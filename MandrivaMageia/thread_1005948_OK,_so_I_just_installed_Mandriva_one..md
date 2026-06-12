---
title: "OK, so I just installed Mandriva one."
date: 2008-12-08
forum: Mandriva/Mageia
---

### Post by liamnixon on 2008-12-08
What do I need to know?  By that, I am referring to stuff like command-line tools and basics of RPM.

I was previously using Ubuntu 8.10, by the way.

---

### Post by Vulpus on 2008-12-08
With the latest versions of Mandriva (say from 2007 onwards) you seldom if ever need to use the command line, unless you want to.

You can get details about installing software here:

[http://wiki.mandriva.com/en/Docs/Basic_tasks/Installing_and_removing_software](http://wiki.mandriva.com/en/Docs/Basic_tasks/Installing_and_removing_software)

But really all you need to do is go here:
[http://easyurpmi.zarb.org/](http://easyurpmi.zarb.org/)
and click on the two buttons.  That will setup the repositories for you and you can then use the 'Install & Remove software' function on the main menu.

The biggest diffrence between Ubuntu and 'proper' distros such as Mandriva is that it (Mandriva) uses a Root AND User password.  If you want to install new software you need the root password, if you just want to update your existing software you just need the user password. 

Are you using KDE or Gnome?

---

### Post by ibutho on 2008-12-08
On many RPM based distros, its actually not very often that you use RPM directly. Most distros have some sort of wrapper application that provides things like repository support, automatic dependency resolution etc. On Mandriva, this tool is urpmi and it has a GUI called rpmdrake (you can access the gui by running the rpmdrake command or going to Mandriva Control Center -> Software). This is similar to apt-get and synaptic on Debian/Ubuntu (i.e. they provide added functionality to DPKG).

---

### Post by liamnixon on 2008-12-08
Thanks for the replies!

To answer your question, I'm using gnome.

---

### Post by Vulpus on 2008-12-09
If you are using gnome then you shouldn't find Mandriva too different from Ubuntu.

One other thing to consider is that Mandriva does not install any 'non free' multimedia codecs (expect MP3) by default.

To play files such as MP4, MPEG, AVI etc you have to install these codecs.  The easiest way of doing that is to make sure you have installed the PLF repositories from Easy URPMI (see my previous post) and then try and play the file in Totem (Mplayer).  You will find that the file doesn't play, but if you wait 10-20 seconds you should get a pop-up message asking if you want to install the codec.  There should be a choice of two or more places to download it from.  If you choose Codeina you will have to pay for it, so chosse PLF or Mandriva.

---

### Post by liamnixon on 2008-12-09
Yeah, I have the PLF repository installed now, but RPM seems to run a bit slow.  Is it normally slower that dpkg, or is that just me.

And on a couple minor notes, I can't seem to get rid of the desktop icons (I like my desktop clean), and everything I type is underlined in red.  I'm starting to feel kind of retarded.  It seems like at this stage in my life, I would know how to fix those issues.  I don't THINK I fell off of a turnip truck.  :^o

---

### Post by Vulpus on 2008-12-09
I have seen others say that Synaptic is faster than other systems, so RPM may seem slow to you.

Can't help with the icons as I don't use Gnome.

With regards to everything being underlined in red, I suspect your language settings in Firefox has default to Danish or German or something?

---

### Post by ibutho on 2008-12-09
> **Vulpus said:**
> I have seen others say that Synaptic is faster than other systems, so RPM may seem slow to you.

Can't help with the icons as I don't use Gnome.

With regards to everything being underlined in red, I suspect your language settings in Firefox has default to Danish or German or something?
APT seems to have more or less the same speed as recent versions of YUM and Zypper, but I think urpmi is indeed a little bit slower (I have not done any benchmarks, but its just a conclusion from my personal usage of Debian and Mandriva).

---

### Post by liamnixon on 2008-12-09
Hmm, it doesn't appear to be a language issue.  It was already in english.  I even turned spell-checker off, but no cigar.

Weird.

---

### Post by ibutho on 2008-12-09
What applications are marked in red text?

---

### Post by ibutho on 2008-12-09
What application/s are underlined in red text.

---

### Post by liamnixon on 2008-12-09
Oh, holy crap!  I don't know what I did, but it's stopped!  Gravy!

Thanks for the help!

\\:D/

---

### Post by ibutho on 2008-12-09
> **liamnixon said:**
> Oh, holy crap!  I don't know what I did, but it's stopped!  Gravy!

Thanks for the help!

\\:D/

Cool. I am glad you got the problem sorted. ;)

---

