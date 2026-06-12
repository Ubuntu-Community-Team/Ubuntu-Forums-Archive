---
title: "Rhythmbox Crashes"
date: 2007-11-04
forum: Multimedia &amp; Video
---

### Post by Pepsta on 2007-11-04
Hi All,

lately not sure why Rythmbox thinks it's a good idea to just exit for no apparent reason... :confused: I've searched the forums and people have mentioned similar issues and one options was to run from the command line to see what error is produced, this is what I get;

(rhythmbox:10461): libgnomevfs-WARNING **: trying to read from a non-existing handle

(rhythmbox:10461): libgnomevfs-WARNING **: trying to read from a non-existing handle

(rhythmbox:10461): libgnomevfs-WARNING **: trying to read from a non-existing handle

(rhythmbox:10461): libgnomevfs-WARNING **: trying to read from a non-existing handle
Segmentation fault (core dumped)

does this make sense to anyone...?

Thanks.

---

### Post by Pepsta on 2007-11-05
After some more searching It appears the unprovoked exit of the application was due to the "Cover Art" plugin combined with Proxy Internet access time outs. A bug has been launched in Launchpad for this error. A quick fix is to disable the plugin momentarilly, until a solution is provided.

---

