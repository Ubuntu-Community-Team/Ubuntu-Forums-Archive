---
title: "Play a remote video from ssh with totem"
date: 2009-02-11
forum: Multimedia Software
---

### Post by yoburtu on 2009-02-11
Hello,

I have a problem with Intrepid. I can't play videos with totem from remote resources ssh. This is the error:

** Message: Error: Could not open resource for reading.
gstgnomevfssrc.c(836): gst_gnome_vfs_src_start (): /GstPlayBin:play/GstGnomeVFSSrc:source:
Could not open vfs file "sftp://remoteuser@remotehost/home/remoteuser/video.avi" for reading: Access denied (16)

The video.avi is correct. In the local machine the video play without problems. With Ubuntu Hardy I don't have problems, work fine.

I tried this:

$ totem sftp://remoteuser@remotehost:/home/remoteuser/video.avi
** (totem:14404): DEBUG: Init of Python module
** (totem:14404): DEBUG: Registering Python plugin instance: BBCViewer+TotemPythonPlugin
** (totem:14404): DEBUG: Creating object of type BBCViewer+TotemPythonPlugin
** (totem:14404): DEBUG: Creating Python plugin instance
** (totem:14404): DEBUG: Init of Python module
** (totem:14404): DEBUG: Registering Python plugin instance: YouTube+TotemPythonPlugin
** (totem:14404): DEBUG: Creating object of type YouTube+TotemPythonPlugin
** (totem:14404): DEBUG: Creating Python plugin instance
** Message: no file info
** Message: Error: Could not open resource for reading.
gstgnomevfssrc.c(836): gst_gnome_vfs_src_start (): /GstPlayBin:play/GstGnomeVFSSrc:source:
Could not open vfs file "sftp://remoteuser@remotehost/home/remoteuser/video.avi" for reading: Access denied (16)

and totem says:

"Could not open location; you might not have permissions to open the file".

But I have correct permissions from Nautilus.

Any ideas?. Is this a totem 2.24 bug?.

Best regards.

---

### Post by punx45 on 2009-02-11
sftp normally prompts for a login, does totem support passing that along? im not sure that it does.  check out sshfs and see if that can help.

---

### Post by yoburtu on 2009-02-12
With sshfs work fine.

But I prefer gvfs. Is more easy for users. Best regards.

---

### Post by dmelo on 2009-03-25
you can also do something like this 

ssh dmelo@merov cat movie.avi | mplayer -

You can find more details here [http://diogomelo.net/drupal/node/2](http://diogomelo.net/drupal/node/2)

---

### Post by yoburtu on 2009-03-25
The problem is solved. Read this bug from gnome:

[http://bugzilla.gnome.org/show_bug.cgi?id=571619](http://bugzilla.gnome.org/show_bug.cgi?id=571619)

Best regards.

---

