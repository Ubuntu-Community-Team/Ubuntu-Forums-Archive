---
title: "DVD Creation Guide"
date: 2008-09-09
forum: Multimedia Software
---

### Post by the_de5olate_0ne on 2008-09-09
This guide has been written to help those wishing to easily take most kinds of video formats, turn them into DVD compliant mpeg2 video, author a DVD disc structure, create the necessary image, and burn the DVD. With a little direction on which tools to use and how to use them, Linux can be a very powerful DVD authoring platform.

_[SIZE="4"]Things you will need:[/SIZE]_
1.  A video you wish to put on a DVD
2.  A flavor of Ubuntu
3.  [[COLOR="DeepSkyBlue"]gimp[/COLOR]]("http://www.gimp.org/") (optional)
4.  [[COLOR="DeepSkyBlue"]tovid[/COLOR]]("http://tovid.wikia.com/wiki/Tovid_Wiki")
5.  [[COLOR="DeepSkyBlue"]Audacity[/COLOR]]("http://audacity.sourceforge.net/") (optional)
6.  tovid gui
7.  [[COLOR="DeepSkyBlue"]mplayer/mencoder[/COLOR]]("http://www.mplayerhq.hu/design7/info.html#docs")
8.  [[COLOR="DeepSkyBlue"]ffmpeg[/COLOR]]("http://ffmpeg.mplayerhq.hu/documentation.html")
9.  [[COLOR="DeepSkyBlue"]dvdauthor[/COLOR]]("http://dvdauthor.sourceforge.net/")
10. mkisofs
11. [[COLOR="DeepSkyBlue"]cdck[/COLOR]]("http://freshmeat.net/projects/cdck/") (optional)
12. gnuplot (optional)

You can install all of these applications using [[COLOR="DeepSkyBlue"]Synaptics Package Manager[/COLOR]]("https://help.ubuntu.com/community/SynapticHowto").

--------------------------------------------------------------------------


1. _[SIZE="4"]Prepare your menu background and menu audio.[/SIZE]_
Once you have your video, get or make the background image you wish to have as your DVD menu background. Some considerations are that [[COLOR="DeepSkyBlue"]tovid[/COLOR]]("http://tovid.wikia.com/wiki/Tovid_Wiki") will make it widescreen, so your menu image should be sized to something between 640 x 512 and 720 x 480, respectively. [[COLOR="DeepSkyBlue"]Gimp[/COLOR]]("http://www.gimp.org/") works very well for image resizing, cropping, and editing. Once you have your graphic as you like it, get your audio set as needed. [[COLOR="DeepSkyBlue"]Audacity[/COLOR]]("http://audacity.sourceforge.net/") works very well for audio editing and can output a nice 320 bitrate [[COLOR="DeepSkyBlue"]mp3[/COLOR]]("http://en.wikipedia.org/wiki/Mp3").


2. _[SIZE="4"]Put it all together in tovid.[/SIZE]_
Launch tovid GUI, title your disc, and choose a format if needed. The US is always NTSC. Choose a directory. /tmp is chosen by default, but I prefer to change it to my [[COLOR="DeepSkyBlue"]home directory[/COLOR]]("http://en.wikipedia.org/wiki/"). Add a menu. Give it a title. 'Main' works well as a title. Select your image and audio appropriately. Choose how and where you want your menu buttons and text. Add the video. Since the name of the video gets placed on the menu, I usually rename it to 'PLAY'. Choose the [[COLOR="DeepSkyBlue"]aspect ratio[/COLOR]]("http://en.wikipedia.org/wiki/DVD-Video#Resolution_and_Frame_rate"). The tooltip for [[COLOR="DeepSkyBlue"]aspect ratio[/COLOR]]("http://en.wikipedia.org/wiki/DVD-Video#Resolution_and_Frame_rate") tells you how to select the right one. Leave output resolution alone. Decide on a quality. I usually use 10 and mpeg2enc as my encoding options. Now choose the Encode tab and click 'Start encoding'. [[COLOR="DeepSkyBlue"]Tovid[/COLOR]]("http://tovid.wikia.com/wiki/Tovid_Wiki") will now encode your video to DVD compliant video, and render and encode a menu. You will be left with Main.mpg and PLAY.mpg, your menu and movie. At this point, go ahead and make sure both look right by playing them in your favorite player. I usually use [[COLOR="DeepSkyBlue"]mplayer[/COLOR]]("http://www.mplayerhq.hu/design7/info.html#docs") or [[COLOR="DeepSkyBlue"]Xine[/COLOR]]("http://xinehq.de/"). Also, an xml file is created that describes your DVD.


