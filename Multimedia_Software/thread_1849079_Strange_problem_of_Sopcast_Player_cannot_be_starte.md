---
title: "Strange problem of Sopcast Player: cannot be started"
date: 2011-09-23
forum: Multimedia Software
---

### Post by lf28 on 2011-09-23
Hi all,

I have just installed the sopcast player from the PPA in Ubuntu 11.04. The installation finishes without any problem. But the player cannot be launched at all. When I open it from utility, nothing happens. Then I launch it from terminal, it gives the following error messages:

Traceback (most recent call last):
  File "/usr/share/sopcast-player/lib/sopcast-player.py", line 790, in <module>
    pySop.main()
  File "/usr/share/sopcast-player/lib/sopcast-player.py", line 152, in main
    self.populate_channel_treeview(chinese)        
  File "/usr/share/sopcast-player/lib/sopcast-player.py", line 332, in populate_channel_treeview
    channel_group_iter = self.channel_treeview_model.append(None, self.prepare_row_for_channel_treeview_model(channel_group))
TypeError: value is of wrong type for this column

Have tried remove and reinstall, no luck.

---

