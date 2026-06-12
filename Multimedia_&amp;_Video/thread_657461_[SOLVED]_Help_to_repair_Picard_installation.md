---
title: "[SOLVED] Help to repair Picard installation"
date: 2008-01-03
forum: Multimedia &amp; Video
---

### Post by starfry on 2008-01-03
Hi,., I have rather foolishly tried to build Picard 0.9 on Feisty which meant trying to update Qt and PyQt. I failed miserably so re-installed what I messed up, but now Picard 0.7 does not work. Here is the output I get when running it:

% picard
Traceback (most recent call last):
  File "/usr/bin/picard", line 2, in <module>
    from picard.tagger import main; main('/usr/share/locale')
  File "/usr/lib/python2.5/site-packages/picard/tagger.py", line 54, in <module>
    from picard import musicdns, version_string, log
  File "/usr/lib/python2.5/site-packages/picard/musicdns/__init__.py", line 28, in <module>
    from picard.util.thread import proxy_to_main
  File "/usr/lib/python2.5/site-packages/picard/util/thread.py", line 75, in <module>
    class ThreadPool(QtCore.QObject):
  File "/usr/lib/python2.5/site-packages/picard/util/thread.py", line 107, in ThreadPool
    def call(self, queue, func, next, priority=QtCore.Qt.LowEventPriority):
AttributeError: LowEventPriority
%

If anyone can point me in the direction of what I need to do to fix this I'd really appreciate it.

(re-installing the OS is not an option ;) )

TIA

---

