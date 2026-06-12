---
title: "Plugins in ardour"
date: 2006-04-01
forum: Multimedia &amp; Video
---

### Post by christhemonkey on 2006-04-01
When i go to automation --> Plugins, there are no options listed just a sort of empty menu dialog.
I have plenty of LADSPA effects on the machine.  I can see and use them in jack rack, but this doesnt seem to help?

Are these plugins not the LADSPA effects? am i missing something here?.

Help appreciated.

---

### Post by dolson on 2006-04-01
I am not well versed in Ardour yet, but did you enable any plugins in the mixer window first, and then go to automation?

I don't know if that will solve it, but this is what I think... You can only automate plugins that you have set up to run on that track.

Just a thought. Let us know if that works or not.

---

### Post by christhemonkey on 2006-04-02
Cheers very much, i will try that now.

---

### Post by christhemonkey on 2006-04-02
That was what i needed thankyou very much!
I have the ardour-doc package, but cant seem to find any sort of help files?
I have done:
```
locate ardour
```
but all the places it listed had no files that looked helpful.
Any help?

---

### Post by dolson on 2006-04-04
```
dana@digory:~$ dpkg -L ardour-doc
/.
/usr
/usr/share
/usr/share/doc
/usr/share/doc/ardour-doc
/usr/share/doc/ardour-doc/TODO.Debian
/usr/share/doc/ardour-doc/README.Debian
/usr/share/doc/ardour-doc/AUTHORS
/usr/share/doc/ardour-doc/AUTHORS.es
/usr/share/doc/ardour-doc/FAQ.gz
/usr/share/doc/ardour-doc/CONTRIBUTORS
/usr/share/doc/ardour-doc/CONTRIBUTORS.es
/usr/share/doc/ardour-doc/README
/usr/share/doc/ardour-doc/README.fr.gz
/usr/share/doc/ardour-doc/README.it.gz
/usr/share/doc/ardour-doc/README.ru.gz
/usr/share/doc/ardour-doc/TRANSLATORS
/usr/share/doc/ardour-doc/copyright
/usr/share/doc/ardour-doc/examples
/usr/share/doc/ardour-doc/examples/ardour_ui.rc.gz
/usr/share/doc/ardour-doc/examples/ardour.rc.gz
/usr/share/doc/ardour-doc/examples/ardour_system.rc.gz
/usr/share/doc/ardour-doc/NEWS.Debian.gz
/usr/share/doc/ardour-doc/BUILD.gz
/usr/share/doc/ardour-doc/BUILD.ru.gz
/usr/share/doc/ardour-doc/README.es.gz
/usr/share/doc/ardour-doc/changelog.Debian.gz
```

Not a lot of useful docs there...

If you need help using Ardour, you might want to check out the documentation on the website, but be warned that it's very sparse... Eventually it will be complete, and sold in the form of a book, which I will buy and encourage others to buy as well, to support Ardour.

At this point though, it's pretty much a matter of figuring it out by experimentation, and help from others. The mailing lists or Ardour forums may be useful for you.

Here is the manual, online, in an ever-changing format:
[http://ardour.org/manual](http://ardour.org/manual)

---

### Post by christhemonkey on 2006-04-04
Thankyou that is what i was looking for.

---

