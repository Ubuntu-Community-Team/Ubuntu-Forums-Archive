---
title: "Radiotray application"
date: 2012-03-13
forum: Multimedia Software
---

### Post by desar on 2012-03-13
Hello!
I have been using radiotray for weeks, but know clicking the icon or starting from terminal doesn't launch it. I know there are some threads about it and I have read them.
I have removed and reinstalled it several times but it doesn't work.

Also I think that it may be a problem regarding to bookmarks, or the high number of listed radio but I don't know how to fix it.

I can't find a config.xml file, they're all .py

Here is what I get in terminal.

I would appreciate a lot your help.
------------------------------------------------------------------------
Traceback (most recent call last):
  File "/usr/bin/radiotray", line 15, in <module>
    radiotray.main(sys.argv[1:])
  File "/usr/lib/python2.6/dist-packages/radiotray/radiotray.py", line 37, in main
    RadioTray()
  File "/usr/lib/python2.6/dist-packages/radiotray/RadioTray.py", line 84, in __init__
    self.systray = SysTray(self.mediator, self.provider, self.cfg_provider, self.default_cfg_provider, eventManager, tooltipManager)
  File "/usr/lib/python2.6/dist-packages/radiotray/SysTray.py", line 134, in __init__
    self.gui.buildMenu()
  File "/usr/lib/python2.6/dist-packages/radiotray/SysTrayGui.py", line 64, in buildMenu
    self.update_radios()
  File "/usr/lib/python2.6/dist-packages/radiotray/SysTrayGui.py", line 149, in update_radios
    self.provider.walk_bookmarks(self.group_callback, self.bookmark_callback, self.radioMenu)
  File "/usr/lib/python2.6/dist-packages/radiotray/XmlDataProvider.py", line 368, in walk_bookmarks
    self.walk_bookmarks(group_func, bookmark_func, new_user_data, group + "/group[@name='"+ child_name +"']")                
  File "/usr/lib/python2.6/dist-packages/radiotray/XmlDataProvider.py", line 368, in walk_bookmarks
    self.walk_bookmarks(group_func, bookmark_func, new_user_data, group + "/group[@name='"+ child_name +"']")                
  File "/usr/lib/python2.6/dist-packages/radiotray/XmlDataProvider.py", line 358, in walk_bookmarks
    children = self.root.xpath("/bookmarks" + group + "/group | " + "/bookmarks" + group + "/bookmark")
  File "lxml.etree.pyx", line 1317, in lxml.etree._Element.xpath (src/lxml/lxml.etree.c:36891)
  File "xpath.pxi", line 290, in lxml.etree.XPathElementEvaluator.__call__ (src/lxml/lxml.etree.c:103188)
  File "xpath.pxi", line 212, in lxml.etree._XPathEvaluatorBase._handle_result (src/lxml/lxml.etree.c:102495)
  File "xpath.pxi", line 197, in lxml.etree._XPathEvaluatorBase._raise_eval_error (src/lxml/lxml.etree.c:102318)
lxml.etree.XPathEvalError: Invalid predicate

--------------------------------------------------------------------------

---

### Post by ron999 on 2012-03-13
> **desar said:**
> 
I can't find a config.xml file, they're all .py


Hi
Find that config.xml file.
/home/ron/.local/share/radiotray/**config.xml**
Rename it config.xml.bak
You might need to be root (gksudo nautilus)
Then re-start RadioTray.

---

### Post by desar on 2012-03-13
Now I found it and changed the name. but it's the same thing. It won't work.

I also deleted the *Bookmark.xml* file, changed the value from false to true in *config* file, but terminal has the same output again, and icon won't launch the program.

thanks anyway bro.

---

### Post by ron999 on 2012-03-13
> **desar said:**
> Now I found it and changed the name. but it's the same thing. It won't work.

OK
Uninstall radiotray and
delete the radiotray folder
/home/ron/.local/share/**radiotray**/config.xml
Then install radiotray-[COLOR="Red"]v0.7.2[/COLOR] from the website here ---> [http://radiotray.sourceforge.net/]("http://radiotray.sourceforge.net/")

---

### Post by desar on 2012-03-14
I tried everything but it didn't function.
The only choice was to install an earlier version like **0.61**.
Now it works well, there isn't any big difference except the missing ability to organize the radio stations in groups, but no problem as long as I can listen them.
Thanks for your time.

---

