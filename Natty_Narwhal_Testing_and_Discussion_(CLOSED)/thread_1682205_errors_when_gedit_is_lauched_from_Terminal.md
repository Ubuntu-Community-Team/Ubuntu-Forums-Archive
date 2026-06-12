---
title: "errors when gedit is lauched from Terminal"
date: 2011-02-05
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by zika on 2011-02-05
```
:~$ gedit .fluxbox/startup 
2011-02-05 19:22:50,045 DEBUG resources - Initializing resource locating
2011-02-05 19:22:50,430 DEBUG Preferences - <value key='BibtexExtensions'> not found
2011-02-05 19:22:50,596 DEBUG JobManager - Created JobManager instance 50174032
2011-02-05 19:22:50,639 DEBUG GeditLaTeXPlugin - activate
2011-02-05 19:22:50,639 DEBUG WindowContext - init
2011-02-05 19:22:50,774 DEBUG GeditWindowDecorator - _init_tab_decorators: initialized 0 decorators
Error in sys.excepthook:
RuntimeError

Original exception was:
RuntimeError
Error in sys.excepthook:
RuntimeError

Original exception was:
RuntimeError
2011-02-05 19:22:50,891 DEBUG GeditWindowDecorator - active_tab_changed
2011-02-05 19:22:50,892 DEBUG GeditWindowDecorator - ---------- ADJUST: None
2011-02-05 19:22:50,894 DEBUG GeditWindowDecorator - No window-scope views for this extension
2011-02-05 19:22:50,894 DEBUG GeditWindowDecorator - _set_selected_bottom_view: 0
2011-02-05 19:22:50,907 DEBUG GeditWindowDecorator - _set_selected_side_view: 0
2011-02-05 19:22:50,914 DEBUG GeditWindowDecorator - tab_added
Error in sys.excepthook:
RuntimeError

Original exception was:
RuntimeError
Error in sys.excepthook:
RuntimeError

Original exception was:
RuntimeError
Error in sys.excepthook:
RuntimeError

Original exception was:
RuntimeError
Error in sys.excepthook:
RuntimeError

Original exception was:
RuntimeError
Error in sys.excepthook:
RuntimeError

Original exception was:
RuntimeError
2011-02-05 19:22:51,412 DEBUG GeditTabDecorator - loaded
2011-02-05 19:22:51,450 DEBUG GeditTabDecorator - _adjust_editor: URI has changed
2011-02-05 19:22:51,451 DEBUG GeditWindowDecorator - ---------- ADJUST: 
2011-02-05 19:22:51,451 DEBUG GeditWindowDecorator - No window-scope views for this extension
2011-02-05 19:22:51,451 DEBUG GeditWindowDecorator - _set_selected_bottom_view: 0
2011-02-05 19:22:51,451 DEBUG GeditWindowDecorator - _set_selected_side_view: 0
Error in sys.excepthook:
RuntimeError

Original exception was:
RuntimeError
Error in sys.excepthook:
RuntimeError

Original exception was:
RuntimeError
Error in sys.excepthook:
RuntimeError

Original exception was:
RuntimeError
Error in sys.excepthook:
RuntimeError

Original exception was:
RuntimeError
Error in sys.excepthook:
RuntimeError

Original exception was:
RuntimeError
Error in sys.excepthook:
RuntimeError

Original exception was:
RuntimeError
Error in sys.excepthook:
RuntimeError

Original exception was:
RuntimeError
Error in sys.excepthook:
RuntimeError

Original exception was:
RuntimeError
Error in sys.excepthook:
RuntimeError

Original exception was:
RuntimeError
Error in sys.excepthook:
RuntimeError

Original exception was:
RuntimeError
Error in sys.excepthook:
RuntimeError

Original exception was:
RuntimeError
Error in sys.excepthook:
RuntimeError

Original exception was:
RuntimeError
2011-02-05 19:23:00,672 DEBUG GeditTabDecorator - saved
Error in sys.excepthook:
RuntimeError

Original exception was:
RuntimeError
2011-02-05 19:23:00,695 DEBUG GeditWindowDecorator - tab_removed
2011-02-05 19:23:00,716 DEBUG GeditLaTeXPlugin - deactivate
:~$
```

---

### Post by Harry33 on 2011-02-06
> **zika said:**
> ```
:~$ gedit .fluxbox/startup 
2011-02-05 19:22:50,045 DEBUG resources - Initializing resource locating
2011-02-05 19:22:50,430 DEBUG Preferences - <value key='BibtexExtensions'> not found
2011-02-05 19:22:50,596 DEBUG JobManager - Created JobManager instance 50174032
2011-02-05 19:22:50,639 DEBUG GeditLaTeXPlugin - activate
2011-02-05 19:22:50,639 DEBUG WindowContext - init
2011-02-05 19:22:50,774 DEBUG GeditWindowDecorator - _init_tab_decorators: initialized 0 decorators
Error in sys.excepthook:
RuntimeError
...
:~$
```

