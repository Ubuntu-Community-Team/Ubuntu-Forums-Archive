---
title: "PSST privacy tool installation"
date: 2009-09-15
forum: Networking &amp; Wireless
---

### Post by ddeted on 2009-09-15
Hi,
I m trying to find a solution to do VoIP over an encryption channel. (IP to IP !!)
I didn't find another solution than PSST (psst.sourceforge.net => see PSST II ALpha)
This is a very interesting tool, you create a public/private key give public key to your contact and this enable encryption of your VoIP calls. (Windows and Linux!!!)
The problem is that this tool is really old (2003)...
And i have problem to make it run on ubuntu, i have the following error when i start psst (python):

/tmp/psst-II-linux/tkpsst.py:21: DeprecationWarning: the md5 module is deprecated; use hashlib instead
  import webbrowser, thread, math, md5, base64
/tmp/psst-II-linux/tkpsst.py:23: DeprecationWarning: the sha module is deprecated; use the hashlib module instead
  import sha
/tmp/psst-II-linux/tkpsst.py:33: RuntimeWarning: Python C API version mismatch for module SSLCrypto: This Python has API version 1013, module SSLCrypto has version 1011.
  import SSLCrypto
/tmp/psst-II-linux/audio.py:11: RuntimeWarning: Python C API version mismatch for module fastaudio: This Python has API version 1013, module fastaudio has version 1011.
  import fastaudio
/tmp/psst-II-linux/audio.py:12: RuntimeWarning: Python C API version mismatch for module speex: This Python has API version 1013, module speex has version 1011.
  import speex
Traceback (most recent call last):
  File "./psst", line 6, in <module>
    import tkpsst as psst
  File "/tmp/psst-II-linux/tkpsst.py", line 41, in <module>
    import Tree
ImportError: No module named Tree

As you can see the problem seems to come from the "Tree" module...
But ii can't find any package containing that module..

Could someone give me an help about how to run that program ?
Or perhaps do you know a software that do the same thing ...

I don't understand why a so good program is not implemented in standard ubuntu/debian packages...

Thanks for your help.

---

