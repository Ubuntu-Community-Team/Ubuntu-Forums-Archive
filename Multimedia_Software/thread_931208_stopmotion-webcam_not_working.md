---
title: "stopmotion-webcam not working"
date: 2008-09-27
forum: Multimedia Software
---

### Post by helpineed on 2008-09-27
Help.

I have installed Stopmotion on to my system and am trying to get my webcam working with it. I have installed vgrabbj and my webcam is working-I tested it with Cheese. When I push the camera button the screen doesn't show anything and is black. I opened Stopmotion with terminal and when I push the camera button it said:```
Device doesn't support width/height
There was no map allocated to be freed...

```

Help

---

### Post by Aearenda on 2008-09-27
Vgrabbj doesn't work with all cameras, unfortunately. In your case, it may only be that you need to adjust the capture parameters. 

1. In Stopmotion, go to Settings->Configure Stopmotion.
2. Click on the Video Import tab. 
3. Click on the "vgrabbj VGA singleshot" entry
4. Click the 'Edit' button.
5. If the text of the settings fields is obscured by input boxes that are too small, drag the lower edge of the whole dialogue box down - this makes the text boxes bigger.
6. Look at the pre-poll command. It has a parameter to set the image capture size - and I think it defaults to vga. On my system, I have modified it so:```
vgrabbj -f $IMAGEFILE -d $VIDEODEVICE -b -D 0 -i cif
```It is the '-i cif' that makes the change.
7. Click 'Apply' and give it a test.

If it works, you can try it as a daemon, by making the same change to the daemon entry and leaving that one selected.

If it doesn't work, try starting a terminal and type ```
 vgrabbj -s /dev/video0
```
This should tell you the max and min width and height, and if you then type ```
vgrabbj --help
```the info for the -i parameter will let you match up with the setting you need.

Please let me know how you get on!

---

### Post by helpineed on 2008-09-27
Okay, I tried putting that code in to Stopmotion but it didn't work still when I pushed the camera button. I tried it in terminal and when I pushed the button it printed```
Reading image from /dev/video0
```every half second or so. When I tried changing your code, it already looked perfect.

---

### Post by Aearenda on 2008-09-28
1. What does ```
vgrabbj -s /dev/video0
``` show?
2. In Stopmotion's preferences, Video Device tab, does the camera's decription show is as /dev/video0?

---

### Post by helpineed on 2008-09-28
1.It shows:```
vgrabbj, Version 0.9.6
Videodevice name: /dev/video0 (Logitech QuickCam EC)
Capabilities
Type     : 1	Values can be looked up at videodev.h
Channels : 1
Audio    : 0
MaxWidth : 352
MaxHeight: 288
MinWidth : 160
MinHeigth: 120

Current Settings:
Brightness: 16384
Hue       : 0
Color     : 0
Contrast  : 8192
Whiteness : 0
Depth     : 24
Palette   : RGB24 (4)
Width     : 160
Height    : 120
Chromakey : 0

```

2.Yes

---

### Post by Aearenda on 2008-09-28
Good - now if you do this command:```
vgrabbj -f test.jpg -d /dev/video0 -b -D 0 -i cif
```(which should take one photo and then stop) does the output file test.jpg open properly using ```
eog test.jpg
```?

Also, please post the contents of .stopmotion/preferences.xml (if it's all squashed up, don't worry, mine is).

---

### Post by helpineed on 2008-09-28
When i open an image a blank one comes up - just black.
Also, I'm a bit confused about the xml thing. :confused:

---

### Post by Aearenda on 2008-09-28
Ok, since the image is black we'll skip the xml file for now! For the record, the .stopmotion folder is a hidden folder (because its name starts with a '.') in your home folder, where Stopmotion keeps its stuff. This is sort of similar to finding  registry entries in Windows, but only sort of! 
To post the file's contents, 'gedit .stopmotion/preferences.xml' would show it, then CTRL/A CTRL/C selects all and copies it, and of course CTRL/V pastes it. 

Anyway, the image is black. That's probably why you're not seeing anything in Stopmotion! I don't have the same camera as you, so all we can do now is try different parameters to vgrabbj until it works, if it does. It may not - so the process can get quite frustrating from now on. The issue as I understand it is that vgrabbj works with cameras that worked in the earlier Video-for-linux (V4L) system. Now we have V4L2, which works with more cameras, and programs like Cheese use it. This is why your camera works with Cheese. What we need is an equivalent of vgrabbj that works with V4L2 devices, but I haven't found one that is compatible with Stopmotion's awkward way of getting images yet.

For now, the vggrabbj help suggests using -g on QuickCams, so let's try```
vgrabbj -f test.jpg -d /dev/video0 -b -D 0 -g
```but I don't really expect any change.

Also, just so I know what camera chipset this is, please do ```
lsusb
```in a terminal and post the output (select it with the mouse and use right-click or CTRL/SHIFT/C to copy).

---

### Post by Aearenda on 2008-09-28
I think I've found a way to do it - but one problem remains. I have persisted with this issue because I have a much better V4L2 webcam that I would like to get to work with Stopmotion, but so far failed. Following a Google link I came across the page at [http://wiki.skolelinux.de/RalfGesellensetter/WebCam](http://wiki.skolelinux.de/RalfGesellensetter/WebCam), which is in German. I understand enough to realise he is close to achieving what we need. The pre-poll command ```
mplayer tv:// -tv driver=v4l2:device=$VIDEODEVICE:fps=10:outfmt=rgb16 -fps 10 -frames 1 -quiet -really-quiet -vo jpeg:optimize=100:quality=100 || mv 00000001.jpg $IMAGEFILE
```works for my V4L2 camera, but only very slowly, and with some green frames. This may be enough for you, since we are doing stop motion - but I want to speed it up. The problem is that it needs a second process moving the files (which have incrementing filenames) into the right spot for Stopmotion to use as a daemon. I'm still working on that!

---

### Post by Aearenda on 2008-09-28
I've made progress with this - enough to be happy with for now. Here's how to duplicate what I have done:

EDIT: There's a better way - see the Motion discussion in post 7 of okey666's thread [http://ubuntuforums.org/showthread.php?t=956338](http://ubuntuforums.org/showthread.php?t=956338).

1. Set up a script to start mplayer and to move the frames it creates, like this:
1.1 Start a terminal session
1.2 Type ```
gedit startmplayer
```
1.3 Paste this text into the file:```
#!/bin/bash
# Crude script to push mplayer frames from V4L2 camera to Stopmotion
# $1 is videodevice
# $2 is imagefile
# $3 is FPS captured
# $4 is loop delay
# $5 is folder to use

# Delete old files if any - leading 0 is just in case this is run in the home directory!
rm $5/0*.jpg

mplayer tv:// -tv driver=v4l2:device=$1:fps=$3:outfmt=rgb16 -fps $3 -quiet -really-quiet -vo jpeg:outdir=$5:optimize=100:quality=100 &

# cd to cut down overhead in loop
cd $5

while true ; do
  for FILE in 0*.jpg ; do
      if [ -s $FILE ] ; then 
	mv $FILE $2
      fi
  done
  sleep $4
