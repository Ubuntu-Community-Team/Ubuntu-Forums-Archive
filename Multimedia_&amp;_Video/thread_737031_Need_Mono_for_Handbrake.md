---
title: "Need Mono for Handbrake"
date: 2008-03-27
forum: Multimedia &amp; Video
---

### Post by mondoUNC on 2008-03-27
So I was trying out the new Banshee alpha and I must've uninstalled mono not paying attention to what i was doing. Wouldn't be a big deal except that now I can't reinstall handbrake.

I'm trying to use the deb from [here]("http://sourceforge.net/project/showfiles.php?group_id=207412&package_id=248322")

I keep getting the error```
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  mono: Depends: mono-common (= 1.2.5-2ubuntu1~ppa1) but 1.2.6+dfsg-5ubuntu2~ppa1 is to be installed
        Depends: mono-jit (= 1.2.5-2ubuntu1~ppa1) but 1.2.6+dfsg-5ubuntu2~ppa1 is to be installed
E: Broken packages

```

I'm guessing I need to fixes my sources or something and it should just be an easy update and install, but I'm not really sure what to do. Can anyone help?

---

### Post by MoLE on 2008-04-13
Looks like you have a personal package archive (ppa) in your sources.list which is providing a version of mono which is not that required by the handbrake deb.

What does your sources.list say?

---

