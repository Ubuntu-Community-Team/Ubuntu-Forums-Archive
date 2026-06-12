---
title: "Launching Wengophone"
date: 2007-01-05
forum: Multimedia &amp; Video
---

### Post by pingvin on 2007-01-05
Hi there,

I'm looking for a bit of help with Wengophone 2.0, as downloaded from Wengo's website. I downloaded the 16MB (I think) binary and, according to instructions on the site, to run it I type ```
LD_LIBRARY_PATH=. ./qtwengophone
``` once in the wengophone directory. Also, there is a script in this directory, and both methods work fine. However, they both leave me with a dirty big terminal running along side Wengophone. Does any one know how to run it 'quietly', ie. without the terminal? Preferably from some kind of panel launcher :-)

Many thanks in advance,

Mike

Btw, I run Dapper with Gnome, if that helps.

---

### Post by pingvin on 2007-01-06
SOLVED: Thanks to st14n:

 Re: Anybody got Wengo working on Edgy?
Quote:
Originally Posted by pingvin View Post
Is there a way to run it 'quietly'? And to create a nice little launcher button?
To run it from a terminal with no output and with the wengophone process in the background, start it with
Code:

./wengophone.sh &> /dev/null &

That is, you start the script 'wengophone.sh' instead of 'qtwengophone', redirect all output to /dev/null (that is means showing no ouput), and send the process to the background.

If you want an entry in the menu, use the program 'alacarte' and add a entry that launches '/PATH-TO-WENGOPHONE/wengophone.sh'.

---