done
```
1.4 Type the following command to make the file executable:
```
chmod u+x startmplayer
```
1.5 Create a hidden directory for the script to use where there will be no other JPEG files:
```
mkdir .tempjpgs
```
1.6 Close the terminal session

2. Tell Stopmotion how to use the script
2.1 Start Stopmotion and go to Settings->Configure Stopmotion
2.2 Select the "Video Import" tab
2.3 Click the "Add" button
2.4 Click on the now-highlighted empty row of the table, under the "Name" column
2.5 Type a name for the new entry - I used "Mplayer"
2.6 Press <TAB> and type a comment if you wish
2.7 Click the "Edit" button
2.8 Drag the bottom edge of the dialogue box down if the three text boxes are too squashed to see what you are typing properly.
2.9 In the "Start deamon" box type ```
./startmplayer $VIDEODEVICE $IMAGEFILE 2 0.25s .tempjpgs &
```
Here... 
 - the "./" characters tell Stopmotion to find the program in the current directory
 - $VIDEODEVICE and $IMAGEFILE are required to pass the camera name and target filename in from Stopmotion
 - "2" specifies that 2 frames per second should be processed (more on this later)
 - "0.25s" specifies that the script should sleep for a quarter of a second on each cycle (see later)
 - ".tempjpgs" tells the script the name of the folder created earlier.
 - "&" causes the command to be started in a separate process so that Stopmotion can do its work as well.

2.10 In the "Stop deamon" box type ```
killall startmplayer && killall mplayer
```
This makes sure that the capture processes are stopped properly.
2.11 Click "Apply" then "Close"

Now test it!

The script starts a second process for mplayer, which takes the webcam input using V4L2 and creates frames in the specified folder at the specified rate. These have a filename that is 8 digits long, incrementing by 1 for each frame. 
The script looks for files of non-zero size (which approximates to 'finished') and then moves it (or them) to the place where Stopmotion wants them. It then sleeps for the specified time so that the processor has chance to do other things. Thus each successive frame gets written over the previous one in the location where Stopmotion is watching - this is what vgrabbj does for V4L1 webcams. 

On my system this gives me a slow but usable capture system, with pictures of better quality than I was getting with my old V4L1 camera. There is a significant delay in the video on my 1GHz Pentium-M system, which is caused by the mplayer conversion process as well as my kludgy capture process I think. 

The frames-per-second and delay settings allow you to tune the script on your system simply by modifying the "Start deamon" setting in Stopmotion. I experimented with 1 frame per second and 0.5s, which was too unresponsive, and 3 frames with 0.1s, which loaded the processor too much, and settled on the settings I have given. Since this is an interpreted script, I don't recommend setting it to loop too fast! It isn't necessary anyway for stop motion work.

I hope this helps - if I find a better way I will add it to this thread. What we *really* need is for vgrabbj to become V4L2 aware, but it doesn't seem likely that this will happen.

PS: Stopmotion uses the spelling 'deamon' - I think it should be 'daemon' really but I've shown it how it is.
PPS: Just in case anyone thinks of it, yes, I tried dvgrab -V, and no, it doesn't work with my webcam.
PPPS: Yes, this is getting silly. It's late! I have tried the package 'webcam' but it doesn't seem to go faster than 1 frame per second. It's not so laggy though. I've also looked at luvcview (creates its own weird window) and webcamd (lacks documentation then tells me to RTFM when I ask it for help - how rude. Googling it suggests it's not going to be any use anyway).


EDIT: There's a better way - see the Motion discussion in post 7 of okey666's thread [http://ubuntuforums.org/showthread.php?t=956338](http://ubuntuforums.org/showthread.php?t=956338).

---

### Post by helpineed on 2008-09-28
It's still not working.:-x

When I push the camera button it spits out```
rm: cannot remove `.tempjpgs/0*.jpg': No such file or directory
mplayer: could not connect to socket
mplayer: No such file or directory

```

---

### Post by Aearenda on 2008-09-29
Mine says that too, and then works.

Maybe the camera is still giving black images...

Are there any files in the .tempjpgs folder, and if so, do they contain a useful image or just blackness?

Is .stopmotion/capturedfile.jpg just black?

Please post the output from ```
dmesg | grep uvcvideo
```

---

### Post by helpineed on 2008-09-29
There are no files in .tempjpgs,

capturedfile.jpg is just black

and your command doesn't give out anything

---

### Post by Aearenda on 2008-09-30
Ok, so the camera isn't using the uvcvideo driver - I should have asked you to do```
dmesg | grep video
```
The output from ```
lsusb
``` would also be useful.

---

### Post by helpineed on 2008-09-30
```
dmesg | grep video

```
returns
```
[   21.626437] Boot video device is 0000:00:02.0
[   34.626558] Linux video capture interface: v2.00

```
and
```
lsusb

