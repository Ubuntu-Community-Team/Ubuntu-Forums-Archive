---
title: "Installing Flash On Opera"
date: 2016-12-31
forum: Multimedia Software
---

### Post by shane_faulkinbury2 on 2016-12-31
I just loaded Opera on my Ubuntu 16.04 LTS desktop and I was on Youtube and the videos won't play.  So I went to Adobes website to get Flash for the browser and downloaded and installed the apt for Opera and the videos still won't play.  Does anyone have any suggestions?

I know there is a way to load it through my terminal if that would help?

---

### Post by ajgreeny on 2017-01-01
Try enabling the canonical-partner repos which you will find in the Other Software tab in software-sources and then install **adobe-flashplugin** package which I believe is all you need for opera as well as other browsers.

---

### Post by shane_faulkinbury2 on 2017-01-01
Much appreciated AJ.  All I had to do is check the canonal-partners repos in Other Software!  The flash-plugin was already installed.

---

### Post by Yellow Pasque on 2017-01-01
Youtube should be using html5 for playback; it should not be using Flash.
See this for suggestions: [https://help.ubuntu.com/community/OperaBrowser](https://help.ubuntu.com/community/OperaBrowser)

---

