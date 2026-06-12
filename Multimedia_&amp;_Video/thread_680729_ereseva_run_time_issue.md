---
title: "ereseva run time issue"
date: 2008-01-28
forum: Multimedia &amp; Video
---

### Post by panantha on 2008-01-28
Hello,

I downloaded the source for the tapioca voip libraried and have successfully compilied. i have installed ereseva to use voice in gtalk. But when i execte the program i get the following errors in the command line

"
Traceback (most recent call last):
  File "/usr/local/bin/ereseva", line 25, in <module>
    from ereseva import ereseva
  File "/usr/local/lib/python2.5/site-packages/ereseva/ereseva.py", line 34, in <module>
    from chat_window import ChatWindow
  File "/usr/local/lib/python2.5/site-packages/ereseva/chat_window.py", line 40, in <module>
    from message_logger import MessageLogger
  File "/usr/local/lib/python2.5/site-packages/ereseva/message_logger.py", line 28, in <module>
    import elementtree.ElementTree as ElementTree
ImportError: No module named elementtree.ElementTree

"

Can somebody please help me in solving this issue

-Praveen

---

### Post by Dasani on 2008-02-11
**First make sure you have the latest version of ElementTree:**
Go to synaptic, and type in ElementTree. It should already be installed (if not, then install),    and the version should 2.6 something

[B]If that's all fine, then open that file with sudo privileges and edit the import line for elementtree:[/B\
In a terminal type
*sudo gedit /usr/local/lib/python2.5/site-packages/ereseva/message_logger.py*
Then comment out the line saying
*import elementtree.ElementTree as ElementTree*
and paste in this line below it
*import xml.etree.ElementTree as ET*

Then try to start ereseva again from the command. It might give you the same error for another py file. Repeat the process.
Then start ereseva from Applications>Internet to see the GUI.

Should work, gluck

---