```
returns
```
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 002: ID 046d:092c Logitech, Inc. QuickCam Chat
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000 
```

---

### Post by Aearenda on 2008-09-30
Thanks - it seems that this Quickcam should be using the gspca driver. With it plugged in,```
lsmod | grep spca
```and```
dmesg | grep spca
``` should confirm this, as well as pick up any warnings from the driver. 

Just a thought - what is the modified time for the file .stopmotion/capturedfile.jpg? (ls -l ~/.stopmotion/capturedfile.jpg will show it - or look in its properties using Nautilus). I'm just wondering whether we have a new file here, or an old one that indicates a problem with the mplayer process. 

Are you using 32-bit or 64-bit Ubuntu? If 64-bit, [http://sudan.ubuntuforums.com/showthread.php?t=634393](http://sudan.ubuntuforums.com/showthread.php?t=634393) offers some hope.

I was too hasty in thinking it would behave more like my Quickcam earlier in this thread. I have come across several pages describing problems with this camera, and solutions that require the compilation of a new driver with auto-exposure turned off. I really have no idea whether this is likely to help in your case or not. I will do some more research and post again when I come to a conclusion about what to recommend next. In the meantime, please post the output of the two commands above, and any comments you have about my other musings above.

---

### Post by Aearenda on 2008-09-30
I wonder if you've hit something like the gamma problem this thread describes - with a possible workaround in step 4. [http://ubuntuforums.org/showthread.php?t=651375](http://ubuntuforums.org/showthread.php?t=651375)

---

### Post by Aearenda on 2008-10-02
I also wonder if the updated driver referred to in [http://ubuntuforums.org/showthread.php?t=926101](http://ubuntuforums.org/showthread.php?t=926101) will help - you'll need to install the dkms package first.

---

### Post by kyleskimskate on 2008-10-17
ok so i read this whole thread thing, and I have and eye toy which i configured to work on ubuntu, but when i pull up the capture for stopmotion, the image is all distorted and colorful, messed up, and it repeats the image in like nine different panels all in the preview thing. HELP! i'd attach a screenshot but i don't know how

---

### Post by Aearenda on 2008-10-18
kyleskimkate: Unfortunately, the way to make a webcam work with Stopmotion is VERY hardware-dependent. Stopmotion relies on external software to grab the image from the camera, and that software works best with older web cameras. Stopmotion is presently much easier to do with a program like MonkeyJam (it's free) on Windows (sorry!).

I don't think a screen capture is needed, your description gives me a good idea of what you are seeing. For the record, if you are running a default Ubuntu setup, pressing the <PrtScr> or <PrintScreen> key on the keyboard will capture the screen, and then open a dialogue where you can tell it where to save the file. Then you can upload the saved file as an attachment.

The first thing we should do is determine what camera hardware you have - as the computer sees it, not as the box describes it!

To do this, please follow these steps:
1. Start a command-line window from the Applications->Accessories->Terminal menu

2. Type this:```
lsusb
```Then press <Enter>.

3. Find the line in the output from that command that refers to your camera - typically it contains the word 'camera' or 'webcam' or the manufacturer's name. It will look something like this:
```
Bus 004 Device 008: ID 0c45:6005 Microdia Sweex Mini WebCam
```

4. Copy that line by selecting it using the mouse and then right-clicking on it and choosing 'copy'.

5. Switch to your web browser and paste the details into your reply to this message.

6. Close the Terminal window (click on the X at top right!)

---

### Post by kyleskimskate on 2008-10-18
ok i think this might be it:Bus 001 Device 005: ID 054c:0155 Sony Corp- i'm not very sure though. it didn't say like namtai or eyetoy, but that was the closest thing:)

---

### Post by kyleskimskate on 2008-10-18
ok here is a screenshot of what im getting

---

### Post by Aearenda on 2008-10-19
That's the right USB detail line, and it confirms the type of camera you have. Searching using that USB identifier, this thread shows up: [http://ubuntuforums.org/showthread.php?t=272328](http://ubuntuforums.org/showthread.php?t=272328)

It suggests you may have a Jpeg decompression problem, or you may be simply expecting the wrong resolution from the camera. Sorting it out is a bit complex so let's take things step by step. 

We need to gather some more information to begin. First, do you have this camera working for any other Ubuntu apps, such as Ekiga?

Second, let's confirm what drivers your system has loaded for the camera - please copy this command and paste it into a Terminal window (as before) and then post the output using copy and paste:
```
lsmod | grep ov51
```

Third, let's see what vgrabbj says about it - post the output of this command (also run in a Terminal):
```
vgrabbj -s /dev/video0
```You might need to resize the window to see all the output.

Finally, in StopMotion, please go to Settings->Configure Stopmotion, click on the 'Video Import' Tab, click the 'Edit' button, drag the bottom of the window downwards to make the text in the three boxes near the bottom readable, and then post the contents of the 'Pre-poll' or 'Start deamon' line, whichever is set - most likely something like ```
vgrabbj -f $IMAGEFILE -d $VIDEODEVICE -b -D 0 -i cif -L250
```

---

### Post by kyleskimskate on 2008-10-19
First: yes, my camera is working in cheese. 
Seconds: The code spits out-ov51x_jpeg            156120  0 
videodev               29440  1 ov51x_jpeg
usbcore               146028  9 snd_usb_audio,snd_usb_lib,usb_storage,libusual,usbhid,ov51x_jpeg,ehci_hcd,uhci_hcd
Third: The code gives- vgrabbj, Version 0.9.6
Videodevice name: /dev/video0 (OV519 USB Camera)
Capabilities
Type     : 513	Values can be looked up at videodev.h
Channels : 1
Audio    : 0
MaxWidth : 640
MaxHeight: 480
MinWidth : 64
MinHeigth: 48

Current Settings:
Brightness: 32768
Hue       : 40960
Color     : 33792
Contrast  : 31744
Whiteness : 26880
Depth     : 12
Palette   : YUV420 (10)
Width     : 640
Height    : 480
Chromakey : 0
Fourth:-
dvgrab --format jpeg --jpeg-overwrite --jpeg-deinterlace --jpeg-width 640 --jpeg-height 480 --frames 25 $IMAGEFILE. 
Hope this helps!

---

### Post by Aearenda on 2008-10-19
Good - the driver looks right and works elsewhere, and the vgrabbj output shows the camera is capable of 640x480, which is what Stopmotion is trying to do.

More questions (unfortunately I don't have this camera so all we can do is try things until we figure it out):

1. Did you choose the DVgrab setting, or is that just what StopMotion had by default?


2. On the DVgrab setting you have quoted, what happens if you remove the --jpeg-deinterlace parameter, leaving the rest of the line as it is (by the way, I think the last character on the line after $IMAGEFILE should be '&', which causes the dvgrab command to start a new process alongside StopMotion). To test this, you can run the dvgrab command in a Terminal window like this:
```
dvgrab --format jpeg --jpeg-overwrite --jpeg-deinterlace --jpeg-width 640 --jpeg-height 480 --frames 25 test.jpg
```
This will tie up the terminal window while it is running, and you should stop it after a half a minute by pressing <CTRL> and c. Then take a look at the file test.jpg and see if it is jumbled up or not using ```
eog test.jpg
``` 

EDIT: I would be surprised if step 2 here works. It may be necessary to start another Terminal window and use ```
killall -9 dvgrab
```to get control back in the first window. It may also be necessary to add the -v4l2 -I /dev/video0 parameters for dvgrab, so that the command line in the terminal is now```
dvgrab -v4l2 -I /dev/video0 --format jpeg --jpeg-overwrite --jpeg-deinterlace --jpeg-width 640 --jpeg-height 480 --frames 25 test.jpg
```


3. What happens if you select either of the standard vgrabbj settings in StopMotion configuration? Again, you can test from a Terminal window, by running this command: ```
vgrabbj -f test.jpg -d /dev/video0 -i vga
```but this one will take one image and then stop; use eog to see if the image is any good.

---

### Post by kyleskimskate on 2008-10-19
First: the pre poll command was from Dv cam(experimental) setting
Second:That command gives-raw1394 - failed to get handle: No such file or directory.

Third:the code gives-Can't open "/dev/video0" as VideoDevice!
Fatal Error (non-daemon), exiting...
There was no map allocated to be freed...
Device /dev/video0 was already closed...
I don't know why. It runs video on cheese!:confused:

---

### Post by Aearenda on 2008-10-19
I suspect you should be using the vgrabbj daemon setting in StopMotion, not DVgrab. I only suggested trying that because it was apparently how you got the image you posted earlier. But let's leave that aside for the moment, and concentrate on your disappearing camera. In post 24, you said vgrabbj reported the camera on /dev/video0. Are you sure you hadn't left Cheese open, or some other program that was using the camera, when you tried step 3 in my post 25?

What does ```
ls -l /dev/vid*
``` show?

If you restart your computer with the camera plugged in, then run ```
vgrabbj -f test.jpg -d /dev/video0 -i vga
```what is the result?

If that fails to open /dev/video0, please run the 'ls' command above again, and see if the camera is now showing as /dev/video1 or something similar.

---

### Post by kyleskimskate on 2008-10-19
cheese wasn't open, terminal and firefox were the only things up.
The first code gives:crw-rw----+ 1 root video 81, 0 2008-10-19 08:45 /dev/video0
And how recent does the restart have to be? i restarted my computer about 9 this morning. I ran the second code and got: Reading image from /dev/video0
-and nothing else came up just went back to kyle@ykyle-desktop:~$:(
Ok ijustrestarted not and it gives the same thing

---

### Post by Aearenda on 2008-10-19
Good - the restart was only since the camera disappeared, so this morning's was ok - and the camera has reappeared, and vgrabbj has taken a picture successfully. 

Vgrabbj doesn't show you the picture, it just puts it in the named file - so if you run```
eog test.jpg
```what do you see?

---

### Post by kyleskimskate on 2008-10-19
i get this picture

---

### Post by Aearenda on 2008-10-19
So, the original image we saw in StopMotion most likely comes from an early test with vgrabbj.

1. Vgrabbj has a palette parameter that might help - please try this:```
vgrabbj -f test.jpg -d /dev/video0 -i vga -F 1 && eog test.jpg
```
This should take a picture and then show it if the picture was taken successfully, with the palette set to 1. There might be a message from vgrabbj saying it couldn't set the palette - but it will take a picture anyway in most cases.

Then repeat it for each number at the end of the line from 2 up to 17 (this comes from vgrabbj's help info). Do any of them look right?

2. You can also test with 'cif' or 'sif' substituted for 'vga' to see if smaller pictures have the same effect - like this:```
vgrabbj -f test.jpg -d /dev/video0 -i sif && eog test.jpg
```

3. Maybe the camera just wants to use its own resolution - so try 
```
vgrabbj -f test.jpg -d /dev/video0 -g && eog test.jpg
```

In the end, however, I suspect the problem is to do with the format of the image being returned - vgrabbj does not understand it properly. I'll do some research on this in the meantime.

---

### Post by kyleskimskate on 2008-10-19
yaaaaaayyyyy! that first code got a regular image! what now?

---

### Post by Aearenda on 2008-10-19
Great! Now we need to tell StopMotion to use those settings. I'm assuming here that when you said > that first code got a regular imageyou were using '-F 1' - if not, substitute the number that worked below, instead of '1'.

1. Start StopMotion and go to Settings->Configure StopMotion. 
2. Click on 'Video Import'
3. Click on the line that says 'vgrabbj VGA deamon'.
4. Click on the 'Edit' Button.
5. Drag the bottom of the dialogue box down so you can see the text in the bottom three boxes properly.
6. In the 'Start deamon' box, change it so that it reads like this:
```
vgrabbj -f $IMAGEFILE -d $VIDEODEVICE -D 0 -i vga -F 1 -L250
```
7. In the 'Stop deamon' box, make it read```
killall vgrabbj
```
8. Click 'Apply' and give it a test!

---

### Post by kyleskimskate on 2008-10-19
yay!!!!!!!!!!!!!!!!!!!!!!!!!!

---

### Post by kyleskimskate on 2008-10-19
thank you so much

---

### Post by Aearenda on 2008-10-19
You're welcome! By the way, at the bottom right of each post in the forum is a little icon that looks like a medal hanging off a red ribbon. That's how to register thanks for a useful post on the forum, if you want to!

I hope you enjoy StopMotion. I have found it a little unstable when using sound in the past, so make sure you save your work as you go.

---

### Post by kyleskimskate on 2008-10-19
dude i'm going to thank you so many times! thanx!

---

### Post by Aearenda on 2008-10-19
Just once will do! Have fun!

---

### Post by kyleskimskate on 2008-10-20
ok i need your genius for a few more things. sorry but i'm just so nub. can you help?

---

### Post by Aearenda on 2008-10-20
Depends on what it is - if a different topic (even if still on StopMotion) then a new thread is a good way to go, so that others see it too.

---

### Post by kyleskimskate on 2008-10-20
ok if your there, can you help me out with these issues?
In cinelerra, when i attempt to record, it crashes randomly either after or before i have started or stopped recording, and no image is coming up in the video in preview thing.
Also, when i try and do sound capture on either the sound recorder or audacity, it says for audacity: Error while opening sound device. Please check the input device settings and the project sample rate, and for sound recorder it says that the multimedia settings are wrong, so i went to system<prefs<sound< and tested the audio capture device and if works:confused:

---

### Post by kyleskimskate on 2008-10-20
ok so when i attempt to capture video on cinelerra, doesn't matter which input, nothing comes up on the video in, and i never import because it always crashes at the recording part. Don't know whats going on, video works on everything else.
Another issue I'm having is that when i try to open sound recorder or audacity, i either get Error while opening sound device. Please check the input device settings and the project sample rate, or it says that my multimedia setting are wrong. I went to system<preferences<sound and set the capture to my mic, and tested it, and it worked! It still says my settings are wrong though....:confused::confused:

---

### Post by Aearenda on 2008-10-21
I am afraid I have never used Cinelerra, so I definitely suggest you start a new thread for that. It wouldn't be appropriate to work on that in this thread anyway.

For Audacity, there are integration problems with the Pulse sound system in Hardy - lots of threads around on that - but according to [https://help.ubuntu.com/community/UbuntuStudio/Audio](https://help.ubuntu.com/community/UbuntuStudio/Audio) you could try starting audacity like this: ```
pasuspender -- audacity
``` 
If that doesn't work, then I suggest you use the forum search to find other ideas. Most of them suggest stopping Pulse one way or another. Again, that belongs in a separate thread really.

Good luck!

---

### Post by Johny_123 on 2008-10-21
:confused::confused:

---

### Post by kyleskimskate on 2008-10-21
whatcha mean johnny?

---

### Post by okey666 on 2008-10-27
I am also having problems with stopmotion.

my thread:[http://ubuntuforums.org/showthread.php?t=956338](http://ubuntuforums.org/showthread.php?t=956338)

After using your script my webcam started to work, but whenever I pressed the take image button stopmotion crashed (as you can see on the above thread). Thinking it was something with the script, I tried using a program called motion instead. (its great by the way, good framerate and loads of configuration options). Using motion I get a picture but it still crashes when I click the take photo button. (see full errors etc in thread above).

I used to grab (back in gutsy/fiesty) images using a dv-cam, but the quality etc was v.bad. I have never has this error before until I upgraded to Intrepid. In hardy, stopmotion just got a segmentation fault straight away.

Could you help me?

---

### Post by Aearenda on 2008-10-27
Thanks for the tip about motion, I'll give it a try. I'll reply further on your thread, rather than confuse this one further!

EDIT: Motion works with StopMotion, and is a good deal neater than my script above. I recommend anyone reading this thread to take a look at the Motion discussion in post 7 of okey666's thread at [http://ubuntuforums.org/showthread.php?t=956338](http://ubuntuforums.org/showthread.php?t=956338).

---

### Post by kyleskimskate on 2008-11-02
omg. aerenda! do you have intrepid ibex? stopmotion stopped working with it! i did this whole thread and its not working. btw if this helps, your picture test code gives me Unable to set supported video-palette
Fatal Error (non-daemon), exiting...
There was no map allocated to be freed...
in terminal, and it can't open with the eog test

---

### Post by Aearenda on 2008-11-03
I have a test installation of Intrepid, but as my laptop has an old nvidia graphics chip built in I can't upgrade properly until the legacy drivers are released. 

It sounds to me that your webcam driver has changed in Intrepid. This isn't StopMotion itself that is causing the problem. There are already several threads around about that kind of thing with webcams in Intrepid.

I suggest you try the following:
1. Unplug your webcam from the computer and wait a few moments.
2. Plug it back in again.
3. In a terminal do ```
dmesg | tail -20
```and post any relevant info about the camera.

---

### Post by kyleskimskate on 2008-11-03
This is what I think is info about the camera;'
[ 2532.072038] usb 1-2: reset high speed USB device using ehci_hcd and address 3
[ 5610.072038] usb 1-2: reset high speed USB device using ehci_hcd and address 3
[21392.076034] usb 1-2: reset high speed USB device using ehci_hcd and address 3
[32358.072037] usb 1-2: reset high speed USB device using ehci_hcd and address 3
[34350.152067] usb 2-1: USB disconnect, address 2
[34350.157466] gspca: disconnect complete
[34361.060024] usb 2-1: new full speed USB device using uhci_hcd and address 3
[34361.257360] usb 2-1: configuration #1 chosen from 1 choice
[34361.267358] gspca: probing 054c:0155
[34361.468067] ov519: I2C synced in 1 attempt(s)
[34361.468080] ov519: starting OV7xx0 configuration
[34361.481063] ov519: Sensor is an OV7648
[34361.510466] gspca: probe ok
[34361.511551] gspca: probing 054c:0155
I don't know if problem is maybe that it says ov519, and thats the stuff I have for my camera, but the sensor is read as ov7648. Idk, it may be not even relevant to that!:lolflag:

---

### Post by Aearenda on 2008-11-03
Nothing looking wrong there. I suggest you try the backported drivers mentioned in [http://ubuntuforums.org/showthread.php?t=966398](http://ubuntuforums.org/showthread.php?t=966398), and if that doesn't help try reading the threads that come up with a search for 'gspca intrepid'. Beyond that, all I can suggest is trying different palettes with the -F parameter on vgrabbj, but I guess you already tried that.

---

### Post by kyleskimskate on 2008-11-03
alrighty! thanx!

---

### Post by hbuch on 2008-12-02
> **Aearenda said:**
> I've made progress with this - enough to be happy with for now. Here's how to duplicate what I have done:

EDIT: There's a better way - see the Motion discussion in post 7 of okey666's thread [http://ubuntuforums.org/showthread.php?t=956338](http://ubuntuforums.org/showthread.php?t=956338).

1. Set up a script to start mplayer and to move the frames it creates, like this:
1.1 Start a terminal session
1.2 Type ```
gedit startmplayer
```
1.3 Paste this text into the file:```
#!/bin/bash
# Crude script to push mplayer frames from V4L2 camera to Stopmotion
# $1 is videodevice
# $2 is imagefile
# $3 is FPS captured
# $4 is loop delay
# $5 is folder to use

