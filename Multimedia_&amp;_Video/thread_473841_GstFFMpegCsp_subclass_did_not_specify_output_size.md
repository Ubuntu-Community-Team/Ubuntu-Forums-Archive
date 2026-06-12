---
title: "GstFFMpegCsp: subclass did not specify output size"
date: 2007-06-14
forum: Multimedia &amp; Video
---

### Post by mseewald on 2007-06-14
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/gstreamer0.10-pitfdll/+bug/114079](https://bugs.launchpad.net/ubuntu/+source/gstreamer0.10-pitfdll/+bug/114079) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Dear Ubuntu'ians,

I had a weird problem with the error "GstFFMpegCsp: subclass did not specify output size" when trying to play WMV or AVI files from samba shares with totem-gstreamer. Finally solved it, by reading the [bug report]("https://bugs.launchpad.net/ubuntu/+source/gstreamer0.10-pitfdll/+bug/114079") and applying the [patch.]("http://bugzilla.gnome.org/attachment.cgi?id=86129&action=view") Maybe the instructions below are useful to others as well.

**Solution:**

```
wget -O decoders-srcpad-use-fixed-caps-1.diff "http://bugzilla.gnome.org/attachment.cgi?id=86129&action=view"
sudo apt-get source gstreamer0.10-pitfdll
sudo apt-get install libgstreamer0.10-dev libgstreamer-plugins-base0.10-dev cdbs
cd gstreamer0.10-pitfdll-0.9.1.1+cvs20060515
patch -p0 < ../decoders-srcpad-use-fixed-caps-1.diff
dpkg-buildpackage -rsudo -uc -us
sudo dpkg -i ../"gstreamer0.10-pitfdll_0.9.1.1+cvs20060515-1ubuntu1_i386.deb"

```

Regards,
Michael

PS: For me, the bug was weird because I saw it first a couple of weeks ago after installing Feisty Fawn for the first time. Then doing some deinstallations (totem-gstreamer), trying some other packages (totem-xine, others), it somehow disappeard (unreproducibly). It returned a couple of days ago for reasons still unknown to me. I could get rid of it by applying the patch.

---

### Post by mirceade on 2007-07-18
Confirming this "bug?!"... Same problems over here! Any idea of when this fix will be included in the repos'?

---

### Post by unknownsoldierX on 2007-08-30
sudo apt-get source gstreamer0.10-pitfdll

I get an error saying that it doesn't exist

---

### Post by ushaba on 2007-12-02
i am actually having this problem on gutsy, and while the patch works, every time synaptic tries to update it wants me to reinstall the same old buggy version of the plugin without the patch. is there a way to tell synaptic not to upgrade one specific file so i don't keep  getting notifications, while still allowing me to "upgrade all" without having to unclick the gstreamer plugin every time?

---

### Post by rakudave on 2008-03-16
bump!
same problem for me, patch worked but synaptics keeps telling me to "downgrade"

---

