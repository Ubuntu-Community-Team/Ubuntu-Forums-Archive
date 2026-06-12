---
title: "maverick alpha3 Synaptic CD rom"
date: 2010-08-21
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by bprins on 2010-08-21
Hi guys,

I've installed maverick on a second partition just to see what it brings me, but I can't get my wireless up and running. Had the same issue on lucid (and karmic... but ok..:)). So what I need to do is install build-essential and linux-headers. But, Synaptic won't let me.

I've ticked the CDrom box in software sources.

When I try to install build-essentials it complains that it can't access the CDrom, which is strange, because it is mounted (/media/ubuntu 10.10 i386).

I've mounted the cdrom to /cdrom, but same problem remains.

I've tried to install packages 1 by 1 using gdebi installer, but can't succeed because gdebi is convinced that there is a circular dependency between gc++ and libgc++ (which is a lie!).

Question1:
How can I get synaptic to "find" my CDrom drive?

Question2:
Is there an alternative way to get build-essential installed? I don't understand why its not installed by default, but I guess ubuntu has a reason not to.

Hope somebody can help me further; If I find out my own, I'll post back.

Thanks.

Bas

PS: In lucid, when I add my CDrom, I immediately get a popup with the question if I want to open synaptic for the CDrom. Maverick doesnt do that. Strange isn't it :-)

---

### Post by mörgæs on 2010-08-21
You will probably have more luck in this forum:

[http://ubuntuforums.org/forumdisplay.php?f=385](http://ubuntuforums.org/forumdisplay.php?f=385)

---

### Post by Sef on 2010-08-21
Moved to Maverick T & D.

---

### Post by ktp on 2010-08-21
> **bprins said:**
> PS: In lucid, when I add my CDrom, I immediately get a popup with the question if I want to open synaptic for the CDrom. Maverick doesnt do that. Strange isn't it :-)

have you tried using Ubuntu Software Center? I don't know if this will work but something to try.

---

### Post by ronacc on 2010-08-21
try installing it with dpkg , if it bitches about the dependencies use the --force option .

---

### Post by mc4man on 2010-08-21
Found 2 ways to add the cdrom, the first just sort of happened in software sources, after adding the cdrom and 'reload' got a message to insert blah, blah. (disk was already inserted
repeatedly clicking on that message produced the pop up up in screenshot, after which could install build-essential from cdrom. (w/ no internet


The other way (starting over), was to run this in terminal, also worked fine
```
sudo apt-cdrom add /media'/Ubuntu 10.10 i386'
```

Ex.
> 
doug@doug-laptop:~$ sudo apt-cdrom add /media'/Ubuntu 10.10 i386'
Using CD-ROM mount point /media/apt/
Identifying.. [786a83eda89de0336f23ead07ae12f87-2]
Scanning disc for index files..
Found 2 package indexes, 0 source indexes, 0 translation indexes and 1 signatures
This disc is called: 
'Ubuntu 10.10 _Maverick Meerkat_ - Alpha i386 (20100727)'
Copying package lists...gpgv: Signature made Tue 27 Jul 2010 03:09:37 AM EDT using DSA key ID FBB75451
gpgv: Good signature from "Ubuntu CD Image Automatic Signing Key <cdimage@ubuntu.com>"
Reading Package Indexes... Done
Writing new source list
Source list entries for this disc are:
deb cdrom:[Ubuntu 10.10 _Maverick Meerkat_ - Alpha i386 (20100727)]/ maverick main restricted
ect.

The apt-cdrom method seems more reliable..


Edit: as far as gdebi - depending on where you are update wise - date of the live cd in your case, gdebi-gtk may work,  sorta work ( [one package only]("https://bugs.launchpad.net/ubuntu/+source/gdebi/+bug/614690") ) or not work at all ([filedescriptor flags error]("https://bugs.launchpad.net/ubuntu/+source/gdebi/+bug/620297")

---

### Post by bprins on 2010-08-22
Hi,

Thanks for the pointers. Didn't manage to get it working using apt-cdrom. I got further though, but in the end it still complained about not being able to find the files in /media/Ubuntu blabla/pool/b/build-essential etc. Thus, for some reason something in the path doesn't add up.

BUT: the less userfriendly way of using dpkg for each individual package did work. I had to force-all a lot, and re-do a package after installing dependencies etc, but, the result is there. I am now on internet, in maverick. jippie kai yee.

I can start playing around with alsa :-)

Thanks guys.

Bas

---

