---
title: "cant find video file after converting in pytube"
date: 2009-03-30
forum: Multimedia Software
---

### Post by adjock12 on 2009-03-30
Can anyone help me? I am using pytube to convert flv video files to mp4 for my Ipod. My only problem is that I can't find the video after it is converted. Pytube tells me where it put it, but when I go there I can't find it. Can anyone help me?
Thanks:popcorn:

---

### Post by divague on 2009-03-30
try searching through the terminal, open a terminal and type:

```
$sudo find / -name *name_of_the_file*
```

---

### Post by adjock12 on 2009-03-30
I tried that and this is wat I got:

alex@Alex-laptop:~$ sudo find / -name T.N.T
find: /home/alex/.gvfs: Permission denied

So any other suggestions? Or am I doing something wrong?:confused:

---

### Post by SilvaRizla on 2009-03-30
It gets created in the same dir as the script as far as I know, if not it goes to your home folder (/home/YOURNAME).  My script is kept in my home folder for simplicity

---

### Post by adjock12 on 2009-03-30
Nope still nothing. When I download the video and ask it to convert it to mp4 it does it. It also tells me where to find it. But when I go there the file is empty even when I tell it to show hidden files.

---

### Post by aeiah on 2009-03-30
post the whole output of the terminal when you run pytube

---

### Post by adjock12 on 2009-03-30
Here it is. At the end it says Error. What is that about? Pytube still tells me that it worked and the file is downloaded.

```
alex@Alex-laptop:~$ pytube
You are running Python 2.5.2 (r252:60911, Jul 31 2008, 17:28:52) 
[GCC 4.2.3 (Ubuntu 4.2.3-2ubuntu7)]

(pytube.py:9429): libglade-WARNING **: Error loading image: Failed to open file './pytube.png': No such file or directory

(pytube.py:9429): libglade-WARNING **: could not convert string to type `GdkPixbuf' for property `icon'

(pytube.py:9429): libglade-WARNING **: Radio button group menuitem4 could not be found
./pytube.py:647: GtkWarning: gtk_radio_button_set_group: assertion `!g_slist_find (group, radio_button)' failed
  self.wTree = gtk.glade.XML(self.gladefile, "mainwindow")
./pytube.py:647: GtkWarning: gtk_tree_model_get_n_columns: assertion `GTK_IS_TREE_MODEL (tree_model)' failed
  self.wTree = gtk.glade.XML(self.gladefile, "mainwindow")
./pytube.py:647: GtkWarning: gtk_combo_box_set_row_span_column: assertion `row_span >= -1 && row_span < col' failed
  self.wTree = gtk.glade.XML(self.gladefile, "mainwindow")
./pytube.py:647: GtkWarning: gtk_combo_box_set_column_span_column: assertion `column_span >= -1 && column_span < col' failed
  self.wTree = gtk.glade.XML(self.gladefile, "mainwindow")
./pytube.py:647: GtkWarning: gtk_tree_row_reference_new: assertion `GTK_IS_TREE_MODEL (model)' failed
  self.wTree = gtk.glade.XML(self.gladefile, "mainwindow")
./pytube.py:647: GtkWarning: gtk_cell_view_set_displayed_row: assertion `GTK_IS_TREE_MODEL (cell_view->priv->model)' failed
  self.wTree = gtk.glade.XML(self.gladefile, "mainwindow")
Configuration file found
Configuration: {0: '0', 1: '1', 2: '/home/alex/Videos for ipod', 3: '1', 4: 'adjock12', 5: 'Stephanie', 6: '/usr/bin'}
Latest version: <!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd"><html><head>    <meta content="NOARCHIVE" name="ROBOTS"></head><body style="margin-left: 6px;margin-top: 6px;margin-right: 6px;marginbottom: 6px;"><div align="center"><iframe height="1040" width="790" scrolling="auto" frameborder="0" src="http://www.kolmic.com/?dn=bashterritory.com&pid=2PO28GNS8"></iframe></div></body></html>
Current version: 0.0.11.4
Downloading Thumbnails from: http://www.youtube.com/watch?v=ggLbeVlvpKw - ggLbeVlvpKw
Added: AC/DC - T.N.T - http://www.youtube.com/watch?v=ggLbeVlvpKw
HTTP Error 404: Not Found
URL: http://www.youtube.com/watch?v=ggLbeVlvpKw   -   ERROR:HTTP Error 404: Not Found