# Delete old files if any - leading 0 is just in case this is run in the home directory!
rm $5/0*.jpg

mplayer tv:// -tv driver=v4l2:device=$1:fps=$3:outfmt=rgb16 -fps $3 -quiet -really-quiet -vo jpeg:outdir=$5:optimize=100:quality=100 &

# cd to cut down overhead in loop
cd $5

while true ; do
  for FILE in 0*.jpg ; do
      if [ -s $FILE ] ; then 
	mv $FILE $2
      fi
  done
  sleep $4
done
```
1.4 Type the following command to make the file executable:
```
chmod u+x startmplayer
```
1.5 Create a hidden directory for the script to use where there will be no other JPEG files:
```
mkdir .tempjpgs
```
1.6 Close the terminal session

2. Tell Stopmotion how to use the script
2.1 Start Stopmotion and go to Settings->Configure Stopmotion
2.2 Select the "Video Import" tab
2.3 Click the "Add" button
2.4 Click on the now-highlighted empty row of the table, under the "Name" column
2.5 Type a name for the new entry - I used "Mplayer"
2.6 Press <TAB> and type a comment if you wish
2.7 Click the "Edit" button
2.8 Drag the bottom edge of the dialogue box down if the three text boxes are too squashed to see what you are typing properly.
2.9 In the "Start deamon" box type ```
./startmplayer $VIDEODEVICE $IMAGEFILE 2 0.25s .tempjpgs &
```
Here... 
 - the "./" characters tell Stopmotion to find the program in the current directory
 - $VIDEODEVICE and $IMAGEFILE are required to pass the camera name and target filename in from Stopmotion
 - "2" specifies that 2 frames per second should be processed (more on this later)
 - "0.25s" specifies that the script should sleep for a quarter of a second on each cycle (see later)
 - ".tempjpgs" tells the script the name of the folder created earlier.
 - "&" causes the command to be started in a separate process so that Stopmotion can do its work as well.

2.10 In the "Stop deamon" box type ```
killall startmplayer && killall mplayer
```
This makes sure that the capture processes are stopped properly.
2.11 Click "Apply" then "Close"

Now test it!

The script starts a second process for mplayer, which takes the webcam input using V4L2 and creates frames in the specified folder at the specified rate. These have a filename that is 8 digits long, incrementing by 1 for each frame. 
The script looks for files of non-zero size (which approximates to 'finished') and then moves it (or them) to the place where Stopmotion wants them. It then sleeps for the specified time so that the processor has chance to do other things. Thus each successive frame gets written over the previous one in the location where Stopmotion is watching - this is what vgrabbj does for V4L1 webcams. 

On my system this gives me a slow but usable capture system, with pictures of better quality than I was getting with my old V4L1 camera. There is a significant delay in the video on my 1GHz Pentium-M system, which is caused by the mplayer conversion process as well as my kludgy capture process I think. 

The frames-per-second and delay settings allow you to tune the script on your system simply by modifying the "Start deamon" setting in Stopmotion. I experimented with 1 frame per second and 0.5s, which was too unresponsive, and 3 frames with 0.1s, which loaded the processor too much, and settled on the settings I have given. Since this is an interpreted script, I don't recommend setting it to loop too fast! It isn't necessary anyway for stop motion work.

I hope this helps - if I find a better way I will add it to this thread. What we *really* need is for vgrabbj to become V4L2 aware, but it doesn't seem likely that this will happen.

PS: Stopmotion uses the spelling 'deamon' - I think it should be 'daemon' really but I've shown it how it is.
PPS: Just in case anyone thinks of it, yes, I tried dvgrab -V, and no, it doesn't work with my webcam.
PPPS: Yes, this is getting silly. It's late! I have tried the package 'webcam' but it doesn't seem to go faster than 1 frame per second. It's not so laggy though. I've also looked at luvcview (creates its own weird window) and webcamd (lacks documentation then tells me to RTFM when I ask it for help - how rude. Googling it suggests it's not going to be any use anyway).


EDIT: There's a better way - see the Motion discussion in post 7 of okey666's thread [http://ubuntuforums.org/showthread.php?t=956338](http://ubuntuforums.org/showthread.php?t=956338).

Hi,

I am happy to report that the above hack works GREAT!!!! THANK YOU Aearenda!!!!!! After MONTHS of struggling with Stopmotion, vgrabbj, and my Logitech QuickCam 9000 I was finally able to make a stopmotion film last night and export it to an mpeg 4 file. Again, THANK YOU!!!!!! I am looking forward to working with my 8 year old son on the final three episodes of Star Wars with action figure actors.

I totally recommend this hack. It was easy to implement because it was  explained it so well.

Heather Buch :p

---

### Post by Aearenda on 2008-12-02
I'm glad it worked for you! Did you try the Motion alternative in post 7 of okey666's thread [http://ubuntuforums.org/showthread.php?t=956338](http://ubuntuforums.org/showthread.php?t=956338) as well?

---

### Post by kyleskimskate on 2008-12-04
ok this is probably the most simple thing to solve ever... but w/e
when i try to install motion, the f-prot tries to install itself, but it cannot install... i get this
Setting up f-prot-installer (0.5.14) ...
dpkg: error processing f-prot-installer (--configure):
 subprocess post-installation script returned error exit status 30
Errors were encountered while processing:
 f-prot-installer
E: Sub-process /usr/bin/dpkg returned an error code (1)
i don't know if there is a new source to the file download, or intrepid needs a new way to install via terminal, but I just can't figure it out

---

### Post by Aearenda on 2008-12-05
It's because you have a previous failed installation, which will retry every time you install anything else. I think you could do ```
sudo apt-get remove f-prot-installer
```to sort things out for now. I suspect that package is just a wrapper that downloads f-prot from somewhere else, and it is failing for some reason.

---

### Post by kyleskimskate on 2008-12-05
ok i did that and now get this:
Package f-prot-installer is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package f-prot-installer has no installation candidate
????

---

### Post by Aearenda on 2008-12-05
I wouldn't claim to be an expert in this area, and google throws up many approaches to this problem. This really ought to be a new thread since it has nothing to do with the original title. There's probably a 'proper' way to fix this, but I don't know it.

BTW, did you download the f-prot-installer manually? It seems to be obsolete.

Here's what I would do, but if this blows up, don't blame me!

The error occurs because a previously installed package has failed during the post-installation phase. The post-installation procedure is repeated thereafter until it works, or until it is dealt with another way. So, we have to trick it into thinking it worked, and then remove it.

1. In a terminal, CD to the working directory:```
cd /var/lib/dpkg/info
```
2. Use 'ls' to find the postinst procedure for the f-prot-installer. It's probably called something like 'f-prot-installer.postinst' but then again...

3. Assuming it is called that, do ```
gksudo gedit f-prot-installer.postinst
```

4. At the beginning, there will probably be one line like this: '#!/bin/sh'. If there isn't, stop and tell me what is there.

5. After that line, there is probably a 'set -e'. Move the cursor below that line, or if it doesn't exists, just after the first line.

6. Insert a line containing just 'exit 0'.

7. Save the file and quit the editor.

8. Now get apt-get to sort things out, hopefully ```
sudo apt-get -f install
```

9. If that works, now try the remove command I gave before again, to get rid of the non-working package.

If this doesn't work, then we'll have to do some more research then go and work deeper inside the package management system using 'dpkg' itself.

---

### Post by kyleskimskate on 2008-12-08
well, i think this might be the problem....
when i do the gksudo gedit f-prot-installer.postinst
there is nothing in the document...
that may be a problem........:lolflag::guitar::confused:

---

### Post by Aearenda on 2008-12-09
Is there anything else in that folder with a name beginning with 'f-prot-installer'?

---

### Post by kyleskimskate on 2008-12-09
how do i get to that folder?

---

### Post by Aearenda on 2008-12-09
Steps 1 and 2 from post 57 - or just use nautilus (the file explorer) and go 'up' as far as you can, then navigate to /var then lib then dpkg then info. 

You never said where you got the f-prot-installer from - if I can get it from the same place, I might be able to help you better.

The issue here is making sure we delete f-prot-installer without causing any damage to things that need to stay working!

---

### Post by kyleskimskate on 2008-12-10
in the f-prot installer.list there is 
/etc
/etc/ppp
/etc/ppp/ip-up.d
/etc/ppp/ip-up.d/f-prot-installer
/etc/cron.d
/etc/cron.d/f-prot-installer
 the f-prot-installer.postrm doesn't run

---

### Post by Aearenda on 2008-12-10
Hmm, I was just after the list of files in /var/lib/dpkg/info with names starting with f-prot-installer - anyway, it sounds like the following might work, since the post-install and post remove files are corrupt:

1. In a terminal, CD to the working directory:```
cd /var/lib/dpkg/info
```

2. Edit the setup procedure: ```
gksudo gedit f-prot-installer.postinst
```

3. Insert the following:```
#!/bin/bash
exit 0
```

4. Save the file and exit gedit.

5. Do this in the terminal:
```
sudo cp f-prot-installer.postinst f-prot-installer.postrm
```

6. What we have done so far is to replace the post-installation and post-removal procedures, which seem to be empty, with ones that succeed in doing nothing. Next we need to attempt to complete the setup - do this in the terminal session: ```
sudo apt-get -f install
```Hopefully this will now report success - if not, please tell me what the error message was.

7. Assuming the previous step worked, next we should remove the non-functioning package - again in the terminal, do this:```
sudo apt-get remove f-prot-installer
```If that does not work, try ```
sudo dpkg -r f-prot-installer
```Please let me know what happens!

---

### Post by kyleskimskate on 2008-12-10
ok when i put in 
sudo cp f-prot-installer.postinst f-prot-installer.postrm
i get nothing coming up after i do all your steps. 
I kind of ignored that, and went on. When I do 
sudo dpkg -r f-prot-installer i get
 warning: ignoring request to remove f-prot-installer, only the config
 files of which are on the system.  Use --purge to remove them too.
......

---

### Post by kyleskimskate on 2008-12-10
whoa. hang on. my stuff installs now. but i can't run motion. even as root from terminal

---

### Post by Aearenda on 2008-12-10
Ok, so we have got rid of the failed f-prot installation - that's good.

The motion fail is a different issue. What error message does it give? Have you googled it?

---

### Post by kyleskimskate on 2008-12-10
no error message. Just nothing runs. This scrolls in terminal though:
[0] Processing thread 0 - config file /etc/motion/motion.conf
[0] Motion 3.2.9 Started
[0] ffmpeg LIBAVCODEC_BUILD 3355136 LIBAVFORMAT_BUILD 3409664
[0] Thread 1 is from /etc/motion/motion.conf
[1] Thread 1 started
[1] cap.driver: "ov519"
[1] cap.card: "EyeToy USB camera Namtai"
[1] cap.bus_info: "0000:00:10.0"
[1] cap.capabilities=0x05000001
[1] - VIDEO_CAPTURE
[1] - READWRITE
[1] - STREAMING
[1] Supported palettes:
[1] 0: JPEG (JPEG)
[1] Test palette JPEG (320x240)
[1] Using palette JPEG (320x240) bytesperlines 320 sizeimage 29390 colorspace 00000007
[1] found control 0x00980900, "Brightness", range 0,255 
[1] 	"Brightness", default 127, current 127
[1] found control 0x00980901, "Contrast", range 0,255 
[1] 	"Contrast", default 127, current 127
[1] found control 0x00980902, "Color", range 0,255 
[1] 	"Color", default 127, current 127
[1] mmap information:
[1] frames=4
[1] 0 length=32768
[1] 1 length=32768
[1] 2 length=32768
[1] 3 length=32768
[0] motion-httpd/3.2.9 running, accepting connections
[0] motion-httpd: waiting for data on port TCP 8080
[1] Using V4L2
[1] Started stream webcam server in port 8081
I wonder if this is realated at all to Kopete not running.... yea i get that message and nothing comes up. It all looks ok..

---

### Post by Aearenda on 2008-12-10
That looks to me like motion IS working as it is designed to. By default it creates a web server - which isn't what we want for StopMotion use. Have you seen the motion config file at [http://ubuntuforums.org/showpost.php?p=6042382&postcount=7](http://ubuntuforums.org/showpost.php?p=6042382&postcount=7)?

---

### Post by kyleskimskate on 2008-12-10
yea the code looks right.... it's just there is no box opening up for motion... Should there be?

---

### Post by Aearenda on 2008-12-11
No! It's just supposed to save the pictures in a spot where Stopmotion can find them, if you have it all set up as in that thread.

NOTE: You have to change the file save path - in the file it says 
```
target_dir /home/oscar/.stopmotion
```You should replace 'oscar' as appropriate!

---

### Post by kyleskimskate on 2008-12-11
oh. ok. I get it now. Thanks!

---

### Post by kyleskimskate on 2008-12-11
how do i change the file path? I put it into terminal and it doesn't work. God i wish i wasn't such a n00b sometimes

---

### Post by Aearenda on 2008-12-11
Everyone has to start somewhere! You can do this in a terminal:
```
gksudo gedit /etc/motion/motion.conf
```Then you should be able to find the line and change it, then save the file again. After that, stop motion if it is running, then start it again.

---

### Post by kyleskimskate on 2008-12-11
here? in these?
File path for motion triggered ffmpeg films (mpeg) relative to target_dir
# Default: %v-%Y%m%d%H%M%S
File path for timelapse mpegs relative to target_dir
# Default: %Y%m%d-timelapse
File path for motion triggered images (jpeg or ppm) relative to target_dir
# Default: %v-%Y%m%d%H%M%S-%q
File path for snapshots (jpeg or ppm) relative to target_dir
# Default: %v-%Y%m%d%H%M%S-snapshot
Paste where those weird symbols are?

---

### Post by Aearenda on 2008-12-11
No, not like that! Those are all 'relative to target_dir', and all you need to change is 'target_dir' itself. You just have to replace the word 'oscar' in the bit I quoted above with your username - so I would open the file for editing as in post 73, use CTRL/F to bring up the 'find' dialogue, enter 'oscar' as the text to search for, and that should bring up the line that looks like this: 'target_dir /home/oscar/.stopmotion'. Then change 'oscar' to your username, and save the file. As far as I recall that's the only change that is necessary, but I don't have it installed any more so I can't be entirely sure. You could repeat the search for 'oscar' after making the change just to check.

---

### Post by kyleskimskate on 2008-12-11
its says: Phrase not found

---

### Post by Aearenda on 2008-12-11
Ok, let's rewind a bit:
1. How did you install 'motion'? (e.g. from add/remove programs, synaptic package manager, or by compiling your own later version?)
2. Did you install the configuration file for use with Stopmotion posted in [http://ubuntuforums.org/showpost.php?p=6042382&postcount=7](http://ubuntuforums.org/showpost.php?p=6042382&postcount=7) ?
3. Do 'gksudo gedit /etc/motion/motion.conf' again, but instead of searching for 'oscar', look for the line that starts 'target_dir' and tell us what that line contains, please.

---

### Post by kyleskimskate on 2008-12-12
1: I did sudo apt-get install motion
2: No
3: It just comes up with those things i gave you asking if they were correct. (two posts before this one)
File path for motion triggered ffmpeg films (mpeg) relative to target_dir
# Default: %v-%Y%m%d%H%M%S
File path for timelapse mpegs relative to target_dir
# Default: %Y%m%d-timelapse
File path for motion triggered images (jpeg or ppm) relative to target_dir
# Default: %v-%Y%m%d%H%M%S-%q
File path for snapshots (jpeg or ppm) relative to target_dir
# Default: %v-%Y%m%d%H%M%S-snapshot

---

### Post by Aearenda on 2008-12-12
Ok, I had understood you to have followed the discussion on 'motion' above and to have installed the configuration file in the thread referred to. So, do this:

1. Get the compressed file attached to [http://ubuntuforums.org/showpost.php?p=6042382&postcount=7](http://ubuntuforums.org/showpost.php?p=6042382&postcount=7) and save it on your desktop.
2. Show your desktop, right-click on the downloaded file and choose 'extract here'.
3. In a terminal, do this:```
sudo mv Desktop/motion.conf /etc/motion/
```
4. In the terminal, do: ```
gksudo gedit /etc/motion/motion.conf
```
5. In Gedit, press CTRL/F and find the line that contains 'oscar'. It should look like this: > target_dir /home/oscar/.stopmotion
6. Change 'oscar' to your username and save the file.
7. In the terminal, just in case, do:```
sudo killall motion
```
8. Configure the Stopmotion 'deamon start' and 'stop' entries as shown in [http://ubuntuforums.org/showpost.php?p=6042382&postcount=7](http://ubuntuforums.org/showpost.php?p=6042382&postcount=7)
9. Assuming 'motion' is ok with your camera, I reckon it should now be working in Stopmotion! Please let us know how you got on.

---

### Post by kyleskimskate on 2008-12-12
so... now the stopmotion preview is going to work with the camera, or the motion pictures export to where stopmotion can import them. if they do export, where? the camera option is still blank on stopmotion

---

### Post by rhysjones_1 on 2008-12-12
ahh this is soo annoying!

---

### Post by kyleskimskate on 2008-12-12
well i'm sorry im' such a noob. would you care answering my question?

---

### Post by Aearenda on 2008-12-12
rhysjones_1: Persistence makes computers recognise their masters.

kyleskimskate: I just installed motion and stopmotion on my 8.10 system, followed the instructions above, and motion delivers images that stopmotion can use straight away. They show up on the Stopmotion window, I can capture them, and so on. The only thing I would change is to take the time and date stamp off in motion.conf. Remember that motion is meant to be a motion detector - there has to be some movement in the frame to trigger it to take a picture, but the removal of a hand should be enough. 

The /etc/motion/motion.conf file tells motion to save the pictures in /home/oscar/.stopmotion/capturedfile.jpg unless you change it - i.e. by replacing 'oscar' with your username, as I have explained, which should mean that the captured file is placed in the .stopmotion folder under your home directory. Try 'ls .stopmotion' in a terminal.

Stopmotion just polls that location for new pictures, and places them in its window once the 'camera on' button is pressed. That's all it ever does. Normally, you use vgrabbj to put the pictures there. The only reason to use motion instead is that it supports newer webcams than vgrabbj. Don't forget that you have to set the stopmotion settings to start motion and kill it, as described in okey666's post that I keep referring to. You can start motion in a separate terminal as you did before to see if it is complaining about anything.

---

### Post by Aearenda on 2008-12-12
I think rhysjones_1 meant the computer stuff is annoying, not you! Don't take it to heart.

Here's how to get rid of the timestamp:
```
gksudo gedit /etc/motion/motion.conf
```
1. Find the line that begins with 'text_right'
2. Make it look like this:```
text_right " "
```
3. Save the file

---

### Post by kyleskimskate on 2008-12-12
ok I tried ls .stopmotion and got this.
capturedfile.jpg  preferences.xml  preferences.xml.OLD
Stopmotion has like one frozen frame even if I move something. (Attached image) the lines are ok I think because xawtv has those and the image comes out fine. I have the start daemon as motion, stop daemon as killall motion, and i get this the whole time on screen

---

### Post by Aearenda on 2008-12-12
So, motion has deposited at least one image there - you can tell because the timestamp is showing. I would not be able to work with those lines on the screen! That indicates that the camera is sending a format that Stopmotion doesn't really understand, and maybe motion too - which would be why it can't detect any motion. Does the image look right if you do this: ```
eog ~/.stopmotion/capturedfile.jpg
```I expect it is all messed up there too.

Looking back, I see we had to set your webcam to 'vga' mode for vgrabbj in Hardy. The equivalent for motion is yet another edit of /etc/motion/motion.conf. Here we go:

1. In a terminal do```
gksudo gedit /etc/motion/motion.conf
```

2. Find line 70 that says 'width 320' and change '320' to '640'.

3. Below that, find line 73 that says 'height 240' and change '240' to '480'.

4. Save the file and try Stopmotion again.

It is possible that your camera and motion just aren't going to get along, particularly since you see the same corruption in other programs. Does Cheese still get it right?

---

### Post by kyleskimskate on 2008-12-13
dude you are genius. the image works, and when i move, the image updates! you have been thanked again! :):P:lolflag: w00t

---

### Post by Aearenda on 2008-12-13
No genius, just persistent. I'm glad it's working again - have fun!

---

### Post by rhysjones_1 on 2008-12-13
no I'm sorry 
i meant when this happens it's so annoying
happened me me a few months ago
didn't mean to offend

---

### Post by kyleskimskate on 2008-12-24
So would this be essentially the same thing in order to make the camera work with kopete? Or is that different thread material?:confused:

---

### Post by Aearenda on 2008-12-24
It's probably the same issue (setting the camera mode to 640x480 or 'VGA') but kopete would need to understand the camera driver itself, I don't think it could operate via an intermediate file - it needs to be much more fluid than stopmotion, by definition! I don't use kopete, sorry.

---

### Post by kyleskimskate on 2008-12-24
OK, so different thread material?

---

### Post by Aearenda on 2008-12-24
Yes - you need to use a title that will attract attention from someone who knows how to get kopete to adjust the camera settings.

---

### Post by michote on 2008-12-25
Hi I got a Quickcam 9000 Pro
I tried Aearenda's skript, wich works fine and very fast with 
```
./.stopmotion/startmplayer $VIDEODEVICE $IMAGEFILE 10 0.05s .tempjpgs &
```

I also tried motion (compiled newest version) and changed the conf file. but it's very slow and I've got a lot of grey boxes. Maybe it's because I'm taking 960x720 Images.

@Aearenda: Is it possible to take 960x720 images using Mplayer?

stopmotion (6.2, intrepid repros) seems to have a lot of problems writing its own preference.xml. I always get xml prasing errors at startup. does anyone know how to fix this?

EDIT: Mplayer doesn't work for me with 960x720, but I got motion working :D

---

### Post by Aearenda on 2008-12-25
Reading the output of 'man mplayer' it looks like you could try changing the mplayer parameters in the script, where it says > driver=v4l2:device=$1:fps=$3: outfmt=rgb16 so that it says > driver=v4l2:device=$1:fps=$3:width=960:height=720:outfmt=rgb16 but I can't promise this will work - I haven't tried it. Maybe that's what you already did. I suspect motion is the better solution, so maybe you should stick with that now it is working :-)

I suggest you attach (as a file, not inline) your preferences file here so we can see what is in it.

---

### Post by michote on 2008-12-26
Yes that's what I tried with Mplayer. I found it in a german [gentoo-wiki]("http://de.gentoo-wiki.com/wiki/Logitech_QuickCam_Pro_9000").
But the output is always 640x480.

my preference.xml is empty that's the problem. It seems to be a [bug]("https://bugs.launchpad.net/ubuntu/+source/stopmotion/+bug/300041").

---

### Post by Aearenda on 2008-12-26
I think you can grab the stopmotion source and compile the latest version for yourself to sort that out. Or, working from that bug, try this in a command line:```
env LC_ALL=C stopmotion
```

EDIT: What version of stopmotion do you have installed? 
See [http://developer.skolelinux.no/info/studentgrupper/2005-hig-stopmotion/index.php?side=3](http://developer.skolelinux.no/info/studentgrupper/2005-hig-stopmotion/index.php?side=3)

---

### Post by michote on 2008-12-26
using ```
env LC_ALL=C stopmotion
``` it works, and I set all the preferences I need.
now I set the preference.xml to readonly and I can use it in german.
a more or less useable workaround ;)

---

### Post by Katilyst666 on 2009-01-08
Okay, I just figured out how to use this basically. And it stopped working.

I get this error when i click the capture image Icon: "Grabbing failed. This May happen if you try to grab from an invalid device. Please check your grabber settings in the prefrences menu." 

I have a Creative (WebCam Live!)
```
vgrabbj, Version 0.9.6
Videodevice name: /dev/video0 (WebCam Live!   )
Capabilities
Type     : 1	Values can be looked up at videodev.h
Channels : 1
Audio    : 0
MaxWidth : 640
MaxHeight: 480
MinWidth : 48
MinHeigth: 32

