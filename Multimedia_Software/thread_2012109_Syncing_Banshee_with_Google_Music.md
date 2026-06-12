---
title: "Syncing Banshee with Google Music"
date: 2012-06-28
forum: Multimedia Software
---

### Post by db579 on 2012-06-28
Is there any way to sync Google music manager with banshee so that it only uploads specific playlists for example? 

The official support page says this 

[http://support.google.com/googleplay/bin/answer.py?hl=en&answer=1311216](http://support.google.com/googleplay/bin/answer.py?hl=en&answer=1311216)

But the option doesn't appear to exist on the Linux client. Is there any way around this?

---

### Post by slosd on 2012-08-02
There is an extension "FolderSync" in the banshee-community-extensions package (it's in 12.04, if you don't have that you can run ```
sudo add-apt-repository ppa:banshee-team/ppa
``` to add the banshee repository unless you already have it). 

I never tried it but it says it "copies and synchronizes music files from playlists into user specified folders". 
So you need to configure the extension to copy songs from, say, the "Google Music" playlist to a folder "X" and add this folder "X" to the folders the google music manager watches. 
Unfortunately this will probably duplicate the files you add to this playlist on your system. It would be nice if the extension would allow the user to configure it to create symlinks instead of "real" files. 

Hope this will work for you.

---

### Post by db579 on 2012-08-02
Hi, thanks for the suggestion. Unfortunately my library is really quite large so duplicates wouldn't really be an ideal solution for me. If that could be done with symlinks that could work well though...

---

### Post by slosd on 2012-08-02
> **db579 said:**
> Hi, thanks for the suggestion. Unfortunately my library is really quite large so duplicates wouldn't really be an ideal solution for me. If that could be done with symlinks that could work well though...

I just added this quick and dirty implementation. I'm not the project owner so it's in my own copy [https://gitorious.org/~slosd/banshee-community-extensions/slosds-banshee-community-extensions](https://gitorious.org/~slosd/banshee-community-extensions/slosds-banshee-community-extensions)
If you know how to build this you can use it immediately. Works well on my system.

---

### Post by db579 on 2012-08-02
Thanks a lot for your effort! I have to admit I'm not entirely sure what you've sent me though.

Do I just want to click source tree and download master as tar.gz and then extract and install from within Banshee or is there more to it?

---

### Post by slosd on 2012-08-02
This is from [http://banshee.fm/download/development/](http://banshee.fm/download/development/)

Install build tools and dependencies:
```
sudo apt-get install git-core autoconf automake libtool intltool gcc make libgconf2.0-cil-dev libgconf2-dev
sudo apt-get build-dep banshee
```

Get my changes (this will create a new folder in your current directory):
```
git clone git://gitorious.org/~slosd/banshee-community-extensions/slosds-banshee-community-extensions.git slosds-banshee-community-extensions
cd slosds-banshee-community-extensions
```

Make sure everything we need is executable:
```
chmod +x configure autogen.sh
```

Then build the extension (this creates the extensions in ./bin):
```
./autogen.sh
make
```

I don't know a way to have an extension somewhere in your home directory override an installed extension. This is how to replace it with backup ;)
```
sudo mv /usr/lib/banshee/Extensions/Banshee.FolderSync.dll /usr/lib/banshee/Extensions/Banshee.FolderSync.dll.bak
sudo cp bin/Banshee.FolderSync.dll /usr/lib/banshee/Extensions
```

---

### Post by db579 on 2012-08-02
Amazing thank you! Just going to try it now.

---

### Post by db579 on 2012-08-02
Got it installed (I think the third line should be:)

```

chmod +x configure.ac autogen.sh

```

But it doesn't sync any playlists. This seems to have been a bug at some point, do you have any idea how it works on your system? Thanks!

[https://mail.gnome.org/archives/banshee-list/2012-April/msg00138.html](https://mail.gnome.org/archives/banshee-list/2012-April/msg00138.html)

---

### Post by slosd on 2012-08-02
> **db579 said:**
> Got it installed (I think the third line should be:)

```

chmod +x configure.ac autogen.sh

```
I have a script called configure. You definately need this. 
**EDIT** This was probably just neccessary because I had troubles with file permissions. Should be alright like you did it if autogen.sh ends with something like ```
    RadioStationFetcher:   yes
    RandomByLastfm:        yes
    StreamRecorder:        yes
    Telepathy:             yes
    ZeitgeistDataprovider: no

```

> **db579 said:**
> But it doesn't sync any playlists. This seems to have been a bug at some point, do you have any idea how it works on your system? Thanks!

[https://mail.gnome.org/archives/banshee-list/2012-April/msg00138.html](https://mail.gnome.org/archives/banshee-list/2012-April/msg00138.html)

[LIST=1]
[*] Is it enabled?
[*] Go to Tools > Synchronize to Folder
[*] Select a folder (there seems to be a bug I discovered while testing it: [https://bugzilla.gnome.org/show_bug.cgi?id=681060](https://bugzilla.gnome.org/show_bug.cgi?id=681060))
[*] Check "Create as symbolic link"
[*] Press "Start sync"
[/LIST]

If this doesn't help you try running banshee from the command line:
```
banshee --debug
```
and post the last few lines that are printed after you pressed "Start sync".

---

### Post by db579 on 2012-08-02
This is the terminal output:

```


[1 Debug 14:32:51.800] Start of Sync triggered!
[1 Debug 14:32:51.802] Target folder is set to: file:///home/dan/test/
[14 Debug 14:32:51.804] Sync thread started!
[14 Debug 14:32:51.805] sync DONE, returning


```

Seems like it should have worked? Just returns instantly though and nothing is appears in the folder.

---

### Post by slosd on 2012-08-02
You need to select a playlist in the new list on the left (not the usual list that's always there)

The last disadvantage is that you need to trigger the syncing yourself.

---

### Post by db579 on 2012-08-02
I don't think I have a new list to select from? Here is a screenshot so you can see what I mean

---

### Post by slosd on 2012-08-02
> **db579 said:**
> I don't think I have a new list to select from? Here is a screenshot so you can see what I mean

I have an additional list, hm...
Are you sure there is nothing you can drag to make this list wider/appear?

---

### Post by db579 on 2012-08-02
Nothing obvious... dragging the standard list wider doesn't add anything to it. The folder sync pane doesn't allow me to resize or move anything as far as I can tell...

Bit stumped here...

---

### Post by db579 on 2012-08-02
Ah sorry ignore that just found it! Bit fiddly but the folder sync pane was resizeable after all!

Weirdly though the lists are not quite the same? (there are duplicates, one or two missing and a couple of old deleted playlists back) Any idea why that is?

---

### Post by slosd on 2012-08-02
> **db579 said:**
> Nothing obvious... dragging the standard list wider doesn't add anything to it. The folder sync pane doesn't allow me to resize or move anything as far as I can tell...

Bit stumped here...

I don't think it's terribly important but do you have the latest banshee release 2.4.1?

And check again. I can resize the list so that it is barely visible:

---

### Post by slosd on 2012-08-02
> **db579 said:**
> Weirdly though the lists are not quite the same? (there are duplicates, one or two missing and a couple of old deleted playlists back) Any idea why that is?

Same for me, I guess you can just ignore that. Smart playlists are missing. The extension seems to be in an early development state.

---

### Post by db579 on 2012-08-02
Okay well thanks a lot, really appreciate your time and help.

---

### Post by slosd on 2012-08-02
> **db579 said:**
> Okay well thanks a lot, really appreciate your time and help.

Does it work? And does google music manager react when the files get added?

---

### Post by db579 on 2012-08-02
Bit of a shame the playlists seem a bit messed up but yes I think it works! Google Music manager is uploading (deathly slowly but I guess it always is) so this largely seems to solve what I wanted. 

The only thing that's slightly bugging me about it is the numbers don't all match up. The banshee playlist has 4,314 songs in it, the folder with the symlinks 4,287 and google music manager finds 4,285...

---