```

---

### Post by divague on 2009-03-31
> Added: AC/DC - T.N.T - [http://www.youtube.com/watch?v=ggLbeVlvpKw](http://www.youtube.com/watch?v=ggLbeVlvpKw)
HTTP Error 404: Not Found
URL: [http://www.youtube.com/watch?v=ggLbeVlvpKw](http://www.youtube.com/watch?v=ggLbeVlvpKw)   -   ERROR:HTTP Error 404: Not Found

It seems that the video is not available.

---

### Post by adjock12 on 2009-03-31
The only problem is that it is saying that for any video I try to bring down. The video and link were both working through firefox. So I'm not sure why it is saying that it can't find it. Also does the gtk warnings in the code I posted have anything to do with it? They all say something failed.

---

### Post by andrew.46 on 2009-03-31
Hi adjock12,

> **adjock12 said:**
> The only problem is that it is saying that for any video I try to bring down. The video and link were both working through firefox. So I'm not sure why it is saying that it can't find it. Also does the gtk warnings in the code I posted have anything to do with it? They all say something failed.

Indeed it *is* there, an early clip of ac/dc. Angus looks very young :-). Perhaps you could try a different tool, although I see you are after videos for an iPod and perhaps pytube has some conversion settings for this? 

Interestingly enough this script seems to have started on these forums:

[http://ubuntuforums.org/showthread.php?t=559164](http://ubuntuforums.org/showthread.php?t=559164)

And I also note that the project has restarted and perhaps you might try the new version the author offers from his new website:

[http://www.marcosrodriguez.me/pytube/](http://www.marcosrodriguez.me/pytube/)

Hope this helps?

Andrew

---

### Post by adjock12 on 2009-03-31
So I downloaded the new version and tried it out. I downloaded the video and converted it. Still running into the same problem. The video isn't showing up anywhere. I also tried converting into other formats and it worked. Those videos showed up exactly where it said they were. Any suggestions?

The first thing of code is when i download and convert into flv and the second is downloading and converting into mp4:

alex@Alex-laptop:~$ pytube
```

(pytube.py:25815): libglade-WARNING **: Radio button group menuitem4 could not be found
./pytube.py:646: GtkWarning: gtk_radio_button_set_group: assertion `!g_slist_find (group, radio_button)' failed
  self.wTree = gtk.glade.XML(self.gladefile, "mainwindow")
./pytube.py:646: GtkWarning: gtk_tree_model_get_n_columns: assertion `GTK_IS_TREE_MODEL (tree_model)' failed
  self.wTree = gtk.glade.XML(self.gladefile, "mainwindow")
./pytube.py:646: GtkWarning: gtk_combo_box_set_row_span_column: assertion `row_span >= -1 && row_span < col' failed
  self.wTree = gtk.glade.XML(self.gladefile, "mainwindow")
./pytube.py:646: GtkWarning: gtk_combo_box_set_column_span_column: assertion `column_span >= -1 && column_span < col' failed
  self.wTree = gtk.glade.XML(self.gladefile, "mainwindow")
./pytube.py:646: GtkWarning: gtk_tree_row_reference_new: assertion `GTK_IS_TREE_MODEL (model)' failed
  self.wTree = gtk.glade.XML(self.gladefile, "mainwindow")
./pytube.py:646: GtkWarning: gtk_cell_view_set_displayed_row: assertion `GTK_IS_TREE_MODEL (cell_view->priv->model)' failed
  self.wTree = gtk.glade.XML(self.gladefile, "mainwindow")
