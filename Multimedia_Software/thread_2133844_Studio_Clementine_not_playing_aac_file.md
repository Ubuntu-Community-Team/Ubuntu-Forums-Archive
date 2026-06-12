---
title: "Studio Clementine not playing aac file"
date: 2013-04-09
forum: Multimedia Software
---

### Post by 33Nicolas on 2013-04-09
It'sfrustrating being that close from your almost ideal systema and only be hung back because your player won't play an aac file.

Anyone has had that problem? I'm pretty new here and mostly a GUI guy wanting to use the terminal more.

Thanks, Nicolas

---

### Post by ibjsb4 on 2013-04-09
I do not use Clementine, but post #18 indicates it could be missing plugins.

[http://ubuntuforums.org/showthread.php?t=2099985](http://ubuntuforums.org/showthread.php?t=2099985)

The missing plugins are part of the restricted extras package.  If not already installed you could ..

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by speartip on 2013-04-09
Clementine is playing aac files fine here on 12.04.
As is mentioned you may need to install the restricted extras.
```
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by 33Nicolas on 2013-04-09
Thanks, they were already installed.

---

### Post by Yellow Pasque on 2013-04-09
What does this command return?
```
gst-inspect-0.10 | grep -i aac
```

---

### Post by speartip on 2013-04-10
I have checked in synaptic to see what "aac" programs are installed.
Check if you have libfaac0, faac, & faad installed.
I also have the medibuntu repo enabled, with libavcodec-extra-53 installed.

Just another question.
Is it all aac files that wont play or just a specific one?

---

### Post by mmstick on 2013-04-10
Considered renaming aac to m4a? VLC also doesn't play AAC files if they have AAC extension as well, as it looks for M4A extension instead. Not really sure why they haven't patched that yet though.

---

### Post by 33Nicolas on 2013-04-11
Good point will do. thx

---