Current Settings:
Brightness: 32896
Hue       : 0
Color     : 0
Contrast  : 32768
Whiteness : 39321
Depth     : 8
Palette   : (null) (0)
Width     : 320
Height    : 240
Chromakey : 0
roegge@Teh-Pirate:~$ 
```

I don't know what to do now & My bf says I have to fix. I'm a total noob & this is the first time I've ever used the terminal to try to fix anything. 

help please!

---

### Post by Aearenda on 2009-01-08
Ok, let's find out a bit more...

Are you saying it used to work and now it doesn't? Or that it never worked? 

Is it the same after a reboot?

Did you change anything that might have made it stop working?

When you reply, please click the button that says 'Go Advanced' and then use the 'paperclip' attachment button to attach the file 'preferences.xml' from the hidden '.stopmotion' folder in your home folder.

---

### Post by Katilyst666 on 2009-01-09
Well, I just figured out how to use the program. Now I'm trying to get the webcam to work with it. I tried the stuff you did in post #2 so on & so forth. followed your directions & I just think I messed up. & it still isn't working. 

Even after I rebooted it wouldn't work

before i tried this I just clicked the camera button & it was blank. So that's why I tried to follow your directions. :)  

I had to convert the .xml to a .txt so i could upload it.

---

### Post by Aearenda on 2009-01-09
Ok, so next we do indeed have to try something in a terminal window! But it shouldn't be too hard - and in fact the Linux command line is much easier than the Windows equivalent.

So, first start the terminal from Applications->Accessories->Terminal.

Next, copy this command from the browser, and then paste it in to the Terminal window using its edit menu:```
vgrabbj -f test.jpg -d /dev/video0 -i vga
```
If this produces an error message, copy it into your reply.

Next, type this: ```
eog test.jpg
```This displays the picture the previous command took, if it exists. Does it match where the camera was pointing at the time?

---

### Post by Light821 on 2009-01-09
[http://www.kolotibablo.com/?ref=422881](http://www.kolotibablo.com/?ref=422881) good money be sure !

---

### Post by Narasinha on 2009-04-21
Aearenda: Many many thanks for your mplayer script solution for v4l2 cameras in stopmotion. It was exactly what I needed in order to get my Logitech Quickcam Communicate MP to work.:popcorn:

---

### Post by Aearenda on 2009-04-21
I'm glad it helped! I wish there was a better way though.

---

### Post by dchurch24 on 2009-11-02
Hi, I know this is a bit of an old thread, but I am having the exact same problems as others here.

My webcam works fine in Cheese, just not in Stopmotion.

If I run:

```

