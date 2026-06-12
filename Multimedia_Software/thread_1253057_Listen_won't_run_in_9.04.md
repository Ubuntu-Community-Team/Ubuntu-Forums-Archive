---
title: "Listen won't run in 9.04"
date: 2009-08-29
forum: Multimedia Software
---

### Post by jeffbarish on 2009-08-29
Since upgrading to 9.04, I can no longer run Listen.  I tried running it with Python 2.5 to avoid the deprecation warnings, but I still get:

No iPod support
location: /usr/lib/xulrunner-1.9.0.13/libxpcom.so 
before 3
0:00:01.440674360 12485  0xa1afbc0 ERROR           GST_PIPELINE ./grammar.y:604:_gst_parse_yyparse: no element "gconfaudiosink"
0:00:01.440759687 12485  0xa1afbc0 ERROR           GST_PIPELINE ./grammar.y:872:_gst_parse_launch: Unrecoverable syntax error while parsing pipeline gconfaudiosink
0:00:01.440823659 12485  0xa1afbc0 ERROR           GST_PIPELINE ./grammar.y:604:_gst_parse_yyparse: no element "autoaudiosink"
0:00:01.440859099 12485  0xa1afbc0 ERROR           GST_PIPELINE ./grammar.y:872:_gst_parse_launch: Unrecoverable syntax error while parsing pipeline autoaudiosink
No audio sink found for Gstreamer


I reinstalled gstreamer0.10-plugins-good and listen.  No change.

---

