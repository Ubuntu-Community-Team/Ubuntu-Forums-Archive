---
title: "QDVDAuthor install is imcomplete on Lucid amd64"
date: 2010-07-03
forum: Multimedia Software
---

### Post by Nick Payne on 2010-07-03
I just installed QDVDAuthor via Synaptic - no errors indicated on the install. On first running it, I get a dialog containing the following:

```
There are newer versions available for :
Masks: The masks library is missing on your system.
Buttons: The button library is missing on your system.
Transitions: The transitions library is missing on your system.
Do you want to download the latest libraries now ?
Could not locate any GUI for root
Please execute the following commands as root.
#!/bin/bash cd /tmp 
wget http://qdvdauthor.sourceforge.net/data/masks.tar.bz2 -O masks.tar.bz2 
cd /usr/share/qdvdauthor/ 
tar -xjf /tmp/masks.tar.bz2 
cd /tmp 
wget http://qdvdauthor.sourceforge.net/data/buttons.tar.bz2 -O buttons.tar.bz2 
cd /usr/share/qdvdauthor/ 
tar -xjf /tmp/buttons.tar.bz2 
cd /tmp 
wget http://qdvdauthor.sourceforge.net/data/alpha_trans.tar.bz2 -O alpha_trans.tar.bz2 
cd /usr/share/qdvdauthor/ 
tar -xjf /tmp/alpha_trans.tar.bz2
```

I executed the commands and it now works ok.

---

### Post by graemev on 2010-12-21
Thanks that helps.

Seem qdvdauthor ignores proxy settings , so mots INTERNET access fails (sometime silently) this
fixed thses things...just need a way of getting some templates now ... since the interface won't allow
local file install and the internet access again does not work.

---

