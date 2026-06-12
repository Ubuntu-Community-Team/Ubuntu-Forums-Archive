---
title: "HOWTO: Edit playlists on the Sansa View using the MTP protocol"
date: 2009-01-29
forum: Multimedia Software
---

### Post by glennric on 2009-01-29
I recently purchased a Sansa View MP3 player for my wife.  I tried some of the software available for creating and editing playlists, and was not satisfied with the results.  Amarok, Gnomad2, and Qlix work to some extent, but I had various problems with these on the Sansa View.  So I wrote a program to do it.  I call it the "MTP Playlist Editor" or "playedit".

You can install playedit from my ppa repository
```
deb http://ppa.launchpad.net/glennric/ppa/ubuntu intrepid main
```

Playedit depends on at least version 0.3.5 of libmtp.  I have included version 0.3.6 in my repository.  So to install playedit after adding the above repository, run the following commands from a terminal:
```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install playedit
```

I am calling this a beta release, and am hoping for some input as to how users feel about the interface, and any bugs that may be found.  Eventually I intend to make this program more than a playlist editor, and make it capable of adding and removing music, and more.  Feel free to visit the projects home page at [http://playedit.sourceforge.net/index.html]("http://playedit.sourceforge.net/index.html").  Also please report any bugs or make feature requests at the projects Sourceforge page [https://sourceforge.net/projects/playedit/]("https://sourceforge.net/projects/playedit/")

---

