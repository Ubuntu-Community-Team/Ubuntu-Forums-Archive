---
title: "Movie thumbs in nautilus"
date: 2006-11-04
forum: Multimedia &amp; Video
---

### Post by aka5ha on 2006-11-04
Hello All,

On edgy, to get movie thumbs, I install totem-xine.  Then, nautilus crashes on quicktime mov files.  Is there a way I can exclude files with mov extensions from being thumbnailed?  This would solve my problem.  

Right now I do not have totem-xine installed, and so I have no movie thumbnails in nautilus.  

Or is there something I am missing?  Is there another way to get movie thumbs without totem-xine?  

Thanks very much!  

P.S. Not all mov files crash nautilus, only move files created with my Leica digital camera, for what it's worth.  

Thanks again for any comments you may have

---

### Post by featherking on 2006-11-04
Right click on your .MOV file in nautilus and see what the MIME type: video/"file_type" is listed there. Remember what it says there or write it down. run the gconf-editor from the run dialog or the command line

```
gconf-editor
```

Then go to desktop > gnome > thumbnailers > and click the MIME type you wrote down earlier. Then in the right pane uncheck the "enable" box. There are a couple of references in that thumbnailers folder on my computer, you may want to disable all references to "quicktime"

*Note* - I dont have any quicktime files on this machine, but this method did work with avi files and divx that i do have. Let me know if this helps

---

### Post by aka5ha on 2006-11-04
Dear featherking,

Your suggestion worked beautifully.  Thanks so much for the help,

aka5ha.  

> **featherking said:**
> Right click on your .MOV file in nautilus and see what the MIME type: video/"file_type" is listed there. Remember what it says there or write it down. run the gconf-editor from the run dialog or the command line

```
gconf-editor
```

Then go to desktop > gnome > thumbnailers > and click the MIME type you wrote down earlier. Then in the right pane uncheck the "enable" box. There are a couple of references in that thumbnailers folder on my computer, you may want to disable all references to "quicktime"

*Note* - I dont have any quicktime files on this machine, but this method did work with avi files and divx that i do have. Let me know if this helps

---

