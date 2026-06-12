---
title: "Unable to burn audio CD with ogg files using GnomeBaker"
date: 2010-04-04
forum: Multimedia Software
---

### Post by paperplate9 on 2010-04-04
For the longest I have been unable to burn an audio CD that contains ogg files with GnomeBaker, and have always had to decode to wav manually. Well I'm tired of doing that, so want to get to the bottom of the problem.

Upon adding an ogg file to the file list, the error I receive is:

"The plugin to handle a file of type audio/ogg is not installed."

I have all the gstreamer0.10-plugins-[base|bad|good|ugly] packages installed.

I can play an .ogg file with rhythmbox.

Using gconf-editor, /system/gstreamer/0.10/audio/profiles/cdlossy  is "active" and the cdlossy profile is listed in /system/gstreamer/0.10/audio/global/profile_list

At a loss on what I need to do.

---

### Post by cottfcfan on 2010-04-04
Without installing Gnomebaker i'm not sure, but Brasero works fine for me burning ogg files.
 I've checked in synaptic to see what I have installed.
"vorbis-tools, libogg0, python-mutagen, libtheora0, & libvorbis0a" are all installed as well as ubuntu-restricted-extras.
 See if you have all these installed, if not one of them might help.
Otherwise use Brasero.

---

### Post by paperplate9 on 2010-04-04
> **cottfcfan said:**
> Without installing Gnomebaker i'm not sure, but Brasero works fine for me burning ogg files.
 I've checked in synaptic to see what I have installed.
"vorbis-tools, libogg0, python-mutagen, libtheora0, & libvorbis0a" are all installed as well as ubuntu-restricted-extras.
 See if you have all these installed, if not one of them might help.
Otherwise use Brasero.

Brasero can add my ogg files to the project. But I always had a problem with Brasero crashing during the burn process.

PS: I also already had all those packages installed.

---

### Post by cottfcfan on 2010-04-04
Ive just installed Gnomebaker and i see what you mean.
there's obviously some codec missing but i can't find it.
Maybe some other forum member can help.

---

### Post by paperplate9 on 2010-04-04
So you can confirm that you also receive the same error when adding an ogg file?

Should have mentioned, I'm using GnomeBaker 0.6.4 and gstreamer 0.10 on Karmic. Straight from apt-get installs. Even did a GnomeBaker build from source with the same error.

---

### Post by paperplate9 on 2010-04-04
Well, since I had the source, I decided to dive in. Found the problem, and it's due to mime-types & how GnomeBaker registers plugins.

Upon initialization in src/media.c, GnomeBaker registers the "vorbisdec" plugin. Running `gst-inspect vorbisdec` verified that I had this plugin installed with gstreamer0.10.

However, when GnomeBaker registers the plugin, the mime-type it registers it for is **application**/ogg.

If I were to `cat /etc/mime.types | grep ogg`, I see:
application/ogg                                 ogx
audio/ogg                                       oga ogg spx
video/ogg                                       ogv

So basically what was happening was Ubuntu? was telling GnomeBaker you've got an **audio**/ogg file. But since there's no plugin registered for audio/ogg, it fails & gives you the error.

So I did a quick hack in src/media.c by creating another vorbisdec registration with the audio/ogg mime type & it was successfully able to load the file, correct length and all.

The peculiar thing is that within /usr/share/mime/audio/ogg.xml, there is a:
<sub-class-of type="application/ogg" />

which I guess links audio/ogg as a subtype of application/ogg, but GnomeBaker just does a basic string comparison of the registered plugin's mime type (app/ogg) and the file's mime type (aud/ogg) and returns good stuff only on a match.

