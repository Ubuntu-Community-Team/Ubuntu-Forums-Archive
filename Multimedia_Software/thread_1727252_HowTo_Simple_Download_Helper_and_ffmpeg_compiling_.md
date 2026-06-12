---
title: "HowTo: Simple Download Helper and ffmpeg compiling for flv files like youtube"
date: 2011-04-12
forum: Multimedia Software
---

### Post by fixitdude on 2011-04-12
You can use the "Download Helper" plugin with Firefox, and have it automatically call ffmpeg to convert the ".flv" videos to avi format so you can play them with xine or other players.

The problems I was having is frame stopping when playing with the flash player, why it slows things down so much I don't know, but if I download the videos I can play them at full HD quality.

Once you install the "Download Helper" plugin, you will see three little balls rotating around next to the URL entry area when you start a video (when you hit play).

A little tip: When you start a download it may sit there not going, you have to close the video window and it will start downloading, this may be due to the server only allowing one download at a time. Use "Quick download" after you've already picked a folder to download to the first time, then it remembers it, nice)

Right click on Download Helper and choose Preferences then select Conversion and click on "Conversion Enabled", now you want to set all that stuff to be the Converter FFMpeg and configure the conversion rules to convert with files with extensions "flv", and make the options for outputting AVI video and set the checkmark for "Same Quality", if you don't then it makes the HD stuff low res. (that's under the "Details" button)

If you figured all that out then it should convert a youtube or other such video automatically after it's done downloading it.

The problem I had was even with the newest version of ffmpeg from the ubuntu archives, it still wouldn't convert even from the command line.

So I went to [http://ffmpeg.org/](http://ffmpeg.org/) and got the latest version. At the time it was "FFmpeg version SVN-r19954" and it's been working good since so I don't mess with it.

After downloading and unpacking it and putting it in it's own folder, cd into that folder in a terminal and I did this:

./configure --enable-static
make                   (NOTE: lots of warnings but no errors)
sudo cp /usr/bin/ffmpeg /usr/bin/ffmpeg-old1
sudo cp ffmpeg /usr/bin/ffmpeg

Notice that I saved the old copy so I could go back if needed.

The command line I use for testing ffmpeg so I can watch the debug info output (highly recommended so you can figure out if it's even working) 

ffmpeg -sameq -i input-file.flv output-file.avi

Now xine will play those youtube videos. Man that was a lot of typing...

Have fun!

---

### Post by lovinglinux on 2011-04-12
Nice tutorial. However, I don't know why you need to add a resource intensive conversion step, when you can watch flv videos with vlc, gnome-moplayer, smplayer and probably others? You probably don't have the necessary codecs and are solving the problem using conversion, which is really not needed.

BTW, check my [FlashVideoReplacer]("http://www.webgapps.org/addons/flashvideoreplacer") extension. It allows you to watch YouTube videos and some other web sites using a different plugin like gecko-mediaplayer or even launching the video with an external player.

---

### Post by fixitdude on 2011-04-17
Necessary codecs? I have whatever latest codecs are supplied in the Ubuntu archives, w32codecs and all the medibuntu stuff. Some .flv files just will not play.

For example, Youtube .flv files played for a while then they changed something.

I really don't care about the few seconds of resources as long as when it's done I can watch the video in full HD without frame skipping. It's not like I can't browse or do other things while it's converting.

And not everyone has a fantastic net connection, so this way you can watch full HD stuff on a big screen without a fast connection.

A lot of sites change the resolution when they detect a crappy connection so you get the blocky lowres version, I haven't had that happen with the download method and I think it's because it's hard for them to change the stream without the flash player running.

You have a interesting solution there I was not aware of and you could use either method depending on the situation, as long as the plugins don't conflict somehow.

Download Helper works for me on all my favorite sites, but if one didn't then maybe the FlashVideoReplacer would.

Something that's really needed is a plugin that will record an entire show off a site like hulu, commercials and all, into a file for later play. I have to stick with their player no matter how bad the connection is or how choppy the video gets.

---