Configuration file found
Configuration: {0: '0', 1: '1', 2: '/home/alex', 3: '1', 4: 'adjock12', 5: 'Stephanie', 6: '/usr/bin'}
Latest version: 0.0.11.5
Current version: 0.0.11.5
Downloading Thumbnails from: http://www.youtube.com/watch?v=ggLbeVlvpKw - ggLbeVlvpKw
Added: AC/DC - T.N.T - http://www.youtube.com/watch?v=ggLbeVlvpKw
media len:7950119
downloaded: 10240
rate: 54079.7779879 bytes/s
progres :0.0012880310345


```

```

alex@Alex-laptop:~$ pytube

(pytube.py:26576): libglade-WARNING **: Radio button group menuitem4 could not be found
./pytube.py:646: GtkWarning: gtk_radio_button_set_group: assertion `!g_slist_find (group, radio_button)' failed
  self.wTree = gtk.glade.XML(self.gladefile, "mainwindow")
./pytube.py:646: GtkWarning: gtk_tree_model_get_n_columns: assertion `GTK_IS_TREE_MODEL (tree_model)' failed
  self.wTree = gtk.glade.XML(self.gladefile, "mainwindow")
./pytube.py:646: GtkWarning: gtk_combo_box_set_row_span_column: assertion `row_span >= -1 && row_span < col' failed
  self.wTree = gtk.glade.XML(self.gladefile, "mainwindow")
./pytube.py:646: GtkWarning: gtk_combo_box_set_column_span_column: assertion `column_span >= -1 && column_span < col' failed
  self.wTree = gtk.glade.XML(self.gladefile, "mainwindow")
./pytube.py:646: GtkWarning: gtk_tree_row_reference_new: assertion `GTK_IS_TREE_MODEL (model)' failed
  self.wTree = gtk.glade.XML(self.gladefile, "mainwindow")
./pytube.py:646: GtkWarning: gtk_cell_view_set_displayed_row: assertion `GTK_IS_TREE_MODEL (cell_view->priv->model)' failed
  self.wTree = gtk.glade.XML(self.gladefile, "mainwindow")
Configuration file found
Configuration: {0: '0', 1: '1', 2: '/home/alex', 3: '1', 4: 'adjock12', 5: 'Stephanie', 6: '/usr/bin'}
Latest version: 0.0.11.5
Current version: 0.0.11.5
Downloading Thumbnails from: http://www.youtube.com/watch?v=ggLbeVlvpKw - ggLbeVlvpKw
Added: AC/DC - T.N.T - http://www.youtube.com/watch?v=ggLbeVlvpKw
media len:7950119
downloaded: 10240
rate: 50893.3636207 bytes/s
progres :0.0012880310345

FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-pthreads --enable-libvorbis --enable-libtheora --enable-libogg --enable-libgsm --enable-dc1394 --disable-debug --enable-shared --prefix=/usr
  libavutil version: 1d.49.3.0
  libavcodec version: 1d.51.38.0
  libavformat version: 1d.51.10.0
  built on Mar 16 2009 21:16:26, gcc: 4.2.4 (Ubuntu 4.2.4-1ubuntu3)

Seems stream 0 codec frame rate differs from container frame rate: 1000.00 (1000/1) -> 25.00 (25/1)
Input #0, flv, from '/home/alex/YouTube_-_AC_DC_-_T.N.T.flv':
  Duration: 00:03:25.0, start: 0.000000, bitrate: 64 kb/s
  Stream #0.0: Video: flv, yuv420p, 320x240, 25.00 fps(r)
  Stream #0.1: Audio: mp3, 22050 Hz, mono, 64 kb/s
Unknown codec 'aac'


```

The part where it goes Download, rate, progress goes forever so I deleted that part of the code. I don't think that it was important. If needed let me know. I think I found the problem though. Unknown codec 'aac' How do I fix this? Thanks

---

### Post by andrew.46 on 2009-03-31
Hi,

Well the file has been located anyway:

```
/home/alex/YouTube_-_AC_DC_-_T.N.T.flv
```

Looks like pytube wants to convert your flash video to aac sound using FFmpeg but is failing on aac. 4 things:

[LIST=1]
[*]For the gtk warnings you might be best to approach the maker of the script although I could not see an email link on his page. Does the graphical interface look a little odd? This would tie in with some of the errors.
[*]Is there an option in the program to simply 'copy' the audio? It is low quality mp3 but FFmpeg will happily *copy* this into an mp4 container even if FFmpeg is not compiled against lame.
[*]Can you run the following command, which will show if your copy of FFmpeg can deal with aac:

```

