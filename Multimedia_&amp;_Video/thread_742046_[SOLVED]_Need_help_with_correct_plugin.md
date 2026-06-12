---
title: "[SOLVED] Need help with correct plugin"
date: 2008-04-01
forum: Multimedia &amp; Video
---

### Post by famous3warriors on 2008-04-01
I have ubuntu studio x86 64 bit system.  I can play movies bought right from a store but a friend of mine made some movies for me to watch.  I can see the movie in my home dvd player but in my desktop I can't.  I keeps giving me a blank cd msg.  What can I do to fix that.  Thanks for your help.

---

### Post by warp99 on 2008-04-01
Put the DVD in the tray, open a console, and type the following:

```
mplayer dvd://
```

then post the output here (roughly about the first 50 lines).

---

### Post by famous3warriors on 2008-04-02
I apologize for not responding sooner warp99 I was in a bunch of meetings but this is what I get.

---

### Post by warp99 on 2008-04-02
Well according to the package list for Ubuntu Studio you don't have an application to play DVDs:

[https://wiki.ubuntu.com/UbuntuStudio/PackageList](https://wiki.ubuntu.com/UbuntuStudio/PackageList)

[https://help.ubuntu.com/community/UbuntuStudio/Applications](https://help.ubuntu.com/community/UbuntuStudio/Applications)

So you're going to have to install one, We need to install a player and the associated applications to play commercial (encrypted) DVD's. First is we need to update your repository list to access medibuntu for the libraries for encrypted DVD access. This guide will show you how:

[https://help.ubuntu.com/community/Medibuntu?highlight=%28medibuntu%29#head-7486ed038a9becc1dff10a24cc07a38a00d70e9f](https://help.ubuntu.com/community/Medibuntu?highlight=%28medibuntu%29#head-7486ed038a9becc1dff10a24cc07a38a00d70e9f)

Next you need to do the following:

```

sudo apt-get update
sudo apt-get install mplayer mplayer-gui libdvdread3 libdvdcss2
```

this will install the media application mplayer, a GUI front end for mplayer, and the correct libraries to read encrypted DVDs. Then issue the command:

```
mplayer dvd://
```

or use the GUI front end. Hope this helps.

---

### Post by famous3warriors on 2008-04-02
Ok I did exactly what you told me and this was the end result. But the wierd thing of it is that I can play regular dvd's not ripped dvd's

---

### Post by warp99 on 2008-04-02
Sorry, my bad, it use to be that you needed to install the GUI for mplayer, but not anymore. Use the following string instead:

```
sudo apt-get install mplayer libdvdread3 libdvdcss2
```

That should work. Please see my signature for more helpful tips.

---

### Post by wolfen69 on 2008-04-02
were the homemade dvd's burned with dvd+r?

---

### Post by famous3warriors on 2008-04-04
Thanks warp99 and wolfen69 I really do appreciate your help.  Yeah these movies were done in a dvd +r 16x.  I can't play them on my desktop but I can play them on my laptop and I has studio 7.10 i386.  So that's ok as long as I can see the movie's some where.

---

