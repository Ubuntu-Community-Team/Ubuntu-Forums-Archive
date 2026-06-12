---
title: "fix: om-synth installation in Edgy"
date: 2006-10-31
forum: Multimedia &amp; Video
---

### Post by tecteun on 2006-10-31
the om-synth installation in Edgy (and maybe other distro's) isn't functioning properly....

there is a bug in the script /usr/bin/launchomsynth

when running launchomsynth it says: 
/usr/bin/launchomsynth: 9: Syntax error: "(" unexpected

line 9 : function is_om_running()

has to be:
is_om_running()   <<---- without the prefixed "function"

now om_synth starts fine!

Hope someone makes use of this knowledge, 
k lets synthesize!! w00t 
:cool:

---

