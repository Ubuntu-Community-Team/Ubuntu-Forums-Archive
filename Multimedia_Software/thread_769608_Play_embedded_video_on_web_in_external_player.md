---
title: "Play embedded video on web in external player"
date: 2008-04-26
forum: Multimedia Software
---

### Post by OMRebel on 2008-04-26
I just did a fresh install of 8.04, but it never dawned on me that FF 3 came with it.  For a website I subscribe to, they go through a company called Jump TV.  The video that is streamed is embedded into a webpage, and when loading up that page in FireFox, nothing happens.  I used to use an extension called Embedded, which would let me see the links of any embedded video, so I could launch it with whichever media player I wanted.  But, that extension isn't available for FF3.

The media that is embedded in Windows Media.  The url for it usually ends in swf, so that means (and I could be wrong), that it's embedded in some sort of Flash player built into the site.

Any suggestions on getting this to work?

Thanks.

---

### Post by cor2y on 2008-04-26
You could manually download the extension (the .xpi file)and hack it (edit the install.rdf) to work with firefox 3
An Example of what to look for to edit
```

<!-- FireFox -->
    <em:targetApplication>
        <Description>
        <em:id>{ec8030f7-c20a-464f-9b0e-13a3a9e97384}</em:id>
        <em:minVersion>1.5</em:minVersion>
        <em:maxVersion>2.0.*</em:maxVersion>
        </Description>
    </em:targetApplication>
``` Replace 2.0.* with 3.0.* save and then manually install and it will work in most cases with firefox3
All you need to edit the .rdf is gedit and the archive manager fileroller.

---

