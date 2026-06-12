---
title: "Jumptv on Ubuntu Linux Howto"
date: 2006-11-26
forum: Multimedia &amp; Video
---

### Post by mat_london on 2006-11-26
Simple Jumptv Howto

A quick explanation of how I got Jumptv working on my Ubuntu Edgy PC which is also an answer to my own thread posted earlier this week re  multi stream mms  video streams.

Requires:

Ubuntu Edgy, Latest mplayer for edgy (does not need svn), Firefox with downthemall plugin installed ( [http://www.downthemall.net/](http://www.downthemall.net/) ) optional one time access to a windows PC.

1.   Sign up to your chosen Jumptv stream here [http://www.jumptv.com/](http://www.jumptv.com/)
2.   Optionally use a windows PC to sign in at [https://www.jumptv.com/en/node/88](https://www.jumptv.com/en/node/88) and sign in, click on the "Tune my video" link at the bottom right hand corner of the window describing your TV Channel. Use the set automatically button to set your region & bandwidth automatically.
3.  Using your Ubuntu PC visit [https://www.jumptv.com/en/node/88](https://www.jumptv.com/en/node/88) and sign in. This should take you to the TV channel you have signed up to.
4.   Right click on this page and select DownThemAll from the drop down menu.
5.   When the DownThemAll window opens, scroll to the bottom and select to download the link [http://www.jumptv.com/controller.php?action=createASX&channelID=***](http://www.jumptv.com/controller.php?action=createASX&channelID=***) (where *** is your channel ID - this will be filled in so there is no need to add anything here)
6.   Using gedit or a similar text editor open the file you have downloaded which is called controller.php
7.   Read through the controller.php file, highlight the first link you come to begining with [http:// ](http:// ) & copy this.
8.   Open up your terminal and type mplayer -v "  then paste in the link you have just copied followed by a closing " 
This should then look like this "http://secure9.jumptv.com/zzzzzz?WMThinning=1&Customer_ID=XXXX&Product_ID=YYY&Asset_ID=XXXX&Stream_ID=XXXXXX&User_Token=XXXXXXXXXXXXXXXXX"
9.  Hit return and mplayer should start with your channel playing in a tiny window. If you are on a low bandwidth connection this may be all your connection will allow, mplayer automatically selects the lowest bandwidth stream.
However multiple bandwidth streams are all available from the same Jumptv link under the mms:// protocol. To access these hit Ctrl C in your terminal and scroll back up your terminal window, if multiple bandwidth streams are available, you will see something like this:

============ ASF Stream group == START ===
 stream count=[0x8][8]
   stream id=[0x1][1]
   max bitrate=[0x11574][71028]
   stream id=[0x2][2]
   max bitrate=[0xd6ac][54956]
   stream id=[0x3][3]
   max bitrate=[0x6802][26626]
   stream id=[0x4][4]
   max bitrate=[0x3921][14625]
   stream id=[0x5][5]
   max bitrate=[0xeb260][963168]
   stream id=[0x6][6]
   max bitrate=[0x505d0][329168]
   stream id=[0x7][7]
   max bitrate=[0x19bb8][105400]
   stream id=[0x8][8]
   max bitrate=[0xd098][53400]
============ ASF Stream group == END ===
Found movie at 0x1B2C - 0x1B2C
ASF: 4 audio and 4 video streams found

I haven't beeen able to test this on any other Jumptv channels, but on my one,  1-4 are audio and 5-8 are video. If it is different you should be able to work it out by deduction as the video channels will have bitrates around 10 times higher
than the audio channels.

e.g.

_Audio Stream_

stream id=[0x1][1]
max bitrate=[0x11574]**_[71028]_**

_Video Stream_

stream id=[0x5][5]
max bitrate=[0xeb260]**_[963168]_**

In mplayer the -vid and -aid commands stand for video id and audio id and allow you to select which available streams you want from those available.

Use the 0x6 not the 6 naming convention from the stream description, the beginning of your command might then look like this:

mplayer -v -vid 0x6 -aid 0x2 

other commands I am using are 

-pp 6 (this forces full post processing)

-vo gl2 (I have the latest nvidia drivers, this forces full gl2 video output)

-ao oss (mplayer struggles using alsa on my PC so I am using oss instead)

-autosync 30 (don't what this does ! but it improves the picture on my PC)

My command now looks something like this:

mplayer -v -vid 0x6 -aid 0x2 -pp 6 -vo gl2 -ao oss -autosync 30 "http://secure9.jumptv.com/XXXX?WMThinning=1&Customer_ID=XXXXX&Product_ID=XXX&Asset_ID=XXXX&Stream_ID=XXXX&User_Token=XXXXXXXXXXXXXXX"

With any luck you should now be able to view your Jumptv subscription on your Ubuntu PC at your chosen bandwidth.

I've worked this out by trial and error with very little knowledge of mplayer etc, so am not sure how much further info I'll be able to give to any Q's

Mat

---

### Post by ineksuyu on 2007-05-02
Hi,

It's really a great how to, however I could not find that file to download in Downthemall..
Also, I'm using Feisty. Have you tried this method on Feisty as well?

thanks,

H.

---

### Post by Siasia on 2007-08-03
I managed to watch JumpTV live streams in mozilla-firefox-2.0.0.4 and installed mplayerplug-in(don't remember the version of this one) compiled with WMP support under Gentoo Linux.

---

