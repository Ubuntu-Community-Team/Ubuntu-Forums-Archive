---
title: "exception when I chat with a contact"
date: 2011-03-10
forum: Networking &amp; Wireless
---

### Post by aaronhdzid on 2011-03-10
Hi I have an exception message in my emesene, but is with just one ouf of my contacts, do you know what does it mean?

Exception
You are using emesene 1.6.1 "mate" so you're free to complain here:
[http://forum.emesene.org/index.php/board,19.0.html](http://forum.emesene.org/index.php/board,19.0.html)
Check already existing tickets for duplicates first, please.
Traceback (most recent call last):

  File "/usr/share/emesene/plugins_base/LogConversation.py", line 390, in connectLogger
    self.activeLoggers.append(MyLogger(self.controller,conversation,self))

  File "/usr/share/emesene/plugins_base/LogConversation.py", line 109, in __init__
    self.logFile.seek(-15,2)

IOError: [Errno 22] Invalid argument

And I have also other exceptions when I try to connect, this happens at the begining with just one account and then with my two accounts, but after that there is a message that said that I logged from another place. 

Exception
You are using emesene 1.6.3 - "Uberlândia" so you're free to complain here:
[http://forum.emesene.org/index.php/board,19.0.html](http://forum.emesene.org/index.php/board,19.0.html)
Check already existing tickets for duplicates first, please.
Traceback (most recent call last):

  File "/home/jack/Desktop/emesene-1.6.3/PluginManager.py", line 257, in startActivePlugins
    self.startPlugin(name)

  File "/home/jack/Desktop/emesene-1.6.3/PluginManager.py", line 232, in startPlugin
    self.loaded_plugin[ name ].start()

  File "/home/jack/Desktop/emesene-1.6.3/plugins_base/CurrentSong.py", line 97, in start
    self.Slash.register('currentsong', self.currentSongHandler, \

AttributeError: 'NoneType' object has no attribute 'register'

do you know how to solve it? and what does it mean? I will appreciatte your help, because there is no
more support for versions 1.x of emesene

---

### Post by zenwalker on 2011-03-10
Is there any problem in using new ver of emesene or better try other IM's? 

Sorry, exceptions are some thing developers can only help.

---

