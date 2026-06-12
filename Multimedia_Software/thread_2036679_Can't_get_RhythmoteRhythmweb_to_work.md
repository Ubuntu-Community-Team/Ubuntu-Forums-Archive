---
title: "Can't get Rhythmote/Rhythmweb to work"
date: 2012-08-02
forum: Multimedia Software
---

### Post by RichardC400 on 2012-08-02
All I want is to be able to use my android device as a control for Rhythmbox
I looked into it and found to items:
Rhythmote, and Rhythmweb.
They both told me the same thing:
Download, extract and move the file to ~/.gnome2/rhythmbox/plugins
and I did.
Then it says open Rhythmbox and go to Edit>Plugins> and check rhythmote/ruckusDJ/rhythmweb for installation.
I went into plugins, and none of them were there.
I'm running 12.04 and rhythmbox version 2.96

---

### Post by davidmohammed on 2012-08-02
yes - those plugins only work on rhythmbox 0.1x.

The version in 11.10/12.04 and later require GTK3+ - those plugins will needs to be recoded.

During my testing I couldnt get the original rhythmweb 0.1x to work correctly even on Natty (11.04).  Looks like from the code the HTTP response being generated is incorrect but I'm no expert.

Anyway - to give those more knowledgable a starter-for-10 - I've converted rhythmweb to GTK3+ - its on my [GitHub repo]("https://github.com/fossfreedom/rhythmweb").

If you are interested in this - feel free to hack the code to get it to generate the correct HTTP headers/response when clicking the web remote control options.

To run - clone the repo

save the folder in ~/.local/share/rhythmbox/plugins
activate it in rhythmbox

Put some tracks into the playqueue.

Use your favourite browser and browse to localhost:8000

---

### Post by davidmohammed on 2012-08-03
... this alternative solution maybe something you may be interested in

[https://github.com/bsaleil/rhythmbox-android-remote]("https://github.com/bsaleil/rhythmbox-android-remote")

It looks from the description as an application that listens for events from the banshee android app and translates this into instructions that rhythmbox can understand.

Hope this helps.

---

