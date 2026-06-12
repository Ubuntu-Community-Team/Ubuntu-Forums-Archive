---
title: "Compiz Animations Plugin"
date: 2011-02-09
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by skymera on 2011-02-09
Hi,

I've been using Natty for about 4 weeks and generally running OK.
However I'm unable to open the "animations" setting in CCSM.

Here is the ouput from terminal:

```

Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/ccm/Pages.py", line 1304, in ShowPlugin
    pluginPage = PluginPage(plugin)
  File "/usr/lib/python2.7/dist-packages/ccm/Pages.py", line 128, in __init__
    groupPage = GroupPage(name, group)
  File "/usr/lib/python2.7/dist-packages/ccm/Pages.py", line 1380, in __init__
    sga = SubGroupArea(subGroupName, subGroup)
  File "/usr/lib/python2.7/dist-packages/ccm/Settings.py", line 1482, in __init__
    multiList.Read()
  File "/usr/lib/python2.7/dist-packages/ccm/Settings.py", line 132, in Read
    self._Read()
  File "/usr/lib/python2.7/dist-packages/ccm/Settings.py", line 759, in _Read
    self.Store.append(values)
TypeError: value is of wrong type for this column

```

I've had a look at the lines mentioned however cannot understand what is wrong. Is this problem known or is it new?

Thanks!

---

### Post by mc4man on 2011-02-09
see here
[https://bugs.launchpad.net/ubuntu/+source/compizconfig-settings-manager/+bug/705856](https://bugs.launchpad.net/ubuntu/+source/compizconfig-settings-manager/+bug/705856)

---

### Post by tjeremiah on 2011-02-09
same thing happens for "Place Windows".

---

### Post by JOHNNYG713 on 2011-02-09
They are revamping Compiz and it WILL be awhile before we see it up and running! Like we're used to) Lets hope they spend some time and add Lot's "O" Candy !!! That works !

---

### Post by skymera on 2011-02-09
ah ok, thanks for replies!

I'll just wait till all kinks worked out.

---

### Post by hugmenot on 2011-02-10
On the topic of regressions, is anyone here using the »put« plugin?

I&#8217;ve noticed odd behaviours with it.

In &#8250;put within viewport&#8249; it doesn&#8217;t calculate the middle of the desktop by taking any panels into account. This means it sometimes shoves windows under the panels.

With &#8250;put to arbitrary viewport&#8249; it get&#8217;s stuck with the target viewport number when used the first time. 

E.g., If <Super>1,2,3,4 are key bindings to move a window, and <Super>2 is pressed the first time, any later <Super>1,3,4 will also go to Desktop 2.

---

