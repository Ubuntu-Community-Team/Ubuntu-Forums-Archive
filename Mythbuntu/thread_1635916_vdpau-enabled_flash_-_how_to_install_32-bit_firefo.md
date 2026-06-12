---
title: "vdpau-enabled flash - how to install 32-bit firefox?"
date: 2010-12-02
forum: Mythbuntu
---

### Post by ZedThou on 2010-12-02
The flash 10.2 beta supports hardware-accelerated playback on 32 bit linux systems. I am running the 64-bit mythbuntu distribution on my ION frontend, so I wondered what would be the best way to go about installing a 32 bit firefox with dpkg / apt. Or is this even necessary, will nspluginwrapper do instead?

---

### Post by thatguruguy on 2010-12-02
At least according to the comments [here]("http://www.omgubuntu.co.uk/2010/12/adobe-flash-10-2-beta-released/"), the hardware acceleration for 32-bit flash doesn't work on a 64-bit build.  However, you can get a 64-bit version of the flash "square" preview [here]("http://labs.adobe.com/downloads/flashplayer10_square.html").  Although the site says it is preview #2, released on September 27, the file is actually preview #3, released on November 16.

---

### Post by ZedThou on 2010-12-02
I went with nspluginwrapper to run the 32 bit flash player on 64 bit firefox. I'm doing this remotely so I won't be able to test vdpau flash playback until I get home. For anyone else who cares to try it, the steps are as follows

```


# make sure nspluginwrapper is installed

$ sudo apt-get install nspluginwrapper

# download and uncompress the player

$ wget http://download.macromedia.com/pub/labs/flashplayer10/flashplayer10_2_p2_32bit_linux_111710.tar.gz

$ tar zxvf flashplayer10_2_p2_32bit_linux_111710.tar.gz

# install the player with nspluginwrapper, full path in the plugin name seems necessary

$ sudo nspluginwrapper -i `pwd`/libflashplayer.so

# make sure it all worked

$ nspluginwrapper -l


```

Edit: as thatguruguy points out, nspluginwrapper might not be enabling hardware accel, I'll have to wait until later to test.

---

### Post by thatguruguy on 2010-12-02
> **ZedThou said:**
> I went with nspluginwrapper to run the 32 bit flash player on 64 bit firefox. I'm doing this remotely so I won't be able to test vdpau flash playback until I get home. For anyone else who cares to try it, the steps are as follows

```


# make sure nspluginwrapper is installed

$ sudo apt-get install nspluginwrapper

# download and uncompress the player

$ wget http://download.macromedia.com/pub/labs/flashplayer10/flashplayer10_2_p2_32bit_linux_111710.tar.gz

$ tar zxvf flashplayer10_2_p2_32bit_linux_111710.tar.gz

# install the player with nspluginwrapper, full path in the plugin name seems necessary

$ sudo nspluginwrapper -i `pwd`/libflashplayer.so

# make sure it all worked

$ nspluginwrapper -l


```Edit: as thatguruguy points out, nspluginwrapper might not be enabling hardware accel, I'll have to wait until later to test.

The link I pointed to would give you flashplayer10_2_p3_64bit_linux_111710.tar.gz, which is apparently a later version (p3 vs. p2) and is native for 64-bit. I question whether following your method has any benefits.

---

### Post by ZedThou on 2010-12-02
> **thatguruguy said:**
> The link I pointed to would give you flashplayer10_2_p3_64bit_linux_111710.tar.gz, which is apparently a later version (p3 vs. p2) and is native for 64-bit. I question whether following your method has any benefits.

Yes, well all of the 64 bit "Square" players at [http://labs.adobe.com/downloads/flashplayer10_square.html](http://labs.adobe.com/downloads/flashplayer10_square.html) are "p3" and dated Sept 27, while all the 32 bit players at [http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html) are "p2" and dated Nov 22. So I don't know where the naming scheme comes from. Anyway, I still haven't seen a case of anyone getting vdpau flash playback on 64 bit linux systems and haven't had the chance yet to test myself.

---

### Post by thatguruguy on 2010-12-02
> **ZedThou said:**
> Yes, well all of the 64 bit "Square" players at [http://labs.adobe.com/downloads/flashplayer10_square.html](http://labs.adobe.com/downloads/flashplayer10_square.html) are "p3" and dated Sept 27, while all the 32 bit players at [http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html) are "p2" and dated Nov 22. So I don't know where the naming scheme comes from. Anyway, I still haven't seen a case of anyone getting vdpau flash playback on 64 bit linux systems and haven't had the chance yet to test myself.


As mentioned in my earlier post, the date on the download page for square is wrong. They didn't update the text when they put up the new files.

EDIT: Moreover, I just downloaded the p2 file to check.  If you open the file, you'll see that it was last modified on November 15, 2010.  Again, the file I pointed you to was last updated November 16, 2010.  The dates in the text of the webpage don't matter.

---

### Post by gradinaruvasile on 2010-12-02
> **ZedThou said:**
> The flash 10.2 beta supports hardware-accelerated playback on 32 bit linux systems. I am running the 64-bit mythbuntu distribution on my ION frontend, so I wondered what would be the best way to go about installing a 32 bit firefox with dpkg / apt. Or is this even necessary, will nspluginwrapper do instead?

A bit of offtopic - running this plugin filled my screen with random garbage that remained there after i closed the browser, and it appeared in many programs if that area was black.
It cleared after suspend/resume, but all vdpau using videos (with smplayer) had a tearing effect (really bad) until i restarted gdm (+unloaded the nvidia module from the memory before restartig gdm).

But the performance is not consistent - some 1080p videos use as much as 20% CPU, some other, low res ones use 100%.
And there is a weird effect - the terminals black backgrounds are transparent if put over the playing video - the text is visible on them though.
I use 32 bit Debian Squeeze, 260.19.21 driver from nvidias site, nvidia 8200 IGP.

---

### Post by ZedThou on 2010-12-03
> **thatguruguy said:**
> As mentioned in my earlier post, the date on the download page for square is wrong. They didn't update the text when they put up the new files.

EDIT: Moreover, I just downloaded the p2 file to check.  If you open the file, you'll see that it was last modified on November 15, 2010.  Again, the file I pointed you to was last updated November 16, 2010.  The dates in the text of the webpage don't matter.

Getting back on topic, the point of this thread was that the linux 32-bit flash 10.2 beta utilizes vdpau and the 64-bit does not. So then how does one go about running the 32-bit plugin on a 64-bit system?

I've come up with a solution, the new thread is at [http://ubuntuforums.org/showthread.php?t=1636333](http://ubuntuforums.org/showthread.php?t=1636333)

---

