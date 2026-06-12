---
title: "rm to avi"
date: 2007-02-11
forum: Multimedia &amp; Video
---

### Post by darkmediator on 2007-02-11
Hi
How can I convert rm to avi in linux?

---

### Post by tbroderick on 2007-02-11
Don't know if you can, but try mencoder.

---

### Post by darkmediator on 2007-02-11
How to try that?

---

### Post by tbroderick on 2007-02-11
Install mencoder and the w32codecs. 

[How to Enable Multiverse]("https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/extra-repositories.html")

[Installing Packages with Apt]("https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/apt.html")

[Installing the w32codecs]("https://help.ubuntu.com/community/RestrictedFormats/WindowsCodecs")

Once all those things are done, you can try using mencoder. Try searching with google to see if there ar any examples of people converting .rm to .avi because mencoder has a lot of settings to choose from. A real basic example would be;

```
mencoder replayerfile.rm -ovc lavc -oac pcm -o new.avi
```

I have not converted any .rm, but have converted .wmv. This is what I use for that;

```
mencoder file.wmv -ovc lavc -oac mp3lame -o file.avi -ofps 30000/1001
```

---

### Post by darkmediator on 2007-02-12
thanx man...but the process is too slow!

---

### Post by DrZeus on 2007-06-17
i think here is the answer:
[URL="http://www.linuxdevcenter.com/pub/a/linux/2003/04/06/mplayer.html"]
http://www.linuxdevcenter.com/pub/a/linux/2003/04/06/mplayer.html[/URL]

---

### Post by artistgay on 2007-10-20
> **tbroderick said:**
> Install mencoder and the w32codecs. 

[How to Enable Multiverse]("https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/extra-repositories.html")

[Installing Packages with Apt]("https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/apt.html")

[Installing the w32codecs]("https://help.ubuntu.com/community/RestrictedFormats/WindowsCodecs")   

Once all those things are done, you can try using mencoder. Try searching with google to see if there ar any examples of people converting .rm to .avi because mencoder has a lot of settings to choose from. A real basic example would be;

```
mencoder replayerfile.rm -ovc lavc -oac pcm -o new.avi
```

I have not converted any .rm, but have converted .wmv. This is what I use for that;

```
mencoder file.wmv -ovc lavc -oac mp3lame -o file.avi -ofps 30000/1001
```

The commands in the w32 codecs  link do not work.....getting a 404 not found!!
Maybe there is another way to get the w32 codecs for Gutsy???:confused:

---

### Post by GavinZac on 2008-05-17
> **artistgay said:**
> The commands in the w32 codecs  link do not work.....getting a 404 not found!!
Maybe there is another way to get the w32 codecs for Gutsy???:confused:

medibuntu

---

