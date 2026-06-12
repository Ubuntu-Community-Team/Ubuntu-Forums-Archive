---
title: "Autorun for .deb files?"
date: 2010-09-03
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by kuvanito on 2010-09-03
what's up with maverick and not been able to open or run application installs like frostwire,googles earth and so on?

i can not run any .deb file for installation like i do with lucid.

---

### Post by seeker5528 on 2010-09-03
> **kuvanito said:**
> i can not run any .deb file for installation like i do with lucid.

Do you have gdebi installed?

Later, Seeker

---

### Post by mc4man on 2010-09-03
gdebi-gtk is currently broken, you can use dpkg or gdebi from the cli.

sudo dpkg -i /path/to/whatever.deb

If the package to be installed requires add. package(s) from available repos then use gdebi instead of dpkg

sudo gdebi /path/to/whatever.deb

(or instead of typing path ect., just open a termnal, type the command, hit spacebar, then drag & drop your .deb onto the terminal, click in the window to return focus and press enter on keyboard

---

### Post by ktp on 2010-09-03
> **seeker5528 said:**
> Do you have gdebi installed?

Later, Seeker

it's not since it's broken right now.

---

### Post by kuvanito on 2010-09-03
i think i'll wait for the final release of maverick,lots of broken things there. ):P

---

### Post by cariboo on 2010-09-04
That's why it's called a beta. If you don't like broken, wait for the final release. :)

---

### Post by clive littlewood on 2010-09-04
Hi All

I've just had a partial upgrade and now when I double click any .debs the software center opens and install the package.

Great !!!!!

Clive

---

### Post by cariboo on 2010-09-04
The graphical gdebi, now works the way it should for me. I just double clicked a .deb, it automagically installed the dependencies and installed the app without crashing.

---

### Post by seeker5528 on 2010-09-04
> **clive littlewood said:**
> Hi All

I've just had a partial upgrade and now when I double click any .debs the software center opens and install the package.

I remember that being on the ToDo list for Software Center, but I don't install things that are not in a repository very often.

OK, I just did:

```
apt-get -d install ktorrent ktorrent-data
```

to download, but not install ktorrent, with the dependency on libktorrent2 that gave me 3 .debs in /var/cache/apt/archives.

Browsed there in Nautilus and double click the .deb file for ktorrent. Gdebi is what came up to install it.

Gdebi did claim it failed to install, but the only error I could see didn't look like it had anything to do with the actual installation process, it showed before hand that the file supplied a newer version of ktorrent than the installed version, showed after that the file supplied the same version that was already installed.

So in spite of the error message, it seems to have worked just fine. 

Grrr!!! After right clicking on the .deb file the choosing open with, Sofware Center did show as an option, then after choosing customize on the 'open with' menu, even though I didn't change anything Software Center show up higher in the list than Gdebi, looking for another upgrade to install...... Okular looks good and has a dependency.

*******, it came up in Software Center, but I don't see a way to upgrade if there is already an older version installed.

Going to the properties of the .deb in Nautilus, gdebi shows up twice since I have gdebi-kde installed, chose the second one which is gdebi-kde, not as informative about the actual progress being made, but outside of that I think I like it better. Installed Okular, which pulled in libokularcore1 as a dependency, with no error messages.

Later, Seeker

---

### Post by kuvanito on 2010-09-04
gdbei will start and run like normal BUT it won't install anything,try it!:D

---

### Post by webme on 2010-09-04
seems like an earlier partial upgrade delete the gdebi package and after reinstall it from SCenter works very good!!! in my case i was troubled 2 weeks with gdebi, untull today!!!

---

### Post by cariboo on 2010-09-04
That's because gdebi-gtk was broken, as was stated earlier in the thread.

---

