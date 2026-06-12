---
title: "DeVeDe halts"
date: 2009-08-12
forum: Multimedia Software
---

### Post by PeterVR on 2009-08-12
DeVeDe just halts after a while.

I started a DVD compilation yesterday (5 titles, 1 .avi in every title). I tried several times, result is always the same. DeVeDe creates a main menu (MPG+XML) and starts building an MPG from the first .avi. Somewhere in between 60 and 120 MB, the program just halts. 

The "Creating..." window doesn't respond anymore. When it gets hidden behind an other window, and shown again, it's blank. Last time I tried I left the system like this for 9 hours just to check nothing is happening. Nothing was.

I start DeVeDe command line so I get some feedback. When I hit Ctrl-C here, I get this output:
```
elemento:  /usr/bin
**^C**Traceback (most recent call last):
  File "/usr/local/lib/devede/devede_convert.py", line 371, in time_callback
    retval=self.runner.refresh()
  File "/usr/local/lib/devede/devede_executor.py", line 212, in refresh
    if self.read_line_from_output():
  File "/usr/local/lib/devede/devede_executor.py", line 243, in read_line_from_output
    readed=element.readline(self.read_chars)
KeyboardInterrupt

```
also the blanked out "Creating..." window gets filled in again. The only gain is that now I can press the Cancel button instead of having to kill the process.


Anybody recognise this problem? Anybody have a solution?

---

