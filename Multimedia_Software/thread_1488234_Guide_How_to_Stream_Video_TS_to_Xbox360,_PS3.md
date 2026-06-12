---
title: "Guide: How to Stream Video_TS to Xbox360, PS3"
date: 2010-05-19
forum: Multimedia Software
---

### Post by senormoll on 2010-05-19
Hey guys, I had kind of a hard time finding how to do this, so I figured since these forums have always been so helpful to me that I'd post a compilation of things I've learned that eventually led me to be able to stream Video_TS DVD files to my xbox360 and ps3.  I'm not taking credit for any of this--just wanna make a singular guide for it.

1.  Follow this link: [https://help.ubuntu.com/community/Ps3MediaServer](https://help.ubuntu.com/community/Ps3MediaServer)
     The PS3MediaServer application is what decodes the video to be able to be streamed.  So if you want to be able to do it at any given time, make sure to add the path to the executable to your startup programs, as the guide states.
     The most important thing to have, for our purposes here, is ffmpeg.  This allows you to decode mpeg files for streaming.  The other stuff it includes are helpful too, as they allow xvid's and such to be streamed.

2.  Search the Software Center for Avidemux.  It's under Audio and Video, and it's a great video editing program.  We won't be doing much editing, but we still need the program.

3.  With Avidemux, open the first large VOB file in your Video_TS folder (usually VTS_01_1.VOB).  It will ask you if you want to index it, click yes.  It will ask you if you want to append the multiple files, also click yes.  It will take about 1-2 minutes, and you will have the full movies loaded.  The timestamp on the bottom should be 01:45:09.500 or however long your movie is.

4.  On the left hand side, where it says format, select 'MPEG-TS (A+V)' from the dropdown.  Then up top, click save.  Name it what you want, but add .mpg to the end of the name to make sure your 360 or ps3 recognize it as a mpeg file.  Then hit Save.  This will also take minute or two.

5.  Now, when you open PS3 Media Server, you may need to click the tray icon to pull up the main window.  Under the Navigation/Share Settings tab, on the bottom, add the directories that contain the files you want to stream.  You can select a directory as high up as you want, but just know that there is a subdirectory limit (I don't know if it's imposed by the PS3 or the MediaServer, but it's like 8 or something).  

6.  Now, when you boot up your PS3, go to Videos (you have to go to the section for the type of file you want to play, like Music or Video, otherwise it won't play).  Go to the Media Server item, and you should see the folders you are sharing.  Just select the .mpg file and enjoy!


Explanation of what we did:  VOB files are really just mpegs, so we just used an editing program to make the 3 or 4 VOB files into one long file, and then renamed it .mpg so that the consoles would know what it is.  You can achieve this any way you'd like, including in Windows or Mac, so that's why I'm explaining it in detail.  Then, PS3MediaServer uses the ffmpeg package to decode the mpg file and stream it over your local network.  For me, PS3MediaServer took no setting up aside from adding directories, but be sure to follow the instructions for that program and make sure the right ports are forwarded on your router.

I hope this helps a few people out there who are looking to stream ripped movies to their consoles, because these forums have always been very helpful to me :)

---

