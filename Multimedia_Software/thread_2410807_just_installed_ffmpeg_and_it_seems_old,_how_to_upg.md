---
title: "just installed ffmpeg and it seems old, how to upgrade it?"
date: 2019-01-21
forum: Multimedia Software
---

### Post by babag on 2019-01-21
i just installed ffmpeg and it seems to be v3.4.4 from sometime in 2017. i'd like to get a newer version since they're up to v4.1 now. what would be the way to do this? i know how to install but not how to upgrade something that's already there.

thanks,
babag

---

### Post by vernies on 2019-01-21
If you constantly want to have updates, then clone it's repository. That way you can build latest updates just by fetch & pull.

Take a look at [Compilation Guide]("https://trac.ffmpeg.org/wiki/CompilationGuide/Ubuntu"). Here's a quote from the link:
> **Updating FFmpeg**

[COLOR=#000000][FONT=Verdana]Development of FFmpeg is active and an occasional update can give you new features and bug fixes. First you need to delete (or move) the old files:
[/FONT][/COLOR]```
rm -rf ~/ffmpeg_build ~/bin{ffmpeg, ffprobe, ffplay, x264, x265}
```

[COLOR=#000000][FONT=Verdana]Now can just follow the guide from the beginning.[/FONT][/COLOR]

---

### Post by Dennis N on 2019-01-21
There is a PPA. Here is one Google search turned up:
[https://launchpad.net/~jonathonf/+archive/ubuntu/ffmpeg-4](https://launchpad.net/~jonathonf/+archive/ubuntu/ffmpeg-4)
Judge for yourself. It has a package for Ubuntu 18.04.

---

### Post by kostkon on 2019-01-21
You could try the snap package:
```
snap install ffmpeg
```

---

### Post by slickymaster on 2019-01-21
*Thread moved to **Multimedia Software**.*

---

### Post by mc4man on 2019-01-21
> **kostkon said:**
> You could try the snap package:
```
snap install ffmpeg
```

The snap ffmpeg is pretty well done, worth trying.
If you don't have a .deb version of ffmpeg installed then it's likely it can be run by just a command of ffmpeg  ...
Otherwise use snap run ffmpeg  ...

Overall pretty well configured, vaapi hardware decoding/encoding is broken but the value of that is limited (nvenc does work..
Missing av1 encoding via libaom but again not too useful as incredibly slow (4-8 hrs. per min here..

The snap will auto-update.

Edit: if needed ffplay and ffprobe are in snap, commands would be 
```
snap run ffmpeg.ffplay   
snap run ffmpeg.ffprobe
```

---

### Post by babag on 2019-01-26
this looks good! do i have to uninstall the current installation before installing the snap?

thanks,
BabaG

---

### Post by deadflowr on 2019-01-26
> **babag said:**
> this looks good! do i have to uninstall the current installation before installing the snap?

thanks,
BabaG

Nope.
Snap and regular apt-based packages (as well as flatpak packages, too) can all run side by side (by side).

---

### Post by babag on 2019-01-26
cool. if i have both installed, though, how do i specify which one i want to use when on the command line? i normally would just issue 'ffmpeg blah blah blah' to run a command. is there some way i would specify which version i want to run?

thanks,
BabaG

---

### Post by mc4man on 2019-01-26
> **babag said:**
> cool. if i have both installed, though, how do i specify which one i want to use when on the command line? i normally would just issue 'ffmpeg blah blah blah' to run a command. is there some way i would specify which version i want to run?

thanks,
BabaG

If you have both a snap & .deb version installed then ffmpeg will call the .deb binary, i.e, /usr/bin/ffmpeg. 
The snap would then be used  with command of /snap/bin/ffmpeg

If only the snap is installed then command of  ffmpeg will use the snap binary This is set by the default install's   $PATH which has /snap/bin last.
$ $PATH
bash: /usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games:/snap/bin:

---

### Post by mc4man on 2019-01-26
Note about snap ver.

If you have Intel gpu then likely any time you use it you'll see some  `libGL error:... messages. 
Not fatal, just means no vaapi support for decoding, encoding, and ffplay may not work at all.
[https://github.com/snapcrafters/ffmpeg/issues/16](https://github.com/snapcrafters/ffmpeg/issues/16)
Also it's possible that libfdk-aac en/decoding will be dropped, may matter to some, issue #32 @ above ( the native ffmpeg aac encoder is fine for most..


(- i've another alt. to[ ffmpeg here]("https://launchpad.net/~mc3man/+archive/ubuntu/bionic-media"). It's built only for the use of the binaries ffmpeg, ffplay, ffprobe. Also it's not useful to build on so the ffmpeg and it's header files are installed to /opt/ where the system won't find (pkg-config
Mildly better than snap for lightly used stuff like libaom av1 encoding  & libdav1d av1 decoding in ffplay (which works). nvenc & vaapi en/decode work fine. fdk-aac is latest upstream

There is also a standalone binaries only build here, it's run directly from dir. it's placed in
[https://johnvansickle.com/ffmpeg/](https://johnvansickle.com/ffmpeg/)

---

### Post by babag on 2019-01-26
thanks! does the above mean that encoding aac might not work? i do that sometimes.

---

### Post by mc4man on 2019-01-27
> **babag said:**
> thanks! does the above mean that encoding aac might not work? i do that sometimes.

No, it will always work. Atm with the snap you can use either -c:a aac (the native aac encoder) or -c:a libfdk_aac (the fdk-aac encoder)

---

### Post by babag on 2019-01-27
perfect. thanks!

---

