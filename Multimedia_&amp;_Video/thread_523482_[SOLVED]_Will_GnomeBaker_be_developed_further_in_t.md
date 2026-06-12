---
title: "[SOLVED] Will GnomeBaker be developed further in the future?"
date: 2007-08-11
forum: Multimedia &amp; Video
---

### Post by altonbr on 2007-08-11
Will GnomeBaker be developed further in the future?

According to its download page on SourceForge ([http://sourceforge.net/project/showfiles.php?group_id=127397](http://sourceforge.net/project/showfiles.php?group_id=127397)), GnomeBaker stopped at 0.6.0 (0.6.1 doesn't seem to be used by any distro I can find) which was September/October 15th, 2006. Since that is 10 months coming onto a year without active development, does any one know the future plans for the program?

Personally, I'm content with the program the way it is, but Gnome needs to keep active on all its products to have a consistent desktop.

---

### Post by altonbr on 2007-08-28
Bump.

---

### Post by altonbr on 2007-09-02
Seriously, look: [https://launchpad.net/ubuntu/+source/gnomebaker](https://launchpad.net/ubuntu/+source/gnomebaker)

The only updates to it in the past year are patches. Is this project dead? Who will add HD-DVD or BLU-RAY support when the time comes?

---

### Post by Pygi on 2007-09-03
> **altonbr said:**
> Seriously, look: [https://launchpad.net/ubuntu/+source/gnomebaker](https://launchpad.net/ubuntu/+source/gnomebaker)

The only updates to it in the past year are patches. Is this project dead? Who will add HD-DVD or BLU-RAY support when the time comes?

Why don't you contribute patches? :)

KR,
M.

---

### Post by altonbr on 2007-09-04
> **Pygi said:**
> Why don't you contribute patches? :)

KR,
M.

I'm only a Web Programmer, not a C/C++/Python developer.

---

### Post by altonbr on 2007-09-25
Found it: [https://wiki.ubuntu.com/GoogleSoC2007/Results#head-d31ae9d2261678e946ad463a2cb081056c665348](https://wiki.ubuntu.com/GoogleSoC2007/Results#head-d31ae9d2261678e946ad463a2cb081056c665348)

---

### Post by Pygi on 2007-09-25
> **altonbr said:**
> Found it: [https://wiki.ubuntu.com/GoogleSoC2007/Results#head-d31ae9d2261678e946ad463a2cb081056c665348](https://wiki.ubuntu.com/GoogleSoC2007/Results#head-d31ae9d2261678e946ad463a2cb081056c665348)

Since you found that, you probably also found that I released GB 0.6.2 ;)

Kind regards,
M.

---

### Post by altonbr on 2007-09-25
> **Pygi said:**
> Since you found that, you probably also found that I released GB 0.6.2 ;)

Kind regards,
M.

Hahaha, yes I did. Thanks for working on it and not telling me you little sneak, hahaha. Good job!

Is this the only changelog info though?

> * debian/patches/01_fix_executable_name.dpatch: fixes the name of
  genisoimage in execfunctions.c (Closes: #442947)

---

### Post by Pygi on 2007-09-25
> **altonbr said:**
> Hahaha, yes I did. Thanks for working on it and not telling me you little sneak, hahaha. Good job!

Is this the only changelog info though?

That's the point where distro packages (Debian/Ubuntu/Fedora) diverge from official upstream sources.
I've mis-named genisoimage binary, so cdrkit backend wasn't working properly. The patch those distros
carry fixes the problem.

Changelog:
# A lot of fixes 
# Support for backend systems (cdrkit, cdrtools)

That would be a real changelog :)
Let me know if I can be of any help :)

EDIT: Regarding HDDVD or/and BluRay (and ofcourse a computer that could manage those) would you be willing to donate drives and discs for those to be implemented? Or at least do you have those, and are willing to do some major testing which might involve coasters? If so, I believe I can promise best implementation on those in F/OSS world as part of libburnia project ([http://libburnia-project.org](http://libburnia-project.org)) as a investment in the future ;)

Kind regards,
M.

---

### Post by altonbr on 2007-10-02
I wish I had an HDDVD drive or Blu-ray drive to help, but I don't. I'm usually the last to buy such new technology. I'll probably own one by 2010 or so.

So I can't help you there, but I'd love to help you with the UI and general ideas. For instance, I have a problem of not being able to burn a CD with more than 7 directories. Some stated it was the ISO standard, but others have proven that this does not happen with Nautlius' burner nor K3B.

Full discussion is here: [http://ubuntuforums.org/showthread.php?t=288786](http://ubuntuforums.org/showthread.php?t=288786)

I'll love to discuss this privately if you're looking for help.

---

