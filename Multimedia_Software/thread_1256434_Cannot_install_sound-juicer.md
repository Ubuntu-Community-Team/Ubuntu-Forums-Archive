---
title: "Cannot install sound-juicer"
date: 2009-09-02
forum: Multimedia Software
---

### Post by argie53 on 2009-09-02
When I try to install Audio CD Extractor I get an error message as follows:

Cannot install 'sound-juicer'
This application conflicts with other installed software.
To install 'sound-juicer' the conflicting software must be removed first.

Switch to the synaptic package manager to resolve this conflict.

Which is the conflicting software?
What do you remove?

Please help!

Thanks

---

### Post by bootdoc on 2009-09-02
open synaptic and try to install from there.  when you "mark for installation" it should tell you which application is blocking the install.  If it doesn't tell you at that point click the apply button and you should get a message there.  if you get nothing there you can try using apt-get install sound-juicer and when it fails try apt-get install -f.

good luck.

---

