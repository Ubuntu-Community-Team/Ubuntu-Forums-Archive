---
title: "FUSEPod - first play"
date: 2006-11-26
forum: Multimedia &amp; Video
---

### Post by fatbastard spice on 2006-11-26
Saw some good things about FUSEPod so thought i'd have a go at getting it working as i'm not particularly impressed by any of the standard iPod synchronisation applications.

Firstly FUSEPod uses the FUSE libraries to create a virtual representation of the ridiculous obfuscation that is the iPod music library. It allows you to display the files with understandable file names in a hierarchy that (by default) mimics the browsing hierarchy you use on the iPod. You can also stuff around with the configuration file to determine what hierarchy you want to use.

Now just want to warn anyone that this might be a case of the blind leading the blind. I'm not the most experienced linux user about, so if you're not sure of what you're doing wait until some more knowledgeable poster points out any problems with what i've done. I'm sure there's more elegant ways to achieve this and i'd be grateful of any feedback.

So here's the steps i used to get it working.

First installed a bunch of dependencies for the compilation:
```
sudo apt-get install libfuse2 fuse-utils libfuse-dev libgpod0 libgpod-dev libtag1c2a libtag1-dev build-essential
```

Then i grabbed the tarball from the [sourceforge page]("http://sourceforge.net/projects/fusepod/"). Extracted that and then moved into the extracted directory. Then it was a matter of:
```
sudo ./configure
sudo make
sudo make install
```

Then create a directory to mount your virtual iPod and mount it:
```
sudo mkdir /media/mPod
sudo fusepod /media/mPod -o allow_other
```

Now the first time i tried this it just hung there. So i forgot about it and tried it the next day, which was after a couple of restarts. So not sure if there's something else required to get it working, or if i'd just forgotten something that the restart did.

Finally, as i'm a bit anal i removed the dev libraries and build essential
```
sudo apt-get remove libfuse-dev libgpod-dev libtag1-dev build-essential
sudo apt-get autoremove
```

There's some usage instructions in the readme in the tarball, and there's drag and drop support for adding new files via the Transfer directory. To me it looks really nice, though you may not find it that exciting. It&#8217;s just the whole nerdy virtual hierarchy and multidimensional taxonomy approach of FUSE that&#8217;s making me think it&#8217;s cute.

---