**So, assuming the mime type setup is correct (stuff in /usr/share/mime/*) I would say for those having the same problem to just add an extra line in src/media.c to register vorbisdec with mime type audio/ogg:**

```
    media_register_plugin("audio/ogg", "vorbisdec"); /* I added this line */
    media_register_plugin("application/ogg", "vorbisdec");
```What tipped me off was this trace of messages (looking for audio/ogg but couldn't find a match):
```
gbcommon_get_mime_type - uri [file:///test.ogg] mime [audio/ogg]
[0x9120080] [media_get_plugin_status] [media.c] [359]
media_get_plugin_status - plugin mime_type [application/x-id3] requested [audio/ogg]
media_get_plugin_status - plugin mime_type [audio/mpeg] requested [audio/ogg]
media_get_plugin_status - plugin mime_type [audio/x-mp3] requested [audio/ogg]
media_get_plugin_status - plugin mime_type [application/ogg] requested [audio/ogg]
media_get_plugin_status - plugin mime_type [application/x-flac] requested [audio/ogg]
media_get_plugin_status - plugin mime_type [audio/x-flac] requested [audio/ogg]
media_get_plugin_status - plugin mime_type [application/x-mod] requested [audio/ogg]
media_get_plugin_status - plugin mime_type [application/x-wav] requested [audio/ogg]
media_get_plugin_status - plugin mime_type [audio/x-wav] requested [audio/ogg]
media_get_plugin_status - plugin mime_type [video/x-ms-asf] requested [audio/ogg]
media_get_plugin_status - plugin mime_type [audio/mp4] requested [audio/ogg]
media_get_plugin_status - plugin mime_type [audio/x-m4a] requested [audio/ogg]
media_get_plugin_status - plugin mime_type [audio/x-ms-wma] requested [audio/ogg]
[0x9120080] [gnomebaker_show_msg_dlg] [gnomebaker.c] [223]
gnomebaker_show_msg_dlg - message [The plugin to handle a file of type audio/ogg is not installed.]

```

I don't know if this is a bug or what or if my system is just misconfigured, but I guess you can say this "solved".

---

### Post by paperplate9 on 2010-04-04
Since cat /etc/mime.types|grep ogg says that application/ogg files should have an "ogx" extension, you could also just do that...

1) rename file to ogx
2) symlink with an ogx extension to the ogg file

---

### Post by paperplate9 on 2010-04-04
Another pet peeve I've had with GnomeBaker is that when you try to import a playlist, it resets the size of your audio CD to the first option (which is a 20 minute CD).

I found that there's an option you can change to have it default to a certain disk size (for me, that's an 80 minute CD).

/apps/GnomeBaker/AudioDiskSize

is an index into that drop down;

Since "80 min. CD" is option #3 (0-based), if I set AudioDiskSize to 3, whenever I create a new project or import a playlist, the 80 minute CD will be preselected. 

One of the many advantages of open-source software.

---

### Post by cottfcfan on 2010-04-05
paperplate9...
Well done, don't think i'd have solved that.
I think other members will benefit from your findings.

---

### Post by paperplate9 on 2010-04-05
> **cottfcfan said:**
> paperplate9...
Well done, don't think i'd have solved that.
I think other members will benefit from your findings.

Well, I really didn't wanna have to go through all that (hence the reason why I originally posted this thread since I'd been avoiding it so long). But I guess that's the nature of the "beast" (having a problem and not giving up til you find a solution).

I'm still wondering why I haven't found any other instances of this problem as I figured GnomeBaker was popular.

---

### Post by ricardisimo on 2010-04-17
> **paperplate9 said:**
> Another pet peeve I've had with GnomeBaker is that when you try to import a playlist, it resets the size of your audio CD to the first option (which is a 20 minute CD).

I found that there's an option you can change to have it default to a certain disk size (for me, that's an 80 minute CD).

/apps/GnomeBaker/AudioDiskSize

is an index into that drop down;

Since "80 min. CD" is option #3 (0-based), if I set AudioDiskSize to 3, whenever I create a new project or import a playlist, the 80 minute CD will be preselected. 

One of the many advantages of open-source software.

I cannot find any usable configuration file for GnomeBaker, and certainly no directory named "/apps/GnomeBaker/AudioDiskSize" anywhere. I'm assuming that Koala or Jaunty brought some changes in this regard.

So, the question is: How do I change the default disk size on Karmic (or very soon Lucid)? Perhaps the more important question is "Who the hell would call 21 minutes a 'sane default'?" Thanks.

---

### Post by paperplate9 on 2010-04-17
> **ricardisimo said:**
> I cannot find any usable configuration file for GnomeBaker, and certainly no directory named "/apps/GnomeBaker/AudioDiskSize" anywhere. I'm assuming that Koala or Jaunty brought some changes in this regard.

So, the question is: How do I change the default disk size on Karmic (or very soon Lucid)? Perhaps the more important question is "Who the hell would call 21 minutes a 'sane default'?" Thanks.

Hi, ricardisimo. I guess I forgot to specify - you change the setting through gconf-editor.

Regards

---

### Post by yorubatribe on 2010-05-13
I was happy to hear there was fix for ogg problem but I can't seem to find the file media.c to edit on Ubuntu (Lucid Lynx 64bit) . What is the absolute path to that file?

---

### Post by paperplate9 on 2010-05-13
> **yorubatribe said:**
> I was happy to hear there was fix for ogg problem but I can't seem to find the file media.c to edit on Ubuntu (Lucid Lynx 64bit) . What is the absolute path to that file?

You need to download the source code to GnomeBaker.

The simple fix was just adding vorbisdec for an audio/ogg mime type, but I attached a basic patch file which you can apply by doing `patch -i gnomebaker_media.c.patch.txt media.c` while in the src directory.

GnomeBaker follows your standard build process (./configure && make && make install).

Hope it helps.

---

### Post by yorubatribe on 2010-05-14
Thank you, [paperplate9]("http://ubuntu-ky.ubuntuforums.org/member.php?u=858926"). I downloaded the source files for Gnomebaker and edited the media.c file in /usr/src/gnomebaker-0.6.4/src with the missing line of plugin information you described earlier:

```
 media_register_plugin("audio/ogg", "vorbisdec"); 
```Then I simply recompiled gnomebaker. Everything works just fine now. (this is on Lucid Lynx 64 bit). It looks like Ubuntu needs to fix the binary that Synaptic provides. Thanks again.

---

### Post by brcre on 2010-05-23
Thread summed up.  Hope it works for others as well as it worked for me.

---

### Post by BinaryMn on 2011-08-03
For those that aren't programmers, here's a step-by-step guide on how to do this. Credit to the patch goes to paperplate9. I just put it up on Dropbox to make things easier. Obviously, you need to do all this in a shell prompt.

```
$ cd
~$ wget http://gnomebaker.sourcearchive.com/downloads/0.6.4-1ubuntu1/gnomebaker_0.6.4.orig.tar.gz
~$ tar xvf gnomebaker_0.6.4.orig.tar.gz
~$ cd gnomebaker_0.6.4/src
~/gnomebaker-0.6.4/src$ wget http://dl.dropbox.com/u/19897709/gnomebaker_src_media.c.patch.txt
~/gnomebaker-0.6.4/src$ patch < gnomebaker_src_media.c.patch.txt
~/gnomebaker-0.6.4/src$ cd ../
~/gnomebaker-0.6.4$ ./configure

If you get any errors about missing packages, apt-cache search <search term> 
and apt-get install libpackagename* is extremely helpful. 
Also, if you get a error about not having gstreamer installed, apt-get install
libgstreamer0.10-dev and try again.

~/gnomebaker-0.6.4$ make
~/gnomebaker-0.6.4$ sudo make install
```

After that, you're all done. If everything installed without any problems, type in the following to remove the source (which you don't need anymore).

```
~/gnomebaker-0.6.4$ cd
~$ rm -rf gnomebaker-0.6.4
```

Make sure you type that last command in correctly, otherwise you could irrevocably delete data in your home folder.

---

