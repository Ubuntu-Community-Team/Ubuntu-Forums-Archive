---
title: "NVR(/dev/video1) Error: Failed to set audio eno: Invalid argument (22) VIDIOCGMBU"
date: 2008-08-18
forum: Mythbuntu
---

### Post by LarryJ2 on 2008-08-18
This error occurs when I attempt to record from Card 4 (composite in /dev/vidoe1).  /dev/video1 is from a usb  Hauppauge PVR USB2 which otherwise loads OK. I know that because you can do **cat /dev/video1 > test.mpg** then play the file test.mpg on MPlayer  or  look at the /dev/video1 output directly from within MPlayer.
 
> 2008-08-18 08:26:22.448 Started recording: 182 (DSC) "Mon Aug 18 08:25:00 2008": channel 2182 on cardid 4, sourceid 2
2008-08-18 08:26:22.449 NVR(/dev/video1) Error: Failed to set audio
			eno: Invalid argument (22)
VIDIOCGMBUF:: Invalid argument

Does any one know what NVR is?  And, if possible, where/what should I do/look to attempt a fix?

Thanks.

---

### Post by LarryJ2 on 2008-08-18
A search of [http://www.mythtv.org/pipermail/mythtv-users/2007-September/193877.html](http://www.mythtv.org/pipermail/mythtv-users/2007-September/193877.html) turned up this potentially useful post:
(repeated here for benefit of others who may have the same problem)

> > But when I run mythtv-setup, the default card shows up as "Analog v4l
> capture device" with the probe info saying "Hauppauge WinTV pvr usb2
> [pvrusb2]". If I change it to "MPEG-2 encoder card (PVR x-50,PVR-500)"
> the probed info says "Failed to open".
>
> Any pointers or suggestions for troubleshooting this?

I can't provide a sure-fire solution; however, I've got a few suggestions and 
ideas:

1) If you haven't already, read the MythTV wiki entry on the device, which is
   at [http://www.mythtv.org/wiki/index.php/Hauppauge_WinTV-PVR-USB2](http://www.mythtv.org/wiki/index.php/Hauppauge_WinTV-PVR-USB2). It
   doesn't contain any obvious fixes, given your description, but maybe
   something will "click" with something else you've noticed but not mentioned
   in your post (or that I've overlooked in your post).

2) The mythtv-setup program, as noted in the wiki entry, doesn't correctly
   identify the PVR-USB2 as an MPEG encoding device; you've got to explicitly
   enter the device filename. It's not 100% clear that you did this.

3) Was your "cat /dev/video0 > film.mpg" test done as the same user who runs
   the MythTV backend? If not, it could be you've got permissions problems on
   your /dev/video0 device. In fact, I'd recommend checking that detail in
   any event. Be sure that /dev/video0 is readable and writeable by whoever
   runs the backend. If this seems to be a problem, you might read the wiki
   entry on udev
   ([http://www.mythtv.org/wiki/index.php/Device_Filenames_and_udev](http://www.mythtv.org/wiki/index.php/Device_Filenames_and_udev)), although
   it's a bit sparse on setting permissions information (setting the group
   is shown in an example, but not described in detail). The wiki entry will
   at least get you on the right track in terms of finding files to modify,
   though.

4) The author of the PVR-USB2's Linux driver maintains a mailing list; see
   [http://www.isely.net/pipermail/pvrusb2/](http://www.isely.net/pipermail/pvrusb2/) for archives and a link that'll
   let you subscribe. If you can't figure it out here, you could try there.

Best of luck getting your PVR-USB2 working with MythTV!

-- 
Rod Smith

---

### Post by LarryJ2 on 2008-08-18
This might be the problem!  From [http://www.mythtv.org/wiki/index.php/Hauppauge_WinTV-PVR-USB2](http://www.mythtv.org/wiki/index.php/Hauppauge_WinTV-PVR-USB2)
> 
If "NVR: Won't work with the streaming interface, falling back VIDIOCGMBUF:: Invalid argument" appears in the mythbackend.log, it might be due to the incorrect capture device being selected. It should be "MPEG-2 encoder card (PVR-x50, PVR-500)."

---

### Post by newlinux on 2008-08-18
Sounds like you have self-diagnosed. Did you set your card up as a mpeg-2 encoder or a V4L in myth?

---

### Post by LarryJ2 on 2008-08-18
That was the problem.  I just blindly followed the instructions even though myth didn't show any probed info.   Here are some screen shots to show what I ended up with.  My mythbox contains two ATSC cards (an AirtoPC, a KWorld 110 which are inputs DVB0 and DVB1) and the newly installed  Hauppauge WinTV-pvr2 USB connected dongle which was assigned /dev/video1 because my KWorld card also has an NTSC/Svideo/Composite input was assigned /dev/video0.  I didn't want to use the KWorld composite input because this card does not contain a hardware mpeg encoder where I believe the WinTV-pvr2 does.  My mythbuntu box receives OTA local stations via antenna input and dishnetwork satellite via the connection between the composite input of the WinTV-pvr2 and the composite output of the dish 501 receiver.

Hope this helps someone else.  I'll label this as "solved" if I can determine how to do that. :(

LJ

---

### Post by LarryJ2 on 2008-08-18
> NewLinux:Sounds like you have self-diagnosed. Did you set your card up as a mpeg-2 encoder or a V4L in myth?

Eventually as a mpeg.  In the lineedit area (see captureCardSetup.png screenshot above) where you choose the type of card with your left right cursor keys,  I just picked the MPEG-2 encoder card even though my winpvr2 was not listed blindly following the hint #2 (see Rod Smith's post referenced above).  I recall that nothing appeared in the video device lineedit either but I knew that /dev/video1 was assigned to the wintvpvr2 so I just typed it in. I knew the wintv-pvr2's composite mpeg2 stream output was /dev/video1 because that is in dmesg upon bootup.   After typing /dev/video1 into the device lineedit (the small window where you enter info from the keyboard) then I pressed "Enter", quite magically, Probed info: showed **pvrusb2**.
I selected default input: composite because that is where my dishnet receiver's yellow, red, and white baseband connections terminate. (The wintvpvr2 has a corresponding set of yellow, red, and white RCA phono plugs.) 

Also this article was especially helpful:
>     *  If "NVR: Won't work with the streaming interface, falling back VIDIOCGMBUF:: Invalid argument" appears in the mythbackend.log, it might be due to the incorrect capture device being selected. It should be "MPEG-2 encoder card (PVR-x50, PVR-500)." 
(from [http://www.mythtv.org/wiki/index.php/Hauppauge_WinTV-PVR-USB2](http://www.mythtv.org/wiki/index.php/Hauppauge_WinTV-PVR-USB2))

The output of /dev/video0 from your wintv-pvr2 usb  is an mpeg2 stream which contains the video and the audio.  So there is no "audio codec" or audio connection configuration. mplayer will decode this stream for you.  Start mplayer, right click on the tv screen, click file open, set file type to ALL FILES, then navigate to /dev/video0.  Click enter After a brief pause,  your picture and sound should appear. 

Whew!

LJ

---

### Post by LarryJ2 on 2008-08-22
A note to add emphasis for MythUbuntu users struggling with a WinTV-PVR2 USB box.  Getting this box running is easy if you know exactly what to do!  :(

1.  As you monitor the folder /dev,  plug in your USB Hauppauge WinTV-PVR2.  You should see  /dev/video0 (zero)  or /dev/video1 appear after a short delay.  This should be reflected in dmesg also.  Search dmesg for /dev/video* using this:
```
dmesg | grep /dev/video*
```

2.  If not, look back with dmesg and see why the drivers for this device are not being loaded. Usually Linux doesn't required this but this might be an appropriate time to reboot.

3.  Once you have discovered the appropriate /dev/videox output for the box,  open up the mythbuntu  backend setup program.  Navigate to Capture Card Setup:  then using tab navigate to the **Card type:** window then  left right until you come to Mpeg2 encoder card ....  Nothing will appear in "Probed Info". The words **Failed to Open** may appear. Not to worry!

4.  Tab down one line edit window to the "Video Device" lineedit window and type in /dev/video0 or /dev/video1 (depends on step1).  Press enter.
Then and only then will you see Probed Info showing the Hauppauge Mpeg Encoder xxx card (words to that effect).  Next tab down to Default input:  left right until this shows correctly for your setup.  I used composite1 because I'm taking video and stereo audio from the back of my DishNet Satellite Receiver.  If you choose "Television" and your wintvpvr2 doesn't happen to be tuned to an analog ntsc channel that has a signal on it, you'll get nothing but  video noise or snow when you get to step 6.
"

5.  What comes spewing out of /dev/video_ is not an NTSC video signal.  nor is it a baseband video signal such as comes out of the yellow RCA photo jack on, for example, a VCR.  Instead it is an mpeg2 binary  data stream containing the video and audio combined.

6.  I was able to see and listen to the mpeg stream by using mplayer.  Open mplayer,  right click on the screen,  choose file input,  at the bottom choose all files filter,  navigate to /dev/video0 or /dev/video1 as appropriate.  Click Enter after a short delay, you should see whatever your Hauppauge WinTVpvr2 is tuned to.

7.  Nothing seen/heard in mplayer?  Make sure you have chosen an appropriate output.  I have mine connected to my yellow video output and the red and white photo stereo out jacks on the back of my dish receiver.  So therefore, I have to set the default input to Composite1.

8. Mike Isley deserves a gold metal for his support of this device. The sign up form for his mailing list is here: [http://www.isely.net/cgi-bin/mailman/listinfo/pvrusb2](http://www.isely.net/cgi-bin/mailman/listinfo/pvrusb2)

Hope this helps someone.

Larry

---

