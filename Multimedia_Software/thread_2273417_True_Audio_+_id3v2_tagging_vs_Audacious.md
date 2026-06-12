---
title: "True Audio + id3v2 tagging vs Audacious"
date: 2015-04-13
forum: Multimedia Software
---

### Post by andrew.46 on 2015-04-13
I have been experimenting with the True Audio files produced with ttaenc (as a precurser to adding tta support to abcde) and it appears that vlc and MPlayer are happy with id3v2 tagged TTA files but Audacious is not. I have the following sample file for testing:

```

wget http://www.andrews-corner.org/samples/luckynight.tta

```

Which was initially produced with ttaenc and then tagged as follows:

```

id3v2 --album "Treasure Quest Soundtrack" \
      --artist "Jody Marie Gnant" \
      --track "9" \
      --song "Lucky Night" \
      --comment "1-minute song sample demonstrating True Audio (TTA) compression" \
      --genre "Soundtrack" \
      --year "1995" \
      luckynight.tta

```

Can anybody confirm that Audacious chokes on the tagged file? And I would love to know a method to tag TTA files and keep audacious happy as well...

Edit: Error message is:

```

andrew@ilium~/media/luckynight/test$ audacious luckynight.tta 
ERROR mpg123.cc:238 [read_tuple]: mpg123 probe error for file:///home/andrew/media/luckynight/test/luckynight.tta: Message: I am done with this track.
ERROR mpg123.cc:238 [read_tuple]: mpg123 probe error for file:///home/andrew/media/luckynight/test/luckynight.tta: Message: I am done with this track.
ERROR util.cc:180 [audgui_simple_message]: Error opening file:///home/andrew/media/luckynight/test/luckynight.tta:
Error reading metadata
andrew@ilium~/media/luckynight/test$ 


```

---

### Post by Olivia_Zane on 2015-04-13
If the file contains a ID3v2 tag, Audacious will never write an APE tag.  It will by default write an ID3v2.4

ID3 is not a stable standard; there are four different versions of  it.  Audacious uses the most recent version of the standard (ID3v2.4).   If you want tags that can be read by older software, you will probably  need to use a more advanced tag editor that allows you to choose what  type of ID3 tag to write.  I seem to remember EasyTag having an option  for this.
   	I agree that this is a bad situation, and unfortunately it will  continue to cause headaches until 1) people stop releasing  backward-incompatible versions of the ID3 standard and 2) enough time  passes that all software in use supports the current version of the  standard.
   	For the time being, I recommend that you don't use Audacious for tag  editing if you need compatibility with older software.  There simply  aren't enough developers working on Audacious to make it as flexible as  something like EasyTag.

---

### Post by Yellow Pasque on 2015-04-13
Yeah, audacious (3.7-development from git on Debian sid) chokes on it with the tag, apparently thinking it's an mp3 and trying to use mpg123 decoder:
```
INFO probe.cc:136 [file_find_decoder]: Matched MPG123 Plugin by content.
```

Without the tag, audacious uses the correct decoder:
```
INFO probe.cc:136 [file_find_decoder]: Matched FFmpeg Plugin by content.
```

As to Olivia_Zane's point, audacious still tries to use mp3 decoder even with an id3v2.4 tag.

---

### Post by andrew.46 on 2015-04-13
Thanks Temüjin. When I disable the mpg123 plugin (using Audacious 3.6.1) the file is played correctly and the tags are identified.

```

INFO probe.cc:104 [aud_file_find_decoder]: Trying FFmpeg Plugin.
INFO plugin-load.cc:55 [plugin_load]: Loading plugin: /usr/lib64/audacious/Input/ffaudio.so.
INFO probe.cc:104 [aud_file_find_decoder]: Trying FFmpeg Plugin.
INFO probe.cc:112 [aud_file_find_decoder]: Matched FFmpeg Plugin by content.
INFO probe.cc:112 [aud_file_find_decoder]: Matched FFmpeg Plugin by content.

```

So it is an audacious bug. Except that I am weary of irascible developers I would file a bug report with audacious...

---

### Post by mc4man on 2015-04-13
> **andrew.46 said:**
> 

So it is an audacious bug. Except that I am weary of irascible developers I would file a bug report with audacious...
You needn't be worried about bug, either they'll fix or ignore (similar in a way to the mpc issue which I've 'fixed' in ffmpeg source as they've pretty much ignored

Or till then or in lieu of try this patch I just wrote, assumes file has a .tta ext., written for debian packaging.. ( .orig, ect.
```

--- audacious-plugins-3.6.orig/src/ffaudio/ffaudio-core.cc
+++ audacious-plugins-3.6/src/ffaudio/ffaudio-core.cc
@@ -615,6 +615,9 @@ const char * const FFaudio::exts[] = {
     /* Speex */
     "spx",
 
+    /* True Audio */
+    "tta",
+
     /* end of table */
     nullptr
 };
```

---

### Post by andrew.46 on 2015-04-13
Nice mc4man :). Looks like as well the plugin *priority* can be manipulated from $HOME/.config/audacious/plugin-registry but this is not as satisfying as patching...

---

### Post by mc4man on 2015-04-13
Good to know about that config file, never really looked at..
For mpc sv8 I've altered ffmpeg, have had it removed for some time in a ppa shared ffmpeg, no complaints from the few using or myself.
(doesn't seem to make sense to define ext for mpc(sv7) but not mpc(sv8) & don't see the value to begin with, though there may have been..
```
--- a/libavformat/mpc.c
+++ b/libavformat/mpc.c
@@ -232,5 +232,4 @@
     .read_packet    = mpc_read_packet,
     .read_close     = mpc_read_close,
     .read_seek      = mpc_read_seek,
-    .extensions     = "mpc",
 };
```

---

### Post by andrew.46 on 2015-04-14
OK, one last time:

audacious will not play back tagged True Audio (TTA) files
[http://redmine.audacious-media-player.org/issues/531](http://redmine.audacious-media-player.org/issues/531)

:)

---

### Post by andrew.46 on 2015-04-19
> **mc4man said:**
> You needn't be worried about bug, either they'll fix or ignore 

All fixed now, and looks like the developer used the method you suggested:

[https://github.com/audacious-media-player/audacious-plugins/commit/50c769a5c5208e8878c55d98b409d709d1adb78e](https://github.com/audacious-media-player/audacious-plugins/commit/50c769a5c5208e8878c55d98b409d709d1adb78e)

I should have submitted your patch and given you some changelog glory :). This leaves the road clear to add True Audio support with ttaenc in abcde. I am still tossing up whether tagging should be with id3v2 or I should introduce [mid3v2]("http://linux.die.net/man/1/mid3v2") from the mutagen package. Probably mid3v2 I suspect...

---