vgrabbj -f test.jpg -d /dev/video0 -i vga -F 1 && eog test.jpg

```
I get...
```

Device doesn't support width/height
Fatal Error (non-daemon), exiting...
There was no map allocated to be freed...

```

The output from lsusb is:

```

Bus 002 Device 002: ID 093a:2468 Pixart Imaging, Inc. Cammaestro 2.5DU/X-EYE/Orite SC-120/ICGear TravelCam/Easy Snap Snake Eye Webcam

```

Any idea how to make this work? - I'm using Ubuntu 9.10.

EDIT: Wow, Stopmotion is really picky! ;-)
I've just tried it with this:

```

Bus 002 Device 006: ID 093a:2468 Pixart Imaging, Inc. Cammaestro 2.5DU/X-EYE/Orite SC-120/ICGear TravelCam/Easy Snap Snake Eye Webcam

```

and 

```

Bus 002 Device 007: ID 0471:0328 Philips SPC 700NC PC Camera

```

...and whilst both can be viewed using Cheese and Motion, neither work in Stopmotion :-(

---

### Post by Aearenda on 2009-11-02
> **dchurch24 said:**
> Hi, I know this is a bit of an old thread, but I am having the exact same problems as others here.

My webcam works fine in Cheese, just not in Stopmotion.
...

It may be an old thread, but still relevant (apart from the f-prot diversion). It's not Stopmotion itself being picky really, since it just relies on images being placed in a folder over and over. The problem is that most new cameras are supported only with Video4Linux2 drivers, and the vgrabbj utility only works with V4L version 1 drivers. I have not found an equivalent utility for V4L2, though I confess it is a while since I looked.

All is not lost, however - you should be able to use the mplayer script workaround detailed [earlier in this thread]("http://ubuntuforums.org/showpost.php?p=5869544&postcount=10"), or the 'motion' workaround [described in post 7 of another thread]("http://ubuntuforums.org/showthread.php?t=956338"), and further [discussed in this thread]("http://ubuntuforums.org/showpost.php?p=6353793&postcount=79"). Both of these work with V4L2 drivers. The 'motion' way is better, and I suggest you try that first. Let us know how you get on!

---

### Post by dchurch24 on 2009-11-03
Hi,

Thanks for your reply, much appreciated. 

Yeah, I figured that it wasn't really Stopmotions' fault - but after three webcams I was sort of giggling to myself!

I'd rather use motion as I like it and use it in quite a few places, so I am a bit more familiar with it than other solutions.

I tried to find a way to use it last night, but I could only find people saying "try using motion" - I had no idea how to!

I will read the links and report back.

Thank you once again! ;-)

---

### Post by dchurch24 on 2009-11-03
Bugger. Still not working.

Stopmotion starts but the moment I click on the Camera button, it hangs.

Motion is still going strong in the background as it fills my home folder with jpegs that can be viewed. 

It doesn't seem to stop motion from running and simply starts it and then it detects motion and off it goes.

I tried starting Stopmotion with "sudo stopmotion" but then I simply get a 

"segmentation fault" and then it doesn't start.

I am well and truly stuck.

Btw, I am running 9.10 64 bit - not sure if the 64 bit version is giving me the trouble.

---

### Post by Aearenda on 2009-11-03
You shouldn't run Stopmotion with sudo.

What settings are you using with Stopmotion? The easiest way to show me is to attach the file .stopmotion/preferences.xml, after renaming as .txt instead of .xml.

The reason I ask is that when you turn on capture, Stopmotion runs a specified command, and another when you turn it off. It's probably this command that is causing the hang. Often it's caused by missing a '&' at the end of the startup command to get the grab program running in a separate process.

While you're at it, attaching the Motion config as well wouldn't hurt.

Update:
I just installed Stopmotion and Motion on my Karmic system. The Motion conf file was set up without general read access, so I had to run 'sudo chmod 644 /etc/motion/motion.conf' before I could get motion to run.

I made the following changes to /etc/motion/motion.conf, leaving the rest of the settings as installed:```