andrew@skamandros~$ **[COLOR="Red"]ffmpeg -formats | grep aac[/COLOR]**
FFmpeg version SVN-r18204, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --prefix=/usr --mandir=/usr/man --disable-debug 
--enable-shared --disable-static --enable-postproc --enable-avfilter 
--enable-pthreads --enable-libtheora --enable-libvorbis --enable-x11grab
 --enable-libmp3lame --enable-libx264 --enable-libschroedinger 
--enable-libfaac --enable-libfaad --enable-libamr-wb --enable-libamr-nb
 --enable-libgsm --enable-libspeex --enable-nonfree --enable-gpl
  libavutil     50. 2. 0 / 50. 2. 0
  libavcodec    52.22. 3 / 52.22. 3
  libavformat   52.32. 0 / 52.32. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  libavfilter    0. 5. 0 /  0. 5. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Mar 28 2009 10:31:42, gcc: 4.2.4
[B][COLOR="Red"] D  aac             raw ADTS AAC
 D A    aac             Advanced Audio Coding
  EA    libfaac         libfaac AAC (Advanced Audio Codec)[/COLOR][/B]

```

I would lay a bet that the aac material is missing from your copy.
[*]Can I ask what version of Ubuntu you are using? The Fakeoutdoorsman has an encyclopaedic knowledge of Ubuntu versions and FFmpeg limitations for each and could help out here I am sure :-).
[/LIST]

It looks like an interesting script that should be well worth getting running properly. Tying it in with the shifting sands of youtube videos and FFmpeg syntax will always be a little tricky though.

All the best,

Andrew

---

### Post by adjock12 on 2009-03-31
I'm still a huge noob and am learning so here is the code i got when i entered your command. I didnt get the same as you, so does that mean I dont have the necesary aac material? Also there is no copy option. I'm using hardy heron.

```

alex@Alex-laptop:~$ ffmpeg -formats | grep aac
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-pthreads --enable-libvorbis --enable-libtheora --enable-libogg --enable-libgsm --enable-dc1394 --disable-debug --enable-shared --prefix=/usr
  libavutil version: 1d.49.3.0
  libavcodec version: 1d.51.38.0
  libavformat version: 1d.51.10.0
  built on Mar 16 2009 21:16:26, gcc: 4.2.4 (Ubuntu 4.2.4-1ubuntu3)
 D  aac             ADTS AAC

```

Thanks

---

### Post by FakeOutdoorsman on 2009-03-31
> **andrew.46 said:**
> ...
The Fakeoutdoorsman has an encyclopaedic knowledge of Ubuntu versions and FFmpeg limitations for each and could help out here I am sure :-).
Encyclopaedic?  I don't know about that, Andrew, because I cheat at this, but thanks for the kind words.
> I'm still a huge noob and am learning so here is the code i got when i entered your command. I didnt get the same as you, so does that mean I dont have the necesary aac material? Also there is no copy option. I'm using hardy heron.
Hardy's FFmpeg is limited to non-restricted encoders.  What you can do is uninstall FFmpeg, add the [Medibuntu](http://medibuntu.org/) repository, and then install FFmpeg from the new repository.  The version from Medibuntu will allow you to encode with restricted encoders such as aac.
```
sudo apt-get remove ffmpeg
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list --output-document=/etc/apt/sources.list.d/medibuntu.list
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
sudo apt-get install ffmpeg
```

---

### Post by andrew.46 on 2009-03-31
Hi adjock12,

> **adjock12 said:**
> I'm still a huge noob and am learning so here is the code i got when i entered your command. I didnt get the same as you, so does that mean I dont have the necesary aac material? Also there is no copy option. I'm using hardy heron.

Hey I am still a n00b myself! We are all still learning here :-). Just for curiosity I downloaded the script myself (the so-called 'Source' package) and you will be reassured to know that I encountered the same gtk errors and some of the windows were a little odd, as I suspected. I persisted and managed to download the youtube video but on conversion a similar problem to the one you encountered:

```
Input #0, flv, from '/home/andrew/YouTube_-_AC_DC_-_T.N.T.flv':
  Duration: 00:03:25.03, start: 0.000000, bitrate: 307 kb/s
    Stream #0.0: Video: flv, yuv420p, 320x240, 243 kb/s, 25 tbr, 1k tbn, 1k tbc
    Stream #0.1: Audio: mp3, 22050 Hz, mono, s16, 64 kb/s
