---
title: "Multiple audio CDs -&gt; one audio DVD"
date: 2012-08-23
forum: Multimedia Software
---

### Post by George Heine on 2012-08-23
Hello -
I have seen DVDs that condensed the contents of several audio CDs.  The DVD will play on a CD player (or at least on some of them).  It contains several folders, each with the audio tracks from one CD.  Is there any way to burn such a DVD with command-line tools in Linux?  I am familiar with cdrdao, cdrecord aka wodim, also mkisofs and growisofs.  Do I have to worry about the total number of audio tracks exceeding 99?

Thanks for your help.  Looked through posts on this forum for the last year or so, but didn't find anything.

---

### Post by George Heine on 2012-09-02
After a week with no replies on this thread, decided a reality check was in order.  I found one of the disks; it was a CD, not a DVD.  It did, however, have multiple folders with sound tracks in MP3, as well as some JPGs of album covers and a bunch of files titled "desktop.ini".  Checked with the person who created this disk; he had simply  dragged and dropped a bunch of directories into Roxio Media Creator.
There are a total of 119 files, excluding directories; however, only 88 of these are MP3 audio tracks.

So my question is now: how can I duplicate the functionality of Roxio Media Creator in Ubuntu, preferably with command line tools?

Apologies for the mixup, and thanks again for any help - GH

---

### Post by tartalo on 2012-09-02
That looks like a normal data CD and you should be able to create it with any cd recording program.

It will work in any CD player that supports MP3. Nowadays most CD players support MP3, although some mess the intended order of songs, to be safe make sure that both the filenames and the metadata include the tracknumber.

---

### Post by opensshd on 2012-09-02
Yup, sounds like a simple process of ripping the cd audio tracks from the CDs' and then burning the files to DVD as straight data.

You'll need ripper and burning software. There should be no limits as to how many files you can burn to DVD provided they fit in the space allowed by the DVD.

---

### Post by George Heine on 2012-09-18
Thanks for all the responses. Took me a while to follow up on this.  But the ideas of tartalo and opensshd worked.  Used "lame" to recode the audio tracks to MP3, then created a straight data CD from the command line:

```
mkisofs -J -r -v -V <title> -o <iso file>  <top directory>
cdrecord -eject -v -data <iso file>  -pad
```Resulting CD plays each directory, and the tracks in each directory, in alphabetical order by filename.  

One question (if anyone is still following this thread):  How and where does one add metadata on the CD (as tartalo suggests)? 

thanks for your help!

---

### Post by shantiq on 2012-09-19
i have personally not got the machine to play these "Such players will display the **DVD-Audio** logo" (OR to be frank fully understand out to create one; some of you might ::]]) but these dics made here can have much higher specs than mp3


[**http://dvd-audio.sourceforge.net/**]("http://dvd-audio.sourceforge.net/")

> What is DVD-Audio?      [**wiki info**]("http://en.wikipedia.org/wiki/DVD-Audio")

DVD-Audio is a standard for storing uncompressed high quality stereo or multi-channel audio content on a standard DVD disk. Supported sampling frequencies range from 44.1KHz (the Red-Book CD Audio standard) up to 192KHz, with sampling depths of 16, 20 or 24 bits.

A single DVD can contain both DVD-Audio content (in the AUDIO_TS directory) and DVD-Video content (in the VIDEO_TS directory). Most DVD players only recognise and playback the VIDEO_TS content, but an increasing number of dual-format players can play the contents of the AUDIO_TS as well. Such players will display the DVD-Audio logo.

A single DVD-Audio disk is referred to as an Album. An Album can consist of up to 9 Groups, each containing up to 99 Tracks. In addition, the contents of the AUDIO_TS directory can contain references to objects in the VIDEO_TS directory (but not vice-versa).




[**http://dvd-audio.sourceforge.net/GUI.shtml**]("http://dvd-audio.sourceforge.net/GUI.shtml")


get source from here


[**http://sourceforge.net/projects/dvd-audio/files/**]("http://sourceforge.net/projects/dvd-audio/files/")

install with   ./configure && make



AND FOR GUI



**64 **==>    **[ftp://rpmfind.net/linux/Mandriva/devel/cooker/x86_64/media/contrib/release/dvda-author-gui-09.02-2mdv2011.0.x86_64.rpm](ftp://rpmfind.net/linux/Mandriva/devel/cooker/x86_64/media/contrib/release/dvda-author-gui-09.02-2mdv2011.0.x86_64.rpm)**

download file then use    ```
sudo alien -d dvda-author-gui-09.02-2mdv2011.0.x86_64.rpm
```   to make a deb then install



**32**  ===>  

**[http://sourceforge.net/projects/dvd-audio/files/dvda-author-gui/dvda-author-gui-09.02%20linux/](http://sourceforge.net/projects/dvd-audio/files/dvda-author-gui/dvda-author-gui-09.02%20linux/)**

---

