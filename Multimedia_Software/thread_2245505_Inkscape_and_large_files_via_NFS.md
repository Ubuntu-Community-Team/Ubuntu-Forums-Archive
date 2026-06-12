---
title: "Inkscape and large files via NFS"
date: 2014-09-24
forum: Multimedia Software
---

### Post by sgofferj on 2014-09-24
Hi,

yesterday I created a fairly large (14.2MB) SVG with inkscape and saved it via NFS on my storage array. Today when I try to open it directly, inkscape says "Failed to open...". On the console, I see this:
```
sgofferj@enterprise:/serverhome/sgofferj/Documents/stefan.gofferje.net$ inkscape sgn_topics_600.svg 
Entity: line 166345: parser error : AttValue length too long
s1VLbGq+OF/xX609lbegqt+/j7z+yvN/Ss0vdj365jureL5aI3tFJVhgkoahOjgpGFj3d6Bvmapj
                                                                  ^
Entity: line 166345: parser error : Memory allocation failed
s1VLbGq+OF/xX609lbegqt+/j7z+yvN/Ss0vdj365jureL5aI3tFJVhgkoahOjgpGFj3d6Bvmapj
                                                                  ^
Entity: line 166345: parser error : attributes construct error
s1VLbGq+OF/xX609lbegqt+/j7z+yvN/Ss0vdj365jureL5aI3tFJVhgkoahOjgpGFj3d6Bvmapj
                                                                  ^
Entity: line 166345: parser error : Couldn't find end of Start Tag image line 36472
s1VLbGq+OF/xX609lbegqt+/j7z+yvN/Ss0vdj365jureL5aI3tFJVhgkoahOjgpGFj3d6Bvmapj
                                                                  ^

(inkscape:4551): Gtk-WARNING **: Theme file for default has no directories

sgofferj@enterprise:/serverhome/sgofferj/Documents/stefan.gofferje.net$
```

When I copy the file to the local disk, inkscape opens it without problems. Also other (smaller) files from the storage, inkscape can open just fine.
What might be the problem here?

-S

---

