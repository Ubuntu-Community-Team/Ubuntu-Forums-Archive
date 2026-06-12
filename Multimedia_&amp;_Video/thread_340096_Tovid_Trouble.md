---
title: "Tovid Trouble"
date: 2007-01-16
forum: Multimedia &amp; Video
---

### Post by weltercat on 2007-01-16
Hello all
I am using Ubuntu 6.10 on Kernel 2.6.17.10 and I am trying to install Tovid. I am really anxious to see it work. I have been transcoding AVI files to MPG format and then using Qdvdauthor to make the VIDEO_TS files to burn to DVD. I have heard that Tovid will do this with a GUI front end.

This command works:

**tovid -svcd -in chris-farley-snl.avi -out encoded-chris-farley**

this one does not:

**tovidgui**

it produces the following error:

Traceback (most recent call last):
  File "/usr/bin/tovidgui", line 22, in ?
    import wxversion
ImportError: No module named wxversion
There was an error importing the 'wx' libraries. The above
output should help you find what went wrong. Re-installing
wxPython 2.6 (or upgrading from wxPython 2.4 to 2.6) may
help. Consult the tovid homepage (tovid.org) for further
assistance.
Sorry, 'tovidgui' will not work.


I posted this on another board and one of the tovid developers was helping me troubleshoot it. Apparently in boils down to my python installation being either not installed in the correct location or not searching the correct location for the wxversion that the tovidgui needs to run.

I ran the following command 

~$ python -c "import sys; print sys.prefix"

and the output was /usr/local and I believe it should be /usr

If anyone out there recognizes this error and knows how to help me correctly install python, please drop me a line.](*,)

---

### Post by binks on 2007-01-22
tovid gui is not maintained in this version please install from svn and run the gui again as the testing version now works 
binks

---

### Post by bayvista on 2007-04-14
I have installed TOVID from the source tarball and get the following when I try to run the GUI:

Traceback (most recent call last):
  File "/usr/local/bin/tovidgui", line 43, in ?
    from libtovid.gui.frames import TovidFrame
ImportError: No module named libtovid.gui.frames

I can't find any module called "libtovid.gui.frames"

Some help appreciated.

---

