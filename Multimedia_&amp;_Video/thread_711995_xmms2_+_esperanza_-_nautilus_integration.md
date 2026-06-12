---
title: "xmms2 + esperanza - nautilus integration?"
date: 2008-03-01
forum: Multimedia &amp; Video
---

### Post by dgel on 2008-03-01
Hi,

I'm trying to use xmms2 with esperanza, because xmms doesnt integrate in the look and feel of my other programs well and other music players are too bloated in my opinion
(I dont want a huge screen with all options, just a playlist and some buttons will do).

So, the problem I am facing:
I want to be able to select files/folders and have xmms2 play the files (in the folders) and have esperanza start as well.

Is this possible? Does anyone have experience with this?

[offtopic:]
this client / daemon dissociation will scare potential users away if such things are not available..
music continuing after the client is shut down was just weird the first time

---

### Post by kaivalagi on 2008-03-24
Sounds like a need for nautilus scripts to me, I have just started using xmms2 and am looking at the various client options, or lack of, at the moment too.

---

### Post by kaivalagi on 2008-03-25
Looking in more detail, xmms2 is all about medialib and playlists, you need a script to either 1) add files/folder to the default xmms2 playlist which will get played when it gets there or 2) a script to remove existing playlist, create a new playlist and then play it. 

In the console have a look at the xmms2 commands available, this will give you an idea of what's possible. type 'xmms2' to get a list of basic commands, 'xmms playlist' for playlist options etc etc. The one command that stood out to me was 'xmms2 radd' which adds a directory recursively to the playlist...

One or more of these command options in conjunction with a script that picks up nautilus highlighted files/folders should do the trick. Take a look on gnome-look.org for nautilus scripts if you haven't already, it should provide you with enough examples on how.

When I get time I'll have a go myself, I could do with something like this myself ;) For now I am settling for adding my fav music into the playlists upfront which will do for now.

A quick example of a nautilus script is below, this one opens one or more files as root in gedit...something like this but using 'xmms2 radd' instead of gedit would be a start (remembering to remove the root access options):

```
#!/bin/bash

gksudo -k /bin/echo "Give root access?"

for uri in $NAUTILUS_SCRIPT_SELECTED_URIS; do
sudo gedit $uri &
done
```

An executable script file would then need to be put into ~/.gnome2/nautilus-scripts to be available on right click

Hope that helps

---

### Post by kaivalagi on 2008-03-25
Na-Fiann, you owe me a virtual beer!

Find attached 2 perl scripts for Nautilus to play or enqueue files in xmms2 AND load Esperanza if not loaded already. You'll need perl installed if it isn't already (sudo apt-get install perl)

Stick the atached files in your ~/.gnome2/nautilus-scripts folder and make sure they're executable, otherwise they won't show up in the script context menu off right click in nautilus. You may want to rename them, at least to loose the .txt I had to put on the end.

"Play in XMMS2" will clear whatever is in your playlist and startup what you told it to.
"Enqueue in XMMS2" will add what you've selected onto what's already there in your current playlist.

I've just finished them, and only tested them briefly, so come back to me with any issues. If I find any issues in using them myself, I'll repost here.

I initially tried using shell scripts and failed, there were problems with the nautilus URI not being compatible with xmms2, so I used perl instead to get at those handy split functions to seperate out the files or folders nicely...

Enjoy :)

---

