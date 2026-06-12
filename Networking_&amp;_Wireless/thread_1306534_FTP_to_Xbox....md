---
title: "FTP to Xbox..."
date: 2009-10-30
forum: Networking &amp; Wireless
---

### Post by x C0MMAND0 x on 2009-10-30
I have a modded Xbox (Unleash X) with the following STATIC settings:
Ip: 192.168.0.3
Subnet: 255.255.255.0
Gateway: 192.168.0.1

My computer has the folloing STATIC settings
Ip: 192.168.0.2
Subnet: 255.255.255.0
Gateway: 192.168.0.1

They are connect via a CROSSOVER cable.  I am able to ping the Xbox and receive a reply.  However, I can not FTP to it which is what I need to do.  I know it works if I connect it through a router and use DHCP, but that's such a pain and slower.

What am I doing wrong here?  I thought it might be the firewall issue, so I ran 
```
sudo ufw disable
```,
but after rebooting both PC and XBOX, I was still not able to FTP.  Any suggestions?

---

### Post by x C0MMAND0 x on 2009-10-31
Any ideas?

---

### Post by x C0MMAND0 x on 2009-11-01
?

---

### Post by Keith Fox on 2010-01-13
I too need to get into my xbox FTP. I'm doing this because I can't figure out how to move files in the Xbox Media Center, i end up moving things to the wrong folder and totally just forget how to move folders correctly. I find FTP easier to use.  Originally when I modded my xbox I used windows to FTP, first time attempting this in Ubuntu.
I understand we need to get port 20 and 21 open to FTP communicate, the xbox uses port 21. I've tried with FileZilla and gFTP. I thought downloading kMyFirewall would help open the port up after adding an iptables rule to open ftp... still not it.
I found this online but doesn't work:  [http://www.cyberciti.biz/faq/iptables-open-ftp-port-21/](http://www.cyberciti.biz/faq/iptables-open-ftp-port-21/)

Did you ever get yours to FTP correctly? If so please help me out too.

---

### Post by puppywhacker on 2010-01-13
we are talking the classical xbox right? and not the xbox360?

step one is to get the xbox to talk ftp, I don't think the classical dashboard does that, but any other like xbmc does.

step two is to use passive ftp and only a single thread at the same time. The builtin ftpserver is probably not supporting the whole ftp subset. The passive mode will make the client open the ftp data connection rather than the server (or the other way round)...

---

### Post by changingstate on 2010-01-13
Yeah, you were using the router and it shows in the network config :D

I have a modded Xbox (Unleash X) with the following STATIC settings:
Ip: 192.168.0.3
Subnet: 255.255.255.0
Gateway: 192.168.0.2

My computer has the folloing STATIC settings
Ip: 192.168.0.2
Subnet: 255.255.255.0

Try that.

---

### Post by KarlIvan on 2010-01-13
I don't know why you want to ftp to your xbox, but i know you mentioned movies....let me tell you what I did (and i apologize if you meant xbox, and not xbox 360):

I use windows at home, I like computer games and all the other nice windows functions, i dont like unix unless im at work. that being said, i obviously have a windows machine at home.
My objective was to be able to stream media from my desktop to my big screen without having to lug out my desktop and physically hook up my pc in my living room. If you want to transfer movies to your xbox hd, then that I imagine would be a one time deal, and you wouldnt be making this post. besides, that takes up lots of space on your hard drive, depending on how many movies or media files you have, along with any saved game data if you play your xbox.

i went out and bought the wireless n adapter for my xbox, and a wireless n+ router. apart from my xbox being from 2006, and not having the ability to update properly, its pretty much plug and play across wireless, so I imagine wired would be easier than that.

the biggest thing i noticed right off the bat, was that the windows media center only played windows media files (wmv), otherwise it wouldnt work. needless to say, i literally only had 2 movies that played out of my entire library. the encoder i use when i put my dvds on my harddrive for storage, encodes in divx, and xvid, so no good.

the first thing i tried was transcode360...long story short, they had one release, and then halted the project. didnt work at all.

second thing i tried was tversity, there are some nice setup tutorials on the web about it and that works great. there are only very few codecs not supported (and mp4 (video, audio mp4 works from what i hear) apparently cant play on the xbox regardless of what you do, so i assume you should forget about that). You will need to uninstall all your codecs, reboot your machine, and install ffdshow (its the only one i have installed, and i believe only one of my non-mp4 movies doesnt play, so its much better than any of the other codecs i tried)...and im not sure why you have to do this, but i ran into problems with the transcoding until i did it. besides that though, just pretty much follow the instructions on some of the tutorials online...the one i used is this one:
[http://www.tweaktown.com/articles/1002/playing_divx_and_xvid_content_on_xbox_360_an_easy_guide/index.html](http://www.tweaktown.com/articles/1002/playing_divx_and_xvid_content_on_xbox_360_an_easy_guide/index.html) but there are some other good ones out there too, here is one that i briefly looked over that looked decent:
[[http://www.afterdawn.com/guides/archive/stream_video_xbox_360_tversity.cfm](http://www.afterdawn.com/guides/archive/stream_video_xbox_360_tversity.cfm)]("http://www.afterdawn.com/guides/archive/stream_video_xbox_360_tversity_page_2.cfm")

---

