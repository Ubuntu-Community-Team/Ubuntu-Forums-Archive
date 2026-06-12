---
title: "Opendesktop shared mime mime.cache file"
date: 2009-02-23
forum: Multimedia Software
---

### Post by smcardle on 2009-02-23
Hi,

This is my first post on this forum so I hope it conforms to the norm.

Down to business: I am the author of an open source java mime detection utility called mime-util hosted on source forge. 

As an addition to this utility we would like to extend our  integration to the Opendesktop shared MIME-Info database. I am writing this integration on Intrepid using the supplied "out of the box" files.

One of the files created by the update-mime-database utility is the mime.cache file located in the /usr/share/mime directory. This is a binary memory mapped file containing an accumulation of other generated files such as glob2, magic, subclasses, aliases, icons and XMLnamespaces files. The url for the spec is:
[http://standards.freedesktop.org/shared-mime-info-spec-shared-mime-info-spec-latest.html](http://standards.freedesktop.org/shared-mime-info-spec-shared-mime-info-spec-latest.html)

So far I have successfully extracted all types described in the spec with the exception of the glob2 entries. The offset location for the globs in the mime.cache file should contain a CARD32 entry containing the number of globs in the file. On Intrepid this reports that it only contains 2 glob entries. However, looking at the XML globs2 source file there are infact 720 glob entries.

The 2 glob entries I am able to retrieve are:

glob=*.anim[1-9]j mimeType=video/x-anim weight=50
glob=README* mimeType=text/x-readme weight=10


Can anybody tell me why this is? Is it a problem with the update-mime-database utility? or are the default file distributed with Intrepid just wrong?

I look forward to any feedback from the community regarding this issue.

Regards

Steven McArdle

---

