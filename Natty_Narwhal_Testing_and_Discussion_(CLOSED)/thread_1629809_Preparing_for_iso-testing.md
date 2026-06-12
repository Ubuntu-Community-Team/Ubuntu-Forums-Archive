---
title: "Preparing for iso-testing"
date: 2010-11-24
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by kansasnoob on 2010-11-24
Knowing that Alpha1 pops on Dec 2 I decided to review unresolved issues/bugs carried over from Maverick in hopes that it might expedite the bug filing process so here I go:

No restart option after choosing to "Continue Testing"
[https://bugs.launchpad.net/ubuntu/+source/casper/+bug/657086](https://bugs.launchpad.net/ubuntu/+source/casper/+bug/657086)

Install alongside option displays incorrect device designations
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/657397](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/657397)

Maverick ubiquity confusion w/ auto-resize option
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/655950](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/655950)

Ubiquity doesn't suggest to install on unallocated free space
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/652852](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/652852)

Maverick ubiquity windows can not be resized/maximized
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/628097](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/628097)

Can't choose where to install grub in ubiquity (now just lacks option to not install grub)
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/615033](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/615033)

What am I forgetting?

Adding one just so all of my ubiquity bugs are in one place:

Choosing use entire partition actually results in using entire disc
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/682429](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/682429)

---

### Post by VMC on 2010-11-24
Well I have major troubles getting daily-live installed and then Compiz crashes every time. Hopefully by alpha time it will be resolved. 

I've been following the natty changes and there is some work yesterday that may effect daily-live. install.

The Compiz issue is [_here_]("https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/678518").

---

### Post by kansasnoob on 2010-11-24
> **VMC said:**
> Well I have major troubles getting daily-live installed and then Compiz crashes every time. Hopefully by alpha time it will be resolved. 

I've been following the natty changes and there is some work yesterday that may effect daily-live. install.

The Compiz issue is [_here_]("https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/678518").

I'm not very bright when it comes to Compiz so I don't pay a lot of attention to it during installation testing. However, it's a requirement when I perform upgrade testing:

[http://testcases.qa.ubuntu.com/Testing/Cases/DesktopUpgrade](http://testcases.qa.ubuntu.com/Testing/Cases/DesktopUpgrade)

> Post-upgrade tests

    Desktop effects
        If you had compiz running, test if it is still running after the upgrade
        If compiz was not running, try to enable it via System/Preferences/Apperance, then go to Desktop Effects and set it to "Normal effects"
        Verify that it works by pressing SUPER(windows key)+e
        Verify that the workspace layout and the keybindings are preserved
        Open the Example Documents and play the "Experience ubuntu.ogg" and see if that playing works
        Press ALT+F2 and type "glxgears" and see if it works
        Watch out for screen artifacts

        Please report any problems you observe and include some details of the problem and the files "~/.xsession-errors" and the output of "lspci -n" 

Does that sound adequate to duplicate that bug?

If it matters I'm only able to test i386.

---