Could that be due to this bug #713919 here:
[https://bugs.launchpad.net/ubuntu/+source/fluxbox/+bug/713919](https://bugs.launchpad.net/ubuntu/+source/fluxbox/+bug/713919)

---

### Post by zika on 2011-02-06
> **Harry33 said:**
> Could that be due to this bug #713919 here:
[https://bugs.launchpad.net/ubuntu/+source/fluxbox/+bug/713919](https://bugs.launchpad.net/ubuntu/+source/fluxbox/+bug/713919)No, I do not think so. I'll explore. It happens with and without FluxBox...
(It does not crash, it works OK...)

---

### Post by Harry33 on 2011-02-06
> **zika said:**
> No, I do not think so. I'll explore. It happens with and without FluxBox...
(It does not crash, it works OK...)

So what happens if you start gedit with a command:
```
gedit
```
I get absolutely no warnings and gedit launches.

Or if you type:
```
gksudo nautilus
```
Again with no warnings, Nautilus launches with root priviledges.

---

### Post by zika on 2011-02-06
> **Harry33 said:**
> So what happens if you start gedit with a command:
```
gedit
```
I get absolutely no warnings and gedit launches.

Or if you type:
```
gksudo nautilus
```
Again with no warnings, Nautilus launches with root priviledges.
I get the stuff I posted in #1...

Again (this time from (UbuntuClassicDesktop(no effects)):
```
:~$ gedit
2011-02-06 14:56:39,200 DEBUG resources - Initializing resource locating
2011-02-06 14:56:39,575 DEBUG Preferences - <value key='BibtexExtensions'> not found
2011-02-06 14:56:39,702 DEBUG JobManager - Created JobManager instance 36944016
2011-02-06 14:56:39,733 DEBUG GeditLaTeXPlugin - activate
2011-02-06 14:56:39,734 DEBUG WindowContext - init
2011-02-06 14:56:39,841 DEBUG GeditWindowDecorator - _init_tab_decorators: initialized 0 decorators
Error in sys.excepthook:
RuntimeError

Original exception was:
RuntimeError
Error in sys.excepthook:
RuntimeError

Original exception was:
RuntimeError
2011-02-06 14:56:40,027 DEBUG GeditWindowDecorator - active_tab_changed
2011-02-06 14:56:40,027 DEBUG GeditWindowDecorator - ---------- ADJUST: None
2011-02-06 14:56:40,030 DEBUG GeditWindowDecorator - No window-scope views for this extension
2011-02-06 14:56:40,030 DEBUG GeditWindowDecorator - _set_selected_bottom_view: 0
2011-02-06 14:56:40,030 DEBUG GeditWindowDecorator - _set_selected_side_view: 0
2011-02-06 14:56:40,035 DEBUG GeditWindowDecorator - tab_added
Error in sys.excepthook:
RuntimeError

Original exception was:
RuntimeError
2011-02-06 14:56:43,455 DEBUG GeditWindowDecorator - tab_removed
2011-02-06 14:56:43,477 DEBUG GeditLaTeXPlugin - deactivate
```

UbuntuClassicDesktop```
:~$ gedit
2011-02-06 14:58:53,166 DEBUG resources - Initializing resource locating
2011-02-06 14:58:53,243 DEBUG Preferences - <value key='BibtexExtensions'> not found
2011-02-06 14:58:53,256 DEBUG JobManager - Created JobManager instance 34269392
2011-02-06 14:58:53,260 DEBUG GeditLaTeXPlugin - activate
2011-02-06 14:58:53,260 DEBUG WindowContext - init
2011-02-06 14:58:53,331 DEBUG GeditWindowDecorator - _init_tab_decorators: initialized 0 decorators
Error in sys.excepthook:
RuntimeError

Original exception was:
RuntimeError
Error in sys.excepthook:
RuntimeError

Original exception was:
RuntimeError
2011-02-06 14:58:53,375 DEBUG GeditWindowDecorator - active_tab_changed
2011-02-06 14:58:53,375 DEBUG GeditWindowDecorator - ---------- ADJUST: None
2011-02-06 14:58:53,377 DEBUG GeditWindowDecorator - No window-scope views for this extension
2011-02-06 14:58:53,378 DEBUG GeditWindowDecorator - _set_selected_bottom_view: 0
2011-02-06 14:58:53,378 DEBUG GeditWindowDecorator - _set_selected_side_view: 0
2011-02-06 14:58:53,383 DEBUG GeditWindowDecorator - tab_added
Error in sys.excepthook:
RuntimeError

Original exception was:
RuntimeError
2011-02-06 14:58:57,105 DEBUG GeditWindowDecorator - tab_removed
2011-02-06 14:58:57,126 DEBUG GeditLaTeXPlugin - deactivate
```

So, now we have all3, FB, UCD(NE), UCD...

**After some (Sunday) thinking:**

What I see as a possible culprit is LaTeX plugin... :)

Yes, that's the right answer...

**Case closed...**

---

### Post by Yellow Pasque on 2011-02-06
Please mark solved.

---

### Post by zika on 2011-02-06
> **Temüjin said:**
> Please mark solved.It's not solved. Just problem located...
I thought about marking it solved, but...

Off-topic: Is latest version of gstreamer0.10-delta compatible with Natty?
It surely works. Audible impressions will follow. I know I liked it while on Maverick...

---