# Number of frames to capture after motion is no longer detected (default: 0)
post_capture 10
#*Makes sure things have settled after the hands are out of the scene!

# Use ffmpeg to encode mpeg movies in realtime (default: off)
ffmpeg_cap_new off
#*In spite of the comment, it was on after installation.

# Draws the timestamp using same options as C function strftime(3)
# Default: %Y-%m-%d\n%T = date in ISO format and time in 24 hour clock
# Text is placed in lower right corner
; text_right %Y-%m-%d\n%T-%q
text_right \ 
# Note the space - it's '\<SPACE>' - I think " " should work as well.
#*This kills the timestamp in the picture.

# The mini-http server listens to this port for requests (default: 0 = disabled)
webcam_port 0
# This was on as installed. We don't need it.

# TCP/IP port for the http server to listen on (default: 0 = disabled)
control_port 0
# As previous.

# Command to be executed when a picture (.ppm|.jpg) is saved (default: none)
# To give the filename as an argument to a command append it with %f
on_picture_save mv %f /home/YOUR-USER-NAME/.stopmotion/capturedfile.jpg
# Puts a completed picture where stopmotion wants it. Also avoids generating hundreds of files.
# REPLACE <YOUR-USER-NAME> WITH YOUR USER NAME!

#*This is not a complete motion.conf file - leave the rest of the settings, replace only the ones named here!

