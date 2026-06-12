---
title: "Google-Earth install fails"
date: 2010-10-04
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by Yumi on 2010-10-04
I need the latest version of google-earth so I downloaded a .bin file. Trying to install with sh results in the following error:

setup.data/setup.xml:1: parser error : Document is empty
setup.data/setup.xml:1: parser error : Start tag expected, '<' not found
Couln't load 'setup.data/setup.xml'


Is this a google-earth problem or Maverick, and maybe some advice on how to correct the problem.

---

### Post by sendblink23 on 2010-10-04
I surfed a bit... found this

can you give it a try:

```
./GoogleEarthLinux.bin --target /tmp/ge
cd /tmp/ge/setup.data/bin/Linux/x86/
mv setup.gtk setup.gtk2
cd /tmp/ge
./setup.sh
```

or try this, a comment posted from someone around the internet:
> Kumar, rather than installing the .bin file, you might want to try adding the Medibuntu repositories ( visit this page:  [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu) ) and then install the programme from Synaptic («System» &#8594; «Administration»). Besides ensuring that the latest version is installed and that updates will be available via the Ubuntu updater, doing so automatically places a Google Earth button on «Applications» &#8594; «Internet». In my experience, this is the easiest way to installing Google Earth on Ubuntu ; moreover it provides access to a lot of other useful applications....

---

### Post by Yumi on 2010-10-04
Thank you. The code worked. Your googeling is better than mine  :P

---

