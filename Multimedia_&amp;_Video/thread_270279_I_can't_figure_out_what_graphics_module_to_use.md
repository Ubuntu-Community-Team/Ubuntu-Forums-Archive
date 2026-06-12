---
title: "I can't figure out what graphics module to use"
date: 2006-10-03
forum: Multimedia &amp; Video
---

### Post by kernco on 2006-10-03
After installing Ubuntu it was using the vesa driver by default, which is very slow.  I have a new Averatec 2260-EK1 laptop, which has a VIA K8N890 graphics chip.  I switched the driver to "via" and X would not start with the error "no device detected".  I tried building the driver myself and also building openchrome, but the via driver will still not work.  Am I using the wrong driver?  How do I figure out what driver to use?

---

### Post by shellster on 2007-01-06
Here are some open source drivers: [https://help.ubuntu.com/community/OpenChrome](https://help.ubuntu.com/community/OpenChrome)  They worked fine for me.

---