```
I left /etc/default/motion as installed, which prevents Motion from running until I want it.

I added a new video import setting in Stopmotion configuration called 'Motion' with a suitable comment, then set the Pre-poll command to blank, the 'start deamon' command to 'motion &' and the 'stop deamon' command to 'killall motion'. Note that we are ignoring the filename and camera  parameters Stopmotion wants us to use, because these settings are encoded in motion.conf - it would be possible to automate everything, but I'm too lazy. It also occurs to me that I should really have made a local copy of motion.conf and edited that, telling Motion to use it as it starts up, rather than change the permissions on /etc/motion/motion.conf. I'm too lazy for that too.

This works for me, though the picture size is small - that can be adjusted in motion.conf.

---

### Post by dchurch24 on 2009-11-04
Ha ha - you are the Stopmotion GOD!

That worked a treat! 

I think it was the 644 that did it - I had setup a video import exactly as you specified yesterday, but it just hung.

Now with the 644 on the motion.conf it runs perectly (if a little slow - I can put up with that - I don't imagine making stop motion movies is a speedy exercise in any case ;-) )

Thank you so very much! It's people like yourself who make this community as successful as it is!

---

### Post by Aearenda on 2009-11-04
I'm glad it works for you! You are right about it being slow - but that's the best way with making movies this way, otherwise the result is nowhere near as smooth as it should be. Have fun!

---

### Post by dchurch24 on 2009-11-04
Thank you, I will.

You've just made my two daughters very happy - we're going to animate their toys this weekend now.

---

### Post by dchurch24 on 2009-11-08
Hi again,

Sorry to keep dredging this thread up.

My daughters and I made a short animation over this weekend using StopMotion - and even though I say so myself, it's surprisingly good!

The problem is that I can't export to any video format.

When I try to export I get this:

```

FFmpeg version git-aa02318, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-nonfree --enable-shared --enable-pthreads --enable-libx264 --enable-libfaac --enable-libtheora --extra-cflags=-fPIC --extra-cflags=-DPIC
  libavutil     50. 3. 0 / 50. 3. 0
  libavcodec    52.32. 0 / 52.32. 0
  libavformat   52.36. 0 / 52.36. 0
  libavdevice   52. 2. 0 / 52. 2. 0
  libswscale     0. 7. 1 /  0. 7. 1
  built on Jul 20 2009 01:11:25, gcc: 4.3.3
/home/dave/.stopmotion/packer/test/images/%06d.jpg: I/O error occurred
Usually that means that input file is truncated and/or corrupted.

```

I tried exporting with images created inside Stopmotion with my webcam, and also with imported files from my dslr. - I get that error either way.

The files are in that path (/packer/test/images etc...) - I thought it might be that a path variable was pointing in the wrong place, but it seems not.

---

### Post by Aearenda on 2009-11-08
I've only used mencoder before. I've had a go with ffmpeg just now, and unfortunately I haven't been able to recreate your problem. I only used a short sequence of webcam shots though.

The "%06d" in the filename indicates that Stopmotion is specifying a name consisting of a six-digit number with preceding zeroes to ffmpeg. The error suggests that ffmpeg can't find ANY files like that. Check the files in /home/dave/.stopmotion/packer/test/images to make sure they are named 000001.jpg, 000002.jpg, etc. This could be why it didn't work on your DSLR photos.

Have you altered the ffmpeg command in stopmotion preferences?
Mine has```
ffmpeg -r 10 -b 1800 -i "$IMAGEPATH/%06d.jpg" "$VIDEOFILE"
```What ffmpeg parameters are you using when you try to use your photos instead?

---

