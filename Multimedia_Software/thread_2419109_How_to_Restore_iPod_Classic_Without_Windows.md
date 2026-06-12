---
title: "How to Restore iPod Classic Without Windows"
date: 2019-05-16
forum: Multimedia Software
---

### Post by woodsyboredom on 2019-05-16
I need a little help installing Rockbox onto my iPod 5th Generation video. I am running Ubuntu Studio 18.04. I have downloaded the Rockbox Utility bootloader ant opens and is all set to install but I get a message telling that "permission is denied" I know that I need to run the Rockbox Utility in root or sudo and I found these instructions:

"I don't know if you guys are still having trouble with this or not, but what you need to do is download the Rockbox automatic installer from [http://www.rockbox.org/twiki/bin/vie...ility#Download](http://www.rockbox.org/twiki/bin/vie...ility#Download) and extract it. Then right click on the executable and click on "open with other application..." Instead of selecting a program, go down to the arrow where it says "use a custom command" and simply type in
Code: gksu"

The problem I'm having is that when I right click on "open with other application..." I do not get an option that says "use a custom command". I've tried to run Rockbox utility from Terminal but it doesn't know how to locate it in my downloads file and i don't know how to tell it how to look. Rockbox is not in the Software loader nor the synaptic package loader. I just need to run
 it in root. How?

---

### Post by Chronon on 2019-07-17
In a terminal, if you cd to the correct location then you should be able to type in a few letters from the file name and use TAB to autocomplete and it will locate it for you.

---

