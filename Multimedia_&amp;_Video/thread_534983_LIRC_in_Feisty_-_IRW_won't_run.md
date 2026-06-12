---
title: "LIRC in Feisty - IRW won't run?"
date: 2007-08-25
forum: Multimedia &amp; Video
---

### Post by Seantiago on 2007-08-25
Hi there.

I followed the instructions here: [https://help.ubuntu.com/community/Install_Lirc_Feisty]("https://help.ubuntu.com/community/Install_Lirc_Feisty")

to try to set up my StreamZap remote to work with my Feisty installation. Everything seemed to go pretty smoothly, up to the point when I reached the "Star LIRC and Test" section. I typed in this command:

```
$ sudo /etc/init.d/lirc start
```

which worked out ok, but then when I typed in this:

```
$ irw
```

it returned me to the command prompt. It's supposed to hang, so that I can press buttons on the remote and see that the everything is communicating nicely. I've tried rebooting my computer and running dmesg as the howto suggests, but dmesg literally gives me nothing. Any ideas what in the dickens is going on here?

Thank you.

---

### Post by Seantiago on 2007-08-25
Never you mind, fellows, that was a false alarm. Turns out I didn't follow that howto nearly as closely as I thought I had. I seem to have missed a whole section. Everything seems to be running quite nicely now. Thanks anyways.

---

