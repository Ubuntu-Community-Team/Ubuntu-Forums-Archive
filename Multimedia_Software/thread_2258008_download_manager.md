---
title: "download manager"
date: 2014-12-24
forum: Multimedia Software
---

### Post by sarower2 on 2014-12-24
which download manager is the best for ubuntu 14.04 ??? and how to install ???:popcorn:

---

### Post by sudodus on 2014-12-24
Welcome to the Ubuntu Forums :-)

Program packages are often installed from the Ubuntu repositories. This is different from Windows. Some programs are not available that way, and are more complicated to install. In that case you must use the instructions available. But start with the vast amount of programs that can be installed from the Ubuntu repositories :-)

If you want an intuitive way to do it, use the ***Software Center***

If you want a more advanced GUI tool, install ***Synaptic*** (via the Software Center) and activate some more repositories.

If you want full flexibility, use the command line tool ***apt-get*** with superuser privileges in a terminal window, for example

```
sudo apt-get install synaptic
```

```
sudo apt-get install ubuntu-restricted-extras
```

to get codecs, flashplayer and other things to play music and video,

```
sudo apt-get install gimp
```

to get the GNU Image Manipulation Program.

---

### Post by ajgreeny on 2014-12-24
A download-manager for what particular purpose?

I suspect most users have no specific download-manager installed, though there are some add-ons for browsers, such as **downthemall** for firefox
[https://addons.mozilla.org/en-US/firefox/addon/downthemall/?src=ss](https://addons.mozilla.org/en-US/firefox/addon/downthemall/?src=ss)
or for chromium
[https://chrome.google.com/webstore/detail/getthemall-downloader-gta/nbkekaeindpfpcoldfckljplboolgkfm?hl=en-GB](https://chrome.google.com/webstore/detail/getthemall-downloader-gta/nbkekaeindpfpcoldfckljplboolgkfm?hl=en-GB)

---

