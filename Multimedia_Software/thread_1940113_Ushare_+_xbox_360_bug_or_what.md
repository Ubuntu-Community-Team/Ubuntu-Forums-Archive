---
title: "Ushare + xbox 360 bug or what?"
date: 2012-03-13
forum: Multimedia Software
---

### Post by hate29 on 2012-03-13
I have installed correctly and got up and working ushare with xbox 360. Xbox 360 sees my pc and all files that I share. All my videos are mp4 format and I thought that this wouldn't be problem but no. Xbox sees all videos but won't play them, it won't even give me error code or something.

After a bit thinking I figured out that xbox doesn't show the ending of my files (*.mp4). *.avi files played back perfectly and if I changed .mp4 to .avi it played perfectly well too. But I don't want to change all my mp4:s endings to .avi as they are mp4. Next thing I tried was to add .avi to the end of the movie file. Example: movie.mp4 --> movie.mp4.avi. That file looked in xbox like this: movie.mp4 and played perfectly. So I'm quite confused with this? I haven't tried to change movie.mp4 to movie.mp4.mp4 but I'm quite sure that it will work too. But I'm quite sure that it will work fine too.Also videos with ä or ö letters in them wouldn't play.

Are these "bugs" in ushare or in xbox? Is there any fix for this or should I just begin to change my filenames?

---

### Post by Rorke on 2012-04-21
Hi - sorry, this isn't help, but further request for assistance.
I have an Xbox slim, but it says I can't connect to another computer unless I have Microsoft Windows Media.

Is there an Ubuntu way round this?

Can I hace the Xbox, open source style? I'm not interested in the MS subscription Xbox Live.

---

### Post by syerges on 2012-05-06
Mine only works on both XBox 360 and playstation 3 with the following settings exactly...if i change any of them, then it stops working.
In Ushare's config file:
USHARE_OVERRIDE_ICONV_ERR=yes
USHARE_ENABLE_WEB=yes
USHARE_ENABLE_TELNET=no
USHARE_ENABLE_XBOX=yes
USHARE_ENABLE_DLNA=no


The enable_dlna really messed me up because it says ps3 won't work without it, but it's wrong. also make sure to look up your xbox and ps3 ip addresses and open up the port to them from your pc.

My computer's IP address was found by right clicking on my internet connection and then clicking on "connection information" and it is 192.168.0.11

My Xbox and PS3's IP addresses were found by going to network settings, they are 192.168.0.10 and 192.168.0.13 so I had to use the following codes in terminal. sorry, don't know how to do that code thing here....

I used the same port as you so you shouldn't have to change that number.

sudo ufw allow proto tcp from 192.168.0.11 to 192.168.0.10 port 49153
sudo ufw allow proto tcp from 192.168.0.11 to 192.168.0.13 port 49153

---

