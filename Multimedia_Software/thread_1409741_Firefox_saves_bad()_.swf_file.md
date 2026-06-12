---
title: "Firefox saves bad(?) .swf file"
date: 2010-02-17
forum: Multimedia Software
---

### Post by quadproc on 2010-02-17
I have been trying to save .swf files from Firefox but the saved files will not play back.  Here are the details:

Using Firefox 3.0.17 with Shockwave Flash 10.0 r45 on a 64 bit system (Intel i7 950 with lots of RAM, ATI HD4870x2 with "ati" driver (not fglrx)) running Ubuntu 9.04 with kernel 2.6.28-18, I can display files just fine (for example, "Shoplifter Win" from today's YouTube).  Then I try to save the just played file by following Tools > Page Info > Media, select the file with the .swf suffix, and Save As.  FF creates a file.  Then I visit some other URL to make FF forget the stored image data.

Next, I use Places to access the directory where I saved the .swf file, right click on the saved file's icon, select Open With, select Firefox.  I get a message: "An error occurred, please try again later."  in the middle of a black window.  Running the _file_ command on the saved file produces "Macromedia Flash data (compressed), version 10".

Thinking that the problem might be in Firefox's file reading function, I tried several other media players and each produced some kind of error when it read the saved file:

Gstreamer says:  An error occurred\n GStreamer encountered a general supporting library error.
Mplayer says: LAVF_header: av_open_input_stream() failed
Opera says: An error occurred, please try again later. (just like FF)
vlc says and does nothing and shows 0s for time data

So I am suspecting that Firefox created a bad saved file.

I have tried numerous uninstalls and installs of various Firefox related software and other video players but none of these attempts has made any difference.

I have read lots of other people's problem reports regarding troubles with the combination of Firefox and .swf files but none of them seems to be this problem.

Does anyone know what is going on, and/or how to create a good saved file?

Thanks for any help or suggestions.

quadproc

---

### Post by amsterdamharu on 2010-02-18
The youtube video is not the flash file, the flash file is just the player. Parameters in the html tag tells the player what to play and what other swf files to load.

You can download a flash animation and see if that works;

[http://www.istockphoto.com/stock-flash-11978394-backgrounds-with-flowers.php](http://www.istockphoto.com/stock-flash-11978394-backgrounds-with-flowers.php)
has
[http://www.istockphoto.com/file_thumbview_approve/11978394/2/istockphoto_11978394-backgrounds-with-flowers.swf](http://www.istockphoto.com/file_thumbview_approve/11978394/2/istockphoto_11978394-backgrounds-with-flowers.swf)

---

### Post by VertexPusher on 2010-02-18
> **quadproc said:**
> Does anyone know what is going on, and/or how to create a good saved file?
Go to a YouTube page, watch a video. Then open the /tmp folder. You will see a file named like "Flashxyzxyz". That's the video. If you double-click it, your default media player will play it back.

When you close the browser window or navigate to another page, the video file will be deleted from /tmp. If you want to keep it, make a copy.

---

### Post by quadproc on 2010-02-18
> **VertexPusher said:**
> Go to a YouTube page, watch a video. Then open the /tmp folder. You will see a file named like "Flashxyzxyz". That's the video. If you double-click it, your default media player will play it back.


Excellent!  Thanks, VertexPusher, that worked when I added a .swf to the saved file name.

Now I am curious - just what did Firefox save when I followed the Tools > Page Info > Media chain?  Anyone?

quadproc

---

### Post by amsterdamharu on 2010-02-18
[http://ubuntuforums.org/showthread.php?t=1409741#2](http://ubuntuforums.org/showthread.php?t=1409741#2)

The media file in temp is not flash but some sort of video file usually with the flv file extension.

---

### Post by lidex on 2010-02-19
quadproc:
Check out this firefox extension for downloading video; it will even convert the format. I have it setup to convert to avi and then playback with xine. You'll want to add the icon to the toolbar to access all the functionality:

[http://www.downloadhelper.net/index.php]("http://www.downloadhelper.net/index.php")

---

### Post by VertexPusher on 2010-02-19
> **quadproc said:**
> that worked when I added a .swf to the saved file name.
The proper extension here would be either .flv (Flash Video) or .mp4 (MPEG-4 media; Flash can play these too). But in Linux the extension doesn't matter anyway. Media players and file managers will recognize the type by looking at the file header.

> Now I am curious - just what did Firefox save when I followed the Tools > Page Info > Media chain?  Anyone?
You saved the YouTube video player applet. That's basically a small program/script embedded into the web page which handles download and playback of the video.

---

### Post by VertexPusher on 2010-02-19
> **lidex said:**
> Check out this firefox extension for downloading video; it will even convert the format. I have it setup to convert to avi and then playback with xine. You'll want to add the icon to the toolbar to access all the functionality:

[http://www.downloadhelper.net/index.php](http://www.downloadhelper.net/index.php)
DownloadHelper is a useless tool for the following reasons:
[list][*]It doesn't work with all video sites, sometimes even stops working with YouTube.[*]It's slow. Once you watched a video, the file is cached in /tmp anyway. Why download it again with a separate tool?[*]Converting FLV to AVI is just dumb because all the media players can play back the original files just fine. By converting them to AVI, you will only degrade their quality even further.[/list]

---

### Post by lovinglinux on 2010-02-19
> **quadproc said:**
> Excellent!  Thanks, VertexPusher, that worked when I added a .swf to the saved file name.

Don't bother with complicated instructions about the /tmp folder. You can download videos from YouTube and other web sites automatically with [Video DownloadHelper](https://addons.mozilla.org/en-US/firefox/addon/3006).

> **quadproc said:**
> Now I am curious - just what did Firefox save when I followed the Tools > Page Info > Media chain?  Anyone?

Flash videos are not swf, they use flv or mp4 extension. You probably saved the flash player itself, instead of the video content. 

> **jason smith1 said:**
> **Why the version 3.x is so bad for saving complete web pages? Because, in the version of 2.0.0.20 I can easily save full a web pages without any error messages and without waiting time for scanning such as in the version 3.x **

Use the [Mozilla Archive Format](https://addons.mozilla.org/en-US/firefox/addon/212) extension to save them as maff archives.

I also recommend [ScrapBook](https://addons.mozilla.org/en-US/firefox/addon/427) + [ScrapBook MAF Creator](https://addons.mozilla.org/en-US/firefox/addon/13251).


> **VertexPusher said:**
> DownloadHelper is a useless tool for the following reasons:
[list][*]It doesn't work with all video sites, sometimes even stops working with YouTube.[*]It's slow. Once you watched a video, the file is cached in /tmp anyway. Why download it again with a separate tool?[*]Converting FLV to AVI is just dumb because all the media players can play back the original files just fine. By converting them to AVI, you will only degrade their quality even further.[/list]

[list][*] Video Download helper never failed on me.
[*]You don't need to buffer the video entirely to save it with VDH. I use it on a daily basis and it works great, specially for video players that combine several flash chapters. Just click each chapter and save with VDH, then close the video page.
[*]There is no need to convert the video, since the conversion tool is optional[/list]

Perhaps you don't realize that what is good for you might not be good for others and vice versa.

---

### Post by quadproc on 2010-02-19
> **VertexPusher said:**
> The proper extension here would be either .flv (Flash Video) or .mp4 (MPEG-4 media; Flash can play these too). But in Linux the extension doesn't matter anyway. Media players and file managers will recognize the type by looking at the file header.


You saved the YouTube video player applet. That's basically a small program/script embedded into the web page which handles download and playback of the video.
Thanks, lovinglinux, that makes sense because I did find that the saved file was only about 50 K bytes.

the real video files seem to take about 5 MB per minute of play time.

quadproc

---