3. _[SIZE="4"]Create the disc structure.[/SIZE]_
After [[COLOR="DeepSkyBlue"]tovid[/COLOR]]("http://tovid.wikia.com/wiki/Tovid_Wiki") tells you it's encoded successfully, click OK and go to the Burn tab. Click the Start button. It will now, after telling you burning is experimental, create the necessary VOBs, BUPs, and IFOs, and create the VIDEO_TS and AUDIO_TS folders. It will place them in the folder you told it to in the beginning, with the folder name how you titled the disc. An example is I used '/home/mike/' as my directory and my DVD was called 'Home Movies'. So my VIDEO_TS and AUDIO_TS folders are inside '/home/mike/Home Movies/'.


4. _[SIZE="4"]Create the image with mkisofs.[/SIZE]_
Once you've located the parent folder that contains your VIDEO_TS and AUDIO_TS folders, launch terminal. The command to convert the DVD structure to the proper image for burning is:

mkisofs -dvd-video -upf -o '/output/directory/and/file/for/iso' '/input/directory/containing/VIDEO_TS/'

My example would be:
mkisofs -dvd-video -udf -o '/home/mike/Desktop/Home Movie.iso' '/home/mike/Home Movie/'

This will create a nice neat [[COLOR="DeepSkyBlue"].iso[/COLOR]]("http://en.wikipedia.org/wiki/Universal_Disk_Format") file of your DVD.


5. _[SIZE="4"]Check the image with isoinfo.[/SIZE]_
When mkisofs finishes, confirm the structure is right by using isoinfo:

isoinfo -i '/input/image.iso' -l

You will get a list of the files contained in the image. VIDEO_TS.IFO should start at the earliest part of the disc, except for . and ..


6. _[SIZE="4"]Burn the disc off.[/SIZE]_
Insert a DVD and right-click your [[COLOR="DeepSkyBlue"].iso[/COLOR]]("http://en.wikipedia.org/wiki/Universal_Disk_Format") file. Choose 'Write to Disc' and ensure it's using the right speed and drive. Click Write. When it finishes, provided your initial source video was encoded well, you will have a nice, high quality, DVD compliant video DVD that should play well in most machines.


7. _[SIZE="4"]Check the disc integrity.[/SIZE]_
Should you wish to go a step further and check the quality of the disc, you can use [[COLOR="DeepSkyBlue"]cdck[/COLOR]]("http://freshmeat.net/projects/cdck/") and gnuplot. Use the [[COLOR="DeepSkyBlue"]cdck[/COLOR]]("http://freshmeat.net/projects/cdck/") command as follows:

cdck -d /dev/scd0 -p

Change the name of your drive as needed. [[COLOR="DeepSkyBlue"]cdck[/COLOR]]("http://freshmeat.net/projects/cdck/") will now test for any bad sectors as well as access times for all. It will tell you how stable or unstable the disc is. Should you wish to plot the results, launch gnuplot from the terminal and type the following:

plot '/home/youruser/cdck-plot.dat'

A nice plot will appear. A healthy disc arcs instead of being flat.

--------------------------------------------------------------------------

[SIZE="4"]I hope this guide helps those looking for a DVD creation solution in Linux.[/SIZE]

---