WARNING: The bitrate parameter is set too low. It takes bits/s as argument, not kbits/s
Unknown encoder 'aac'
```

So the answer is quite simple:

[LIST=1]
[*]Your copy of FFmpeg needs to be updated and I see the FakeOutdoorsman has already given directions for that :-).
[*]The python script needs to be updated as its syntax refers to an older version of FFmpeg. For example on line 332:
```
secondstep = self.configops[6] + '/ffmpeg -i "' + str(self.videosave)+ i + '".flv -y -f mp4 -vcodec mpeg4 -maxrate 1000k -b 700k -qmin 3 -qmax 5 -bufsize 4096 -g 300 **[COLOR="Red"]-acodec aac -ab 192[/COLOR]** -s 320x240 -aspect 4:3 "' + str(self.videosave)+ i + '.mp4"'
```
to work with my copy of FFmpeg it should be:

```
-acodec libfaac -ab 192k
```

but I note other FFmpeg changes that need to be made in the script.
[/LIST]

I have a deep suspicion that there needs to be a little more work done on this script before it becomes completely usable. If you were keen you could try and contact the developer and work with him to iron out some bugs? I believe that he has only just restarted work on this script and he would probably like some feedback.

Andrew

---

### Post by FakeOutdoorsman on 2009-03-31
I believe "-acodec aac" will work with Medibuntu's FFmpeg, but I'd still recommend changing the script to include the missing "k" that Andrew has pointed out.

---

### Post by andrew.46 on 2009-03-31
Hi,

Mind you rather than foraging through 1000 lines of python try the following, which is how I personally do this:

```

$ sudo apt-get remove youtube-dl
$ sudo wget wget http://bitbucket.org/rg3/youtube-dl/raw/1dd3c78e417e/youtube-dl -O /usr/local/bin/youtube-dl
$ sudo chmod +x /usr/local/bin/youtube-dl

``` 

and to download the AC/DC track:

```

$ cd Desktop
$ youtube-dl -b -o '%(stitle)s.%(ext)s' 'http://www.youtube.com/watch?v=ggLbeVlvpKw'

```

You will note that this already encoded with h264 video and aac sound:

```

Duration: 00:03:25.51, start: 0.000000, bitrate: 452 kb/s
Stream #0.0(und): Audio: aac, 44100 Hz, stereo, s16
Stream #0.1(und): Video: h264, yuv420p, 384x288 [PAR 1:1 DAR 4:3], 25 tbr, 25 tbn, 49.99 tbc

```

And is far higher quality than if you simply download the low quality flv + mp3 version and then convert it.

Andrew

---

### Post by adjock12 on 2009-03-31
ok great guys, but one thing, how do u change the script? what would i need to open? do i do it from terminal? I did what you all suggested with installing medibuntu. Pytube for some reason got uninstalled when i did this and i reinstalled it. Now it is just taking forever to convert the video. I think it stops working at this point. I will be glad to try and get in contact with the developer and ill let u guys know the result. In the meantime though any suggestions are still welcome. Thanks

---

### Post by andrew.46 on 2009-03-31
Hi adjock,

> **adjock12 said:**
> ok great guys, but one thing, how do u change the script? what would i need to open? do i do it from terminal? I did what you all suggested with installing medibuntu. Pytube for some reason got uninstalled when i did this and i reinstalled it. Now it is just taking forever to convert the video. I think it stops working at this point. I will be glad to try and get in contact with the developer and ill let u guys know the result. In the meantime though any suggestions are still welcome. Thanks

Well, if you really want to spend some time tinkering there is a safe way :-). First get yourself a book on python and put it on the shelf for later. Next download the bare tarball:

```

