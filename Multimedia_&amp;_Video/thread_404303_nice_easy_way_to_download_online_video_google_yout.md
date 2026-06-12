---
title: "nice easy way to download online video google youtube"
date: 2007-04-08
forum: Multimedia &amp; Video
---

### Post by sdowney717 on 2007-04-08
nice easy way to download online video google youtube
[http://www.videodl.org/](http://www.videodl.org/)

simply put the url in the onscreen box
select download link
and you save it to your harddrive

---

### Post by crispy_420 on 2007-04-08
Or you can just ues the firefox extension built for that.

[https://addons.mozilla.org/en-US/firefox/addon/2390](https://addons.mozilla.org/en-US/firefox/addon/2390)

---

### Post by kazuya on 2007-06-01
I used that add-on, it is installed, but I still cannot record or save youtube videos..
How do you save the youtube video using this firefox add-on...

I used to recall a while back seeing a "save as" button for saving the video to desktop..

Is there a howto for installing and using the addon: [https://addons.mozilla.org/en-US/firefox/addon/2390](https://addons.mozilla.org/en-US/firefox/addon/2390)

to save my youtube videos from firefox  or opera,...

Thanks.

---

### Post by kazuya on 2007-06-04
It works using the plugin as shown below: {Credit goes to you helpful guys}
The howto for installing and using the addon: 
Go or click on Link & download.
[https://addons.mozilla.org/en-US/firefox/addon/2390](https://addons.mozilla.org/en-US/firefox/addon/2390)

then Restart Firefox

To save youtube videos from firefox, go to youtube site, click on video to start it.
As video starts, there should be an icon at the bottom of firefox panel to the far right {below}.

Click on this and the file gets downloaded to your desktop>
The file would be called <getvideo> - you may have to change the file name to something more unique.

Looking at how to convert from flv to avi next.

---

### Post by pn4577 on 2007-06-29
I experienced that these plug ins and links use other web servers to extract the video URL. But the fewer people know what I download, the better. I prefer a more private way ;)
I use an easy shell script to download the flash videos. The first (and only) commandline parameter is the YouTube video URL.
```

#!/bin/sh

#extract video id from URL
vid=`echo "$1" | sed 's/.*\?.*=\(.*\)/\1/'`

echo "downloading video (id=$vid)"
wget `wget -q "http://www.youtube.com/watch?v=$vid" -O - | sed -n 's/^.*player.*.swf\([^"]*\).*$/http:\/\/www.youtube.com\/get_video\1/p'` -O $vid.flv

```

Save the content into a file named something like *getvid.sh* and don't forget to set the execution flag ;)
```
chmod a+x getvid.sh
```

Calling *./getvid.sh <YouTube URL>*, the flash video is downloaded to a file named "<video id>.flv" in the current directory.

If you don't have the wget command installed, do so by invoking
```
sudo apt-get install wget
```

Cheerio :D

---

### Post by kantor on 2007-07-06
I use this script to download and encode the video in mpg format. Tu use it you need to have ffmpeg and wget installed on your system:

```
 sudo apt-get install ffmpeg wget
```

the script download the file from youtube and encode it with the video's title as file name of the encoded mpg:

```
#!/bin/bash
if [[ $# -lt 1 ]];then video_url=$1; exit 1; fi
video_url=$1
tmp_file="tmp_video.flv"
base_url="http://youtube.com/get_video.php?"
video_id=$(links2 -source ${video_url} | grep player2.swf | cut -d? -f2 | cut -d\" -f1)
video_url=${base_url}${video_id}
if [[ -f ${tmp_file} ]]; then rm -f ${tmp_file} ; fi
wget ${video_url} -O ${tmp_file}
video_name=$( links2 -source http://www.youtube.com/watch?v=adzkV58Gpqs | egrep '<h1 id="video_title">'| cut -d\< -f2 |cut -d\> -f2)
ffmpeg -i ${tmp_file} -ab 56 -ar 22050 -b 500 -s 320x240 "$video_name.mpg"
rm -f ${tmp_file}
```

hope it's useful... it's not all my work but i did my part

---

### Post by blueb73 on 2007-07-11
the download helper extension rocks!


but, does anyone know how to enable fast forwrd and rewind for flv files on the movie player?

---

### Post by ibharathy on 2008-06-17
thanks it was useful..

---

