---
title: "stream url grabbing (flash)"
date: 2009-02-16
forum: Multimedia Software
---

### Post by sr_guy on 2009-02-16
I'm trying to grab source streams so that I can setup a "VOD" list of sorts in mythbuntu.  I'll use this link as an example:

[http://www.history.com/video.do?name=iceroadtruckers](http://www.history.com/video.do?name=iceroadtruckers)


It plays flash video on the website. Same implies with other TV network sites like CBS & ABC. I want to sniff those stream URL's so that I can play them in mythstream on my mythbuntu setup.

I've tried the following progs:

-streamsniff (for some reason won't detect these streams at all)

-wireshark (gives me the source stream ip address, but not the direct url to the stream)

Are there any other programs that will grab and reveal those url's for those streams that run under linux?

---

### Post by neu2buntu on 2009-02-16
not sure about mythubuntu but how i do it in ubuntu is i use firefox .then say goto page where stream is and click > tools >page info > media . and this shows a list of all the images on page and what you are looking for the embedded player url just copy and paste it to wherever u need it. there will also be embedded players for advertisements so u may have to elimanate which is the stream u want... hop this helps

---

### Post by neu2buntu on 2009-02-16
here are the 3 embedded plaqyer url of the site (will probably be the 1st 1you want)

[http://www.history.com/bcplayers/Player/3Tier/SharedFiles/swf/media/AETNBrowser.swf](http://www.history.com/bcplayers/Player/3Tier/SharedFiles/swf/media/AETNBrowser.swf)

[http://www.history.com/bcplayers/Player/3Tier/SharedFiles/swf/media/AETNPlayer.swf](http://www.history.com/bcplayers/Player/3Tier/SharedFiles/swf/media/AETNPlayer.swf)

[http://spe.atdmt.com/ds/I2IWCLNGTLGT/W_DVD/W_DVD_728x90_v2.swf?ver=1&clickTag1=http://adserver.adtech.de/adlink|611|1361690|0|225|AdId=2164817;BnId=1;itime=797877788;key=key1+key2+key3+key4;nodecode=yes;link=http://clk.atdmt.com/go/129382299/direct;ai.66624574;ct.1/01&clickTag=http://adserver.adtech.de/adlink|611|1361690|0|225|AdId=2164817;BnId=1;itime=797877788;key=key1+key2+key3+key4;nodecode=yes;link=http://clk.atdmt.com/go/129382299/direct;ai.66624574;ct.1/01]("http://spe.atdmt.com/ds/I2IWCLNGTLGT/W_DVD/W_DVD_728x90_v2.swf?ver=1&clickTag1=http://adserver.adtech.de/adlink%7C611%7C1361690%7C0%7C225%7CAdId=2164817;BnId=1;itime=797877788;key=key1+key2+key3+key4;nodecode=yes;link=http://clk.atdmt.com/go/129382299/direct;ai.66624574;ct.1/01&clickTag=http://adserver.adtech.de/adlink%7C611%7C1361690%7C0%7C225%7CAdId=2164817;BnId=1;itime=797877788;key=key1+key2+key3+key4;nodecode=yes;link=http://clk.atdmt.com/go/129382299/direct;ai.66624574;ct.1/01")

as you can see the 3rd stream is an advertyisement so it will be stream 1 or 2 that you want here

---

### Post by sr_guy on 2009-02-16
Firefox is only pulling the flash advertisements. I need they actual stream links. 

Any other video stream sniff options?

---

### Post by halpulaar on 2010-04-05
Hi,

I appreciate this is more than a year old and could create a new thread. I just hoped someone could post the solution and the admin chaps can then mark this as "solved".

I have a similar problem where I want to find the streaming url of the radio playing at this address: [http://www.sudfm.net/ecouter/listen.php](http://www.sudfm.net/ecouter/listen.php)

Any chance to get at least some guidance. Solutions mentioned above did not help (either too complicated -wireshark; either no info -firefox tools)

Thanks in advance

---

### Post by LuridCinema on 2010-04-05
Download helper plugin for firefox will grab the videos and save them for you... I use it to grab vids all the time

---

### Post by halpulaar on 2010-04-07
Thanks for the response.
Please bear in mind this is LIVE Radio and not video. If it still works, please let me know the exact name of the plugin.

Thanks again

---

### Post by Anita_Tsai on 2010-04-07
> **luridcinema said:**
> download helper plugin for firefox will grab the videos and save them for you... I use it to grab vids all the time
 =d>

---

### Post by ron999 on 2010-04-07
.......

---

### Post by V. Wayne on 2010-04-07
Here is how I capture any embedded flash video with sound on any website and save the file on my hard drive.

First you have to install the following packages.  I currently use Ubuntu 9.10.

pavucontrol - PulseAudio Volume Control
pulseaudio -  PulseAudio sound server
recordmydesktop - Captures audio-video data of a Linux desktop session
gtk-recordMyDesktop -  a Graphical frontend for recordmydesktop


1. Setting up to capture audio.

Open the PulseAudio Device Chooser which should be in the path Applications/Sound & Video/PulseAudio Device Chooser.
The PulseAudio Device Chooser icon should now be on your upper right desktop panel.
Click on the PulseAudio Device Chooser icon and select Volume Control. The Volume Control window should open and select the Recording tab. Next to "Show:" be sure to select Applications from the dropdown box. You should see grayed out "no application is currently recording audio" that's ok... leave it open for now.

2. Ok now you are ready to capture the video.  

Go to a website that has the video you want to capture.
Open gtk-recordmydesktop, which should be in the following path Applications/Sound & Video/gtk-recordMyDesktop. A solid red circle icon should now be on your upper right desktop panel. Do not click on it now or it will start recording.

You should also see the recordmydesktop window on top of the browser window and be sure the box next to Sound Quality is checked. If necessary, move the recordmydesktop window to an area where it is not covering the flash video you want to capture.

Next click the Select Window button on recordmydesktop - your cursor should change to a "+" sign when you move it within the recordmydesktop window.
In the recordmydesktop window place the "+" cursor in the upper left corner of the video you want to capture, hold down the left mouse button and drag the cursor just over the video window you want capture; which should now be covered solid red and release left mouse button.

Now you should see in your web browser window a black outline box framing the video window.

Click on the the solid red icon to start recording and click on the video in your broswer to start it playing.

Now go to the PulseAudio Volume Control window to see if there is an Alsa plugin meter capturing the sound. Be sure next to "ALSA Capture from" the "Monitor of Internal Audio Analog Stereo" box is selected.

Once the PulseAudio Device Chooser Volume Control is setup properly you will not have repeat this audio setup process for future flash video captures.

recordmydesktop will begin saving the file in an .ogv file on your hard drive for you to playback. The default file is out.ogv

---

### Post by luisella on 2010-04-20
On windows there is [URL Snooper]("http://all-streaming-media.com/find-stream-URL/Project-URL-Snooper-Find-the-actual-stream-URL-Free-download.htm"), here is a tutorial example on how to use it [http://stream-recorder.com/forum/tutorial-dl-comedy-central-t6324.html](http://stream-recorder.com/forum/tutorial-dl-comedy-central-t6324.html)

Here [http://ubuntuforums.org/showthread.php?t=418212](http://ubuntuforums.org/showthread.php?t=418212) a user report of trying to run it with wine, unsucessfully. The mentioned firefox plugins don't work when the URL is obfuscated, like for Comedy Central or CBS videos, as reported in these discussion [http://ubuntuforums.org/showthread.php?t=1457560](http://ubuntuforums.org/showthread.php?t=1457560)

---