$ cd Desktop
$ wget  http://marcosrodriguez.me/pytube/releases/pytube-0.0.11.5.tar.gz
$ tar xvf pytube-0.0.11.5.tar.gz

```

Navigate into the pytube-0.0.11.5 folder and open the file 'pytube.py' with your favourite text editor and have a good look at it. Python is not a compiled language so any changes you make will be immediate. To run the program, with your alterations, from this folder on your Desktop simply run './python.py' in a terminal from this folder.

You will see the possible culprit for the gtk errors at lines 10 an onwards:

```

try:
	import pygtk
	pygtk.require("2.0")
except:
	pass
try:
	import gtk
	import gtk.glade
	import shutil


``` 

Simply search for 'aac' to see the FFmpeg syntax problems. If you break something simply untar the tarball and try again :-). This is the safest way.

Andrew

---

### Post by adjock12 on 2009-03-31
Thank you guys!!!!! That worked!!!! one more question, do I have to type in that code every time to download in mp4(of course changing the html each time)?

Andrew64 I didn't see that post when i posted earlier so that is why i asked. Thank you for the simple solution.

Thank you everyone for all the help, I really appreciate it!

p.s. How do you mark a thread as solved?

---

### Post by andrew.46 on 2009-04-01
Hi adjock,

> **adjock12 said:**
> Thank you guys!!!!! That worked!!!! one more question, do I have to type in that code every time to download in mp4(of course changing the html each time)?

You are talking about the fancy youtube-dl syntax? That will download the best possible quality video *when it is available*. Good news is that youtube seems to be converting to this format, very few seem to be only in the low quality version only. The full options can be seen:

```

andrew@skamandros~$ youtube-dl -help
Usage: youtube-dl [options] url...

Options:
  -h, --help            print this help text and exit
  -v, --version         print program version and exit
  -u UN, --username=UN  account username
  -p PW, --password=PW  account password
  -o TPL, --output=TPL  output filename template
  -q, --quiet           activates quiet mode
  -s, --simulate        do not download video
  -t, --title           use title in file name
  -l, --literal         use literal title in file name
  -n, --netrc           use .netrc authentication data
  -g, --get-url         simulate, quiet but print URL
  -e, --get-title       simulate, quiet but print title
  -f FMT, --format=FMT  video format code
**[COLOR="Red"]  -b, --best-quality    alias for -f 18[/COLOR]**
  -m, --mobile-version  alias for -f 17
  -i, --ignore-errors   continue on download errors
  -r L, --rate-limit=L  download rate limit (e.g. 50k or 44.6m)
  -a F, --batch-file=F  file containing URLs to download
  -w, --no-overwrites   do not overwrite files

```

I have outlined in red the '-b' option I have used. Don't forget to visit the web site every now and then as the author updates periodically to match changes on the youtube end. BTW you might be interested to hear that youtube-dl is also written in Python :-). So yes, you will need to type this in every time or script it.

> Andrew64 I didn't see that post when i posted earlier so that is why i asked. Thank you for the simple solution.

I am a little puzzled that everybody is not downloading the new high quality videos so it is good to see one convert at least :-). I will admit to having pillaged my own work:

Mini guide: Download high quality youtube vids suitable for your phone ...
[http://ubuntuforums.org/showthread.php?t=1037760](http://ubuntuforums.org/showthread.php?t=1037760)

which has not been all that popular. I think the commandline has scared most people off.

All the best,

Andrew

---

### Post by FakeOutdoorsman on 2009-04-01
I emailed the Pytube author about the inconsistent "k" but I haven't heard back.

---

### Post by adjock12 on 2009-04-01
great let us know when u get a response

---

