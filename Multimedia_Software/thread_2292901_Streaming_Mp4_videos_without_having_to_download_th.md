---
title: "Streaming Mp4 videos without having to download the whole file"
date: 2015-08-31
forum: Multimedia Software
---

### Post by alcatail on 2015-08-31
Hi I have tried this on a standard VPS with 768 MB of Ram and also a Radxa quad core with 2 GB of ram. I have installed ubuntu 14.04 on both with apache2, php and fastcache using an owncloud data base. I can play videos, if it is a small video it will play and stream. If it is a larger video say bigger than 3 minutes it has to download the whole video before it can play. I have used handbrake to index the videos and I know that the files are indexed. 


I have set the mime types in apache server .conf and also messed around with the mime types in the php. I know it is working because it will do it on the smaller videos but not the larger videos- you have to wait till the whole video is download.

I've been googling and searching the forums for a couple of weeks with no success

I also tried a flv streaming module but that didn't change anything either. 

Can some one please point out the basics required for streaming larger mp4 or such videos to the browser without it waiting till the whole file is downloaded.

Kind regards Michael

---

### Post by SeijiSensei on 2015-09-01
If you only need local access rather than streaming over the Internet, **minidlna** might be a better option.  Lots of devices support the DLNA protocol.

---

### Post by Yellow Pasque on 2015-09-01
Don't people usually use something like Wowza for this? (i.e. something supporting DASH)

---

### Post by alcatail on 2015-09-01
Thanks But I do need it to be streamed over the internet. Am setting up a cloud for a small community organisation. Also am using it for my own family that are overseas, It's heaps quicker to upload over the local network and then they down load over the internet.

What's odd is that small videos will start/stream straight away and it appears that it does stream instantly, but when it is a larger file it has to have downloaded the file on the remote end before it can play. I'm wondering if there is a a max limit somewhere in the configs that causes the file to be downloaded and not streamed.

kind regards

---

### Post by FakeOutdoorsman on 2015-09-01
Sounds like progressive download, and the moov atom has possibly not been relocated to the beginning of the file.

Consider testing this:
```
ffmpeg -i input.mp4 -c copy -movflags +faststart output.mp4
```

---

### Post by alcatail on 2015-09-02
thanks will give it a go tonight and post an update

I followed that and the video encoded successfully, but would not stream unitil downloaded the full stream. So i can rule out that it's the video files. I will look more at php, etc

I can confirm that running on lighttpd (What a nightmare it was using trusted certificates!) and using the ffmpeg command works. I am now in the process of snapshotting and rolling back to apache2 to confirm whether or not it is a combination of lighttpd and the ffmpeg or the ffmpeg alone. I did originally try ffmpeg in apache2 without luck but will confirm with my next test if it works or not.
kind regards
Michael

Confirmed.. I was unable to get apache2 to stream large videos without it first downloading the whole stream and that even after trying multiple video encoders to optimise the file for fast play or streaming. To move forward I had to uninstall and purge apache2, install lighttpd server, php + the various components as per this post >>>
[https://www.howtoforge.com/installing-lighttpd-with-php5-php-fpm-and-mysql-on-ubuntu-14.04-lts](https://www.howtoforge.com/installing-lighttpd-with-php5-php-fpm-and-mysql-on-ubuntu-14.04-lts)
encode the video stream as per [ 						 							[IMG]http://ubuntuforums.org/customavatars/avatar162846_41.gif[/IMG] 						 					]("http://ubuntuforums.org/member.php?u=162846") 				 				 					 						 	[**[COLOR=#000000]FakeOutdoorsman[/COLOR]**]("http://ubuntuforums.org/member.php?u=162846") suggestion ; 
 	Code:
 	ffmpeg -i input.mp4 -c copy -movflags +faststart output.mp4 
 	and Bob's your uncle (You fill be streaming larger videos)

---

### Post by alcatail on 2015-09-21
I've gone full turn on this but I have an answer for apache2. 
History >>> I installed the xsendfile module and couldn't get it to work. I ended up dumping apache2 and going over to lighttpd with all the various mods to get it going. It would work for androids and windows but due to the headers not sending correctly it wouldn't work at all with IOS. Owncloud didn't like Lighttpd and spat out a heap of errors. I persevered but came to an end and went back to a snapshot I had with Apache2. I checked my error logs again and the issue was firmly pointed at xsendfile. I modified my settings for Xsendfile and got it working.

To get it working this is assuming you have a setup running with php and the fastcgi modules installed, etc. If you can get a video to play after it downloads the whole video first then this is for you!

```
[COLOR=#333333][FONT=Monaco]apt-get install libapache2-mod-xsendfile
[/FONT][/COLOR]
``` 

inside your server ssl file add the code ```


<Directory /var/www/owncloud>
    ...
    SetEnv MOD_X_SENDFILE_ENABLED 1
    XSendFile On
    XSendFilePath /
</Directory>
``` 
Bear in mind to test it start with this >>>> XsendFilePath / <<<<<<<
When it works lock it down a little better say where the webserver data directory is. I messed around with this and I ended exposing the data directory where my files that would be served are kept. If someone has a better suggestion please update me!

I am able to stream video to all platforms now (IOS, Android and windows) but Windows XP setups don't work but that's the least of my worries.
You have to process each video with MMPEG - I tried a tonne of programs but ffmpeg seems to be the best.
Now I import my videos to my cloud and wrote a bash script to convert and send the converted to another directory on the cloud.
Run the ffmpeg line as suggested here - that does most videos, I ended up finding a different way of doing it for android mp4's.
Kind regards

Michael

---

