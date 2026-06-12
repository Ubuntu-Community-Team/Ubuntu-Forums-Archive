---
title: "no MP4/M4V option in Handbrake"
date: 2014-05-03
forum: Multimedia Software
---

### Post by teacherjeff2 on 2014-05-03
I just did a clean install of Ubuntu 14.04. Now I've added ppa:stebbins/handbrake-snapshots to the repositories and installed Handbrake. It installs okay; I can start it. Says I have version rev5474 (x86_64).

But for "Format," MKV is the only option. No option for MP4, M4V, or similar.

I've searched, and apparently MP4 support is disabled in some versions. But the things I read suggest that it should still be present in the "snapshot" version, which is what I think I have installed.

Any suggestions? I'm still pretty new at this, and confused. (For that matter, I don't really even know what format I should be using. I just assumed MP4, and have used it in the past.)

---

### Post by SeijiSensei on 2014-05-03
Matroska ("MKV") is a remarkably flexible format that works well with material that has multiple languages or subtitle tracks.  As an open format, it wasn't well-supported initially, but now most any media device can play a Matroska file.  My Android phone can play them just fine with MXPlayer, and on the desktop there are many choices.  However you may have a particular target in mind that may, or may not, support Matroska.  

Matroska is my usual preference because I watch anime and deal with subtitles.  MP4 is a more widely-supported format because it has industry backing.  For instance, MP4 is Sony's preferred format so it will play on a PS3 while Matroska will not.  

If you're just ripping DVDs to watch on your computer with a program like SMPlayer or VLC, then MKV is a fine choice.  If you want to use these files on other devices, you'll need to see if they support Matroska.

---

### Post by teacherjeff2 on 2014-05-03
Thanks. My media player supports Matroska (or at least it's supposed to), so I'm going to give it a try.

I'm still a little curious about why Handbrake won't give me the MP4 option, though.

---

### Post by dannyboy79 on 2014-05-04
do you have all the libavcodec-extra-53, libavutil-extra-51, libavformat-extra-53 installed ? i believe that's required (i could be wrong however) to encode to mp4. I believe handbrake is just a GUI for either ffmpeg or avconv

---

### Post by SeijiSensei on 2014-05-04
Back in 2012, [Stebbins reported]("http://ubuntuforums.org/showthread.php?t=2076246&p=12319446&viewfull=1#post12319446") that he had fixed this problem in handbrake-snapshots, but that's the repository you used.

I suspect the problem is that you didn't run "sudo apt-get update" after installing the Stebbins PPA.  The version in [handbrake-snapshots](https://launchpad.net/~stebbins/+archive/handbrake-snapshots) is 6171svnppa1~trusty1.  The [official version](http://packages.ubuntu.com/trusty/allpackages) is 0.9.9+dfsg-2~2.gbpa4c3e9build1.

Run the command "dpkg -s handbrake".  One of two things will happen.  Either you will get back a report including the version number, or it will say the package is not installed.  If so, use the same command but with "handbrake-gtk" instead.  That package is in the Stebbins repository but not the official one.  

I've found the current snapshot rather unstable on my system, so I've removed it and installed the package for raring in handbrake-releases.  That includes MP4 as a option.  I uninstalled handbrake-gtk, renamed the file /etc/apt/sources.list.d/stebbins-handbrake-snapshots.trusty.list to stebbins-handbrake-releases-raring.list, and edited that file to read:
```
deb http://ppa.launchpad.net/stebbins/handbrake-releases/ubuntu raring main
```  All of those tasks require sudo.  Then I ran
```

sudo apt-get update
sudo apt-get install handbrake-gtk

```
and got a version of Handbrake with MP4 support.

If you don't want to follow that route, you can uninstall Handbrake with "apt-get remove," remove its PPA with "add-apt-repository -r", then install the PPA for [handbrake-releases]("https://launchpad.net/~stebbins/+archive/handbrake-releases") with add-apt-repository.  Don't forget to update.

Now about the why. Ubuntu cannot distribute software with MP4 support because [it is patent-encumbered]("http://en.wikipedia.org/wiki/Comparison_of_container_formats").  Installing "restricted-extras" solves the problem for most proprietary formats, but Handbrake might not be covered by that method.  At the bottom of the [Encoders](https://trac.handbrake.fr/wiki/Encoders) page at the Handbrake wiki it says that "HandBrake does not support external encoders. It is not possible to add an encoder to HandBrake at runtime. *All the encoder libraries are built in and not dynamically linked/loaded at runtime*."  That tells me Ubuntu must compile its official version of Handbrake without the MP4 support, and that adding libraries like libavcodec-* as dannyboy79 suggests will not solve the problem.

---

### Post by teacherjeff2 on 2014-05-04
Thanks. I followed your instructions, adding the raring line to the .list fine. It installed what appears to be the released version of handbrake for raring, which does indeed include an mp4 option. So you've solved my problem.

But just so I understand, could you clarify one thing? I understand (I think) about Ubuntu's not being able to distribute a version with MP4 support. This, as I understand it, the reason for adding the stebbins repositories. But why is MP4 support in the raring version and not in the trusty version? Is it just a question of things not having been updated yet?

BTW, I've investigated things a little, and it appears that MPV is probably the best format for my purposes anyhow, since I watch a lot of flims with subtitles. So I guess all of this wasn't strictly necessary. Still, I learned a lot.

Thanks again for the help.

---

### Post by Yellow Pasque on 2014-05-04
It's a licensing issue. Hopefully, it will be fixed in future releases.

[https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=695225](https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=695225)

---

### Post by SeijiSensei on 2014-05-05
> **teacherjeff2 said:**
> BTW, I've investigated things a little, and it appears that MPV is probably the best format for my purposes anyhow, since I watch a lot of flims with subtitles. So I guess all of this wasn't strictly necessary. Still, I learned a lot.

After I posted earlier, I tried a little experiment with my CD for the show [Monster]("http://www.imdb.com/title/tt0434706/?licb=0.284233766412087").  I tried ripping it to the MP4 container and told Handbrake to use both the English and Japanese audio tracks.  The final product had only the English.  With Matroska I got both.

---

### Post by leonc on 2014-06-14
Ah thanks this worked fine for me in kubuntu.  Was bugging me for ages.

---

### Post by Yellow Pasque on 2014-06-14
Yes, it should be fixed in Ubuntu 14.10 and later (package is currently in the utopic-proposed repo, but should make it out well before final release).

Ubuntu 14.04 users will either have to use a newer version (from [https://launchpad.net/~stebbins/+archive/handbrake-snapshots](https://launchpad.net/~stebbins/+archive/handbrake-snapshots) ) or the older raring version from the handbrake-releases ppa as detailed above.

---

