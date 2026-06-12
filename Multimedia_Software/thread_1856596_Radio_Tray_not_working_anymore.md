---
title: "Radio Tray not working anymore"
date: 2011-10-08
forum: Multimedia Software
---

### Post by snide_tripod on 2011-10-08
The other night I was searching the Software Center and found a nice little internet radio prog. called Radio Tray.  It worked great, for a while.  Now, I does not load when I click on it in the apps menu.  I don't know how to fix it cuz I a fairly new to Linux.  If someone could help me out, it would be much appreciated.  I tried running it in a terminal and this is what was printed on the screen.....

 user@user-desktop:~$  radiotray

Loading configuration...
/home/michael/.local/share/radiotray/bookmarks.xml
/home/michael/.local/share/radiotray/config.xml
PLS playlist decoder
M3U playlist decoder
ASX-familiy playlist decoder
XSPF playlist decoder
ASF playlist decoder
RAM playlist decoder
Using url timeout = 100
Traceback (most recent call last):
  File "/usr/bin/radiotray", line 15, in <module>
    radiotray.main(sys.argv[1:])
  File "/usr/lib/pymodules/python2.7/radiotray/radiotray.py", line 33, in main
    RadioTray()
  File "/usr/lib/pymodules/python2.7/radiotray/RadioTray.py", line 61, in __init__
    self.systray = SysTray(self.mediator, self.provider, self.log)
  File "/usr/lib/pymodules/python2.7/radiotray/SysTray.py", line 83, in __init__
    self.update_radios()
  File "/usr/lib/pymodules/python2.7/radiotray/SysTray.py", line 230, in update_radios
    self.provider.walk_bookmarks(self.group_callback, self.bookmark_callback, self.radioMenu)
  File "/usr/lib/pymodules/python2.7/radiotray/XmlDataProvider.py", line 291, in walk_bookmarks
    self.walk_bookmarks(group_func, bookmark_func, new_user_data, group + "/group[@name='"+ child_name +"']")                
  File "/usr/lib/pymodules/python2.7/radiotray/XmlDataProvider.py", line 291, in walk_bookmarks
    self.walk_bookmarks(group_func, bookmark_func, new_user_data, group + "/group[@name='"+ child_name +"']")                
  File "/usr/lib/pymodules/python2.7/radiotray/XmlDataProvider.py", line 291, in walk_bookmarks
    self.walk_bookmarks(group_func, bookmark_func, new_user_data, group + "/group[@name='"+ child_name +"']")                
  File "/usr/lib/pymodules/python2.7/radiotray/XmlDataProvider.py", line 284, in walk_bookmarks
    children = self.root.xpath("/bookmarks" + group + "/group | " + "/bookmarks" + group + "/bookmark")
  File "lxml.etree.pyx", line 1459, in lxml.etree._Element.xpath (src/lxml/lxml.etree.c:40530)
  File "xpath.pxi", line 324, in lxml.etree.XPathElementEvaluator.__call__ (src/lxml/lxml.etree.c:113864)
  File "xpath.pxi", line 242, in lxml.etree._XPathEvaluatorBase._handle_result (src/lxml/lxml.etree.c:113063)
  File "xpath.pxi", line 227, in lxml.etree._XPathEvaluatorBase._raise_eval_error (src/lxml/lxml.etree.c:112894)
lxml.etree.XPathEvalError: Invalid predicateAgain,


 if anyone can help,     well....

---

### Post by Rasa1111 on 2011-10-08
Hmm
I don't use xubuntu..
But use radio tray in ubuntu almost daily.
Still working fine here.

I have no idea what that terminal output means..

Have to tried purging (completely removing it) and reinstalling?
that's what I would do anyway. lol

Good luck. 
Sorry man.

---

### Post by snide_tripod on 2011-10-08
Purged and reinstalled and ...  NOTHING.  Mybe there is a better internet radio prog out there then?

---

### Post by Rasa1111 on 2011-10-08
Hmm,

 I often use Pandora..
and just recently found an awesome program/app called "Pithos"
that sits right in my top panel and allows me to listen to all my pandora stations right from my desktop. 
and Pandora is now unlimited free listening, so that makes it even better! lol
Pithos also sits right in my sound menu, with clementine/banshee, etc. 
So I can control it right from there. 

You can also use Clementine for online radio.

Nothing else is coming to me at the moment, but if I think of something else I'll let you know.

edit: just remembered you're using xubuntu..
so you might not have the integrated sound menu, etc like I mentioned.
Not sure though.  sorry.

---

### Post by ron999 on 2011-10-08
> **snide_tripod said:**
> Purged and reinstalled and ...  NOTHING.  
Hi
When you uninstalled and purged RadioTray, did you make sure that the (hidden) folder:-
/home/michael/.local/share/**radiotray**
was deleted?

---

### Post by snide_tripod on 2011-10-10
> **ron999 said:**
> Hi
When you uninstalled and purged RadioTray, did you make sure that the (hidden) folder:-
/home/michael/.local/share/**radiotray**
was deleted?

There is no such folder!!  I tried clementine and it did the same thing.  It worked until I shut it down and then it would not load again.  Weird..

Pithos looks nice and loads all the time, but the radio service is not available in Canada.  Darn laws!!  Oh well, I guess for the time being I will have to wait for some genius
 to develop a good I.R player.  Thanks for your help..

---

### Post by ankspo71 on 2011-10-11
Hi,
I imagine you are using Xubuntu 11.04 which uses radiotray 0.6.1. The radiotray homepage offers downloads for version 0.6.4 which is the version in Xubuntu 11.10 (coming soon). So my advice is uninstall radiotray from Xubuntu, then download the newer version from the homepage and give it a try. It might work, but it might not. 
[http://radiotray.sourceforge.net/](http://radiotray.sourceforge.net/)


VLC can play most radio streams too, and it is lightweight considering everything it can do. 

I would recommend streamtuner too, but it doesn't work for me anymore, but you could give that a try too.

Hope this helps.

---

