---
title: "HOW TO: Play RealMedia on Ubuntu  8.10"
date: 2008-11-20
forum: Multimedia Software
---

### Post by NawaMan on 2008-11-20
I was looking for the how to for some time and I found it [here]("http://www.simplehelp.net/2007/07/27/how-to-play-rmvb-files-in-ubuntu/"). The problem is that the how-to is quite outdated (it is for 7.04) and it no longer work. So I make one and post [here]("http://nawa.pn-np.net/blog/2008-11-20-play-realmedia-on-ubuntu-810/"). The server is slow so please be patient.

For those who have no patient, here is a brief:
You need to install MPlayer and use its preference dialog to select appropriate codec setting.

1: Download and install MPlayer and Codec
```

# Install MPlayer
sudo apt-get install mplayer libstdc++5

# Extract the codec
# NOTE that you can find other version of the codec here
# The one using here is the lastest (yes the latest) and for Ubuntu.
wget http://www.mplayerhq.hu/MPlayer/releases/codecs/essential-20071007.tar.bz2
tar -jxvf essential-20071007.tar.bz2
cd essential-20071007

# Move codec to the right place
sudo mkdir -p /usr/lib/win32
sudo cp * /usr/lib/win32
sudo ln -s /usr/lib/win32 /usr/lib/codecs

# Remove residue
cd.. rm -Rf essential-20071007

```

2. Select “RealVideo decoder” and “FFmpeg/libavcodec audio decoders” for VDO and Audio codec family.
[IMG]http://nawa.pn-np.net/blog/wp-content/uploads/06-select-codec.png[/IMG]

DONE :D
Have Fun.

---

### Post by xandones on 2008-11-24
Does Real Player still doesn't works on Ubuntu? I tried installing using RPM but I couldn't. I also tried downloading the BIN file, but I don't know how to use it (YES, I'M NOOB).

---

### Post by oldsoundguy on 2008-11-24
Same issues with streaming here on non flash stuff ... Quick Time and Real Player in FF on 8.10 

found this last week and it works great .. smooth and seamless (provide you aren't on dial up!)

[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

---

### Post by kostkon on 2008-11-24
> **NawaMan said:**
> I was looking for the how to for some time and I found it [here]("http://www.simplehelp.net/2007/07/27/how-to-play-rmvb-files-in-ubuntu/"). The problem is that the how-to is quite outdated (it is for 7.04) and it no longer work. So I make one and post [here]("http://nawa.pn-np.net/blog/2008-11-20-play-realmedia-on-ubuntu-810/"). The server is slow so please be patient.

For those who have no patient, here is a brief:
You need to install MPlayer and use its preference dialog to select appropriate codec setting.

1: Download and install MPlayer and Codec
```

# Install MPlayer
sudo apt-get install mplayer libstdc++5

# Extract the codec
# NOTE that you can find other version of the codec here
# The one using here is the lastest (yes the latest) and for Ubuntu.
wget http://www.mplayerhq.hu/MPlayer/releases/codecs/essential-20071007.tar.bz2
tar -jxvf essential-20071007.tar.bz2
cd essential-20071007

# Move codec to the right place
sudo mkdir -p /usr/lib/win32
sudo cp * /usr/lib/win32
sudo ln -s /usr/lib/win32 /usr/lib/codecs

# Remove residue
cd.. rm -Rf essential-20071007

```

2. Select “RealVideo decoder” and “FFmpeg/libavcodec audio decoders” for VDO and Audio codec family.
[IMG]http://nawa.pn-np.net/blog/wp-content/uploads/06-select-codec.png[/IMG]

DONE :D
Have Fun.
But you are just unecessarily compiling the windows codecs package that is readily offered by the [*Medibuntu* repo]("http://medibuntu.org/") (the package is called [*w32codecs*]("http://packages.medibuntu.org/hardy/w32codecs.html") or [*w64codecs*]("http://packages.medibuntu.org/hardy/w64codecs.html") for 64bit systems). Most of the media players can use these codecs, like the default media player in *Ubuntu*, *totem-gstreamer*.

In my case, I use *totem-xine* and with these codecs I can play real media files just fine.

---

### Post by xandones on 2008-11-24
You don't need to install MPlayer. Just the codec will do. :popcorn:

---

